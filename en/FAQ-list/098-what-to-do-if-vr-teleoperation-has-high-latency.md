# What to do if VR teleoperation has high latency?

## Question
When using OrcaLab for VR teleoperation data collection, I notice significant latency in the VR headset display or robot response, affecting the operation experience and data quality. How can I reduce VR teleoperation latency?

## Answer

VR teleoperation latency is a critical issue that directly affects user immersion and operation precision. Encountering high VR teleoperation latency in OrcaLab typically involves multiple aspects including **PC performance, network connection (Pico to PC), VR device configuration, and simulation settings**. Below is a detailed troubleshooting and optimization guide.

## 📋 Reducing VR Teleoperation Latency — Troubleshooting & Optimization

### 1. **Optimize PC Performance (Critical)**

#### Measures
-   **Ensure Hardware Requirements Are Met**:
    -   **GPU**: NVIDIA RTX 40/50 series graphics card. Ensure the graphics driver is the latest version and meets OrcaLab requirements.
    -   **CPU**: High-performance multi-core processor.
    -   **Memory**: 16GB or above; 32GB or more is especially critical for VR and simulation.
    -   **Storage**: Ensure OrcaLab is installed on an SSD (especially NVMe SSD) to accelerate loading speed and data read/write.
-   **Close Unnecessary Background Programs**: Free up CPU, GPU, and memory resources.
-   **Adjust Power Settings**: Ensure the Windows/Linux system is in high-performance mode, not power-saving mode.
-   **Monitor Hardware Resources**: Use `nvidia-smi` to monitor GPU usage and VRAM, and `htop` or system monitor for CPU and memory.

#### Check
-   Whether graphics driver is latest: `nvidia-smi`.
-   Whether CPU/memory is overloaded: `htop`.

### 2. **Optimize Pico-to-PC Connection**

#### Measures
-   **Use High-Quality USB Data Cable**: Ensure the USB data cable supports high-speed data transfer and the connection is stable and secure.
-   **Change USB Port**: Try connecting the Pico to other USB ports on the PC, especially USB 3.0 or higher-speed ports.
-   **Avoid USB Hubs**: Connect the Pico directly to the PC motherboard's USB port whenever possible, avoiding USB hubs to reduce potential latency.
-   **Keep Pico Device Sufficiently Charged**: Low battery may affect device performance.

#### Check
-   `adb devices`: Confirm the Pico device status is `device`, not `unauthorized` or `offline`.
-   `adb reverse`: Ensure `adb reverse tcp:8001 tcp:8001` is re-executed each time the Pico is reconnected or the PC is restarted.

### 3. **Optimize OrcaLab Simulation Settings**

#### Measures
-   **Reduce Scene Complexity**:
    -   Reduce the number of objects in the scene.
    -   Use low-polygon models or optimize model meshes.
    -   Reduce the resolution of complex materials and textures.
    -   Reduce the number of light sources and shadow quality in the scene.
-   **Adjust Physics Engine Parameters**:
    -   While ensuring stability, appropriately increasing the physics time step can improve simulation speed.
    -   Appropriately reduce the physics solver iteration count, but be aware this may affect physics accuracy and stability.
-   **Reduce Rendering Quality**:
    -   The OrcaLab client may provide rendering quality settings; try lowering the level of graphics effects such as anti-aliasing, shadows, and reflections.
-   **Simplify Simulation Program Logic**:
    -   Optimize Python simulation scripts to reduce unnecessary computation and data transfer.
    -   Improve the efficiency of robot control algorithms.

### 4. **Check VR Device Status**

#### Measures
-   **Pico System Update**: Ensure the Pico Ultra 4 firmware is the latest version.
-   **Close Unnecessary Apps on Pico**: On the Pico device, close all background applications unrelated to VR teleoperation.

#### Check
-   Whether `PicoController.apk` (OrcaGymCtrl) is running normally and in the active state.

### 5. **Eliminate Software/Driver Conflicts**

#### Measures
-   **Graphics Driver Conflicts**: Ensure no other versions of graphics drivers are installed to avoid conflicts.
-   **System Updates**: Ensure the Ubuntu system and its packages are up to date and stable.

## 📝 Comprehensive Troubleshooting Flow

1.  **Check PC Hardware Resources**: Use `nvidia-smi` and `htop` to confirm GPU, CPU, and memory are not overloaded.
2.  **Check Pico-to-PC Connection**: Use `adb devices` and `adb reverse` to confirm the connection is normal, and USB debugging is enabled and authorized on the Pico device.
3.  **Simplify Simulation Scene**: Try loading a very simple scene and robot to see if latency persists.
4.  **Adjust OrcaLab Settings**: Gradually reduce rendering quality and adjust physics parameters.
5.  **Check Pico Device**: Ensure the device is up to date with no background apps running.

## ⚠️ Important Notes

### 1. **Expected Latency**
-   Any VR system has inherent latency (Motion-to-Photon Latency); completely eliminating it is impossible. The goal is to reduce it to an acceptable level (typically below 20ms).

### 2. **Data Quality & Latency**
-   Excessively high latency severely affects teleoperation precision and data collection quality, potentially leading to inaccurate robot control and poor user experience.

## 📝 Summary

High VR teleoperation latency is a multi-factor issue. The main troubleshooting directions are **PC hardware performance, Pico-to-PC USB connection, OrcaLab simulation settings, and the Pico device's own status**. Through systematic troubleshooting and optimization, latency can be significantly reduced, improving the smoothness and precision of VR teleoperation.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [What equipment is needed for VR data collection?](FAQ-list/091-what-equipment-is-needed-for-vr-data-collection.md)
- [How to configure a Pico Ultra 4 device?](FAQ-list/092-how-to-configure-pico-ultra-4-device.md)
- [How to improve simulation speed?](FAQ-list/086-how-to-improve-simulation-speed.md)