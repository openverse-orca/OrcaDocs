# What parameters does the Transform property include?

## Question
In OrcaLab's "Edit Panel," when I select an object, I see the "Transform" property which includes Position, Rotation, and Uniform Scale. What do these parameters represent?

## Answer

The "Transform" property is the fundamental description of any 3D object's position, orientation, and size in three-dimensional space. In OrcaLab's "Edit Panel," `Position`, `Rotation`, and `Uniform Scale` are the core parameters for controlling an object's Transform properties.

## 📋 Transform Property Details

### 1. **Position**

#### Meaning
-   `Position` defines the object's spatial location in the **world coordinate system**. It typically consists of three floating-point numbers corresponding to the X, Y, and Z axes.
-   The **world coordinate system** is a fixed, unchanging reference frame. Typically the X axis represents left/right, Y axis represents front/back, and Z axis represents up/down (specific directions may vary based on OrcaLab's coordinate system conventions, but Z is usually "up").

#### Parameters
-   `X`: The object's position along the world X axis.
-   `Y`: The object's position along the world Y axis.
-   `Z`: The object's position along the world Z axis.

#### Example
-   If an object's Position is `(0, 0, 0)`, it is located at the world origin.
-   Increasing the Z value moves the object upward.

### 2. **Rotation**

#### Meaning
-   `Rotation` defines the object's rotation angle around its own **local coordinate system's** X, Y, and Z axes. It also typically consists of three floating-point numbers representing Euler angles, usually in degrees or radians.
-   The **local coordinate system** is the object's own inherent coordinate system. When the object rotates, its local coordinate system rotates with it.

#### Parameters
-   `X`: The object's rotation angle around its local X axis.
-   `Y`: The object's rotation angle around its local Y axis.
-   `Z`: The object's rotation angle around its local Z axis.

#### Example
-   Setting X rotation to `90` degrees may cause the object to "tip forward."
-   Setting Z rotation to `45` degrees may cause the object to "rotate 45 degrees in the plane."

#### ⚠️ Euler Angle Gimbal Lock
-   Using Euler angles may encounter the "gimbal lock" problem, where at certain angles, one axis's rotation coincides with another, causing loss of one degree of freedom. For precise or complex rotation animations, quaternions are typically used, but the OrcaLab UI provides the more intuitive Euler angles for users.

### 3. **Uniform Scale**

#### Meaning
-   `Uniform Scale` defines the **uniform scaling** factor of the object in all three directions (X, Y, Z). It is typically a single floating-point number representing a uniform scale factor.
-   "Uniform" means X, Y, and Z axes are scaled by the same amount, preserving the object's original aspect ratio and avoiding distortion.

#### Parameters
-   `Scale`: The object's scale factor relative to its original size. `1.0` is original size, `2.0` is doubled, `0.5` is halved.

#### Example
-   If Scale is `1.0`, the object maintains its original size.
-   Setting Scale to `1.5` enlarges the object by 1.5 times in all directions.

#### ⚠️ Non-Uniform Scale
-   Some 3D software also provides Non-Uniform Scale, allowing independent scaling along X, Y, Z axes. The OrcaLab UI provides `Uniform Scale` to avoid accidental object distortion. Non-uniform scaling may require scripting or more advanced tools.

## 🛠️ Modifying Transform Properties in the "Edit Panel"

OrcaLab's "Edit Panel" provides two main methods for modifying Transform properties:

### 1. **Direct Numeric Input**
-   Click the value input box next to Position, Rotation, or Scale.
-   Enter the precise value you want, then press `Enter` to confirm.
-   **Advantage**: Precise control.

### 2. **Slider Adjustment**
-   Hover the mouse cursor over the data bar of a numeric input box; left/right arrows typically appear or it becomes draggable.
-   Hold the left mouse button and drag to adjust values in real-time and see corresponding changes in the "Viewport."
-   **Advantage**: Intuitive, suitable for quick adjustments and previews.



## 💡 Best Practices

-   **Precise Placement**: For precise connections of robot joints or exact alignment of scene elements, prioritize numeric input.
-   **Quick Adjustment**: For rough scene layout or effect adjustments, use slider adjustment or the top move/rotate/scale tools.
-   **Parent-Child Relationship Effects**: When objects have parent-child relationships, the parent's Transform changes propagate to all children. A child's Transform is relative to its parent — a local transformation.
-   **Reset Transform**: Sometimes you may need to reset an object's Transform properties to default values (e.g., Position at (0,0,0), Rotation at (0,0,0), Scale at 1.0), which is typically available in a right-click menu or specific button.

## 📝 Summary

`Position`, `Rotation`, and `Uniform Scale` in OrcaLab's "Edit Panel" are the three core parameters controlling the "transformation" of objects in the scene. `Position` defines location in world coordinates, `Rotation` defines orientation in local coordinates, and `Uniform Scale` defines uniform proportional scaling. Understanding the meaning of these parameters and how to modify them is fundamental to efficient scene building and simulation debugging.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [How to select and edit objects in the scene?](FAQ-list/065-how-to-select-and-edit-objects-in-scene.md)