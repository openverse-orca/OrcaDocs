# How to map VR controller button functions?

## Question
In OrcaLab's VR teleoperation mode, how are the Pico Ultra 4 controller buttons and joysticks mapped to robot control commands in the simulation environment? How can I understand or customize these mapping relationships?

## Answer

In OrcaLab's VR teleoperation data collection scenarios, the Pico Ultra 4 controller buttons and joysticks typically come with a preset set of function mappings for intuitively controlling robots (such as robotic arms) in the simulation environment. Understanding these mapping relationships is crucial for effective teleoperation.

## 📋 Pico VR Controller Function Mapping Overview

According to OrcaLab's VR teleoperation guide, the basic controller function mappings are as follows:

### 1. **Robotic Arm Reset & Grasp Mode Switching**
-   **Operation**: Press the **Left Joystick** and **Right Joystick** in sequence.
-   **Effect**:
    -   The robotic arm in the simulation environment becomes movable.
    -   The robot enters grasp operation mode.
-   **Purpose**: This is the initialization step before actual operation, ensuring the robotic arm is in a controllable state.

### 2. **Left Controller Functions**
-   **Y Button Long Press**:
    -   **Operation**: Long press the `Y` button on the left controller.
    -   **Function**: Triggers the "Left Hand Grasp" operation, typically used to close the robotic arm gripper.
-   **X Button**:
    -   **Operation**: Press the `X` button on the left controller.
    -   **Function**: Triggers the "Left Hand Release" operation, typically used to open the robotic arm gripper.
-   **Left Trigger**:
    -   **Operation**: Press the left controller's trigger once.
    -   **Function**:
        -   First press: Starts the data collection state.
        -   Second press: Saves the collected data and displays the save directory. If data collection fails, proceeds to the next task.

### 3. **Right Controller Functions**
-   **B Button Long Press**:
    -   **Operation**: Long press the `B` button on the right controller.
    -   **Function**: Triggers the "Right Hand Grasp" operation, typically used to close the robotic arm gripper.
-   **A Button Long Press**:
    -   **Operation**: Long press the `A` button on the right controller.
    -   **Function**: Triggers the "Right Hand Release" operation, typically used to open the robotic arm gripper.



## 💡 Mapping Mechanism & Customization

### 1. **Mapping Mechanism**
-   Physical inputs from the VR controller (button states, joystick positions, pose data) are transmitted to the PC through the Pico VR device.
-   Python scripts in the `OrcaManipulation` codebase on the PC receive these VR inputs and convert them into robot control commands (such as joint torques, end-effector velocities, grasp states) that the OrcaLab simulation environment can understand.

### 2. **Custom Mapping (by Modifying Python Scripts)**
-   The OrcaLab client itself may not provide a GUI for customizing VR controller button mappings.
-   To customize mapping relationships, you need to modify the **Python scripts** in the `OrcaManipulation` codebase responsible for VR input processing and robot control (e.g., `data_collection_tele.py` or related control modules).
-   In these scripts, you can find the logic that associates specific controller buttons or axis data with robot actions (such as move, rotate, grasp, release).

#### Example (Pseudocode)
```python
# Hypothetical example in a control script within OrcaManipulation
def process_vr_input(vr_state):
    robot_action = {}

    # Joystick controls end-effector velocity
    robot_action['gripper_velocity_x'] = vr_state.right_joystick.x
    robot_action['gripper_velocity_y'] = vr_state.right_joystick.y

    # Left controller Y button controls left grasp
    if vr_state.left_y_button_pressed:
        robot_action['left_gripper_state'] = 'close'
    elif vr_state.left_x_button_pressed:
        robot_action['left_gripper_state'] = 'open'

    # ... more mapping logic

    return robot_action
```

## ⚠️ Important Notes

### 1. **Script Dependency**
-   Controller mapping functionality is entirely dependent on the data collection scripts in the `OrcaManipulation` codebase. Ensure you are running the correct scripts.

### 2. **Pico Device Connection**
-   Ensure the Pico Ultra 4 device is correctly configured (APK installed, developer mode enabled, ADB connection established), otherwise controller inputs cannot be received by the PC-side scripts.

### 3. **Virtual Environment**
-   Ensure the Python environment running the VR teleoperation scripts is activated and all necessary dependencies are installed.

### 4. **Debugging Mappings**
-   If controller operations do not produce the expected effects, you can:
    -   Add print statements in the Python script to output VR input data and check whether controller events are being correctly received.
    -   Check the script for errors in the mapping logic.

### 5. **Body Pose Tracking**
-   VR headsets typically also provide headset pose tracking. In advanced applications, this data can be used to control robot base movement or serve as robot perception input.

## 📝 Summary

OrcaLab's VR controller button function mapping is implemented through Python scripts in the `OrcaManipulation` codebase. A default set of mappings is provided for robotic arm reset, grasp, release, and data collection start/end. Users can customize controller function mappings by modifying these Python scripts to accommodate specific robot control or task requirements.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [What equipment is needed for VR data collection?](FAQ-list/091-what-equipment-is-needed-for-vr-data-collection.md)
- [How to configure a Pico Ultra 4 device?](FAQ-list/092-how-to-configure-pico-ultra-4-device.md)