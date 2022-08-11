# DataShare Development
The **DataShare** module allows an application to manage its own data and share data with other applications. Currently, data can be shared only between the applications on the same device.

## Available APIs

**Table 1** APIs of the data provider

|API|Description|
|:------|:------|
|onCreate?(want: Want, callback: AsyncCallback&lt;void&gt;): void|Called to initialize service logic when the data provider application is created, for example, when a database is created.|
|insert?(uri: string, valueBucket: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void|Inserts data into the database.|
|update?(uri: string, predicates: DataSharePredicates, valueBucket: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void|Updates data in the database.|
|query?(uri: string, predicates: DataSharePredicates, columns: Array&lt;string&gt;, callback: AsyncCallback&lt;Object&gt;): void|Queries data from the database.|
|delete?(uri: string, predicates: DataSharePredicates, callback: AsyncCallback&lt;number&gt;): void|Deletes data from the database.|

For more details, see [DataShareExtensionAbility](../reference/apis/js-apis-application-DataShareExtensionAbility.md).

**Table 2** APIs of the data consumer

| API                                                      | Description                              |
| :----------------------------------------------------------- | :--------------------------------- |
| createDataShareHelper(context: Context, uri: string, callback: AsyncCallback&lt;DataShareHelper&gt;): void | Creates a **DataShareHelper** instance.             |
| insert(uri: string, value: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void | Inserts a single data record into the database.        |
| update(uri: string, predicates: DataSharePredicates, value: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void | Updates data in the database.          |
| query(uri: string, predicates: DataSharePredicates, columns: Array&lt;string&gt;, callback: AsyncCallback&lt;DataShareResultSet&gt;): void | Queries data from the database.              |
| delete(uri: string, predicates: DataSharePredicates, callback: AsyncCallback&lt;number&gt;): void | Deletes one or more data records from the database.|

For more details, see [DataShareHelper](../reference/apis/js-apis-data-dataShare.md).

## When to Use

**DataShare** can be divided into the following: 

- Data provider: Implement functions of adding, deleting, modifying, and querying data, and opening files, and share data.
- Data consumer: Access the data provided by the provider using **DataShareHelper**.

Examples are given below.

### Data Provider Application Development (Only for System Applications)

1. Import the dependencies.

   ```ts
   import Extension from '@ohos.application.DataShareExtensionAbility'
   import rdb from '@ohos.data.rdb';
   import fileIo from '@ohos.fileio'
   import dataSharePredicates from '@ohos.data.dataSharePredicates'
   ```

2. Override **DataShareExtensionAbility** APIs based on actual requirements. For example, if the data provider provides only data query, override only the query() API.

3. Implement the data provider services. For example, implement data storage of the data provider by using a database, reading and writing files, or accessing the network.

   ```ts
   let DB_NAME = "DB00.db";
   let TBL_NAME = "TBL00";
   let DDL_TBL_CREATE = "CREATE TABLE IF NOT EXISTS "
   + TBL_NAME
   + " (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, age INTEGER, isStudent BOOLEAN, Binary BINARY)";
   
   let rdbStore;
   let result;
   
   export default class DataShareExtAbility extends Extension {
       private rdbStore_;
       
   	// Override the onCreate() API.
       onCreate(want, callback) {
           result = this.context.cacheDir + '/datashare.txt'
           // Create an RDB.
           rdb.getRdbStore(this.context, {
               name: DB_NAME
           }, 1, function (err, data) {
               rdbStore = data;
               rdbStore.executeSql(DDL_TBL_CREATE, [], function (err) {
                   console.log('DataShareExtAbility onCreate, executeSql done err:' + JSON.stringify(err));
               });
               callback();
           });
       }
   
   	// Override the query() API.
       query(uri, predicates, columns,  callback) {
           if (predicates == null || predicates == undefined) {
               console.info('invalid predicates');
           }
           try {
               rdbStore.query(TBL_NAME, predicates, columns, function (err, resultSet) {
                   if (resultSet != undefined) {
                       console.info('resultSet.rowCount: ' + resultSet.rowCount);
                   }
                   if (callback != undefined) {
                       callback(err, resultSet);
                   }
               });
           } catch (err) {
               console.error('error' + err);
           }
       }
       // Override other APIs as required.
       // ...
   };
   ```

4. Define **DataShareExtensionAbility** in **module.json5**.

   | Field| Description                                                    |
   | ------------ | ------------------------------------------------------------ |
   | "name"       | Ability name, corresponding to the **ExtensionAbility** class name derived from **Ability**.        |
   | "type"       | Ability type. The value is **dataShare**, indicating the development is based on the **Datashare** template.|
   | "uri"        | URI used for communication. It is the unique identifier for the client to connect to the server.               |
   | "visible"    | Whether it is visible to other applications. Communication with other applications is allowed only when the value is **true**.|

   **module.json5 example**

   ```json
   "extensionAbilities": [
     {
       "srcEntrance": "./ets/DataShareExtAbility/DataShareExtAbility.ts",
       "name": "DataShareExtAbility",
       "icon": "$media:icon",
       "description": "$string:description_datashareextability",
       "type": "dataShare",
       "uri": "datashare://com.samples.datasharetest.DataShare",
       "visible": true
     }
   ]
   ```

### Data Consumer Application Development

1. Import basic dependencies.

   ```ts
   import Ability from '@ohos.application.Ability'
   import dataShare from '@ohos.data.dataShare'
   import dataSharePredicates from '@ohos.data.dataSharePredicates'
   ```
   
2. Define the URI string for communicating with the data provider.

   ```ts
   // Different from the URI defined in the module.json5 file, the URI passed in the parameter has an extra slash (/), because there is a DeviceID parameter between the second and the third slash (/).
   let dseUri = ("datashare:///com.samples.datasharetest.DataShare");
   ```
   
2. Create a **DataShareHelper** instance.

   ```ts
   let dsHelper;
   let abilityContext;
   export default class MainAbility extends Ability {
   	onWindowStageCreate(windowStage) {
   		abilityContext = this.context;
   		dataShare.createDataShareHelper(abilityContext, dseUri, (err,data)=>{
   			dsHelper = data;
   		});
   	}
   }
   ```
   
3. Use the APIs provided by **DataShareHelper** to access the services provided by the provider, for example, adding, deleting, modifying, and querying data.

   ```ts
   // Construct a piece of data.
   var valuesBucket = {"name": "ZhangSan", "age": 21, "isStudent": false, "Binary": new Uint8Array([1,2,3])};
   var updateBucket = {"name": "LiSi", "age": 18, "isStudent": true, "Binary": new Uint8Array([1,2,3])};
   let da =  new dataSharePredicates.DataSharePredicates();
   var valArray =new Array("*");
   let people = new Array(
   	{"name": "LiSi", "age": 41, "Binary": ar},
   	{"name": "WangWu", "age": 21, "Binary": arr},
   	{"name": "ZhaoLiu", "age": 61, "Binary": arr});
   // Insert a piece of data.
   dsHelper.insert(dseUri, valuesBucket, (err,data) => {
       console.log("dsHelper insert result: " + data);
   });
   // Delete the specified data.
   dsHelper.delete(dseUri, da, (err,data) => {
       console.log("dsHelper delete result: " + data);
   });
   // Update data.
   dsHelper.update(dseUri, da, updateBucket, (err,data) => {
       console.log("dsHelper update result: " + data);
   });
   // Query data.
   dsHelper.query(dseUri, da, valArray, (err,data) => {
       console.log("dsHelper query result: " + data);
   });
   ```
   