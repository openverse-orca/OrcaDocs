# What are common reasons for simulation failure?

## Question
After starting a simulation program in OrcaLab, you may encounter situations where the simulation fails to run properly, exits with errors, or behaves abnormally. What are the common reasons for simulation failures? How should I troubleshoot and resolve these issues?

## Answer

OrcaLab simulation failures have complex and diverse causes, involving **Python environment, simulation program code, scene configuration, asset dependencies, hardware compatibility**, and more. A systematic troubleshooting approach will help you quickly locate the problem.

## 📋 Common Causes of Simulation Failure & Troubleshooting

### 1. **Python Environment or Dependency Issues**

#### Symptoms
-   Terminal reports `ModuleNotFoundError`, `ImportError`.
-   Indicates a Python package is missing or version mismatch.
-   Simulation program exits immediately after starting.

#### Troubleshooting & Resolution
-   **Check Conda Environment Activation**: Ensure you have activated the correct Conda environment before launching OrcaLab (`conda activate orcalab`).
-   **Check Python Dependency Installation**:
    -   Confirm all dependencies in the simulation program's `requirements.txt` (e.g., `OrcaPlayground`) are installed: `pip install -r requirements.txt`.
    -   Check `pip show orca-lab` to confirm core dependencies are met.
-   **Clear Python Cache**: `pip cache purge`, then try reinstalling relevant packages.

### 2. **Simulation Program Code Errors**

#### Symptoms
-   Terminal displays a Python stack trace pointing to your simulation script file.
-   Reports `SyntaxError`, `TypeError`, `NameError`, or other Python code errors.

#### Troubleshooting & Resolution
-   **Carefully Read Error Messages**: Python error messages are typically very detailed, indicating the error type, the file, and the line number where it occurred.
-   **Code Debugging**:
    -   View the complete log in the OrcaLab client's "Terminal Panel."
    -   Try running your simulation Python script directly in a separate terminal, bypassing the OrcaLab client, for better code debugging:
        ```bash
        conda activate orcalab
        python your_simulation_script.py [args]
        ```
    -   Use a Python debugger (such as `pdb`) or an IDE (such as VS Code) for breakpoint debugging.
-   **Check Logic Errors**: Such as robot control logic, task condition judgments, etc.

### 3. **`.orcalab/config.toml` Configuration Errors**

#### Symptoms
-   Simulation program does not appear in the OrcaLab launch dialog.
-   After selecting the simulation program, OrcaLab reports an error or crashes.
-   Reports `Program not found` or `Invalid arguments`.

#### Troubleshooting & Resolution
-   **Check TOML Syntax**: Ensure the `config.toml` file has no syntax errors (e.g., missing quotes, mismatched brackets).
-   **`name` and `display_name` Uniqueness**: Ensure all `external_programs.programs` entries have unique `name` and `display_name` values.
-   **`command` and `args` Paths**:
    -   `command` is typically `"python"`.
    -   Are the module paths (`-m your.module`) or script paths (`your_script.py`) in `args` correct and relative to the `.orcalab/config.toml` directory?
-   **Restart Client**: After each modification to `config.toml`, be sure to restart the OrcaLab client.

### 4. **Missing Asset Dependencies or Version Incompatibility**

#### Symptoms
-   After simulation starts, the scene is missing robot models or key props.
-   Terminal reports `AssetNotFound`, `ResourceLoadError`.
-   Abnormal physics interactions, such as robots "collapsing" or "floating."

#### Troubleshooting & Resolution
-   **Check Asset Subscription Status**: Log into the Asset Library webpage and confirm all asset packages required for the simulation are successfully subscribed.
-   **Restart Client to Sync Assets**: Ensure that after subscribing to or updating asset packages, you have closed and restarted the OrcaLab client to sync assets locally.
-   **Check Asset Paths**: Verify that the asset paths referenced in the simulation script are correct.
-   **Clear Local Asset Cache**: If you suspect local asset files are corrupted, try manually deleting the relevant asset files, then restart the client to re-download.

### 5. **Scene Configuration or Layout Issues**

#### Symptoms
-   Scene loads abnormally; object positions are chaotic.
-   After simulation starts, the robot is not in the expected position.

#### Troubleshooting & Resolution
-   **Check Layout File**: If you loaded a custom layout file, ensure the file is not corrupted and all assets referenced within it exist.
-   **Debug in "No Simulation Program" Mode**: Use "No Simulation Program (Manual Start)" mode to load the scene and manually check the position, rotation, scale, and physical properties of each object.
-   **Check Robot Configuration**: If robot behavior is abnormal, check whether its URDF/USD file definitions are correct, and whether joint limits, motor parameters, etc., are reasonable.

### 6. **Hardware Driver or System Resource Issues**

#### Symptoms
-   GPU-related errors (`CUDA Error`, `OpenGL Error`).
-   Memory overflow (`OutOfMemory`).
-   Extremely low simulation framerate with severe stuttering.

#### Troubleshooting & Resolution
-   **Graphics Driver**: Check that the NVIDIA graphics driver version meets OrcaLab requirements and update to the latest.
-   **System Resources**: Use tools like `nvidia-smi`, `htop` to monitor GPU, CPU, and memory usage to ensure no hardware bottlenecks are reached.
-   **Close Unnecessary Programs**: Close other applications that consume significant resources.

### 7. **Network Connection Issues**

#### Symptoms
-   At simulation startup, if online verification or loading of certain online resources is required, errors may occur.

#### Troubleshooting & Resolution
-   **Check Network Connectivity**: Ensure your computer can access the internet normally.

## 📝 Comprehensive Troubleshooting Flow

1.  **Start with Terminal Error Messages**: Carefully read the output in the OrcaLab client's "Terminal Panel" or the terminal running the simulation script; it usually provides the most direct clues.
2.  **Layer-by-Layer Troubleshooting**: Follow the order of `Python Environment` → `config.toml Configuration` → `Simulation Code` → `Assets/Scene` → `Hardware/System` to troubleshoot layer by layer.
3.  **Simplify the Problem**: Try running the simplest simulation example. If the simple example works normally, the problem is likely in your custom configuration or code.
4.  **Seek Help**: If self-resolution is difficult, provide detailed error information, logs, and your operation steps to the OrcaLab community or technical support for assistance.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [How to configure external simulation programs?](FAQ-list/079-how-to-configure-external-simulation-programs.md)
- [What is a simulation program and how to choose one?](FAQ-list/077-what-is-a-simulation-program-and-how-to-choose.md)
- [What are the common reasons for OrcaLab startup failure?](FAQ-list/026-common-reasons-for-orcalab-startup-failure.md)