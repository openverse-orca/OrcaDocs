# How to configure a Pico Ultra 4 device?

## Question
OrcaLab supports using the Pico Ultra 4 VR device for teleoperation data collection. How should I configure the Pico Ultra 4 device so it can properly communicate with the OrcaLab environment and perform data collection?

## Answer

Configuring the Pico Ultra 4 VR device for OrcaLab teleoperation data collection primarily involves installing the necessary application on the Pico device, enabling developer mode, and establishing an ADB connection on the PC side. Below are the detailed configuration steps:

## 📋 Pico Ultra 4 Device Configuration Process

### Step 1: Install the `PicoController.apk` Application

`PicoController.apk` is the companion control application (also called "OrcaGymCtrl") on the Pico VR device used to communicate with OrcaLab.

1.  **Connect Pico to PC**: Use a USB data cable to connect the Pico Ultra 4 device to your PC and ensure Pico is powered on.
2.  **Copy the APK File**: Copy the `PicoController.apk` file to any accessible directory on the Pico device.
    -   `PicoController.apk` is typically located under the `OrcaManipulation/src/examples/超市场景青龙机器人数采案例/pico安装包/` directory.
3.  **Install on Pico**:
    -   Wear the VR device, and in the VR view, find Pico's **File Manager**.
    -   Browse to the directory where you just copied `PicoController.apk`.
    -   Use the right-hand controller to press the **A button** to confirm installation of `PicoController.apk`.


### Step 2: Enable VR Device Developer Mode

Enabling developer mode is necessary to allow USB debugging and ADB connections.

1.  **Enter Settings**: In the VR view, click: "Settings."
2.  **About Device**: Navigate to "About Device."
3.  **Software Version Number**: Find "Software Version Number."
4.  **Repeatedly Click**: Using the controller's A button, **click 6-7 times continuously** on "Software Version Number." This will activate the hidden developer mode.
5.  **Enable Debugging Switch**: In developer mode, find and enable "USB Debugging" or similar debugging switches.



### Step 3: Launch the VR-Side `OrcaGymCtrl` Application

1.  **Power On VR Device**: Ensure Pico Ultra 4 is powered on.
2.  **Select Library**: In the VR view, select the "Library" menu at the bottom.
3.  **Find and Launch `OrcaGymCtrl`**: Find and launch the "OrcaGymCtrl" application in the Library.
    -   After launching, you will enter a 3D program interface: the left side displays a 3D red-blue-green coordinate axis, with red text in the center.
    -   **Important**: During VR teleoperation, **this interface must remain active and in the foreground at all times**.



### Step 4: Install ADB Tools (PC Side)

ADB (Android Debug Bridge) is a command-line tool used to connect and control Android devices. Pico devices are based on the Android system.

1.  **Install ADB on Ubuntu Terminal**:
    ```bash
    sudo apt install android-tools-adb android-tools-fastboot
    ```

### Step 5: Establish Pico-to-PC Communication (ADB Reverse)

Execute the ADB command on the PC side to reverse-map the port, ensuring OrcaLab on the PC can communicate with `OrcaGymCtrl` on the Pico.

1.  **Connect USB Data Cable**: Ensure the Pico device is connected to the PC via a USB data cable.
2.  **Execute the ADB Reverse Mapping Command**:
    ```bash
    adb reverse tcp:8001 tcp:8001
    ```
    -   **Result**: If successful, it typically displays "start successful." If already executed, running it again may produce no output, which is normal.
    -   **Note**: **This command must be re-executed each time the PC restarts or the PICO USB connection is disconnected.**

## 💡 Post-Configuration Verification

-   After all steps are completed, you can launch the OrcaLab client (in "No Simulation Program (Manual Start)" mode), then run the data collection script.
-   In the VR device, you should be able to control the robot in the simulation using the controllers, and the data collection script should be able to receive VR operation data.

## ⚠️ Common Issues & Troubleshooting

### 1. **Pico Device Not Recognized by PC**
-   Check if the USB data cable is damaged or poorly connected.
-   Ensure the Pico device is powered on, and try a different USB port.
-   Ensure USB debugging is enabled.

### 2. **`adb reverse` Command Fails**
-   Ensure `adb` tools are correctly installed.
-   Ensure "USB Debugging" is enabled on the Pico device.
-   On the Pico, a "Allow USB Debugging" popup may appear on first connection; be sure to click "Allow" in VR.
-   Try restarting the Pico device and PC.

### 3. **Cannot Find `OrcaGymCtrl` in VR View**
-   Ensure `PicoController.apk` (i.e., `OrcaGymCtrl`) has been successfully installed.
-   Check categories like "All Apps" or "Unknown Sources" in the "Library."

### 4. **VR Teleoperation Latency Is Too High**
-   Check PC performance to ensure it meets OrcaLab and VR runtime requirements.
-   Ensure a stable USB connection; avoid using USB hubs.
-   Close unnecessary background programs on the PC.

## 📝 Summary

Configuring the Pico Ultra 4 device for OrcaLab VR teleoperation data collection requires **installing `PicoController.apk` on the Pico and enabling developer mode, while installing ADB on the PC side and establishing an `adb reverse` connection**. Ensuring each step is correctly executed is key to achieving a smooth VR teleoperation experience.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [What equipment is needed for VR data collection?](FAQ-list/089-what-equipment-is-needed-for-vr-data-collection.md)
- [What are the memory and storage requirements for OrcaLab?](FAQ-list/033-memory-and-storage-requirements-for-orcalab.md)