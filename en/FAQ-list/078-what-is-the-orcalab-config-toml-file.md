# What is the .orcalab/config.toml file used for?

## Question
OrcaLab projects often contain a file called `.orcalab/config.toml`. What is the specific purpose of this file? What configuration information does it contain?

## Answer

The `.orcalab/config.toml` file is the core file OrcaLab uses to **configure and manage external simulation programs**. It allows users to integrate custom Python scripts or modules into OrcaLab's startup list and define how these programs run and their parameters.

## 📋 Purpose of the `.orcalab/config.toml` File

### 1. **Define External Simulation Programs**
-   This is its primary function. The file defines a series of externally executable simulation programs in TOML (Tom's Obvious, Minimal Language) format.
-   These programs appear in the "Simulation Program" selection list when the OrcaLab client starts, for users to choose and run.

### 2. **Parameterized Launch**
-   Each defined external program can specify its execution command (e.g., `python`) and a series of command-line arguments (`args`). This allows users to flexibly pass configuration, mode, file paths, and other information to external scripts.

### 3. **Unified Management**
-   Centralizes the configuration of all external programs in a single file, making it easy to view, modify, and version control.

### 4. **Project Isolation**
-   Since `config.toml` is typically located in the project root directory, each OrcaLab project can have its own independent external program configuration, achieving isolation and non-interference between projects.

## 📁 `.orcalab/config.toml` File Structure & Content

The file primarily contains an `external_programs` section with a `programs` array, where each array element (i.e., each `[[external_programs.programs]]` block) defines an external program.

### Example File Content
```toml
# .orcalab/config.toml Example

[external_programs]

# Define external program list
[[external_programs.programs]]
name = "run_sim_loop"                  # Unique program identifier
display_name = "Empty Loop Simulation"  # Name displayed in OrcaLab UI
command = "python"                     # Execution command
args = ["-m", "orca_gym.examples.sim_loop"] # Command-line argument list (module mode here)
description = "A simple empty loop simulation for testing"

[[external_programs.programs]]
name = "run_ackerman"                   # Another program's unique identifier
display_name = "Four-Wheel Chassis Car Simulation" # Name displayed in OrcaLab UI
command = "python"                     # Execution command
args = ["-m", "examples.wheeled_chassis.run_ackerman"] # Command-line argument list
description = "Control a four-wheel chassis vehicle for physics simulation"

# You can add more custom simulation programs here
[[external_programs.programs]]
name = "my_custom_training"
display_name = "My RL Training"
command = "python"
args = [
    "-m",
    "my_project.train_script",
    "--env", "MyRobotEnv",
    "--epochs", "100",
    "--render"
]
description = "Launch a custom reinforcement learning training task"
```

### Key Configuration Parameters

| Parameter | Description |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | **Unique identifier**. Used internally by OrcaLab to find and launch the program. Must not duplicate the `name` or `display_name` of any configured program. |
| `display_name` | **Display name**. Shown to users in the OrcaLab launch dialog UI. Must not duplicate the `name` or `display_name` of any configured program. |
| `command` | **Execution command**. Typically `"python"`, but can be other executable commands. |
| `args` | **Command-line argument list**. Each argument as an array element, passed to the command specified by `command`. Can be a module path (`-m`) or script file path, along with other custom arguments. |
| `description` | **Program description**. Optional parameter displayed in the OrcaLab UI tooltip to help users understand program functionality. |

## 💡 How to Use `.orcalab/config.toml`

### 1. **Add a New Simulation Program**
-   If you have written a new Python simulation script and want to launch it directly in OrcaLab, you need to add a new `[[external_programs.programs]]` block in this file.
-   Referring to the examples, fill in `name`, `display_name`, `command`, and `args`.

### 2. **Modify Existing Program Parameters**
-   You can modify the arguments in `args` to change the behavior of a simulation program, such as adjusting the training `epochs` count or switching to `debug` mode.

### 3. **Verify Configuration**
-   **Ensure Uniqueness**: `name` and `display_name` must be unique; otherwise OrcaLab may not correctly identify programs.
-   **Correct Paths**: Script paths or module paths in `args` need to be relative to the directory containing `.orcalab/config.toml`.
-   **Restart Client**: After each modification to the `config.toml` file, you must **close and restart the OrcaLab client** for changes to take effect.

### 4. **Version Control**
-   Since `config.toml` is an important project configuration, it is recommended to include it in version control systems such as Git for change tracking, collaboration, and rollback.

## ⚠️ Important Notes

### 1. **TOML Syntax**
-   Ensure you follow the TOML file syntax specification. Incorrect syntax will cause the file to be unparseable, and OrcaLab will be unable to load your external programs.
-   In TOML, arrays are denoted with `[]`, and strings with `""`.

### 2. **File Location**
-   OrcaLab only looks for `.orcalab/config.toml` in its **current working directory**. If you launch OrcaLab from different project directories, it will load the `config.toml` from the corresponding project directory.

## 📝 Summary

The `.orcalab/config.toml` file is the "registry" for OrcaLab's external simulation programs. Through it, users can flexibly configure, manage, and launch various custom Python simulation scripts, thereby extending OrcaLab's functionality and enabling more complex robot AI simulation tasks. Understanding and correctly editing this file is key for advanced users of OrcaLab.

## Related Links
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)
- [How to configure external simulation programs?](FAQ-list/077-how-to-configure-external-simulation-programs.md)
- [What is a simulation program and how to choose one?](FAQ-list/075-what-is-a-simulation-program-and-how-to-choose.md)