# 如何配置Pico Ultra 4设备？

## 问题
OrcaLab支持使用Pico Ultra 4 VR设备进行遥操作数据采集。我应该如何配置Pico Ultra 4设备，使其能够与OrcaLab环境正常通信并进行数据采集？

## 回答

配置Pico Ultra 4 VR设备以用于OrcaLab的遥操作数据采集，主要涉及在Pico设备上安装必要的应用程序、开启开发者模式以及在PC端建立ADB连接。以下是详细的配置步骤：

## 📋 配置Pico Ultra 4设备流程

### 第一步：安装`PicoController.apk`程序

`PicoController.apk`是Pico VR设备上用于与OrcaLab通信的配套控制程序（或称"OrcaGymCtrl"）。

1.  **连接Pico到PC**：使用USB数据线将Pico Ultra 4设备连接到您的PC，并确保Pico已开机。
2.  **复制APK文件**：将`PicoController.apk`文件复制到Pico设备的任意可访问目录中。
    -   `PicoController.apk`通常位于`OrcaManipulation/src/examples/超市场景青龙机器人数采案例/pico安装包/`目录下。
3.  **在Pico上安装**：
    -   佩戴VR设备，在VR视角中，找到Pico的**文件管理器**。
    -   浏览到您刚刚复制`PicoController.apk`的目录。
    -   使用右手手柄点击**A键**，确认安装`PicoController.apk`程序。


### 第二步：打开VR设备开发者模式

开启开发者模式是为了允许USB调试和ADB连接。

1.  **进入设置**：在VR视角中，点击："设置"（Settings）。
2.  **关于本机**：导航到"关于本机"（About Device）。
3.  **软件版本号**：找到"软件版本号"（Software Version Number）。
4.  **连续点击**：使用手柄的A键，对着"软件版本号"**连续点击6-7次**。这会调出隐藏的开发者模式。
5.  **打开调试开关**：在开发者模式中，找到并打开"USB调试"（USB Debugging）或类似的调试开关。



### 第三步：启动VR端`OrcaGymCtrl`程序

1.  **开启VR设备**：确保Pico Ultra 4已开机。
2.  **选择资源库**：在VR视角中，选择底部的"资源库"（Library）菜单。
3.  **查找并启动`OrcaGymCtrl`**：在资源库中找到并启动"OrcaGymCtrl"应用程序。
    -   启动后，会进入3D程序界面：左侧显示三维红蓝绿坐标轴，中间有红色文字。
    -   **重要**：在进行VR遥操作时，需要**始终保持此界面激活和在前台**。



### 第四步：安装ADB工具（PC端）

ADB（Android Debug Bridge）是用于连接和控制Android设备的命令行工具，Pico设备基于Android系统。

1.  **在Ubuntu终端安装ADB**：
    ```bash
    sudo apt install android-tools-adb android-tools-fastboot
    ```

### 第五步：建立Pico与PC的通信连接 (ADB Reverse)

在PC端执行ADB命令，反向映射端口，确保PC上的OrcaLab可以与Pico上的`OrcaGymCtrl`通信。

1.  **连接USB数据线**：确保Pico设备通过USB数据线连接到PC。
2.  **执行ADB反向映射命令**：
    ```bash
    adb reverse tcp:8001 tcp:8001
    ```
    -   **效果**：如果执行成功，通常会提示"start successful"。如果已执行过，再次执行可能无输出，属于正常现象。
    -   **注意**：**每次重启PC或断开PICO的USB连接后，都需要重新执行此命令。**

## 💡 配置完成后的验证

-   当所有步骤完成后，您可以启动OrcaLab客户端（以"无仿真程序（手动启动）"模式），然后运行数据采集脚本。
-   在VR设备中，您应该能够通过手柄控制仿真中的机器人，并且数据采集脚本能够接收到VR操作数据。

## ⚠️ 常见问题与排查

### 1. **Pico设备未被PC识别**
-   检查USB数据线是否损坏或连接不良。
-   确保Pico设备已开机，并尝试更换USB端口。
-   确保USB调试已开启。

### 2. **`adb reverse`命令失败**
-   确保`adb`工具已正确安装。
-   确保Pico设备上的"USB调试"已开启。
-   在Pico上，首次连接时可能会弹出"允许USB调试"的弹窗，请务必在VR中点击"允许"。
-   尝试重启Pico设备和PC。

### 3. **VR视角中无法找到`OrcaGymCtrl`**
-   确保`PicoController.apk`（即`OrcaGymCtrl`）已成功安装。
-   检查"资源库"中的"所有应用"或"未知来源"等分类。

### 4. **VR遥操作延迟过高**
-   检查PC性能，确保满足OrcaLab和VR运行要求。
-   确保USB连接稳定，避免使用USB集线器。
-   关闭PC上不必要的后台程序。

## 📝 总结

配置Pico Ultra 4设备进行OrcaLab的VR遥操作数据采集，需要**在Pico上安装`PicoController.apk`并开启开发者模式，同时在PC端安装ADB并建立`adb reverse`连接**。确保每个步骤都正确执行，是实现流畅VR遥操作体验的关键。

## 相关链接
- [VR遥操作与数据采集操作指南](操作指南/数据采集与合成/VR遥操作与数据采集操作指南.md)
- [VR数据采集需要什么设备？](FAQ-list/091-vr数据采集需要什么设备.md)
- [OrcaLab对内存和硬盘有什么要求？](FAQ-list/033-orcalab对内存和硬盘有什么要求.md)