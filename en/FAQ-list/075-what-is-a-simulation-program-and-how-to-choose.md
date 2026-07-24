# What is a simulation program and how to choose one?

## Question
What does "simulation program" refer to in OrcaLab? When starting a simulation, how should I choose the appropriate simulation program?

## Answer

In OrcaLab, a "simulation program" is an external Python script that controls robot behavior, physics interactions, and data processing logic in the simulation scene. It defines the specific tasks and runtime behavior of the simulation.

## 📋 Simulation Program Overview

### Definition
- **Simulation Program**: An independent Python script or module used to control the OrcaLab simulation environment.
- **Purpose**: Specifies simulation goals, robot behavior, sensor data processing, task logic, etc.
- **Runtime**: Selected and executed through the OrcaLab client's launch dialog.

### Configuration File
All simulation programs are configured through the `.orcalab/config.toml` file in the project root directory.



## ⚙️ Simulation Program Types

### 1. **No Simulation Program (Manual Start)**

#### Characteristics
- No external Python script is executed.
- After the simulation environment starts, the user needs to manually operate through the GUI.

#### Applicable Scenarios
- **Scene Editing & Building**: Freely drag and adjust objects in the scene without script control.
- **Manual Debugging**: Test individual object physics behavior, observe collision effects.
- **Interactive Exploration**: Pure 3D environment roaming and experience.

#### Advantages
- **High Flexibility**: Fully controlled by the user.
- **Intuitive Operation**: Real-time interaction through the GUI.

### 2. **Predefined Simulation Programs**

#### Characteristics
- Simulation scripts built into OrcaLab or example projects such as `OrcaPlayground`.
- Typically used to demonstrate OrcaLab's specific capabilities or provide out-of-the-box simulation experiences.

#### Common Example Programs
- **`run_sim_loop`**: Empty loop simulation, typically used for environment testing.
- **`run_character`**: Character simulation for humanoid or generic character animation.
- **`run_legged_train`**: Legged robot training for reinforcement learning.
- **`run_wheeled_chassis`**: Wheeled chassis simulation for vehicle dynamics research.
- **`run_xbot_orca`**: XBot robot simulation for specific robot platform control.
- **`run_ackerman`**: Four-wheel chassis car simulation for vehicle physics simulation.


#### Applicable Scenarios
- **Quick Start**: Learn typical OrcaLab applications.
- **Feature Demonstration**: Showcase OrcaLab's capabilities to others.
- **Basic Testing**: Verify environment configuration and hardware performance.

#### Advantages
- **Convenient & Quick**: Can run without additional configuration.
- **Reference Value**: Can serve as examples for developing custom programs.

### 3. **Custom Simulation Programs**

#### Characteristics
- Python scripts written by users according to their own needs.
- Must be registered in `.orcalab/config.toml` to appear and be launched in the OrcaLab client.

#### Applicable Scenarios
- **Research Projects**: Implement specific robot control algorithms, AI training tasks.
- **Teaching Experiments**: Customize teaching content to meet course requirements.
- **Prototype Development**: Validate new robot systems or interaction logic.

#### Advantages
- **Highly Customizable**: Fully meets personalized needs.
- **Strong Extensibility**: Can integrate various Python libraries and algorithms.

## 💡 How to Choose the Right Simulation Program

Choosing the right simulation program depends on your goals and current task.

### 1. **First Contact with OrcaLab**

-   **Goal**: Understand OrcaLab functionality, familiarize with basic operations.
-   **Recommendation**:
  - First select **"No Simulation Program (Manual Start)"** to familiarize with the interface and manual operations.
  - Try running **`run_ackerman`** (four-wheel chassis car simulation) to experience interactive physics simulation.
  - Run other predefined examples to understand different functional modules.

### 2. **Scene Building or Editing**

-   **Goal**: Create new simulation scenes, adjust object positions and poses.
-   **Recommendation**: Select **"No Simulation Program (Manual Start)"** to freely edit the scene without script control interference.

### 3. **Validating Specific Robot Behavior or Algorithms**

-   **Goal**: Test robot control algorithms, reinforcement learning models, etc.
-   **Recommendation**:
  - Choose the **predefined simulation program** closest to your task as a reference or foundation.
  - If existing programs don't meet your needs, create a **custom simulation program** and configure it in `.orcalab/config.toml`.

### 4. **VR Teleoperation Data Collection**

-   **Goal**: Control a robotic arm for data collection via VR devices.
-   **Recommendation**:
  - First launch OrcaLab and select a scene with a robotic arm (such as the shop scene).
  - In the OrcaLab interface, select **"No Simulation Program (Manual Start)"** to launch.
  - **Run the data collection script separately in a terminal** (e.g., `python data_collection_tele.py`), which will connect to the OrcaLab environment.

## 📝 Configuration File `.orcalab/config.toml`

### Configuration Format
```toml
[[external_programs.programs]]
name = "your_program_name"           # Required: unique program identifier
display_name = "Display Name"        # Required: name displayed in OrcaLab UI
command = "python"                   # Required: execution command
args = ["-m", "examples.your_module.run_script"]  # Required: command-line argument list
description = "Program description"  # Optional: program description
```

### Important Notes
- `name` and `display_name` must be unique across all programs.
- `command` is typically `"python"`.
- `args` defines the module or path for launching the Python script, along with arguments passed to the script.

## ⚠️ Common Issues & Troubleshooting

### Q: Why is my configured simulation program not showing up?
A: 1. Check that the `.orcalab/config.toml` file path is correct.
   2. Check that the `config.toml` file syntax is correct.
   3. Ensure `name` and `display_name` are unique across all programs.
   4. OrcaLab loads this file automatically on startup; you may need to **restart the OrcaLab client**.

### Q: Nothing happens after starting the simulation?
A: 1. Check that the `command` and `args` configuration in `.orcalab/config.toml` is correct.
   2. Check OrcaLab's **Terminal Panel** for error output.
   3. Check that the Python environment is activated and required dependency packages are installed.

### Q: Where is the `.orcalab/config.toml` file?
A: This file is typically in your project root directory. If you're using the `OrcaPlayground` project, it will be at `OrcaPlayground/.orcalab/config.toml`. If it doesn't exist, you can use the `orcalab --init-config` command to generate one in the current working directory.

Understanding the concept and configuration of simulation programs is key to efficiently using OrcaLab for robot simulation and AI training.

## Related Links
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)
- [Configuration file location and adding new simulation programs](environment-setup/orca-lab-quick-start-simulation-v1.0.md)
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)