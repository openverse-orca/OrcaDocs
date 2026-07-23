# How to start a simulation?

## Question
How do I start a simulation program in OrcaLab? What startup methods are available and what should I pay attention to?

## Answer

There are multiple ways to start a simulation in OrcaLab, and you can choose the appropriate startup mode based on different needs. Below is the detailed startup process and guide.

## 🚀 Basic Startup Process

### Step 1: Prepare the Simulation Environment
```bash
# 1. Ensure OrcaLab is running
conda activate orcalab
orcalab

# 2. Ensure the appropriate scene and layout are loaded
Select scene → Load layout → Add necessary assets
```

### Step 2: Start the Simulation Program
```
In the OrcaLab interface:
1. Click the green [Run Simulation] button [▶] in the upper-right corner
2. Select a simulation program from the popup dialog
3. Click [Start] to begin the simulation
4. Observe terminal output to confirm startup status
```


## 🎮 Simulation Program Selection

### 📋 Program Types

#### 1. **No Simulation Program (Manual Start)**
```
Purpose: Manually control the simulation process
Applicable Scenarios:
├── Scene editing and debugging
├── Manual testing of physics effects
├── Interactive scene validation
└── Custom control scripts

Operation Methods:
├── Move objects via interface tools
├── Use keyboard shortcuts for control
├── Mouse interaction
└── Real-time parameter adjustment
```



#### 2. **Predefined Simulation Programs**
```
Common Program Types:
├── run_sim_loop     - Basic simulation loop
├── run_character    - Character simulation
├── run_legged_train - Legged robot training
├── run_wheeled_chassis - Wheeled chassis simulation
├── run_xbot_orca    - XBot robot simulation
├── run_ackerman     - Four-wheel chassis car simulation
└── Custom programs  - User-configured programs
```

#### 3. **Example Program Startup**
Using the four-wheel chassis car as an example:
```
1. Add the hummer_h2_usda_1 asset to the scene
2. Click the [Run Simulation] button
3. Select the "run_ackerman" program
4. Use WASD keys to control vehicle movement after startup
```



## ⚙️ Simulation Program Configuration

### 📝 Configuration File Description
Simulation programs are configured through the `.orcalab/config.toml` file:

```toml
[[external_programs.programs]]
name = "run_ackerman"
display_name = "Four-Wheel Chassis Car Simulation"
command = "python"
args = ["-m", "examples.wheeled_chassis.run_ackerman"]
description = "Control a four-wheel chassis vehicle for physics simulation"
```

### 🔧 Configuration Parameter Descriptions
```
Required Parameters:
├── name         - Unique program identifier
├── display_name - Interface display name
├── command      - Execution command (typically python)
└── args         - Command-line argument array

Optional Parameters:
└── description  - Program function description
```

### ➕ Adding a Custom Program
```toml
# Example: Add a new simulation program
[[external_programs.programs]]
name = "my_custom_sim"
display_name = "My Custom Simulation"
command = "python"
args = ["-m", "my_project.run_simulation", "--config", "config.yaml"]
description = "Custom robot simulation program"
```

## 🎯 Different Startup Scenarios

### 🏫 Teaching Demonstration Scenario
```
Goal: Demonstrate physics simulation effects
Recommended Flow:
1. Select a predefined scene (e.g., orcalab_day)
2. Load default layout
3. Select "No Simulation Program (Manual Start)"
4. Manually demonstrate physics effects

Key Operations:
├── Use move tool to drag objects
├── Observe gravity and collision effects
├── Adjust object parameters in real-time
└── Showcase physics engine capabilities
```

### 🔬 Algorithm Validation Scenario
```
Goal: Validate control algorithm effectiveness
Recommended Flow:
1. Prepare specific robot models
2. Configure algorithm program
3. Select corresponding simulation program to start
4. Monitor algorithm execution effectiveness

Data Collection:
├── Observe terminal log output
├── Record performance metrics
├── Analyze behavioral performance
└── Adjust algorithm parameters
```

### 🎮 Interactive Experience Scenario
```
Goal: Provide immersive simulation experience
Recommended Flow:
1. Select complex scene layout
2. Start interactive simulation program
3. Use keyboard/mouse for control
4. Experience real-time physics feedback

Interaction Methods:
├── Keyboard control (WASD, etc.)
├── Mouse click interaction
├── VR device control
└── Gamepad input
```

## 📊 Simulation Status Monitoring

### 💻 Terminal Output Monitoring
```
Key Information Types:
├── Program startup status
├── Connection status information
├── Frame rate and performance data
├── Error and warning messages
└── User operation feedback

Monitoring Points:
├── Whether startup was successful
├── Whether connection is stable
├── Whether performance is normal
└── Whether errors occurred
```



### 📈 Performance Metrics
```
Important Metrics:
├── FPS (Frame Rate) - Simulation smoothness
├── CPU Usage - Processor load
├── GPU Usage - Graphics card load
├── Memory Usage - Memory consumption
└── Network Latency - Connection quality
```

## 🛑 Stopping the Simulation

### Normal Stop
```
Method 1: Interface Stop
Click the [Stop Simulation] button [⏹]

Method 2: Program Natural End
Wait for the simulation program to complete automatically

Method 3: Shortcut Key Stop
Use the stop shortcut defined by the program
```

### Force Stop
```
Emergency Handling:
1. Close the terminal window
2. End the Python process
3. Restart the OrcaLab client
4. Check system resource status

Command Line:
# Find and end the Python simulation process
ps aux | grep python
kill -9 <Process ID>
```

## ⚠️ Common Startup Issues

### 🚨 Startup Failure Troubleshooting
```
Checklist:
├── Confirm environment configuration is correct
├── Verify dependency packages are installed
├── Check configuration file syntax
├── Confirm asset packages are downloaded
└── Review detailed error messages

Common Errors:
├── Module import failure → Check Python path
├── Asset loading failure → Confirm asset package exists
├── Port conflict → Restart service or change port
└── Permission denied → Check file permissions
```

### 🔧 Performance Optimization Recommendations
```
Improving Startup Speed:
├── Use SSD for asset storage
├── Close unnecessary background programs
├── Optimize network connection
└── Update graphics drivers

Improving Runtime Performance:
├── Reduce scene complexity
├── Adjust rendering quality
├── Optimize physics parameters
└── Monitor system resources
```

## 🔄 Advanced Startup Tips

### Batch Startup
```bash
# Create a startup script
#!/bin/bash
conda activate orcalab
cd /path/to/project
orcalab &
sleep 10
python -m my_simulation.run_auto
```

### Remote Startup
```bash
# SSH remote startup (requires X11 forwarding)
ssh -X user@remote_host
export DISPLAY=:0.0
conda activate orcalab
orcalab
```

### Debug Mode Startup
```bash
# Enable verbose logging
ORCA_LOG_LEVEL=DEBUG orcalab

# Enable performance profiling
ORCA_PROFILE=1 python -m simulation.run_program
```

Starting simulations correctly is a key step in using OrcaLab for project development. Mastering different startup methods and troubleshooting techniques will help you complete simulation tasks more efficiently.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)