# How to select and edit objects in the scene?

## Question
In OrcaLab's 3D viewport, how should I select an object in the scene? After selecting it, how do I modify its Transform properties such as position, rotation, and scale in the "Edit Panel"?

## Answer

OrcaLab provides intuitive interaction methods for selecting and editing objects in the scene. Selecting through the "Viewport" and "Outline Panel," then precisely modifying properties through the "Edit Panel," is key to efficiently building and debugging scenes.

## 📋 Object Selection & Editing Process

### Step 1: Select an Object in the Scene

You can select objects in the scene through two main methods:

#### 1. **Direct Click in the 3D Viewport (Recommended)**
-   **Operation**: Move your mouse over the object you want to select, then click the **left mouse button**.
-   **Effect**: The selected object typically displays a **highlighted border** or **outline**, indicating it has been selected. Simultaneously, the corresponding object in the "Outline Panel" will also be highlighted.

#### 2. **Select in the Outline Panel**
-   **Operation**: In the OrcaLab interface's "Outline Panel" (typically on the left), find the name of the object you want to select, then click its name.
-   **Effect**: The object will be highlighted in the "Viewport," and its properties will be displayed in the "Edit Panel."



#### 💡 Quick Focus on Selected Object
-   After selecting an object in the viewport, hold the **right mouse button** and press the `Z` key. The view will automatically focus on that object, making it convenient for close observation and editing.

### Step 2: Navigate to the "Edit Panel"

-   When you select an object, the "Edit Panel" in the OrcaLab interface (typically on the right) will automatically display the properties of the selected object.



### Step 3: Edit Transform Properties

The "Edit Panel" is primarily used to modify an object's **Transform properties**, including Position, Rotation, and Uniform Scale.

#### 1. **Modify Position**
-   **Function**: Controls the object's X, Y, Z coordinates in 3D space.
-   **Operation**:
    -   **Direct Numeric Input**: Click the X, Y, Z input boxes next to Position, enter precise values, then press Enter to confirm.
    -   **Slider Adjustment**: Hover your mouse over the data bar of the X, Y, Z input boxes to reveal left/right arrows. Hold and drag these arrows to adjust values in real-time, with changes visible in the viewport.

#### 2. **Modify Rotation**
-   **Function**: Controls the object's rotation angle around its own coordinate system's X, Y, Z axes.
-   **Operation**: Similar to Position, you can enter angle values directly or drag the sliders to adjust.

#### 3. **Modify Uniform Scale**
-   **Function**: Controls the uniform scale factor of the object. Changing one value scales all X, Y, Z axes proportionally.
-   **Operation**: Similar to Position, you can enter values directly or drag the sliders to adjust.

## 🛠️ Interface Tool Editing

In addition to entering precise values in the "Edit Panel," you can also use OrcaLab's top **toolbar buttons** (shortcuts 1, 2, 3) in combination with the mouse to intuitively edit objects in the 3D viewport.

### 1. **Move Tool (Translate) - Shortcut 1**
-   After selecting an object, click the top "Move" button (or press the `1` key).
-   In the viewport, a 3D coordinate axis handle consisting of red (X-axis), green (Y-axis), and blue (Z-axis) arrows will appear at the object's center.
-   Click and drag an arrow to move the object along the corresponding axis; drag a plane to move the object along that plane.

### 2. **Rotate Tool (Rotate) - Shortcut 2**
-   After selecting an object, click the top "Rotate" button (or press the `2` key).
-   In the viewport, a rotation handle consisting of red, green, and blue rings will appear at the object's center.
-   Click and drag a ring to rotate the object around the corresponding axis.

### 3. **Scale Tool (Scale) - Shortcut 3**
-   After selecting an object, click the top "Scale" button (or press the `3` key).
-   In the viewport, a scale handle consisting of red, green, and blue cubes will appear at the object's center.
-   Click and drag a cube to scale the object along the corresponding axis; drag the center cube for uniform scaling.

## 💡 Common Tips & Best Practices

-   **Coarse First, Then Fine-Tune**:
    -   For large-scale movement and placement, use the mouse with the top toolbar to drag in the viewport.
    -   For precise positions and angles, enter values directly in the "Edit Panel."
-   **Multi-Select Objects**: Hold the `Ctrl` key (or `Shift` key) to select multiple objects, then move, rotate, or scale them simultaneously.
-   **Save Layout**: After completing scene setup and object editing, be sure to save your work via "File" → "Save Layout" or "Save As" to avoid data loss.

## ⚠️ Important Notes

### 1. **Coordinate System**
- OrcaLab may use different coordinate systems (such as right-handed or left-handed). Pay attention to documentation or interface cues to ensure you understand the X, Y, Z axis directions.

### 2. **Physical Properties**
- Besides Transform properties, objects may also have physical properties such as mass, friction, and restitution coefficients. These are typically further down in the "Edit Panel" or in other panels and need to be adjusted based on simulation requirements.

### 3. **Editing in Simulation Mode**
- In simulation running mode, you can edit an object's Transform properties, but the object's behavior will be influenced by the physics engine. In simulation mode, the `F3` shortcut can be used to reset an object's position (typically restoring it to its initial position before simulation started).

## 📝 Summary

OrcaLab provides two methods to select objects: directly clicking in the "Viewport" and selecting in the "Outline Panel." After selection, you can precisely modify Transform properties such as position, rotation, and scale in the "Edit Panel," or use the top toolbar for intuitive drag editing in the viewport. Mastering these operations is the foundation for efficient scene building and object interaction.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to move and rotate the view in the 3D viewport?](FAQ-list/062-how-to-move-and-rotate-view-in-3d-view.md)