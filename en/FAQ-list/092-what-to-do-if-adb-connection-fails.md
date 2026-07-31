# What to do if ADB connection fails?

## Question
During the VR teleoperation data collection setup in OrcaLab, when attempting to use the `adb reverse tcp:8001 tcp:8001` command to establish a connection between the PC and the Pico VR device, if the connection fails or there is no response, how should I troubleshoot and resolve it?

## Answer

The `adb reverse` command is a critical step in establishing communication between the PC and the Pico device in OrcaLab VR teleoperation. Connection failures are typically due to **ADB tool installation issues, incorrect Pico device configuration, USB connection faults, or insufficient permissions**. Below is a detailed troubleshooting and resolution guide.

## 📋 ADB Connection Failure Troubleshooting & Solutions

### 1. **Check if ADB Tools Are Properly Installed**

#### Symptom
-   Terminal displays `adb: command not found`.

#### Solution
-   **Install ADB**: Run the following command in the Ubuntu terminal to install the Android Debug Bridge (adb) tools.
    ```bash
    sudo apt install android-tools-adb android-tools-fastboot
    ```

### 2. **Pico Device Not Correctly Configured**

#### Symptom
-   PC cannot recognize the Pico device.
-   `adb devices` command cannot list the Pico device.
-   `adb reverse` command reports an error.

#### Solution
-   **Ensure Pico is powered on and connected to PC**: Use a USB data cable to connect the Pico Ultra 4 device to your PC and ensure Pico is powered on.
-   **Enable USB Debugging (Developer Mode)**:
    -   On the Pico VR device, go to "Settings" -> "About" -> continuously click "Software Version" 6-7 times to enable developer mode.
    -   In developer mode, ensure "USB Debugging" is turned on.
-   **Allow USB Debugging Authorization**: When connecting to the PC for the first time, the Pico device (inside the VR headset) may display an "Allow USB Debugging" popup. Be sure to click "Allow" in VR, otherwise the PC cannot communicate with the device.
-   **Launch the VR-side `OrcaGymCtrl` Application**: Ensure `OrcaGymCtrl` is running on the Pico, as `adb reverse` is typically used to communicate with this application.

### 3. **USB Connection Faults or Issues**

#### Symptom
-   PC does not recognize the Pico device.
-   `adb devices` command output is empty or shows `unauthorized`.
-   Data transfer is unstable or interrupted.

#### Solution
-   **Check the USB Data Cable**:
    -   Ensure you are using a USB data cable with **functional data transfer capability**, not a charge-only cable.
    -   Try a different USB data cable.
-   **Change USB Port**: Try connecting the Pico to a different USB port on the PC (especially USB 3.0 or above ports).
-   **Restart the Pico Device and PC**: Sometimes a simple restart can resolve temporary connection issues.

### 4. **ADB Service Issues**

#### Symptom
-   ADB commands execute abnormally.

#### Solution
-   **Restart the ADB Service**:
    ```bash
    adb kill-server
    adb start-server
    ```
-   **Check `adb devices` Status**:
    ```bash
    adb devices
    # Expected output similar to:
    # List of devices attached
    # 123456789ABCDEF        device
    ```
    -   If it shows `unauthorized`, please authorize USB debugging on the Pico device.
    -   If it shows `offline`, check the USB connection and Pico device status.

### 5. **Port Conflict or Permission Issues**

#### Symptom
-   `adb reverse` command reports an error, indicating the port is already in use or permission is insufficient.

#### Solution
-   **Ensure the Port Is Not Occupied**: Typically, `tcp:8001` is unlikely to conflict with other common services, but if it does, try changing the port number (requires synchronized modification in `OrcaGymCtrl` and the data collection script).
-   **Check User Group Permissions**: On some Linux distributions, non-root users may need to be added to the `plugdev` user group to use ADB devices.
    ```bash
    sudo usermod -aG plugdev $USER
    # Takes effect after re-login or restart
    ```

### 6. **Operations After Each PC Restart or PICO Disconnection**

#### Symptom
-   Previously could connect normally, but after restarting PC or re-plugging Pico, connection fails again.

#### Solution
-   **Re-run the `adb reverse` Command**: The OrcaLab official documentation explicitly states that **the `adb reverse tcp:8001 tcp:8001` command must be re-executed each time the PC restarts or the PICO USB connection is disconnected**.

## 📝 Summary

ADB connection failures are typically due to ADB tools not being installed, Pico device not correctly configured (USB debugging not enabled, not authorized, `OrcaGymCtrl` not launched), faulty USB cables, or the `adb reverse` command not being re-executed. Follow the troubleshooting steps above one by one to resolve most connection issues.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to configure a Pico Ultra 4 device?](FAQ-list/090-how-to-configure-pico-ultra-4-device.md)
- [What equipment is needed for VR data collection?](FAQ-list/089-what-equipment-is-needed-for-vr-data-collection.md)