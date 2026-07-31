# How to switch between different camera views?

## Question
In OrcaLab's 3D viewport, I can roam freely, but sometimes I want to observe the scene from a preset or specific camera angle. How can I switch between different camera views?

## Answer

The OrcaLab client's "Camera Panel" module (typically on the same side as the "Outline Panel," accessed by switching tabs) is specifically designed for managing and switching between different observation perspectives in the scene. Through it, you can conveniently switch between free perspective, preset cameras, or custom cameras.

## 📋 Switching Camera Views

### Step 1: Enter the "Camera Panel"

-   In the module on the left side of the OrcaLab client interface, click the "Cameras" tab to enter the "Camera Panel" module.


### Step 2: Select and Switch Cameras

-   In the "Camera Panel," a list is displayed containing all available cameras in the current scene. These may include:
    -   **Default Free Camera**: A perspective that allows you to freely roam using the mouse and keyboard.
    -   **Preset Scene Cameras**: If the scene comes with preset cameras, they will also appear in the list.
    -   **User-Defined Cameras**: Cameras you have added to the scene yourself.
-   **Operation**: In the camera list, click the name of the camera you want to switch to.
-   **Effect**: The 3D viewport will immediately switch to the perspective of the selected camera. For example, if you select a camera fixed to a robot arm, the view will switch to that robot's "first-person" perspective.

### Step 3: Manage and Edit Cameras (Optional)

-   **Add New Camera**: You can typically add a new camera to the scene via the right-click menu in the "Camera Panel" or a specific button in the top toolbar.
-   **Edit Camera Properties**: Select a camera in the "Camera Panel," and its properties (such as position, rotation, field of view FOV, near/far clipping planes, etc.) will be displayed in the "Edit Panel." You can adjust them as needed.
    -   **Position & Rotation**: Adjust the camera's physical position and orientation in the scene.
    -   **Field of View (FOV)**: Affects the "wide-angle" or "telephoto" effect of the camera.
    -   **Near/Far Clip Plane**: Defines the nearest and farthest distances the camera can see.

## 💡 Camera View Application Scenarios

### 1. **Multi-Angle Observation & Debugging**
- **Inspect Robot Behavior from Different Angles**: For example, view a robot's path planning from above, or observe a robotic arm's grasping motion from the side.
- **Debug Scene Elements**: Check the alignment or status of a specific object from a specific camera perspective.

### 2. **Perception Data Collection for AI Training**
- **Simulate Robot Sensors**: Place cameras on robot models to simulate the visual sensors carried by the robot.
- **Generate Diverse Datasets**: By switching between different camera perspectives or adjusting camera parameters, you can generate visual data from different viewpoints for AI model training and generalization.

### 3. **Demonstration & Recording**
- **Cinematic Perspectives**: Set up multiple preset camera paths for smooth transitions during demonstrations or video recording, providing a more cinematic viewing experience.
- **Specific Task Demonstration**: Focus on showcasing the execution process of a key task in the simulation by switching cameras.

## ⚠️ Important Notes

### 1. **Performance Impact**
- Activating multiple cameras in the scene or rendering high-resolution camera images may have some impact on simulation performance.

### 2. **Cameras & Outline Panel**
- Cameras themselves are also objects in the scene and will appear in the "Outline Panel." Operations you perform on cameras in the Outline Panel (such as renaming, deleting) will synchronously affect the Camera Panel.

### 3. **Free Perspective vs. Fixed Perspective**
- The free perspective camera allows users to freely roam using the mouse and keyboard. Cameras added to the scene are typically fixed at a specific position or follow a specific object, providing a fixed observation point.

### 4. **Python Script Control**
- In advanced development, cameras can be dynamically created, managed, and switched through Python scripts, enabling more complex visual control and data collection.

## 📝 Summary

OrcaLab's "Camera Panel" is the core tool for managing and switching 3D viewport perspectives. By selecting different cameras, you can examine your simulation scene from a variety of preset or custom observation points, which is very useful for debugging, demonstration, and perception data collection in AI training.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to move and rotate the view in the 3D viewport?](FAQ-list/062-how-to-move-and-rotate-view-in-3d-view.md)