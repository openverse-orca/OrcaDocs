# What are the Outline and Camera panels used for?

## Question
The left side of the OrcaLab client interface has a module that can toggle between "Outline" and "Camera." What are the functions of these two panels? What roles do they play in scene management and view control?

## Answer

The module on the left side of the OrcaLab client integrates the "Outline Panel" and "Camera Panel," which are key tools for managing scene content and controlling views. These two panels work together to help users efficiently organize and navigate complex 3D simulation scenes.

## 📋 Outline Panel

### 1. **Purpose**
- **Hierarchy Management**: Clearly displays the parent-child hierarchical relationships of all objects in the scene (including robots, props, environmental elements, lights, cameras, etc.) in a tree structure.
- **Object Selection & Location**: Allows users to quickly select any object in the scene and directly jump to that object's position in the viewport.
- **Visibility Control**: Typically allows controlling the visibility of individual objects or entire groups.

### 2. **Main Functions**
-   **Display Scene Hierarchy**: All objects added to the scene are listed in the Outline Panel with indentation reflecting their parent-child relationships.
-   **Object Selection**: Click an object's name in the list to select it. In the "Viewport," the object will be highlighted, and its properties will be displayed in the "Edit Panel."
-   **Add Group**: Combine multiple objects into a group for convenient overall management and operation.
    -   **Method 1**: Right-click in empty Outline area → "Add Group."
    -   **Method 2**: Right-click on any asset in the Outline list → "Add Group."
-   **Delete Asset**:
    -   **Method 1**: Select asset/group in the Outline list, right-click → "Delete."
    -   **Method 2**: Select asset/group in the Outline list, press the `Delete` key on your keyboard.
-   **Rename Asset**: Select asset/group in the Outline list, right-click → "Rename."
-   **Drag to Adjust Hierarchy**: Dragging an object can change its position in the hierarchy, thereby changing its parent-child relationship.

### 3. **Application Scenarios**
-   **Complex Scene Management**: For scenes with many objects and robot components, the Outline Panel is an essential tool for efficient management and navigation.
-   **Parent-Child Relationship Debugging**: Inspect and adjust parent-child hierarchical relationships to ensure correctness of motion and transformations.
-   **Quick Selection**: When objects are densely packed in the viewport and hard to select by clicking, selecting in the Outline Panel is more convenient.


## 📷 Camera Panel

### 1. **Purpose**
- **View Perspective Management**: Used to manage and switch the observation perspective of the OrcaLab client's 3D viewport.
- **Camera Parameter Adjustment**: Typically allows adjusting various camera properties such as position, rotation, focal length, and field of view.

### 2. **Main Functions**
-   **Display Camera List**: Lists all available cameras in the scene, including default cameras and user-added custom cameras.
-   **Switch View Perspective**: Click a camera name in the camera list, and the 3D viewport will immediately switch to that camera's perspective.
-   **Add New Camera**: New cameras can typically be added to the scene via a right-click menu or a specific button.
-   **Edit Camera Properties**: After selecting a camera, you can adjust its Transform properties (position, rotation) and other camera parameters (such as FOV, near/far clipping planes) in the "Edit Panel."

### 3. **Application Scenarios**
-   **Multi-Angle Observation**: Observe the simulation scene and robot behavior from different angles and positions.
-   **Cinematic Recording**: Set up multiple camera positions for recording high-quality simulation videos.
-   **AI Training Perception**: Simulate robots equipped with cameras at different perspectives and parameters to collect diverse visual data.
-   **Robot Perception Debugging**: Observe the environment from the robot's own "eyes" (camera perspective).



## 💡 Collaboration Between Outline & Camera Panels

### 1. **Selection & Observation**
-   Select an object in the Outline Panel, then switch to the Camera Panel and choose an appropriate camera perspective to observe that object.
-   Or, after selecting an object in the Outline Panel, use the "Right Mouse Button + Z" shortcut to quickly focus, then switch to the Camera Panel to adjust the perspective for detailed observation.

### 2. **Managing Objects and Cameras**
-   Cameras themselves are also special objects in the scene and will appear in the Outline Panel. You can rename, group, and delete cameras in the Outline Panel.
-   Select a camera in the Camera Panel, then adjust its parameters in the "Edit Panel" to better control its position and field of view in the scene.

## ⚠️ Important Notes

### 1. **Default Camera**
- OrcaLab typically provides a default free-perspective camera that allows you to freely roam the scene. User-added cameras are fixed at specific positions in the scene.

### 2. **Performance Impact**
- Adding too many cameras in the scene, especially those rendering at high quality, may have some impact on simulation performance.

### 3. **Cameras & Rendering**
- The Camera Panel is primarily used to control the rendering perspective. In AI simulation, there may be virtual sensor cameras that do not directly render to the screen but are used to generate data.

## 📝 Summary

The "Outline Panel" and "Camera Panel" are two closely related modules in the OrcaLab client. The Outline Panel is used to organize and manage all objects and their hierarchies in the scene, while the Camera Panel is used to manage and switch between different observation perspectives. Proficient use of these two tools can greatly improve your efficiency in building, debugging, and observing simulation scenes in OrcaLab.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to move and rotate the view in the 3D viewport?](FAQ-list/062-how-to-move-and-rotate-view-in-3d-view.md)
- [How to select and edit objects in the scene?](FAQ-list/063-how-to-select-and-edit-objects-in-scene.md)