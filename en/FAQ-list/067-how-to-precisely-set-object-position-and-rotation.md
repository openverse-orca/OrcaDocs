# How to precisely set an object's position and rotation?

## Question
In OrcaLab, I need to precisely place scene objects at specific positions or rotate them to exact angles. Besides drag tools, how can I achieve precise control through numeric input?

## Answer

In OrcaLab's "Edit Panel," you can precisely control the position and rotation of selected scene objects through direct numeric input. This is crucial for tasks requiring high-precision scene building and robot pose configuration.

## 📋 Precise Position & Rotation Setting Process

### Step 1: Select the Object to Edit

-   Left-click the object in OrcaLab's **3D Viewport**, or select the object's name in the **Outline Panel**.
-   Once the object is selected, its Transform properties will be displayed in the "Edit Panel."


### Step 2: Navigate to the "Edit Panel"

-   The "Edit Panel" is typically on the right side of the OrcaLab client interface. Here you'll find the "Transform" properties with X, Y, Z input boxes for "Position" and "Rotation."



### Step 3: Precisely Set Position

#### 1. **Understanding Position Parameters**
-   `Position` controls the object's X, Y, Z coordinates in the **world coordinate system**.
-   **X**: Typically represents horizontal position (left/right).
-   **Y**: Typically represents longitudinal position (front/back).
-   **Z**: Typically represents vertical position (up/down).

#### 2. **Numeric Input Operation**
-   Click the `X`, `Y`, or `Z` input box next to Position.
-   Directly enter the precise value you want (can be integer or decimal).
-   After entering, press `Enter` (or click outside the input box) to apply the change.

#### Example
-   Place an object precisely 2.5 units above the world origin:
    -   `Position X`: `0`
    -   `Position Y`: `0`
    -   `Position Z`: `2.5`

### Step 4: Precisely Set Rotation

#### 1. **Understanding Rotation Parameters**
-   `Rotation` controls the object's rotation angle around its **local coordinate system's** X, Y, Z axes, typically in **degrees**.
-   **X**: Rotation angle around the X axis.
-   **Y**: Rotation angle around the Y axis.
-   **Z**: Rotation angle around the Z axis.

#### 2. **Numeric Input Operation**
-   Click the `X`, `Y`, or `Z` input box next to Rotation.
-   Directly enter the precise angle value you want (e.g., `90`, `180.5`, `-45`).
-   After entering, press `Enter` (or click outside the input box) to apply the change.

#### Example
-   Rotate an object 90 degrees around the Z axis:
    -   `Rotation X`: `0`
    -   `Rotation Y`: `0`
    -   `Rotation Z`: `90`

## 💡 Best Practices & Advanced Tips

### 1. **Use Slider Adjustment for Fine-Tuning**
-   While numeric input provides precise control, for minor adjustments, you can hover the mouse over a numeric input box. When left/right arrows appear, hold the left mouse button and drag for slider adjustment, which provides more intuitive fine-tuning.

### 2. **Pay Attention to the Coordinate System**
-   OrcaLab typically uses a right-handed coordinate system, but different engines or models may have different axis conventions (e.g., some software has Y up, others have Z up). Observe the actual scene to understand axis directions and adjust accordingly.

### 3. **Parent-Child Relationship Effects**
-   If an object is a child of a parent object, its Position and Rotation values are relative to the parent's local coordinate system, not the world coordinate system. This means the parent's movement and rotation affect all children's world positions and orientations, while the children's own Transform values remain fixed relative to the parent.

### 4. **Freeze Transforms**
-   Some 3D software has a "Freeze Transforms" feature that treats the object's current position, rotation, and scale as its "original" state and zeros out the Transform values. OrcaLab may achieve a similar effect through specific operations or scripts; consult advanced development documentation for details.

### 5. **Shortcut Assistance**
-   Use `1` (Move tool), `2` (Rotate tool), `3` (Scale tool) to activate handles in the viewport for rough drag adjustments, then go to the "Edit Panel" for precise numeric input.

## ⚠️ Common Questions

### Q: I entered precise values, but the object didn't move or rotate to my expected position?
A: 1. Check that the values you entered are correct.
   2. Confirm you're editing the correct object.
   3. If the object has a parent, note that its Position and Rotation are relative to the parent. If the parent itself has transformations, the object's world position will be affected.
   4. Check if there are physical constraints or scripts overriding the object's Transform properties.

### Q: Why does rotation sometimes behave unexpectedly?
A: This may be the Euler angle "gimbal lock" phenomenon. At certain angles, Euler angles cause one rotation axis to lose independence. For complex rotation animations, quaternions are typically more stable, but UIs generally provide Euler angles. In OrcaLab, you may need to try rotating from different axes or in smaller increments.

## 📝 Summary

Through the Position and Rotation input boxes in OrcaLab's "Edit Panel," you can precisely set the position and angle of scene objects. Understanding the meaning of these parameters, combined with intuitive slider adjustment and viewport tools, will help you efficiently and accurately build and adjust simulation scenes.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What parameters does the Transform property include?](FAQ-list/066-what-parameters-does-the-transform-property-include.md)
- [How to select and edit objects in the scene?](FAQ-list/063-how-to-select-and-edit-objects-in-scene.md)