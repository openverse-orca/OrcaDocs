# Can parameters be adjusted in real-time during simulation?

## Question
While an OrcaLab simulation is running, can I modify object properties in the scene (such as position, physical parameters) or simulation program parameters in real-time? If so, how? If not, what alternatives are available?

## Answer

In OrcaLab, you **can adjust certain properties of scene objects in real-time** (such as Transform), but **cannot modify the code logic or initial launch parameters of a running simulation program in real-time**. OrcaLab provides different mechanisms to handle these two situations.

## 📋 Two Cases of Real-Time Parameter Adjustment

### 1. **Real-Time Adjustment of Scene Object Properties (GUI Interaction)**

#### Scope
-   **Transform Properties**: Including Position, Rotation, and Uniform Scale.
-   **Other Physical Properties**: May include mass, friction coefficient, restitution coefficient, etc. (if OrcaLab's "Edit Panel" provides these options).
-   **Light Properties**: Light color, intensity, direction, etc.

#### How to Operate
1.  **Start Simulation**: First, launch a simulation program in the OrcaLab client (including "No Simulation Program (Manual Start)" mode).
2.  **Select Object**: Select the object whose properties you want to adjust in the 3D viewport or "Outline Panel."
3.  **Use the "Edit Panel"**:
    -   In the right-side "Edit Panel," directly modify Transform property values.
    -   You can enter precise values directly, or hover over the value input box and drag the arrows for real-time adjustment.
4.  **Use Interface Tools**:
    -   Activate the Move (shortcut `1`), Rotate (shortcut `2`), or Scale (shortcut `3`) tools and directly drag the handles in the 3D viewport to change the object's position, rotation, and size.

#### Effect
-   These modifications are **immediately reflected** in the running simulation, and you will see the object change in real-time during the simulation.


### 2. **Real-Time Adjustment of Simulation Program Parameters or Code Logic (Generally Not Supported)**

#### Scope
-   **Simulation Program Command-Line Arguments**: For example, parameters specified at launch such as `--env MyRobotEnv --epochs 100` typically cannot be modified in real-time after the program is running.
-   **Simulation Program Python Code Logic**: For example, PID gains in a robot control algorithm, model parameters of an AI policy, etc., cannot be modified through the GUI after the program is running.

#### Symptoms
-   Attempting to modify these parameters in a running program is typically ineffective, or requires restarting the program to take effect.

#### Solutions & Alternatives

-   **Stop and Restart Simulation**: To modify simulation program parameters or code logic, the most direct approach is to **stop the current simulation, modify the program code or configuration file, then restart the simulation**.

-   **Implement Hot-Reload / Dynamic Configuration via Python Scripts (Advanced)**:
    -   **External Control Interface**: If your simulation program is designed with an external control interface (e.g., via `gRPC`, `WebSocket`, or shared memory) that allows receiving new configuration parameters or control commands at runtime, "near real-time" adjustments can be achieved.
    -   **Configuration File Hot-Reload**: Your simulation program can be designed to periodically check an external configuration file (such as `config.yaml`) and reload certain parameters when the file changes. However, this approach requires corresponding logic implementation within the program.

-   **Use OrcaLab's Python API for Programmatic Control (Advanced)**:
    -   By writing external Python scripts and using the APIs provided by OrcaLab to programmatically control the simulation environment, including dynamically changing object properties and sending robot control commands.
    -   This approach enables more fine-grained and real-time programmatic control, but requires programming skills.

## 💡 Best Practices

### 1. **Distinguish Real-Time vs. Non-Real-Time**
-   Clearly understand which parameters can be adjusted in real-time through the GUI (such as physical object Transforms in the scene) and which require restarting the simulation program (such as the simulation program's own launch parameters and core logic).

### 2. **Parameterize Your Simulation Program**
-   For simulation program parameters that need frequent adjustment (such as PID gains, learning rates), design them as command-line arguments or external configuration files rather than hard-coding them in the script.
-   This way, you only need to modify the `args` in the `config.toml` file or the external configuration file, then restart the simulation.

### 3. **Use "No Simulation Program (Manual Start)" Mode for Scene Debugging**
-   When debugging scene physical properties and object placement, prioritize using "No Simulation Program (Manual Start)" mode so you can focus on GUI operations without worrying about script complexity.

## ⚠️ Important Notes

### 1. **Simulation Stability**
-   Modifying physical properties (such as mass, collision shape) of scene objects in real-time during simulation may cause momentary instability in the physics engine and abnormal object behavior.

### 2. **Data Consistency**
-   If you modify parameters in real-time during data collection, be sure to record these modifications to maintain consistency during subsequent data analysis.

## 📝 Summary

OrcaLab allows users to **adjust the Transform properties of scene objects in real-time** during simulation, achieved through the GUI's "Edit Panel" or direct drag tools. However, for the **core logic and launch parameters** of simulation programs, you typically need to **stop the simulation, make modifications, and restart**. Advanced users can implement more complex programmatic real-time adjustments by designing external control interfaces or leveraging OrcaLab's Python API.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [How to select and edit objects in the scene?](FAQ-list/063-how-to-select-and-edit-objects-in-scene.md)
- [How to precisely set object position and rotation?](FAQ-list/067-how-to-precisely-set-object-position-and-rotation.md)
- [How to configure external simulation programs?](FAQ-list/077-how-to-configure-external-simulation-programs.md)