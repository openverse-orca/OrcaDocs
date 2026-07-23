# How to run data collection scripts?

## Question
When performing VR teleoperation data collection in OrcaLab, I need to run specific Python scripts to start data recording. How should I run these data collection scripts? What are the key steps and notes?

## Answer

OrcaLab's VR teleoperation data collection is started and managed through **independent Python scripts**. These scripts are responsible for connecting to the OrcaLab simulation environment, receiving VR controller data, controlling the robot, and recording data. Successfully running the data collection script is a critical step in completing VR teleoperation tasks.

## 📋 Data Collection Script Execution Process

### Prerequisites

-   **OrcaLab Client Is Running**: The OrcaLab client should be running in "No Simulation Program (Manual Start)" mode and have loaded a layout containing the target robot and scene.
-   **Pico Device Connected & Configured**: Pico VR headset is powered on, `PicoController.apk` (OrcaGymCtrl) is running, and ADB connection is established (`adb reverse`).
-   **OrcaManipulation Codebase Ready**: The `OrcaManipulation` repository has been cloned locally and all dependencies in `requirements.txt` are installed.

### Step 1: Activate the OrcaLab Conda Environment

-   Data collection scripts typically depend on OrcaLab's Python packages and other libraries in the Conda environment. Therefore, be sure to activate the correct Conda environment before running the script.
    ```bash
    conda activate orcalab
    ```

### Step 2: Enter the Data Collection Script Directory

-   Use the `cd` command to enter the directory containing the data collection script. For example:
    ```bash
    cd ~/OrcaManipulation/src/examples/dataCollection
    ```

### Step 3: Launch the Data Collection Script

-   Use the `python` command to run the data collection script. Ensure you specify the correct script filename.
    ```bash
    python data_collection_tele.py
    ```
    -   **Note**: Additional command-line arguments may need to be added based on your task requirements. For example, specifying the configuration file path, output directory, etc. Consult the script itself or its `README.md` file for detailed information.

### Step 4: Observe Terminal Output

-   After the script starts, it displays log information in real-time in the terminal, including connection status, VR data reception, robot control feedback, and data save status. Monitor this output closely to confirm the script is running normally.



### Step 5: Begin VR Teleoperation

-   When the script indicates it has entered the data collection state, put on the Pico VR device and begin teleoperation using the controllers.
-   Follow task prompts, for example: robotic arm reset, grasp target object, place in designated position, etc.
-   Use the left controller trigger to control the start and save of data collection.

## 💡 Key Script Parameters & Configuration

Data collection scripts typically read task parameters from a configuration file (such as a YAML file). For example, in the `OrcaManipulation` examples, there may be an `example.yaml` file:

```yaml
# example.yaml example configuration
level_name: "shop_pick_and_place"
type: "pick_and_place"
actor:
  names: ["product_A", "product_B"]
  spawnable: ["assets/path/to/product_A", "assets/path/to/product_B"]
# ... other randomization, task logic configuration
goal:
  name: "MedicineChest"
  site: "MedicineChest_site"
```

### Key Configuration Items
-   `level_name`: Scene name identifier, used for logging and dataset differentiation.
-   `type`: Task type definition, such as `pick_and_place` (grasp and place).
-   `actor`: Dynamic object loading configuration, including names, paths, joints, randomization rules, etc.
-   `task`: Task goal configuration, such as target object name, placement site.

## ⚠️ Important Notes

### 1. **Conda Environment**
-   Be absolutely sure to activate the correct Conda environment before running the script.

### 2. **Script Path**
-   `cd` to the correct script directory, or provide the full script path when running the `python` command.

### 3. **Configuration File**
-   Data collection scripts typically reference a configuration file. Ensure the configuration file path is correct and its parameter settings (such as asset versions) match your environment.

### 4. **Asset Packages**
-   Ensure all asset packages referenced in the configuration file and scripts are subscribed to in the OrcaLab Asset Library and synced locally through the client.

### 5. **Terminal State**
-   Data collection scripts typically run continuously until the task is completed or manually terminated. Ensure the terminal window is not accidentally closed.

### 6. **Abnormal Situations**
-   If the script reports errors, carefully review the terminal error messages, which typically provide clues for locating the issue.

## 📝 Summary

Running data collection scripts is the core step of OrcaLab VR teleoperation. With the OrcaLab client and Pico device correctly configured, you need to enter the script directory in the correct Conda environment, then launch the script using the `python` command. Pay attention to the configuration file path and parameters in the script, and monitor terminal output to ensure normal operation.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to configure a Pico Ultra 4 device?](FAQ-list/092-how-to-configure-pico-ultra-4-device.md)
- [How to map VR controller buttons?](FAQ-list/093-how-to-map-vr-controller-buttons.md)
- [What to do if ADB connection fails?](FAQ-list/094-what-to-do-if-adb-connection-fails.md)
- [Data Collection Task Configuration File Description](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)