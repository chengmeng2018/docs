# 首选项

首选项为应用提供Key-Value键值型的数据处理能力，支持应用持久化轻量级数据，并对其修改和查询。

数据存储形式为键值对，键的类型为字符串型，值的存储数据类型包括数字型、字符型、布尔型以及这3种类型的数组类型。


> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```js
import data_preferences from '@ohos.data.preferences';
```

## 常量

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

| 名称             | 参数类型 | 可读 | 可写 | 说明                                    |
| ---------------- | -------- | ---- | ---- | --------------------------------------- |
| MAX_KEY_LENGTH   | string   | 是   | 否   | Key的最大长度限制，需小于80个字节。     |
| MAX_VALUE_LENGTH | string   | 是   | 否   | Value的最大长度限制，需小于8192个字节。 |


## data_preferences.getPreferences

getPreferences(context: Context, name: string, callback: AsyncCallback&lt;Preferences&gt;): void

读取指定首选项持久化文件，将数据加载到Preferences实例，用于数据操作，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                                             | 必填 | 说明                                                         |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| context  | [Context](js-apis-ability-context.md)            | 是   | 应用上下文。                                                 |
| name     | string                                           | 是   | 应用程序内部数据存储名称。                                   |
| callback | AsyncCallback&lt;[Preferences](#preferences)&gt; | 是   | 回调函数。当获取Preferences实例成功，err为undefined，object为获取的Preferences实例；否则err为错误码。 |

**示例：**

```js
var preferences = null;
data_preferences.getPreferences(this.context, 'mystore', function (err, object) {
    if (err) {
        console.info("Failed to get preferences. Cause: " + err);
        return;
    }
    preferences = object;
    console.info("Succeeded in getting preferences.");
})
```


## data_preferences.getPreferences

getPreferences(context: Context, name: string): Promise&lt;Preferences&gt;

读取指定首选项持久化文件，将数据加载到Preferences实例，用于数据操作，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名  | 类型                                  | 必填 | 说明                       |
| ------- | ------------------------------------- | ---- | -------------------------- |
| context | [Context](js-apis-ability-context.md) | 是   | 应用上下文。               |
| name    | string                                | 是   | 应用程序内部数据存储名称。 |

**返回值：**
| 类型                                       | 说明                               |
| ------------------------------------------ | ---------------------------------- |
| Promise&lt;[Preferences](#preferences)&gt; | Promise对象，返回Preferences实例。 |

**示例：**

```js
var preferences = null;
let promise = data_preferences.getPreferences(this.context, 'mystore')
promise.then((object) => {
    preferences = object;
    console.info("Succeeded in getting preferences.");
}).catch((err) => {
    console.info("Failed to get preferences. Cause: " + err);
})
```


## data_preferences.deletePreferences

deletePreferences(context: Context, name: string, callback: AsyncCallback&lt;void&gt;): void

从内存中移除指定首选项持久化文件对应的Preferences单实例，并删除指定文件及其备份文件和损坏文件，使用callback异步回调。

删除指定首选项持久化文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                                  | 必填 | 说明                                                 |
| -------- | ------------------------------------- | ---- | ---------------------------------------------------- |
| context  | [Context](js-apis-ability-context.md) | 是   | 应用上下文。                                         |
| name     | string                                | 是   | 应用程序内部数据存储名称。                           |
| callback | AsyncCallback&lt;void&gt;             | 是   | 回调函数。当移除成功，err为undefined，否则为错误码。 |

**示例：**
```js
data_preferences.deletePreferences(this.context, 'mystore', function (err) {
    if (err) {
        console.info("Failed to delete preferences. Cause: " + err);
        return
    }
    console.info("Succeeded in deleting preferences." );
})
```


## data_preferences.deletePreferences

deletePreferences(context: Context, name: string): Promise&lt;void&gt;

从内存中移除指定首选项持久化文件对应的Preferences单实例，并删除指定文件及其备份文件和损坏文件，使用Promise异步回调。

删除指定首选项持久化文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名  | 类型                                  | 必填 | 说明                       |
| ------- | ------------------------------------- | ---- | -------------------------- |
| context | [Context](js-apis-ability-context.md) | 是   | 应用程序或功能的上下文。   |
| name    | string                                | 是   | 应用程序内部数据存储名称。 |

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = data_preferences.deletePreferences(this.context, 'mystore')
promise.then(() => {
    console.info("Succeeded in deleting preferences.");
}).catch((err) => {
    console.info("Failed to delete preferences. Cause: " + err);
})
```


## data_preferences.removePreferencesFromCache

removePreferencesFromCache(context: Context, name: string, callback: AsyncCallback&lt;void&gt;): void

从内存中移除指定首选项持久化文件对应的Preferences单实例，使用callback异步回调。

移除Preferences单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                                  | 必填 | 说明                                                 |
| -------- | ------------------------------------- | ---- | ---------------------------------------------------- |
| context  | [Context](js-apis-ability-context.md) | 是   | 应用程序或功能的上下文。                             |
| name     | string                                | 是   | 应用程序内部数据存储名称。                           |
| callback | AsyncCallback&lt;void&gt;             | 是   | 回调函数。当移除成功，err为undefined，否则为错误码。 |

**示例：**
```js
data_preferences.removePreferencesFromCache(this.context, 'mystore', function (err) {
    if (err) {
        console.info("Failed to remove preferences. Cause: " + err);
        return;
    }
    console.info("Succeeded in removing preferences.");
})
```


## data_preferences.removePreferencesFromCache

removePreferencesFromCache(context: Context, name: string): Promise&lt;void&gt;

从内存中移除指定首选项持久化文件对应的Preferences单实例，使用Promise异步回调。

移除Preferences单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名  | 类型                                  | 必填 | 说明                       |
| ------- | ------------------------------------- | ---- | -------------------------- |
| context | [Context](js-apis-ability-context.md) | 是   | 应用程序或功能的上下文。   |
| name    | string                                | 是   | 应用程序内部数据存储名称。 |

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = data_preferences.removePreferencesFromCache(this.context, 'mystore')
promise.then(() => {
    console.info("Succeeded in removing preferences.");
}).catch((err) => {
    console.info("Failed to remove preferences. Cause: " + err);
})
```


## Preferences

存储实例，提供获取和修改存储数据的接口。

下列接口都需先使用[data_preferences.getPreferences](#data_preferencesgetpreferences)获取到Preferences实例，再通过此实例调用对应接口。


### get

get(key: string, defValue: ValueType, callback: AsyncCallback&lt;ValueType&gt;): void

获取键对应的值，如果值为null或者非默认值类型，返回默认数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                                         | 必填 | 说明                                                         |
| -------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| key      | string                                       | 是   | 要获取的存储Key名称，不能为空。                              |
| defValue | [ValueType](#valuetype)                      | 是   | 默认返回值。支持number、string、boolean、Array\<number>、Array\<string>、Array\<boolean>类型。 |
| callback | AsyncCallback&lt;[ValueType](#valuetype)&gt; | 是   | 回调函数。当获取成功时，err为undefined，data为键对应的值；否则err为错误码。 |

**示例：**

```js
preferences.get('startup', 'default', function(err, data) {
    if (err) {
        console.info("Failed to get value of 'startup'. Cause: " + err);
        return;
    }
    console.info("Succeeded in getting value of 'startup'. Data： " + data);
})
```


### get

get(key: string, defValue: ValueType): Promise&lt;ValueType&gt;

获取键对应的值，如果值为null或者非默认值类型，返回默认数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

 **参数：**
| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| key      | string                  | 是   | 要获取的存储Key名称，不能为空。                              |
| defValue | [ValueType](#valuetype) | 是   | 默认返回值。支持number、string、boolean、Array\<number>、Array\<string>、Array\<boolean>类型。 |

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| Promise<[ValueType](#valuetype)&gt; | Promise对象，返回键对应的值。 |

**示例：**
```js
let promise = preferences.get('startup', 'default');
promise.then((data) => {
    console.info("Succeeded in getting value of 'startup'. Data: " + data);
}).catch((err) => {
    console.info("Failed to get value of 'startup'. Cause: " + err);
})
```

### getAll

getAll(callback: AsyncCallback&lt;Object&gt;): void;

获取含有所有键值的Object对象。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Object&gt; | 是   | 回调函数。当获取成功，err为undefined，value为含有所有键值的Object对象；否则err为错误码。 |

**示例：**

```js
preferences.getAll(function (err, value) {
    if (err) {
        console.info("Failed to get all key-values. Cause: " + err);
        return;
    }
    let allKeys = Object.keys(value);
    console.info("getAll keys = " + allKeys);
    console.info("getAll object = " + JSON.stringify(value));
});
```


### getAll

getAll(): Promise&lt;Object&gt;

获取含有所有键值的Object对象。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**
| 类型                  | 说明                                        |
| --------------------- | ------------------------------------------- |
| Promise&lt;Object&gt; | Promise对象，返回含有所有键值的Object对象。 |

**示例：**
```js
let promise = preferences.getAll();
promise.then((value) => {
    let allKeys = Object.keys(value);
    console.info('getAll keys = ' + allKeys);
    console.info("getAll object = " + JSON.stringify(value));
}).catch((err) => {
    console.info("Failed to get all key-values. Cause: " + err);
})
```

### put

put(key: string, value: ValueType, callback: AsyncCallback&lt;void&gt;): void

将数据写入Preferences实例，可通过[flush](#flush)将Preferences实例持久化，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                      | 必填 | 说明                                                         |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| key      | string                    | 是   | 要修改的存储的Key，不能为空。                                |
| value    | [ValueType](#valuetype)   | 是   | 存储的新值。支持number、string、boolean、Array\<number>、Array\<string>、Array\<boolean>类型。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当数据写入成功，err为undefined；否则为错误码。     |

**示例：**
```js
preferences.put('startup', 'auto', function (err) {
    if (err) {
        console.info("Failed to put value of 'startup'. Cause: " + err);
        return;
    }
    console.info("Succeeded in putting value of 'startup'.");
})
```


### put

put(key: string, value: ValueType): Promise&lt;void&gt;

将数据写入Preferences实例，可通过[flush](#flush)将Preferences实例持久化，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名 | 类型                    | 必填 | 说明                                                         |
| ------ | ----------------------- | ---- | ------------------------------------------------------------ |
| key    | string                  | 是   | 要修改的存储的Key，不能为空。                                |
| value  | [ValueType](#valuetype) | 是   | 存储的新值。支持number、string、boolean、Array\<number>、Array\<string>、Array\<boolean>类型。 |

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = preferences.put('startup', 'auto');
promise.then(() => {
    console.info("Succeeded in putting value of 'startup'.");
}).catch((err) => {
    console.info("Failed to put value of 'startup'. Cause: " + err));
})
```


### has

has(key: string, callback: AsyncCallback&lt;boolean&gt;): void

检查存储对象是否包含名为给定Key的存储键值对，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                         | 必填 | 说明                                                         |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| key      | string                       | 是   | 要检查的存储key名称，不能为空。                              |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。返回存储对象是否包含给定key的存储键值对，true表示存在，false表示不存在。 |

**示例：**
```js
preferences.has('startup', function (err, isExist) {
    if (err) {
        console.info("Failed to check the key 'startup'. Cause: " + err);
        return;
    }
    if (isExist) {
        console.info("The key 'startup' is contained.");
    } else {
        console.info("The key 'startup' dose not contain.");
    }
})
```


### has

has(key: string): Promise&lt;boolean&gt;

检查存储对象是否包含名为给定Key的存储键值对，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | 是   | 要检查的存储key名称，不能为空。 |

**返回值：**
| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回存储对象是否包含给定key的存储键值对，true表示存在，false表示不存在。 |

**示例：**

```js
let promise = preferences.has('startup');
promise.then((isExist) => {
    if (isExist) {
        console.info("The key 'startup' is contained.");
    } else {
        console.info("The key 'startup' dose not contain.");
    }
}).catch((err) => {
    console.info("Failed to check the key 'startup'. Cause: " + err);
})
```


### delete

delete(key: string, callback: AsyncCallback&lt;void&gt;): void

从存储对象中删除名为给定Key的存储键值对，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                      | 必填 | 说明                                                 |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| key      | string                    | 是   | 要删除的存储Key名称，不能为空。                      |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当删除成功，err为undefined；否则为错误码。 |

**示例：**
```js
preferences.delete('startup', function (err) {
    if (err) {
        console.info("Failed to delete the key 'startup'. Cause: " + err);
        return;
    }
    console.info("Succeeded in deleting the key 'startup'.");
})
```


### delete

delete(key: string): Promise&lt;void&gt;

从存储对象删除名为给定Key的存储键值对，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | 是   | 要删除的存储key名称，不能为空。 |

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = preferences.delete('startup');
promise.then(() => {
    console.info("Succeeded in deleting the key 'startup'.");
}).catch((err) => {
    console.info("Failed to delete the key 'startup'. Cause: " + err);
})
```


### flush

flush(callback: AsyncCallback&lt;void&gt;): void

将当前preferences对象中的修改保存到当前的preferences，并异步存储到首选项持久化文件中，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                      | 必填 | 说明                                                 |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当保存成功，err为undefined；否则为错误码。 |

**示例：**
```js
preferences.flush(function (err) {
    if (err) {
        console.info("Failed to flush. Cause: " + err);
        return;
    }
    console.info("Succeeded in flushing.");
})
```


### flush

flush(): Promise&lt;void&gt;

将当前preferences对象中的修改保存到当前的preferences，并异步存储到首选项持久化文件中，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = preferences.flush();
promise.then(() => {
    console.info("Succeeded in flushing.");
}).catch((err) => {
    console.info("Failed to flush. Cause: " + err);
})
```


### clear

clear(callback: AsyncCallback&lt;void&gt;): void

清除此存储对象中的所有存储，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                      | 必填 | 说明                                                 |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当清除成功，err为undefined；否则为错误码。 |

**示例：**
```js
preferences.clear(function (err) {
    if (err) {
        console.info("Failed to clear. Cause: " + err);
        return;
    }
    console.info("Succeeded in clearing.");
})
```


### clear

clear(): Promise&lt;void&gt;

清除此存储对象中的所有存储，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**
| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**
```js
let promise = preferences.clear()
promise.then(() => {
    console.info("Succeeded in clearing.");
}).catch((err) => {
    console.info("Failed to clear. Cause: " + err);
})
```


### on('change')

on(type: 'change', callback: Callback&lt;{ key : string }&gt;): void

订阅数据变更，订阅的Key的值发生变更后，在执行[flush](#flush)方法后，触发callback回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                             | 必填 | 说明                                     |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| type     | string                           | 是   | 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;{ key : string }&gt; | 是   | 回调对象实例。                           |

**示例：**
```js
data_preferences.getPreferences(this.context, 'mystore', function (err, preferences) {
    if (err) {
        console.info("Failed to Gget preferences.");
        return;
    }
    var observer = function (key) {
        console.info("The key " + key + " changed.");
    }
    preferences.on('change', observer);
    preferences.put('startup', 'auto', function (err) {
        if (err) {
            console.info("Failed to put the value of 'startup'. Cause: " + err);
            return;
        }
        console.info("Succeeded in putting the value of 'startup'.");

        preferences.flush(function (err) {
            if (err) {
                console.info("Failed to flush. Cause: " + err);
                return;
            }
            console.info("Succeeded in flushing."); // observer will be called.
        })
    })
})
```


### off('change')

off(type: 'change', callback?: Callback&lt;{ key : string }&gt;): void

取消订阅数据变更，订阅的Key的值发生变更后，在执行[flush](#flush)方法后，触发callback回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名   | 类型                             | 必填 | 说明                                       |
| -------- | -------------------------------- | ---- | ------------------------------------------ |
| type     | string                           | 是   | 事件类型，固定值'change'，表示数据变更。   |
| callback | Callback&lt;{ key : string }&gt; | 否   | 需要取消的回调对象实例，不填写则全部取消。 |

**示例：**
```js
data_preferences.getPreferences(this.context, 'mystore', function (err, preferences) {
    if (err) {
        console.info("Failed to Gget preferences.");
        return;
    }
    var observer = function (key) {
        console.info("The key " + key + " changed.");
    }
    preferences.on('change', observer);
    preferences.put('startup', 'auto', function (err) {
        if (err) {
            console.info("Failed to put the value of 'startup'. Cause: " + err);
            return;
        }
        console.info("Succeeded in putting the value of 'startup'.");

        preferences.flush(function (err) {
            if (err) {
                console.info("Failed to flush. Cause: " + err);
                return;
            }
            console.info("Succeeded in flushing."); // observer will be called.
        })
        preferences.off('change', observer);
    })
})
```

## ValueType

用于表示允许的数据字段类型。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

| 类型            | 说明                           |
| --------------- | ------------------------------ |
| number          | 表示值类型为数字。             |
| string          | 表示值类型为字符串。           |
| boolean         | 表示值类型为布尔值。           |
| Array\<number>  | 表示值类型为数字类型的数组。   |
| Array\<boolean> | 表示值类型为布尔类型的数组。   |
| Array\<string>  | 表示值类型为字符串类型的数组。 |