# How to adjust physics engine parameters?

## Question
As a high-fidelity physics AI simulation system, OrcaLab's physics engine parameters (such as time step, iterations, gravity, etc.) have a significant impact on simulation results and performance. How should I adjust these physics engine parameters to balance accuracy and efficiency?

## Answer

Adjusting OrcaLab's physics engine parameters is key for advanced users to optimize simulation behavior and performance. These parameters determine the accuracy, stability, and running speed of the physics simulation. Typically, these parameters can be configured in the **simulation program's configuration file** or **Python script**.

## 📋 Core Physics Engine Parameters & Adjustment

### 1. **Time Step / Fixed Step**

#### Meaning
-   The amount of simulation time advanced by the physics engine in one simulation step. For example, if the time step is 0.01 seconds, the physics engine computes 100 updates per second.

#### Impact
-   **Accuracy**: **The smaller the time step, the higher the physics simulation accuracy**, more accurately capturing high-speed motion and rapidly changing physical interactions.
-   **Stability**: For complex or high-speed physical systems, small time steps help improve stability, reducing issues such as penetration and jitter.
-   **Performance**: **The smaller the time step, the greater the computation load, and the slower the simulation runs**; conversely, larger time steps increase speed but may decrease accuracy and stability.

#### Adjustment Recommendations
-   **Balance**: Choose the largest possible time step that still ensures sufficient accuracy and stability to improve performance.
-   **Default Value**: OrcaLab typically has a default physics time step (such as 0.01s or 0.005s).
-   **Configuration File/Script**: Look for parameters such as `time_step`, `fixed_dt` in the simulation program's configuration file (e.g., `config.yaml`) or Python script for adjustment.

### 2. **Iterations**

#### Meaning
-   The number of iterations the physics solver performs in each time step to resolve constraints (such as joint limits, collision contacts).

#### Impact
-   **Accuracy**: **More iterations lead to higher constraint satisfaction accuracy**, e.g., reduced joint jitter, more stable collision contacts, and "stiffer" physical effects.
-   **Performance**: **More iterations increase computation load and slow down simulation speed**; conversely, fewer iterations increase speed but may lead to constraint violations, object penetration, or instability.

#### Adjustment Recommendations
-   **Joints/Collisions**: Scenes with many joints or complex collisions may require higher iteration counts to ensure stability.
-   **Balance**: Choose the lowest possible iteration count that still satisfies simulation stability to improve performance.
-   **Configuration File/Script**: Look for parameters such as `solver_iterations`, `physics_steps_per_frame` in the simulation program's configuration file or Python script for adjustment.

### 3. **Gravity**

#### Meaning
-   Defines the gravitational acceleration vector acting on all objects with physical properties in the scene. Typically `[0, 0, -9.81]` (Z-axis downward).

#### Impact
-   **Physical Behavior**: Directly affects the falling speed and parabolic trajectories of objects.

#### Adjustment Recommendations
-   **Usually Unchanged**: For simulations of Earth environments, gravity is typically set to `[0, 0, -9.81]`. In most cases, this parameter does not need adjustment.
-   **Special Scenarios**: If simulating a lunar environment (lower gravity) or zero-gravity environment (such as space), this value can be modified.
-   **Configuration File/Script**: Typically configurable in scene configuration or simulation program.

### 4. **Friction Coefficient**

#### Meaning
-   Defines the magnitude of friction between object surfaces. Typically divided into static friction and dynamic friction.

#### Impact
-   **Sliding & Rolling**: High friction coefficients make objects harder to slide or roll and easier to stop.
-   **Robot Grasping**: For robotic arm grasping tasks, precise friction coefficients are crucial.

#### Adjustment Recommendations
-   **Material Properties**: Friction coefficients are typically defined as properties of object materials or collision bodies. In the OrcaLab client's "Edit Panel," you can select an object and find and modify its physical material properties.
-   **Experimental Adjustment**: Adjust experimentally based on real-world material characteristics until simulation behavior matches expectations.

### 5. **Restitution / Bounciness**

#### Meaning
-   Defines the "elasticity" of object collisions. Values close to 0 indicate almost no bounce after collision (like mud), while values close to 1 indicate perfectly elastic collisions (like a super ball).

#### Impact
-   **Collision Bounce**: Directly affects the height and speed of object rebound after collision.

#### Adjustment Recommendations
-   **Material Properties**: Similar to friction coefficient, restitution is defined as a property of object materials or collision bodies.
-   **Realism**: Adjust based on the real material characteristics of the simulated objects.

## 🛠️ Adjustment Approaches

### 1. **OrcaLab Client "Edit Panel"**
-   For material-related physical properties of individual scene objects such as **friction coefficient and restitution**, you can directly modify them in the "Edit Panel" after selecting the object.
-   Transform properties (position, rotation, scale), while not directly physics engine parameters, directly affect physical interaction and can also be adjusted here.

### 2. **Simulation Program Configuration File (`.orcalab/config.toml` or custom YAML)**
-   Some global physics parameters (such as time step, iterations) or scene-level gravity settings may be defined in the simulation program's configuration file.
-   For example, in projects like `OrcaPlayground`, there may be a `config.yaml` file to configure physics-related parameters.

### 3. **Python Simulation Script**
-   In custom Python simulation scripts, set physics world parameters through OrcaLab's API interfaces (such as `orca-gym`).
    ```python
    # Example pseudocode: actual API may differ
    env = orca_gym.make('MyEnv', physics_timestep=0.005, solver_iterations=8)
    env.set_gravity([0, 0, -9.81])
    ```

## ⚠️ Important Notes

### 1. **Balance Accuracy & Performance**
-   Physics parameter adjustment is typically a trade-off between accuracy and performance. Improving accuracy (small time step, high iterations) usually reduces performance, and vice versa.

### 2. **Stability**
-   Unreasonable physics parameters (such as excessively large time steps, too few iterations) may lead to simulation instability, resulting in abnormal phenomena such as object penetration, jitter, or "explosions."

### 3. **Debugging & Testing**
-   After each physics parameter adjustment, run the simulation for thorough testing and observe whether the behavior meets expectations.

### 4. **Documentation Reference**
-   Consult OrcaLab's official documentation or the API documentation of related libraries such as `orca-gym` to understand specific parameter names, value ranges, and default values.

## 📝 Summary

OrcaLab's physics engine parameters can be adjusted through the client's "Edit Panel," the simulation program's configuration files, or Python scripts. Core parameters include time step, iterations, gravity, friction coefficient, and restitution coefficient. Understanding and appropriately adjusting these parameters is key to achieving high-accuracy, stable, and efficient simulation experiences.

## Related Links
- [How accurate is OrcaLab's physics simulation?](FAQ-list/010-how-accurate-is-orcalab-physics-simulation.md)
- [How to improve simulation speed?](FAQ-list/084-how-to-improve-simulation-speed.md)
- [How to select and edit objects in the scene?](FAQ-list/063-how-to-select-and-edit-objects-in-scene.md)