# What Does "Manual Start (Without Simulation Program)" Mean?

## Problem

When starting a simulation in OrcaLab, what does the "Manual Start (Without Simulation Program)" option mean? What scenarios is it suitable for?

## Answer

**"Manual Start (Without Simulation Program)"** is an important option when launching simulations in OrcaLab. It means that the OrcaLab client will start the 3D simulation environment, but will **not automatically load or run any external Python simulation scripts**. In this mode, users need to manually control the scene through the graphical user interface (GUI) or external connections.

## 📋 Concept Analysis

### Core Meaning
- **No Script Execution**: Does not run any `external_programs` configured in `.orcalab/config.toml`.
- **Manual Control**: All object interactions and operations within the scene are performed by the user through the client interface (mouse, keyboard) or external programs (e.g., VR teleoperation scripts).

### Comparison

| Feature | Manual Start (Without Simulation Program) | Predefined/Custom Simulation Program |
|---------|-------------------------------------------|--------------------------------------|
| **Script Control** | No automatic script execution | Scripts execute automatically |
| **Interaction** | Pure GUI or external command-driven | Script-driven + GUI-assisted |
| **Task Nature** | Exploration, editing, debugging | Automated tasks, AI training, data collection |
| **Applicable Stage** | Scene setup, initial testing | Task execution, algorithm validation |

![Selecting Manual Start Without Simulation Program](../img/shucai/shop_sim1.png)

## 🎯 Applicable Scenarios

The "Manual Start (Without Simulation Program)" mode is very useful during the development and debugging phase of OrcaLab, mainly applicable to the following scenarios:

### 1. **Scene Building and Editing**

- **Purpose**: Build or modify existing simulation scenes from scratch.
- **Operation**:
  - Drag and drop 3D models from the asset library.
  - Use the interface's move, rotate, and scale tools to adjust object position, orientation, and size.
  - Create and manage hierarchical structures in the scene.
- **Advantage**: Freely layout and adjust scene elements without any script interference.

### 2. **Physics Effect Testing and Debugging**

- **Purpose**: Verify the physical behavior of objects in the scene, such as gravity, collision, friction, etc.
- **Operation**:
  - Place objects and observe their physical reactions, such as free fall, rolling, and sliding.
  - Adjust object material properties to test the effects of different physical parameters.
  - Manually push or apply forces to observe object responses.
- **Advantage**: Quickly iterate and test physical parameters without writing code.

### 3. **VR Teleoperation Data Collection**

- **Purpose**: Control robotic arms or other robots in real-time via VR devices for data collection.
- **Procedure**:
  1. OrcaLab starts in "Manual Start (Without Simulation Program)" mode, loading a scene with a robotic arm.
  2. In **another terminal window**, manually run the VR teleoperation data collection script (e.g., `python data_collection_tele.py`).
  3. The script connects to the OrcaLab environment and converts VR controller input into robot control commands.
  4. The user wears the VR device, controls the robot via controllers, while the script collects data.
- **Advantage**: Enables human-machine interaction for data generation, obtaining realistic operational data.

### 4. **External Program Interface Development**

- **Purpose**: Develop external Python scripts or programs that interact with OrcaLab.
- **Operation**:
  - OrcaLab runs as a backend simulator in "Manual Start (Without Simulation Program)" mode.
  - External scripts send control commands and retrieve simulation status through OrcaLab's API interface.
- **Advantage**: Decouples the simulation core from control logic, facilitating development and testing of independent control modules.

### 5. **Teaching Demonstration and Learning**

- **Purpose**: Showcase OrcaLab's basic functions and interactions to beginners.
- **Operation**:
  - Start an empty scene.
  - Step-by-step demonstrate how to add objects from the asset library, how to move, rotate, and scale.
  - Explain the function of each UI module.
- **Advantage**: Intuitive operation, easy to understand, suitable for introductory teaching.

## 💡 Usage Tips and Notes

### When to Choose This Mode
- When you only care about the visual effect and layout of the scene.
- When you need to manually adjust objects in the physical world.
- When you are using external scripts (such as VR teleoperation scripts) to connect to OrcaLab.
- When you want OrcaLab to serve only as a backend for 3D rendering and physics simulation.

### Operation Tips
- **Make full use of GUI tools**: Become proficient with move, rotate, and scale tools.
- **Keyboard shortcuts**: Master view control shortcuts (W/A/S/D, right-click + Z to focus), etc.
- **Outline panel**: Use the outline panel for object selection and hierarchy management.
- **Edit panel**: Use the edit panel to precisely adjust object Transform properties.

### External Script Connection
- If your external script needs to connect to OrcaLab, ensure your script contains the correct connection logic (e.g., using the `orca-gym` library).
- Make sure the external script runs in the same Conda environment as OrcaLab, or has access to the Python libraries required by OrcaLab.

## ⚠️ Frequently Asked Questions

### Q: Why doesn't the robot move in "Manual Start (Without Simulation Program)" mode?
A: Because no control scripts are running in this mode. If you expect the robot to move automatically, you need to load a simulation program containing robot control logic, or control it externally through methods such as VR teleoperation.

### Q: How do I save my scene modifications in "Manual Start (Without Simulation Program)" mode?
A: You can save your scene layout modifications through OrcaLab client's "File" menu, selecting "Save Layout" or "Save As".

### Q: What is the difference between "Manual Start (Without Simulation Program)" mode and "Launch OrcaLab"?
A: "Launch OrcaLab" starts the entire client application. "Manual Start (Without Simulation Program)" is a **simulation run mode** selected after the client starts, which determines whether to simultaneously run an external Python simulation program.

Understanding the "Manual Start (Without Simulation Program)" mode will help you use OrcaLab more flexibly for scene creation, debugging, and integration with external programs.

## Related Links
- [OrcaLab Basic User Guide](../user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [How to Start Simulation](076-how-to-start-simulation.md)
- [VR Teleoperation and Data Collection User Guide](../user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)