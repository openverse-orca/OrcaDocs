# What equipment is needed for VR data collection?

## Question
OrcaLab supports VR teleoperation for data collection. To use this feature, what VR hardware devices and related software environments do I need to prepare?

## Answer

OrcaLab's VR teleoperation data collection feature is designed to efficiently generate high-quality robot demonstration data through an immersive experience. To use this feature, you need to prepare specific VR hardware devices and the corresponding software environment.

## 📋 VR Data Collection Equipment Requirements

### 1. **VR Headset**

#### Recommended Device
-   **Pico Ultra 4**: The VR device explicitly mentioned and supported in the OrcaLab official documentation. Ensure the headset and its controllers are functioning properly.

#### Alternative/Compatible Devices (may require additional configuration)
-   Other VR headsets that support PC VR mode may require additional configuration or driver installation. Refer to the OrcaLab official documentation for specific compatibility details.

### 2. **VR Controllers**

-   **Bundled Controllers**: VR headsets typically come with a pair of interactive controllers for operating in the virtual environment.
-   **Function Mapping**: OrcaLab's VR teleoperation feature maps controller buttons and poses to robot control (such as robotic arm joint control, grasp open/close).

### 3. **High-Performance PC**

VR teleoperation and OrcaLab simulation both require significant computing power. The PC must meet the following requirements:
-   **GPU**: NVIDIA RTX 40/50 series graphics card (see [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md) for specific requirements).
-   **CPU**: High-performance multi-core processor.
-   **Memory**: 16GB or more RAM.
-   **Storage**: SSD drive to ensure fast loading speeds.
-   **Operating System**: Ubuntu 22.04 LTS or 24.04 LTS.

### 4. **USB Cable**

-   **High-quality USB data cable**: Used to connect the Pico VR headset to the PC, ensuring stable data transfer and debugging connection (ADB connection).

## 📋 VR Data Collection Software Environment Requirements

### 1. **OrcaLab Client**
-   The OrcaLab client must be successfully installed and running normally. It is typically launched in "No Simulation Program (Manual Start)" mode to serve as the backend simulator.

### 2. **OrcaGym OrcaManipulation Code Repository**
-   This is an open-source code repository containing Python scripts related to VR teleoperation and data collection. You need to obtain it from GitHub:
    ```bash
    git clone https://github.com/openverse-orca/OrcaManipulation.git
    cd OrcaManipulation
    conda activate orcalab # Activate the OrcaLab Conda environment
    pip install -r requirements.txt # Install project dependencies
    ```

### 3. **PicoController.apk**
-   This is the companion control application (also called "OrcaGymCtrl") that needs to be installed on the Pico VR headset.
-   **Path**: Typically located under the `OrcaManipulation/src/examples/超市场景青龙机器人数采案例/pico安装包/` directory.
-   **Installation Method**:
    -   Copy `PicoController.apk` to the PICO device directory.
    -   In the VR device, find the file manager and use the controller to press the A button to confirm installation.



### 4. **Android Debug Bridge (ADB)**
-   Used to establish a communication connection between the PC and the Pico VR headset.
-   **Installation**: Run the following in the Ubuntu terminal:
    ```bash
    sudo apt install android-tools-adb android-tools-fastboot
    ```
-   **Connection Command**:
    ```bash
    adb reverse tcp:8001 tcp:8001
    ```
    -   **Note**: This command must be re-executed each time the PC restarts or the PICO USB connection is disconnected.

### 5. **VR Device Developer Mode**
-   The Pico VR headset needs "Developer Mode" enabled to allow USB debugging and `adb reverse` connections.
-   **How to Enable**: In the VR view, go to "Settings" -> "About" -> "Software Version," click 6-7 times continuously to activate developer mode, then turn on the "Debugging Switch."



### 6. **Scene Asset Packages**
-   You need to subscribe to the 3D scene and robot asset packages related to the VR data collection task (such as `ShopScene_Scaning` and `openloong`), and load them in the OrcaLab client.

## 📝 Summary

VR teleoperation data collection requires a complete hardware and software environment. Hardware includes a **Pico Ultra 4 VR headset and controllers**, a **high-performance PC**, and a **USB data cable**. Software requires the **OrcaLab client**, **OrcaManipulation code repository**, **PicoController.apk**, **ADB tools**, and **VR device developer mode enabled**. Ensure all these components are properly prepared and configured to smoothly conduct VR data collection.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [How to configure external simulation programs?](FAQ-list/079-how-to-configure-external-simulation-programs.md)