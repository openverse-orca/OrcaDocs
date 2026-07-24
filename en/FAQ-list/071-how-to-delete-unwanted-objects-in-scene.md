# How to delete unwanted objects in the scene?

## Question
When building scenes in OrcaLab, I may add unwanted objects, or need to remove certain elements during cleanup and optimization. How can I delete objects that are no longer needed in the scene?

## Answer

In the OrcaLab client, deleting objects in the scene is a simple and intuitive operation, primarily done through the **Outline Panel** or the **3D Viewport**. Properly deleting objects helps keep the scene clean and improves simulation performance.

## 📋 Deleting Scene Objects

### 1. **Delete via Outline Panel (Recommended)**

#### Advantages
-   More precise, less prone to mistaken deletion.
-   Can clearly see the object to delete and its hierarchical relationships.

#### Steps
1.  **Open the "Outline Panel"**: Ensure the module on the left side of the OrcaLab client interface is in "Outline" mode.
2.  **Select the Target Object/Group**: Find the object or group you want to delete in the Outline list.
3.  **Execute Deletion**:
    -   **Right-Click Menu**: After selecting the object, click the **right mouse button** and select "**Delete**" from the context menu.
    -   **Keyboard Delete Key**: After selecting the object, press the `Delete` key (or `Del` key) on your keyboard.



### 2. **Delete via 3D Viewport**

#### Advantages
-   More intuitive, operates directly in the 3D scene.

#### Steps
1.  **Select the Object in the 3D Viewport**: **Left-click** the object you want to delete to select it (typically displays a highlighted border).
2.  **Execute Deletion**:
    -   **Keyboard Delete Key**: Press the `Delete` key on your keyboard.



## ⚠️ Important Notes for Deletion

### 1. **Irreversible Operation**
-   **Typically, deletion is irreversible**. Once deleted, the object is permanently removed from the scene and cannot be directly recovered.
-   **Use the "Undo" Feature**: If you accidentally delete an object, try using the "Edit" menu's "Undo" (Ctrl+Z) feature to recover. However, this feature typically only recovers the most recent few operations.

### 2. **Parent-Child Relationship Effects**
-   **Deleting a Parent Object**: If you delete a group or a parent object with children, **all its child objects will also be deleted**.
    -   For example, deleting the "Robot Arm Base" may cause the entire robotic arm to be deleted.
-   Before deleting, carefully check the Outline Panel to confirm the object you want to delete has no important child components.

### 3. **Scene Dependencies**
-   **Functional Objects**: Certain objects may be critical to the normal operation of the scene (such as light sources, environment controllers, simulation starting points, etc.). Deleting them may cause scene display anomalies or impaired simulation functionality.
-   **Script References**: If your Python simulation scripts or layout files reference a specific object, deleting it may cause script errors or scene loading failures.

### 4. **Save Layout**
-   Before performing deletion, it is recommended to **save the current layout** first, so you can restore to the previous state if you accidentally delete something or are unsatisfied with the deletion result.
-   After deleting objects, be sure to **save the layout again** for the changes to take effect.

## 💡 Best Practices

### 1. **Confirm in the Outline Panel**
- Always first find the object to delete in the Outline Panel, confirm its name and hierarchy, then perform the deletion. This avoids mistaken deletion in complex scenes.

### 2. **Use Groups**
- Organize related objects into groups. This makes it easy to manage a set of objects and allows you to delete an entire group at once when needed.

### 3. **Hide Before Delete**
- If you're unsure whether an object needs to be deleted, you can first **hide** it in the Outline Panel (typically via an eye icon next to it or a right-click menu entry), observe whether the scene is affected, and then delete once confirmed.

### 4. **Back Up Layout Files**
- For important projects, regularly backing up layout files is a good habit. Even if you accidentally delete objects in the scene, you can recover by loading the backup file.

## 📝 Summary

In OrcaLab, deleting scene objects is primarily done by selecting them in the Outline Panel and using the right-click menu or Delete key, or by selecting in the 3D viewport and pressing the Delete key. When performing deletion, please be cautious, fully understand the impact on parent-child relationships and scene functionality, and develop the habit of saving and backing up promptly.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to add groups and manage asset hierarchy?](FAQ-list/065-how-to-add-groups-and-manage-asset-hierarchy.md)
- [How to save and load custom layouts?](FAQ-list/068-how-to-save-and-load-custom-layouts.md)