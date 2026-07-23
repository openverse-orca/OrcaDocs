# How to troubleshoot data collection failure?

## Question
When performing VR teleoperation data collection with OrcaLab, sometimes the data collection script may not work properly, resulting in data not being saved or the collection process being interrupted. How should I troubleshoot and resolve data collection failures?

## Answer

Data collection failure is a common issue that may involve multiple components, typically related to **VR device connection, OrcaLab client status, data collection script configuration, file write permissions, or disk space**. Systematic troubleshooting is key to resolving the problem.

## 📋 Data Collection Failure Troubleshooting & Solutions

### 1. **Check Pico VR Device-to-PC Connection**

#### Symptoms
-   Data collection script reports errors, indicating it cannot connect to the VR device or receive VR input.
-   VR controller operations are not reflected in the simulation.

#### Troubleshooting & Resolution
-   **Ensure Pico Is Powered On and Running `OrcaGymCtrl`**: Check that the `OrcaGymCtrl` application is installed and launched on the Pico device.
-   **Check ADB Connection**:
    -   `adb devices`: Confirm the Pico device is correctly recognized by the PC, with status as `device`.
    -   `adb reverse tcp:8001 tcp:8001`: Ensure this command has been executed, and re-execute it after each PC restart or Pico reconnection.
-   **USB Connection**: Ensure the USB data cable is stably connected and not loose.
-   **USB Debugging Authorization**: Check whether the Pico device has authorized the PC for USB debugging.

### 2. **Check OrcaLab Client Status**

#### Symptoms
-   Data collection script cannot connect to OrcaLab.
-   OrcaLab client freezes or exits abnormally.

#### Troubleshooting & Resolution
-   **OrcaLab Client Normal Startup**: Ensure the OrcaLab client starts normally in "No Simulation Program (Manual Start)" mode and loads the correct scene and robot.
-   **Check Client Logs**: Review the OrcaLab client's "Terminal Panel" for error or warning messages.
-   **Restart Client**: If the client state is abnormal, try restarting OrcaLab.

### 3. **Check Data Collection Script Configuration & Code**

#### Symptoms
-   Script startup reports errors such as `ModuleNotFoundError`, `FileNotFoundError`, `KeyError`.
-   Script runs but produces no data output.

#### Troubleshooting & Resolution
-   **Conda Environment Activation**: Ensure the correct Conda environment is activated before running the script: `conda activate orcalab`.
-   **Script Dependencies**: Ensure all Python packages required by the script are installed via `pip install -r requirements.txt`.
-   **Configuration File Path & Content**:
    -   Check that the path to the configuration file referenced by the script (such as `example.yaml`) is correct.
    -   Check the content of the configuration file, such as `actor`, `task`, and other module parameters, especially asset paths and site names.
    -   Ensure the asset versions in the configuration file match the actually subscribed asset versions.
-   **Script Logic**:
    -   Carefully read the script's error messages to locate the specific line of code.
    -   Add `print()` statements in the script to output key variables for debugging.
    -   Verify whether VR input data is correctly received and whether robot control commands are correctly sent.

### 4. **File Write Permissions & Disk Space**

#### Symptoms
-   Script reports errors such as `Permission denied` or `No space left on device`.
-   After data collection completes, saved files cannot be found.

#### Troubleshooting & Resolution
-   **Check Output Directory Permissions**: Ensure the data collection script has permission to create and write files in the specified output directory (e.g., `~/OrcaManipulation/data`).
    ```bash
    ls -l /path/to/data/directory
    # If no write permission, try
    chmod u+w /path/to/data/directory
    ```
-   **Check Disk Space**:
    ```bash
    df -h
    ```
    Ensure sufficient disk space to save collected data, especially as image and video data can be very large.

### 5. **Asset Dependencies & Scene Loading**

#### Symptoms
-   After script startup, the simulation scene is missing robots or target objects.
-   Robot cannot move or grasp.

#### Troubleshooting & Resolution
-   **Asset Subscription**: Log into the OrcaLab Asset Library webpage and confirm that all asset packages required for the data collection task have been successfully subscribed.
-   **Client Sync**: Ensure that after subscribing to assets, the OrcaLab client has been restarted to sync assets locally.
-   **Layout Loading**: Ensure the OrcaLab client has loaded the correct scene layout containing robots and target objects.

## 📝 Comprehensive Troubleshooting Flow

1.  **Start with Terminal Error Messages**: This is the most important first step; error messages will guide you.
2.  **Check VR Connection**: Ensure both physical and software connections between the Pico device and PC are normal.
3.  **Check OrcaLab Client**: Confirm the client is running normally and the scene is loading without errors.
4.  **Check Scripts and Configuration**: Carefully verify the data collection script's code and the parameters in the configuration file.
5.  **Check Write Permissions and Disk Space**: Ensure data can be saved normally.

## 💡 Best Practices

-   **Test Step by Step**: Before conducting complex data collection, first try running the simplest example to ensure basic functionality is working.
-   **Detailed Logging**: Enable detailed log output in the data collection script to record more debugging information.
-   **Backups**: Before attempting any large-scale data collection, back up your scripts and configuration files.

## 📝 Summary

Data collection failure is a multi-factor issue requiring systematic troubleshooting of VR device connection, OrcaLab client, data collection script, file permissions, and disk space. By carefully checking each component and debugging based on terminal error messages, data collection failures can be effectively resolved.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to run data collection scripts?](FAQ-list/095-how-to-run-data-collection-scripts.md)
- [Where is collected data saved?](FAQ-list/096-where-is-collected-data-saved.md)
- [How to configure data collection tasks?](FAQ-list/097-how-to-configure-data-collection-tasks.md)
- [What to do if ADB connection fails?](FAQ-list/094-what-to-do-if-adb-connection-fails.md)