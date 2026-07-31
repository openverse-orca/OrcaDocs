# How to set the simulation time step?

## Question
When running simulations in OrcaLab, the time step is a very important physics engine parameter. How should I understand its role and correctly set the simulation time step to balance accuracy and performance?

## Answer

The **Simulation Time Step** is the amount of simulated time advanced by the physics engine during each update of the simulation state. It is one of the core parameters of physics simulation, directly affecting the **accuracy, stability, and running speed** of the simulation.

## 📋 Understanding the Time Step

### 1. **Definition**
-   The time step is the foundation of discretized simulation time. If a simulation runs with a time step of 0.01 seconds, the physics engine computes 100 physics updates per second.

### 2. **Working Principle**
-   The physics engine does not continuously compute the world state but iteratively calculates in discrete time steps. In each time step, the engine computes the next time step's state based on the current forces, velocities, and other information acting on objects.

### 3. **Relationship with Rendering Framerate**
-   The physics time step is typically independent of the rendering framerate (FPS). A simulation may run at a fixed physics time step while rendering displays the latest physics state at the highest possible framerate.

## 📊 Impact of Time Step

### 1. **Accuracy**
-   **Smaller time steps produce higher simulation accuracy**: Small time steps mean the physics engine updates the world state more frequently, capturing physical events (such as collisions, contacts) in finer detail and reducing computation errors, making simulation results closer to the real world.
-   **Larger time steps produce lower simulation accuracy**: Large time steps may "skip" certain transient physical events, leading to reduced accuracy.

### 2. **Stability**
-   **Smaller time steps produce better simulation stability**: For systems with complex physical interactions (such as high-speed collisions, multi-joint robots), small time steps help improve the physics solver's stability, reducing non-physical phenomena like jitter, penetration, or "explosions."
-   **Larger time steps produce less stable simulations**: Large time steps may prevent the physics solver from converging in a single iteration, leading to unstable physical behavior.

### 3. **Performance / Running Speed**
-   **Smaller time steps mean more computation and slower simulation speed**: The physics engine needs to perform more calculations to handle more updates.
-   **Larger time steps mean less computation and faster simulation speed**: The physics engine's computational burden is reduced.

## 🛠️ How to Set the Time Step

Setting the time step in OrcaLab is typically done through the **simulation program's configuration file** or **Python script**.

### 1. **Set via Configuration File**
-   For projects like `OrcaPlayground`, physics engine parameters (including time step) may be managed through a `.yaml` or `.json` format configuration file.
-   You need to find parameters like `physics_timestep`, `fixed_dt`, or `dt` in the corresponding configuration file and modify their values.

#### Example (Pseudocode)
```yaml
# config.yaml example
physics:
  timestep: 0.005 # Set time step to 0.005 seconds
  iterations: 8
  gravity: [0.0, 0.0, -9.81]
```

### 2. **Set via Python Script**
-   In your custom simulation Python script, you can set or initialize the physics engine's time step through APIs provided by OrcaLab.

#### Example (Pseudocode)
```python
import orca_gym

# Specify the time step when creating a simulation environment instance
env = orca_gym.make('MyRobotEnv', physics_timestep=0.005)

# Or modify via setter method after environment creation
env.physics_timestep = 0.005
```

## 💡 Adjustment Recommendations & Strategies

### 1. **Start from Default**
- OrcaLab or its example projects typically provide a recommended default time step. Start by running the simulation with the default value and observe its performance.

### 2. **Balance Accuracy & Performance**
- **For high-accuracy research or specific physical phenomena**: Choose a smaller time step (e.g., 0.001s or less), but be prepared to sacrifice running speed.
- **For rapid iteration and AI training**: If extreme physical accuracy is not required, you can appropriately increase the time step (e.g., 0.01s) while ensuring stability to accelerate training.
- **Debugging phase**: When debugging physical behavior, use a small time step to capture more detail.

### 3. **Observe Simulation Stability**
- If the simulation exhibits unstable phenomena such as object penetration, severe jitter, or objects flying off abnormally, first try **reducing the time step** or **increasing iterations**.

### 4. **Multiple Tests**
- After each time step adjustment, run the simulation multiple times to observe its impact on physical behavior and running speed.

## ⚠️ Important Notes

### 1. **Excessively Large Time Step**
- May lead to physical instability, unrealistic simulation, or even crashes.

### 2. **Excessively Small Time Step**
- Significantly increases computational burden, causing simulation stutter and reduced real-time performance.

### 3. **Difference from Rendering Framerate**
- Do not confuse the physics time step with the rendering framerate. The physics time step determines the frequency of physical computation, while the rendering framerate determines the frequency of screen updates. They are typically independent, but an excessively slow physics time step will affect rendering.

## 📝 Summary

The simulation time step is a core physics engine parameter in OrcaLab that determines the accuracy, stability, and running speed of the physics simulation. Users should set the time step by modifying configuration files or Python scripts and find the balance point most suitable for their simulation tasks through experimentation.

## Related Links
- [How accurate is OrcaLab's physics simulation?](FAQ-list/010-how-accurate-is-orcalab-physics-simulation.md)
- [How to adjust physics engine parameters?](FAQ-list/085-how-to-adjust-physics-engine-parameters.md)
- [How to improve simulation speed?](FAQ-list/084-how-to-improve-simulation-speed.md)