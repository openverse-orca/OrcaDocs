# How to configure data collection tasks?

## Question
When performing VR teleoperation data collection in OrcaLab, I need to configure the data collection script for different tasks (such as pick-and-place, QR code scanning). How should I configure these data collection tasks? What are the core configuration parameters?

## Answer

In OrcaLab, configuring data collection tasks is primarily done by **modifying the configuration file referenced by the data collection script (typically in YAML format)**. This configuration file defines key information such as task type, dynamic objects in the scene, light sources, and task goals, allowing you to flexibly customize different data generation scenarios.

## 📋 Core Modules of the Data Collection Task Configuration File

The configuration file for data collection tasks (e.g., the `example.yaml` file in the `OrcaManipulation` project) typically includes the following core modules:

### 1. **Basic Information**

| Field | Core Function | Key Notes |
|-------------|--------------|--------------------------------------------------|
| `level_name` | Scene name identifier | Used for logging, dataset differentiation, and task replay. Use business-semantic names (e.g., `pharmacy_pick`). |
| `type` | Task type definition | Determines the configuration structure of the `task` module. Currently supports `pick_and_place` (grasp and place) and `scan_qr` (QR code scanning). |

### 2. **Dynamic Objects (Actor)**

| Field | Core Function | Key Notes |
|-------------|------------------|--------------------------------------------------|
| `names` | Names of dynamically loaded objects | Array format; one-to-one correspondence with asset paths in `spawnable`. These are objects that may randomly appear in tasks. |
| `spawnable` | Asset paths | Points to Prefab paths in the Asset Library. Incorrect paths will prevent object generation. |
| `joints` | Object root joints / controllable joints | Defines joints of the object model for pose control. |
| `joints_dof` | Joint degrees of freedom | `1` = single DOF, `3` = spherical joint, `6` = rigid body joint. Count must match `joints` definitions. |
| `random.qpos` | Joint position randomization | `true` = joint positions randomized, `false` = fixed. Used to increase data diversity. |
| `random.nums` | Actor generation count range | Array format (e.g., `[1, 5]`); defines the range for the number of actors of this type generated per task. |
| `random.six_dof.center` | Random center point | Random center point in world coordinate system; objects will be randomly generated around this point. |
| `random.six_dof.bound_position` | XYZ direction offset range | E.g., `[[-0.1, 0.1], [-0.1, 0.1], [0, 0]]` means X, Y directions have ±0.1 random offset, Z direction is fixed. |
| `random.six_dof.bound_rotation` | Rotation range around XYZ axes | In radians; e.g., `[[0, 0], [0, 0], [0, 1]]` means random rotation around the Z axis by 1 unit radian. |

### 3. **Scene Lighting (Light)**

| Field | Core Function | Key Notes |
|-------------|--------------|--------------------------------------------------|
| `names` | Light instance names | Array format; defines light instances in the scene. |
| `spawnable` | Light prefab paths | Points to light Prefab paths. |
| `random.position` | Position randomization | `true`/`false`; whether to enable light position randomization. |
| `random.rotation` | Rotation randomization | `true`/`false`; whether to enable light rotation randomization. |
| `random.center` | Random center point | Center point for random light positions. |
| `random.bound_position` | Position offset range | Random offset range for lights in XYZ directions. |
| `random.bound_rotation` | Rotation range | Random rotation range for lights around XYZ axes (radians). |
| `random.nums` | Generation count range | Array format; number of lights generated per session. |
| `random.cycle` | Update cycle | Update light configuration every `X` tasks to increase data diversity. |

### 4. **Task Logic (Task)**

| Field | Core Function | Key Notes |
|-------------|--------------|--------------------------------------------------|
| `type` | Task type | Must match the top-level `type` (e.g., `pick_and_place`). |
| `goal.name` | Target object/area name | Name of the object or area that is the task goal (e.g., for grasping or placing). |
| `goal.site` | Placement site | The site defined in the scene for placing the target object. If it doesn't exist, the task will fail. |

## 🛠️ New Scene Configuration Steps

1.  **Clarify Task Type**: First determine what type your data collection task belongs to (`pick_and_place` or `scan_qr`); this will determine the basic structure of the configuration file.
2.  **Verify Asset Paths**: Ensure all asset paths referenced in the `spawnable` fields are valid and that the assets are subscribed to in the Asset Library and synced locally.
3.  **Configure Actor Parameters**: Define all dynamic objects involved in the task (such as items the robot will manipulate), including names, asset paths, joint information, and degrees of freedom.
4.  **Set Actor Randomization Rules**: Configure random positions, rotations, and generation counts for objects to increase data diversity and generalization. Be careful not to set random ranges too large to prevent objects from clipping through or falling.
5.  **Configure Light Parameters**: Define lights in the scene and optionally set randomization for light positions, rotations, and quantities to further increase data diversity.
6.  **Configure Task Goals**: Define specific task goals based on task type, such as what object to grasp and which site to place it at.
7.  **Small-Scale Validation**: After configuration, it is recommended to first set `random.nums` to `[1,1]` (i.e., generate only one object) for small-scale testing to verify the configuration is correct, then expand the random ranges.

## ⚠️ Common Configuration Errors & Troubleshooting

### 1. **Asset Loading Failure**
- **Error**: `spawnable` path is incorrect.
- **Troubleshooting**: Verify the Asset Library Prefab path; ensure no typos in the path and that the asset is subscribed.

### 2. **Abnormal Robot Behavior**
- **Error**: `joints` and `joints_dof` counts are inconsistent.
- **Troubleshooting**: Check the array lengths of these two fields and ensure one-to-one correspondence.

### 3. **Abnormal Object Behavior**
- **Error**: Random range is too large, causing objects to clip through or fall.
- **Troubleshooting**: Reduce the `bound_position`/`bound_rotation` range in `six_dof`.

### 4. **Task Cannot Be Completed**
- **Error**: `site` name does not exist.
- **Troubleshooting**: Confirm the site name specified in `goal.site` exists in the scene, or correct the configuration.

## 📝 Summary

Data collection task configuration is accomplished by modifying YAML configuration files, which contain basic task information, dynamic objects (actors), scene lighting, and task logic. Understanding the meaning of each module's fields and configuring them precisely according to task requirements is key to successfully performing VR teleoperation data collection.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to run data collection scripts?](FAQ-list/095-how-to-run-data-collection-scripts.md)
- [Where is collected data saved?](FAQ-list/096-where-is-collected-data-saved.md)