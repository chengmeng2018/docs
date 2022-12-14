# ApplicationInfo

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 7 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

应用程序信息，未做特殊说明的属性，均通过GET_BUNDLE_DEFAULT获取

## ApplicationInfo<sup>(deprecated)<sup>

> 从API version 9开始不再维护，建议使用[ApplicationInfo](js-apis-bundleManager-applicationInfo.md)替代。

**系统能力**: 以下各项对应的系统能力均为SystemCapability.BundleManager.BundleFramework



| 名称                       | 类型                                                         | 可读 | 可写 | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name                       | string                                                       | 是   | 否   | 应用程序的名称。                                               |
| description                | string                                                       | 是   | 否   | 应用程序的描述。                                               |
| descriptionId              | number                                                       | 是   | 否   | 应用程序的描述id。                                             |
| systemApp                  | boolean                                                      | 是   | 否   | 判断是否为系统应用程序，默认为false。                          |
| enabled                    | boolean                                                      | 是   | 否   | 判断应用程序是否可以使用，默认为true。                         |
| label                      | string                                                       | 是   | 否   | 应用程序的标签。                                               |
| labelId<sup>(deprecated)</sup> | string                                                       | 是   | 否   | 应用程序的标签id。<br />\- **说明：** 从API version 9开始废弃，使用labelIndex。 |
| icon                       | string                                                       | 是   | 否   | 应用程序的图标。                                               |
| iconId<sup>(deprecated)</sup> | string                                                       | 是   | 否   | 应用程序的图标id。<br />\- **说明：** 从API version 9开始废弃，使用iconIndex。 |
| process                    | string                                                       | 是   | 否   | 应用程序的进程，如果不设置，默认为包的名称。                   |
| supportedModes             | number                                                       | 是   | 否   | 应用程序支持的运行模式。                                       |
| moduleSourceDirs           | Array\<string>                                               | 是   | 否   | 应用程序的资源存放的相对路径。                                 |
| permissions                | Array\<string>                                               | 是   | 否   | 访问应用程序所需的权限。<br />通过传入GET_APPLICATION_INFO_WITH_PERMISSION获取 |
| moduleInfos                | Array\<[ModuleInfo](js-apis-bundle-ModuleInfo.md)>           | 是   | 否   | 应用程序的模块信息。                                           |
| entryDir                   | string                                                       | 是   | 否   | 应用程序的文件保存路径。                                       |
| codePath<sup>8+</sup>      | string                                                       | 是   | 否   | 应用程序的安装目录。                                           |
| metaData<sup>8+</sup>      | Map\<string, Array\<[CustomizeData](js-apis-bundle-CustomizeData.md)>> | 是   | 否   | 应用程序的自定义元信息。<br />通过传入GET_APPLICATION_INFO_WITH_METADATA获取 |
| removable<sup>8+</sup>     | boolean                                                      | 是   | 否   | 应用程序是否可以被移除。                                       |
| accessTokenId<sup>8+</sup> | number                                                       | 是   | 否   | 应用程序的accessTokenId。                                      |
| uid<sup>8+</sup>           | number                                                       | 是   | 否   | 应用程序的uid。                                                |
| entityType<sup>8+</sup>    | string                                                       | 是   | 否   | 应用程序的实体类型。                                           |