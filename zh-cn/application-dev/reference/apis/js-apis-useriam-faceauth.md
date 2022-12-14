# 人脸认证

提供人脸录入相关接口。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口为系统接口。

## 导入模块

```js
import userIAM_faceAuth from '@ohos.userIAM.faceAuth';
```

## FaceAuthManager

人脸认证管理器对象。

### constructor

constructor()

表示获取人脸认证管理器对象。

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**返回值：**

| 类型                   | 说明                 |
| ---------------------- | -------------------- |
| [FaceAuthManager](#faceauthmanager) | 人脸认证管理器对象 |

**示例：**

  ```js
  import userIAM_faceAuth from '@ohos.userIAM.faceAuth';

  let faceAuthManager = new userIAM_faceAuth.FaceAuthManager();
  ```

### setSurfaceId

setSurfaceId(surfaceId: string): void;

设置录入流程中人脸预览界面 [XComponent](../arkui-ts/ts-basic-components-xcomponent.md#getxcomponentsurfaceid) 持有 Surface 的 ID。

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**需要权限：** ohos.permission.MANAGE_USER_IDM

**参数：**

| 参数名         | 类型                               | 必填 | 说明                       |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| surfaceId       | string     | 是   | [XComponent](../arkui-ts/ts-basic-components-xcomponent.md#getxcomponentsurfaceid) 持有 Surface 的 ID。 |

**示例：**

  ```js
  import faceAuth from '@ohos.userIAM.faceAuth';

  let surfaceId = "123456";
  let manager = new faceAuth.FaceAuthManager();
  try {
      manager.setSurfaceId(surfaceId);
      console.info("set surface id success");
  } catch (e) {
      console.error("set surface id failed, error = " + e);
  }
  ```
