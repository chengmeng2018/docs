# Bundle.bundleMonitor模块(JS端sdk接口)

本模块提供监听应用安装，卸载，更新的能力。

> **说明：** 
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```javascript
import bundleMonitor from '@ohos.bundle.bundleMonitor';
```

## 权限列表

| 权限                                 | 权限等级    | 描述                           |
| ------------------------------------ | ----------- | ------------------------------ |
| ohos.permission.LISTEN_BUNDLE_CHANGE | system_core | 可监听应用的安装，卸载，更新。 |

权限等级参考[权限等级说明]([zh-cn/application-dev/security/accesstoken-overview.md · OpenHarmony/docs - Gitee.com](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/security/accesstoken-overview.md))

## BundleChangeInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

系统接口：为系统接口，三方应用不可调用

| 名称       | 类型   | 可读 | 可写 | 说明                       |
| ---------- | ------ | ---- | ---- | -------------------------- |
| bundleName | string | 是   | 否   | 应用状态发生变化的应用包名 |
| userId     | number | 是   | 否   | 应用状态发生变化的用户id   |

## bundleMonitor.on

on(type: BundleChangedEvent, callback: Callback\<BundleChangedInfo>): void;

注册监听应用的安装，卸载，更新。

**需要权限：**ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**此接口为系统接口

**系统能力：**SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名                       | 类型     | 必填 | 描述               |
| ---------------------------- | -------- | ---- | ------------------ |
| BundleChangedEvent           | string   | 是   | 注册监听的事件类型 |
| Callback\<BundleChangedInfo> | callback | 是   | 注册监听的回调函数 |

**相关错误码**

| 错误码 | 错误信息（此处仅提供错误抛出的关键信息） |
| ------ | ---------------------------------------- |
| 201    | Permission denied.                       |
| 401    | The parameter check failed.              |

**示例：**

```js
import bundleMonitor from '@ohos.bundle.bundleMonitor';

try {
    bundleMonitor.on('add', (bundleChangeInfo) => {
        console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
	})
} catch (errData) {
    console.log(`errData is errCode:${errData.errCode}  message:${errData.message}`);
}
```

## bundleMonitor.off

off(type: BundleChangedEvent, callback?: Callback\<BundleChangedInfo>): void;

注销监听应用的安装，卸载，更新。

**需要权限：**ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**此接口为系统接口

**系统能力：**SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名                       | 类型     | 必填 | 描述                                                       |
| ---------------------------- | -------- | ---- | ---------------------------------------------------------- |
| BundleChangedEvent           | string   | 是   | 注销监听的事件类型                                         |
| Callback\<BundleChangedInfo> | callback | 否   | 注销监听的回调函数，当为空时表示注销当前事件的所有callback |

**相关错误码**

| 错误码 | 错误信息（此处仅提供错误抛出的关键信息） |
| ------ | ---------------------------------------- |
| 201    | Permission denied.                       |
| 401    | The parameter check failed.              |

**示例：**

```js
import bundleMonitor from '@ohos.bundle.bundleMonitor';

try {
    bundleMonitor.off('add');
} catch (errData) {
    console.log(`errData is errCode:${errData.errCode}  message:${errData.message}`);
}
```
