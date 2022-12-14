# BundleInfo
> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

应用包的信息，未做特殊说明的属性，均通过[GET_BUNDLE_INFO_DEFAULT](js-apis-bundle-bundleManager)获取。

## BundleInfo

 **系统能力:** 以下各项对应的系统能力均为SystemCapability.BundleManager.BundleFramework.Core。

| 名称                              | 类型                                                         | 可读 | 可写 | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name                              | string                                                       | 是   | 否   | 应用包的名称                                               |
| vendor                            | string                                                       | 是   | 否   | 应用包的供应商                                               |
| versionCode                       | number                                                 | 是   | 否   | 应用包的版本号                                               |
| versionName                       | string                                                       | 是   | 否   | 应用包的版本文本描述信息                                     |
| minCompatibleVersionCode          | number                                                       | 是   | 否   | 分布式场景下的应用包兼容的最低版本                           |
| targetVersion                     | number                                                       | 是   | 否   | 该标签标识应用运行目标版本                                |
| appInfo                           | [ApplicationInfo](js-apis-bundleManager-applicationInfo.md)         | 是   | 否   | 应用程序的配置信息，通过传入GET_BUNDLE_INFO_WITH_APPLICATION获取                                           |
| hapModulesInfo                    | Array\<[HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md)>     | 是   | 否   | 模块的配置信息，通过传入GET_BUNDLE_INFO_WITH_HAP_MODULE获取                                                 |
| reqPermissionDetails     | Array\<[ReqPermissionDetail](#reqpermissiondetail)>   | 是   | 否   | 应用运行时需向系统申请的权限集合的详细信息，通过传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取|
| permissionGrantStates        | Array\<[PermissionGrantState](js-apis-bundleManager.md#permissiongrantstate)> | 是   | 否   | 申请权限的授予状态，通过传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取                     |
| signatureInfo          | [SignatureInfo](#signatureinfo)                                          | 是   | 否   | 应用包的签名信息，通过传入GET_BUNDLE_INFO_WITH_SIGNATURE_INFO获取                                           |
| installTime                       | number                                                       | 是   | 否   | 应用包安装时间                                          |
| updateTime                        | number                                                       | 是   | 否   | 应用包更新时间                                            |


## ReqPermissionDetail

应用运行时需向系统申请的权限集合的详细信息。

 **系统能力:** 以下各项对应的系统能力均为SystemCapability.BundleManager.BundleFramework.Core。

| 名称                  | 类型                    | 可读 | 可写 | 说明                 |
| --------------------- | ----------------------- | ---- | ---- | ---------------------|
| name                  | string                  | 是   | 是   | 需要使用的权限名称   |
| reason                | string                  | 是   | 是   | 描述申请权限的原因   |
| reasonId              | number                  | 是   | 是   | 描述申请权限的原因ID |
| usedScene             | [UsedScene](#usedscene) | 是   | 是   | 权限使用的场景和时机 |



## UsedScene

描述权限使用的场景和时机。

 **系统能力:** 以下各项对应的系统能力均为SystemCapability.BundleManager.BundleFramework.Core。

| 名称      | 类型           | 可读 | 可写 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| abilities | Array\<string> | 是   | 是   | 使用到该权限的Ability集合   |
| when      | string         | 是   | 是   | 使用该权限的时机。          |

## SignatureInfo

描述应用包的签名信息。

 **系统能力:** 以下各项对应的系统能力均为SystemCapability.BundleManager.BundleFramework.Core。

| 名称      | 类型           | 可读 | 可写 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| appId     | string         | 是   | 否   | 应用的appId                 |
|fingerprint| string         | 是   | 否   | 应用包的指纹信息            |
