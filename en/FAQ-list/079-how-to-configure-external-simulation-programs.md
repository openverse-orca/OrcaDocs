# How to configure external simulation programs?

## Question
OrcaLab supports running external Python simulation programs. How should I configure these external programs so they appear in the OrcaLab client's startup list and execute correctly?

## Answer

OrcaLab manages external simulation programs through the **`.orcalab/config.toml` configuration file**. This TOML-format file allows you to define custom Python scripts and integrate them into OrcaLab's startup workflow. Properly configuring this file is key to running custom simulation tasks.

## 📋 External Simulation Program Configuration Process

### Step 1: Create or Locate the Configuration File

-   **Configuration File Path**: When OrcaLab starts, it looks for the `.orcalab/config.toml` file in the current working directory.
-   **Create a New File**: If your project directory doesn't have a `.orcalab/config.toml` file, you can generate a basic configuration file using the following command:
    ```bash
    conda activate orcalab
    orcalab --init-config
    ```
    This will generate an `.orcalab/` folder in the current directory containing the `config.toml` file.

### Step 2: Edit the `config.toml` File

-   Open the `.orcalab/config.toml` file using a text editor (such as `nano`, `vim`, `VS Code`, etc.).

### Step 3: Add a New Simulation Program Entry

-   In the `config.toml` file, find the `[[external_programs.programs]]` section. Each `[[external_programs.programs]]` block defines an independent simulation program.
-   Add your new program information in the following format:

```toml
# Example: Add a new simulation program
[[external_programs.programs]]
name = "my_custom_sim"               # Required: unique program identifier
display_name = "My Custom Simulation" # Required: name displayed in OrcaLab UI
command = "python"                    # Required: execution command (typically "python")
args = ["-m", "examples.my_module.run_script", "--config", "my_config.yaml"]  # Required: command-line argument list
description = "A custom robot simulation script" # Optional: program description
```

#### Parameter Details

| Parameter | Type | Required | Description |
|----------------|------------|------|------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | string | ✅ Yes | **Unique program identifier**. Used internally by OrcaLab to find and launch the program. Must not duplicate the `name` or `display_name` of any configured program. Use lowercase letters, numbers, and underscores, e.g., `my_program`. |
| `display_name` | string | ✅ Yes | **Display name**. Shown to users in the OrcaLab launch dialog UI. Must not duplicate the `name` or `display_name` of any configured program. |
| `command` | string | ✅ Yes | **Execution command**. Typically `"python"`, but can be other executable commands (e.g., `"python3"`, `"conda"`, etc.), though `python` is most commonly used to run Python scripts. |
| `args` | string array | ✅ Yes | **Command-line argument list**. Each argument as an element of the array. For example:<br>- Module mode: `["-m", "examples.module.run_script"]`<br>- Script mode: `["examples/script.py", "--arg1", "value1"]`<br>- With arguments: `["-m", "examples.module.run", "--config", "config.yaml", "--train"]` |
| `description` | string | ❌ No | **Program description**. Displayed in the OrcaLab UI tooltip to help users understand program functionality. |

### Step 4: Save the `config.toml` File

-   Save your modifications to the `config.toml` file.

### Step 5: Restart the OrcaLab Client

-   For the new configuration to take effect, you need to **close and restart the OrcaLab client**.
    ```bash
    conda activate orcalab
    orcalab
    ```
-   After restarting, your custom simulation program should appear in the "Simulation Program" list in the OrcaLab launch dialog.

## 💡 Configuration Examples

### Example 1: Run a Python Module
```toml
[[external_programs.programs]]
name = "my_module_runner"
display_name = "Run My Python Module"
command = "python"
args = ["-m", "my_project.scripts.main_script", "--mode", "train"]
description = "Launch the training mode of main_script under my_project"
```

### Example 2: Run a Python Script File
```toml
[[external_programs.programs]]
name = "my_script_runner"
display_name = "Run My Python Script"
command = "python"
args = ["scripts/test_sim.py", "--iterations", "1000", "--visualize"]
description = "Directly run the test_sim.py script in the project root"
```

## ⚠️ Important Notes

### 1. **Uniqueness of `name` and `display_name`**
- **Strict Requirement**: `name` and `display_name` must be **globally unique** across all configured programs. If duplicated, OrcaLab may not correctly identify and launch the program.

### 2. **Path Issues in `args`**
- **Relative Paths**: Paths in `args` are typically relative to the **project root directory** where the `.orcalab/config.toml` file is located.
- **Module Mode (-m)**: If using the `-m` flag to run as a module, ensure the Python module path is correct and the module file can be found in Python's `sys.path`.

### 3. **Python Environment**
- The configured `command = "python"` will use the Python interpreter from the Conda environment activated when launching the OrcaLab client. Ensure all dependencies required by your simulation program are installed in that Conda environment.

### 4. **Debugging**
- If a configured external program fails to launch or reports errors:
  - Check the output in the OrcaLab client's "Terminal Panel."
  - Try running the `command` and `args` directly in a separate terminal for debugging.

## 📝 Summary

OrcaLab configures external simulation programs by editing the `.orcalab/config.toml` file in the project root directory. You need to define a unique `name` and `display_name` for each program, specify the execution `command` (typically `python`), and provide detailed `args` command-line parameters. After saving the file and restarting OrcaLab, your custom programs will be available for selection and execution in the launch dialog.

## Related Links
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)
- [What is a simulation program and how to choose one?](FAQ-list/077-what-is-a-simulation-program-and-how-to-choose.md)
- [What are the common reasons for OrcaLab startup failure?](FAQ-list/026-common-reasons-for-orcalab-startup-failure.md)