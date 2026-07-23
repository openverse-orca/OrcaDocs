# How to stop a running simulation?

## Question
After starting a simulation program in OrcaLab, how should I safely and correctly stop the running simulation? What stopping methods are available and what should I pay attention to?

## Answer

Stopping a running simulation in OrcaLab properly to ensure resources are correctly released and data corruption is avoided is important. OrcaLab provides multiple methods to stop simulation programs, and you can choose the most appropriate one based on the situation.

## 📋 Stopping a Running Simulation

### 1. **Stop via the OrcaLab Client Interface (Recommended)**

This is the safest and recommended method to stop a simulation, ensuring OrcaLab can properly clean up resources.

#### Steps
1.  **Click the "Stop Simulation" Button**: In the top menu bar on the right side of the OrcaLab client interface, find and click the **red "Stop Simulation" button [⏹]**.
    -   This button is typically next to the "Run Simulation" button [▶].


#### Effect
-   OrcaLab sends a stop signal to the running external simulation program.
-   The simulation program executes its predefined cleanup logic (such as saving data, closing connections).
-   Simulation activity in the 3D viewport stops, and the physics engine pauses.
-   The "Terminal Panel" may display log information indicating normal program exit.

### 2. **Stop via Internal Simulation Program Logic (Advanced)**

For custom simulation programs, you can write code to implement internal stop logic.

#### Methods
-   **Listen for External Signals**: The simulation program can listen for operating system termination signals (such as `SIGTERM`) and execute cleanup when a signal is received.
-   **Keyboard Events**: The program can listen for specific keyboard keys (such as the `Esc` key) and trigger program exit when pressed.
-   **Task Goal Achieved**: The simulation program can exit on its own when it completes its preset task goals.

### 3. **Force Termination via Terminal (Not Recommended, Emergency Only)**

If the OrcaLab client or simulation program is frozen and cannot be stopped normally through the interface, you can forcefully terminate the process. **Please note that this method may result in unsaved data or improperly released resources.**

#### Steps
1.  **Locate the Simulation Program Process**: In the Linux terminal, use the `ps aux | grep python` command to find running Python processes and identify the process ID (PID) related to your simulation program.
    ```bash
    ps aux | grep python
    # Example output:
    # your_user   1234  0.5  0.1  123456 7890 ?        Sl   10:00   0:05 python -m examples.wheeled_chassis.run_ackerman
    # The PID here is 1234
    ```
2.  **Forcefully Terminate the Process**: Use the `kill -9` command to forcefully terminate the process.
    ```bash
    kill -9 1234 # Replace 1234 with the actual PID
    ```
3.  **Close the OrcaLab Client**: If the OrcaLab client itself is also frozen, you may need to forcefully close its window or end its process through the system task manager.

#### Risks
-   Data loss or corruption.
-   Resources (such as VRAM, file handles) not properly released, which may affect subsequent simulations.
-   May cause the Python environment or OrcaLab client state to become abnormal, requiring a restart or cache cleanup.

## ⚠️ Important Notes

### 1. **Prioritize the Interface Button**
- Always prioritize using the "Stop Simulation" button on the OrcaLab client interface to end the simulation, ensuring safe shutdown and resource cleanup.

### 2. **Save Data**
- If your simulation program generates data during runtime, ensure all important data is saved before the program stops. When stopping via the client button, the program typically has the opportunity to execute save operations.

### 3. **Check Terminal Logs**
- After stopping the simulation, check the OrcaLab client's "Terminal Panel" or the terminal where you ran the script to confirm the program exited normally and whether there are any error or warning messages.

### 4. **Post-Abnormal Exit Handling**
- If a forced termination or abnormal exit occurs, it is recommended to restart the OrcaLab client and check system resources (such as `nvidia-smi`) to ensure no residual processes or unreleased VRAM remain.

## 📝 Summary

To safely and correctly stop an OrcaLab simulation program, prioritize using the "Stop Simulation" button on the client interface. In extreme cases where the program is frozen, forced termination via the terminal may be considered, but be aware of the potential data and resource issues. For custom simulation programs, graceful exit logic can also be implemented within the code.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [How to start a simulation?](FAQ-list/076-how-to-start-simulation.md)
- [How to view simulation logs?](FAQ-list/082-how-to-view-simulation-logs.md)