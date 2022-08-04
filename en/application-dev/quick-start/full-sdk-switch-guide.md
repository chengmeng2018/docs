# Guide to Switching to Full SDK

Both the public SDK and full SDK are toolkits for application development. 

The public SDK is intended for application developers and provided as standard in DevEco Studio. It does not contain system APIs – APIs required by system applications.

The full SDK is intended for original equipment manufacturers (OEMs) and provided separately. It contains system APIs.

The SDK of API version 8 provided in DevEco Studio is a public SDK. If your project depends on any system API, such as the **animator** component, **xcomponent** component, or APIs in **@ohos.application.abilityManager.d.ts**, **@ohos.application.formInfo.d.ts**, or **@ohos.bluetooth.d.ts**, switch to the full SDK by performing the following steps.

## Downloading the Full SDK (of 3.1.1 Release in this example)

Manually download the full SDK. For details, see the source code acquisition section in [OpenHarmony 3.1.1 Release](https://gitee.com/openharmony/docs/blob/master/en/release-notes/OpenHarmony-v3.1.1-release.md).

![image-20220613161049897](figures/en-us_image_0000001655128646.png)




## Checking the Local SDK Location<br>In this example, an eTS project is used. For a JS project, replace **ets** with **js**.

In DevEco Studio, choose **Tools** > **OpenHarmony SDK Manager** to check the location of the local SDK.

![](figures/en-us_image_0000001655128939.png)

![image-20220613160524053](figures/en-us_image_0000001655128998.png)


## Replacing the SDK

1. Make sure the downloaded SDK is a full SDK.

   a. Verify that the name of the downloaded file contains **sdk-full**.

   ![image-20220613220702504](figures/en-us_image_0000001655129232.png)

   b. Verify that the SDK contains system APIs (such as APIs defined in **@ohos.application.abilityManager.d.ts**, **@ohos.application.formInfo.d.ts**, and **@ohos.bluetooth.d.ts**).

   Note: The criteria for identifying system APIs are subject to the released API documentation.

   

2. Replace the SDK. The following uses full SDK 3.1.6.6 for Windows as an example.

    

   a. Decompress the downloaded full SDK file: `ets-windows-3.1.6.5-Release.zip`

   ![image-20220613165018184](figures/en-us_image_0000001655129264.png)

   b. Replace the SDK files.

   Back up the local SDK files. (Copy and rename the version number directory in the **ets** directory, or copy the entire **ets** directory to another local path.)

   Go to the obtained location of the local installed SDK and back up the files therein.

   ![image-20220613161352157](figures/en-us_image_0000001655129041.png)

   Note: The name of the backup version number directory must be different from the value of **version** field in the **oh-uni-package.json** file. In the example below, the name of the backup version number directory is **3.1.6.6_backup**.

   ![image-20220613165018184](figures/en-us_image_0000001655129398.png)

   The configuration in the **oh-uni-package.json** file is as follows:

   ```
   {
     "apiVersion": "8",
     "displayName": "Ets",
     "meta": {
       "metaVersion": "3.0.0"
     },
     "path": "ets",
     "releaseType": "Release",
     "version": "3.1.6.6"
   }
   ```

   **Delete all files in the original SDK (3.1.6.6) directory.** Failure to do so may result in some files being unable to be overwritten.

   

   Copy the full SDK to the location of the local SDK.

   Copy all files in the **ets** directory in the full SDK to the **ets\3.1.6.6** directory in the location of the local SDK.

   Change the value of **version** in the **oh-uni-package.json** file to the current SDK version number.

   

   In the **3.1.6.6\build-tools\ets-loader** directory, open the **cmd/powerShell** window and run the **npm install** command to download the **node_modules** dependency package.

   ![image-20220613171111405](figures/en-us_image_0000001655129333.png)

   

   c. Check for system APIs.

   ![image-20220613213038104](figures/en-us_image_0000001655129372.png)