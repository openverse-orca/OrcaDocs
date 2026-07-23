# How to move and rotate the view in the 3D viewport?

## Question
OrcaLab's 3D viewport is the core area for scene interaction. How should I use the mouse and keyboard to freely move, rotate, and zoom the view to better observe and edit the scene?

## Answer

OrcaLab's 3D viewport provides intuitive combined keyboard and mouse operations, allowing you to easily navigate and view scenes in three-dimensional space. Mastering these shortcuts and operations is crucial for efficient scene building and simulation debugging.

## 📋 3D Viewport Navigation Guide

### 1. **Rotate View (Look Around)**

#### Operation
-   **Right Mouse Button**: Hold down the **right mouse button** and move the mouse.

#### Effect
-   Your viewpoint rotates horizontally and vertically around the current camera position, as if you are turning your head to look around the environment.

### 2. **Move Forward/Backward**

#### Operation
-   **Right Mouse Button + W**: Hold down the **right mouse button**, then press the `W` key to move the view forward.
-   **Right Mouse Button + S**: Hold down the **right mouse button**, then press the `S` key to move the view backward.

#### Effect
-   Your viewpoint translates forward or backward along the current viewing direction, simulating walking.

### 3. **Strafe Left/Right**

#### Operation
-   **Right Mouse Button + A**: Hold down the **right mouse button**, then press the `A` key to move the view left.
-   **Right Mouse Button + D**: Hold down the **right mouse button**, then press the `D` key to move the view right.

#### Effect
-   Your viewpoint translates left or right while maintaining its current orientation, simulating sidestepping.

### 4. **Move Up/Down**

#### Operation
-   **Right Mouse Button + Q**: Hold down the **right mouse button**, then press the `Q` key to move the view up.
-   **Right Mouse Button + E**: Hold down the **right mouse button**, then press the `E` key to move the view down.

#### Effect
-   Your viewpoint translates vertically up or down, simulating flight or elevation.

### 5. **Zoom In/Out**

#### Operation
-   **Mouse Scroll Wheel**: Scrolling forward zooms in (closer), scrolling backward zooms out (farther).

#### Effect
-   Zooms the view in or out centered on the mouse pointer, changing the observation distance.

### 6. **Focus on Selected Object**

#### Operation
-   **Right Mouse Button + Z**: First left-click to select an object in the scene, then hold the **right mouse button** and press the `Z` key.

#### Effect
-   The view quickly moves and focuses on the selected object, filling the screen for convenient close observation and editing.

## 📝 3D Viewport Shortcut Reference

| Function | Shortcut | Notes |
|------------|---------------------------|------------------------------------|
| Move Forward | Right Mouse Button + W | Move forward along camera direction |
| Move Backward | Right Mouse Button + S | Move backward along camera direction |
| Move Left | Right Mouse Button + A | Pan left along camera direction |
| Move Right | Right Mouse Button + D | Pan right along camera direction |
| Move Down | Right Mouse Button + E | Pan down along world Z axis |
| Move Up | Right Mouse Button + Q | Pan up along world Z axis |
| Rotate View | Right Mouse Button (hold and move) | Rotate view around camera center |
| Select Object | Left Mouse Button | Select an object in the scene |
| Zoom View | Mouse Scroll Wheel | Zoom in or out |
| Focus Object | Right Mouse Button + Z | Quickly focus view on selected object |



## 💡 Usage Tips

-   **Combined Operations**: You can achieve more complex navigation by combining these operations. For example, hold the right mouse button and move the mouse to rotate while pressing the `W` key to move forward, achieving flight-like roaming.
-   **Precise Control**: For situations requiring precise view adjustments, use small mouse movements and keyboard presses.
-   **Outline Panel Coordination**: Select an object in the Outline Panel, then use "Right Mouse Button + Z" to quickly focus, then observe and edit details.
-   **Scene Editing Tools**: View navigation is typically used together with the "Move," "Rotate," and "Scale" tools (shortcuts 1, 2, 3) — first navigate the view to the right position, then manipulate objects.

## ⚠️ Important Notes

-   **Camera Speed**: Some simulation software may have options to adjust camera movement speed. For OrcaLab's specific settings, please consult the client's settings or preferences.
-   **View Stuttering**: If your computer's performance is insufficient or the scene is too complex, view movement may stutter. Try simplifying the scene or checking your hardware configuration.

## 📝 Summary

OrcaLab's 3D viewport navigation combines the right mouse button with WASD/QE keys, providing intuitive and powerful view control. Mastering these shortcuts and operations will significantly improve your efficiency in scene building, observation, and debugging in the simulation environment.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [How to select and edit objects in the scene?](FAQ-list/065-how-to-select-and-edit-objects-in-scene.md)