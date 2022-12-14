# EnvironmentCallback

The **EnvironmentCallback** module provides the **onConfigurationUpdated** API for the application context to listen for system environment changes.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> The APIs of this module can be used only in the stage model.


## Modules to Import

```js
import EnvironmentCallback from "@ohos.application.EnvironmentCallback";
```


## EnvironmentCallback.onConfigurationUpdated

onConfigurationUpdated(config: Configuration): void;

Called when the system environment changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | config | [Configuration](js-apis-configuration.md) | Yes| **Configuration** object after the change.|

**Example**
    

  ```js
import AbilityStage from "@ohos.application.AbilityStage";

var callbackId;

export default class MyAbilityStage extends AbilityStage {
    onCreate() {
        console.log("MyAbilityStage onCreate")
        globalThis.applicationContext = this.context.getApplicationContext();
        let EnvironmentCallback  =  {
            onConfigurationUpdated(config){
                console.log("onConfigurationUpdated config:" + JSON.stringify(config));
            },
        }
        // 1. Obtain an applicationContext object.
        let applicationContext = globalThis.applicationContext;
        // 2. Register a listener for the environment changes through the applicationContext object.
        callbackId = applicationContext.registerEnvironmentCallback(EnvironmentCallback);
        console.log("registerEnvironmentCallback number: " + JSON.stringify(callbackId));
    }
    onDestroy() {
        let applicationContext = globalThis.applicationContext;
        applicationContext.unregisterEnvironmentCallback(callbackId, (error, data) => {
            console.log("unregisterEnvironmentCallback success, err: " + JSON.stringify(error));
        });
    }
}
  ```
