# 烧录


烧录是指将编译后的程序文件下载到开发板上的动作，为后续的程序调试提供基础。DevEco Device Tool提供一键烧录功能，操作简单，能快捷、高效的完成程序烧录，提升烧录的效率。


Hi3861V100的镜像烧录通过Windows环境进行烧录，开发者启动烧录操作后，DevEco Device Tool通过Remote远程模式，将Ubuntu环境下编译生成的待烧录程序文件拷贝至Windows目录下，然后通过Windows的烧录工具将程序文件烧录至开发板中。


## 前提条件

- 代码已[编译](quickstart-ide-3861-build.md)完成。

- 根据[USB转串口驱动安装指南](https://device.harmonyos.com/cn/docs/documentation/guide/hi3861-drivers-0000001058153433)安装USB转串口的驱动程序。


## 操作步骤

1. 请连接好电脑和待烧录开发板，需要连接USB口，具体可参考[Hi3861V100开发板介绍](quickstart-appendix-hi3861.md)。

2. 在DevEco Device Tool中，选择**REMOTE DEVELOPMENT &gt; Local PC**，查看远程计算机（Ubuntu开发环境）与本地计算机（Windows开发环境）的连接状态。
   - 如果Local PC右边连接按钮为![zh-cn_image_0000001326512673](figures/zh-cn_image_0000001326512673.png)，则远程计算机与本地计算机为已连接状态，不需要执行其他操作。
   - 如果Local PC右边连接按钮为![zh-cn_image_0000001275432904](figures/zh-cn_image_0000001275432904.png)，则点击绿色按钮进行连接。连接时DevEco Device Tool会重启服务，因此请不要在下载源码或源码编译过程中进行连接，否则会中断任务。

   ![zh-cn_image_0000001285658392](figures/zh-cn_image_0000001285658392.png)

3. 在菜单栏中点击**Project Settings**按钮，进入Hi3861V100工程配置界面。

   ![zh-cn_image_0000001333802045](figures/zh-cn_image_0000001333802045.png)

4. 在“Tool Chain”页签，设置Uploader烧录器工具，可以通过Tool Chain页签中的Install按钮在线安装。

   ![Phoenix-upload](figures/Phoenix-upload.png)

5. 在“hi3861”页签，设置烧录选项，包括upload_port、upload_protocol和upload_partitions。
   - upload_port：选择已查询的串口号。
   - upload_protocol：选择烧录协议，选择“hiburn-serial”。
   - upload_partitions：选择待烧录的文件名称。DevEco Device Tool已预置默认的烧录文件信息，如果需要修改待烧录文件地址，可点击每个待烧录文件后的![zh-cn_image_0000001333642545](figures/zh-cn_image_0000001333642545.png)按钮进行修改。

   ![zh-cn_image_0000001345770181](figures/zh-cn_image_0000001345770181.png)

6. 所有的配置都修改完成后，在工程配置页签的顶部，点击**Save**进行保存。

7. 在“PROJECT TASKS”中，点击hi3861下的**Upload**按钮，启动烧录。

   ![zh-cn_image_0000001333322693](figures/zh-cn_image_0000001333322693.png)

8. 启动烧录后，显示如下提示信息时，请在15秒内，按下开发板上的RST按钮重启开发板。

   ![hi3861-upload-restart](figures/hi3861-upload-restart.png)

   重新上电后，界面提示如下信息时，表示烧录成功。

   ![zh-cn_image_0000001281002722](figures/zh-cn_image_0000001281002722.png)