# How to view simulation logs?

## Question
During OrcaLab simulation program execution, a large amount of log information is generated, including program output, error messages, warnings, etc. How can I view these simulation logs in the OrcaLab client or terminal?

## Answer

Viewing simulation logs is key to troubleshooting issues, monitoring program status, and understanding simulation behavior. OrcaLab provides two main ways to view log information: **the client's "Terminal Panel"** and **the terminal where the simulation program is running**.

## 📋 Two Ways to View Simulation Logs

### 1. **View in the OrcaLab Client's "Terminal Panel" (Recommended)**

The OrcaLab client integrates a "Terminal Panel" module for real-time display of external simulation program output.

#### Steps
1.  **Launch the OrcaLab Client**: Ensure the OrcaLab client is launched and has entered the GUI interface.
2.  **Start a Simulation Program**: Select and start your simulation program in the client.
3.  **Navigate to the "Terminal Panel"**:
    -   At the bottom of the OrcaLab client interface (or according to your layout settings), find and click the "Terminal" tab to enter the "Terminal Panel" module.
4.  **View Logs in Real-Time**:
    -   The "Terminal Panel" displays all standard output (`stdout`) and standard error (`stderr`) information from the simulation program in real-time.
    -   You can scroll to view historical logs and observe the program's running status, print messages, warnings, and any errors.


#### "Terminal Panel" Features
-   **Clear Logs**: Click the "Clear" button in the "Terminal Panel" to clear the currently displayed log information.
-   **Copy Logs**: Click the "Copy" button in the "Terminal Panel" to copy all displayed log content to the clipboard for pasting into a text editor or sharing with others.
-   **Search Logs**: Some terminal panels may provide a search feature to help you quickly locate specific keywords or error messages.

### 2. **View in the Terminal Running the Simulation Program**

If you are running the simulation Python script directly in a Linux terminal outside the OrcaLab client (e.g., a VR teleoperation data collection script), the log information will be output directly to that terminal window.

#### Steps
1.  **Open a Separate Terminal Window**: For running your simulation Python script.
2.  **Activate the Conda Environment**:
    ```bash
    conda activate orcalab
    ```
3.  **Run the Simulation Script**:
    ```bash
    python your_simulation_script.py [args]
    ```
4.  **View Logs in Real-Time**:
    -   All of the script's `print()` output and error messages are displayed in real-time in that terminal window.
    -   You can use the terminal's scroll functionality to view history.

#### Advantages & Disadvantages
-   **Advantages**: When debugging Python scripts, you can directly see more raw output and complete Python stack traces, which is very helpful for troubleshooting complex issues.
-   **Disadvantages**: Not directly integrated within the OrcaLab client; requires managing multiple windows.

## 💡 Log Levels & Verbosity

OrcaLab and its underlying components may support different log levels (such as `DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`).

-   **Default Level**: Typically displays `INFO`, `WARNING`, and `ERROR` level logs by default.
-   **Adjusting Log Level**: When starting a simulation program, you can adjust log verbosity through command-line arguments or environment variables.
    -   **Environment Variable Example**:
        ```bash
        ORCA_LOG_LEVEL=DEBUG orcalab # Enable DEBUG level logging when launching OrcaLab
        ```
    -   **Program Argument Example**:
        ```bash
        python your_simulation_script.py --log-level DEBUG
        ```
    -   **Benefits**: When troubleshooting complex issues, `DEBUG` level logs can provide more detailed internal information.

## ⚠️ Important Notes

### 1. **Log Volume**
-   At `DEBUG` or `INFO` level, log volume can be very large and may quickly fill the terminal buffer. If you need to save the complete log, it is recommended to redirect terminal output to a file:
    ```bash
    python your_simulation_script.py > simulation_log.txt 2>&1
    ```

### 2. **Error Message Analysis**
-   When errors occur, focus on `ERROR` or `CRITICAL` level logs, as well as the Python stack trace. The stack trace will indicate the file, function, and line number where the error occurred.

### 3. **Timestamps**
-   Many logs include timestamps, which are very useful for analyzing the time sequence of problem occurrence.

## 📝 Summary

OrcaLab's simulation logs can be viewed in real-time through the client's "Terminal Panel," making it convenient for users to monitor and manage. For more in-depth Python script debugging, running the simulation script in a separate terminal and viewing the output there is more effective. By adjusting log levels, you can obtain information at different levels of detail to assist with troubleshooting.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [What are common reasons for simulation failure?](FAQ-list/081-common-reasons-for-simulation-failure.md)
- [How to configure external simulation programs?](FAQ-list/079-how-to-configure-external-simulation-programs.md)