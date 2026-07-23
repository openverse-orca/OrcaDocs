# How to add groups and manage asset hierarchy?

## Question
In OrcaLab's "Outline Panel," my scene contains multiple objects — how can I better organize them? How do I add groups, adjust object hierarchy, and perform management operations such as renaming and deleting?

## Answer

In OrcaLab's "Outline Panel," organizing and managing scene assets through **Groups** and **hierarchical relationships** is key to improving work efficiency. This allows you to clearly structure complex scenes, much like managing a file system.

## 📋 Outline Panel Asset Hierarchy Management

The "Outline Panel" displays all objects in the scene in a tree structure showing parent-child relationships, and is the core interface for organization and management.



### 1. **Add Group**

A group is a container for logically organizing multiple related assets, allowing unified operations (such as move, rotate) on all members of the group.

#### Method 1: Right-Click in Empty Outline Area to Create an Empty Group
1.  Move your mouse to an empty area in the "Outline Panel."
2.  Click the **right mouse button**.
3.  In the context menu that appears, select "**Add Group**" (or a similar option).
4.  A new empty group (typically named "Group" or "New Group") will be created.

#### Method 2: Right-Click on Existing Assets to Create a Group
1.  In the Outline Panel, select one or more existing assets.
2.  Click the **right mouse button**.
3.  In the context menu that appears, select "**Add Group**."
4.  The system will automatically place the selected assets into the newly created group.

#### 💡 Use Cases
-   Place all components of a robot (such as the arm body, gripper, sensors) into one group for convenient overall movement.
-   Place scene props from a certain area (such as tables, chairs, computers) into one group.

### 2. **Adjust Asset Hierarchy**

The hierarchical relationship between assets determines their parent-child relationship. Child objects will follow the parent object's transformations (move, rotate, scale).

#### Operation: Drag
1.  **Set as Child Object**: In the Outline Panel, click and drag a child object onto the name of another parent object.
    -   While dragging, the parent object's name typically highlights, indicating a parent-child relationship can be established.
    -   When you release the mouse, the dragged object becomes a child of the target parent object and appears indented.
2.  **Remove Parent-Child Relationship**:
    -   Drag a child object to the root of the Outline Panel (a non-indented position) to detach it from all parent objects and make it a top-level object in the scene.
    -   Or drag it under another sibling object to make it a child of a new parent object.

#### 💡 Use Cases
-   **Robot Joints**: Each link of a robotic arm is a child of the previous link, ultimately all links are controlled by the base.
-   **Combined Objects**: A computer (monitor, keyboard, mouse) as a child of a desk — when the desk is moved, all computer components follow.

### 3. **Rename Assets**

Setting meaningful names for assets and groups improves scene readability and management efficiency.

#### Operation
1.  In the Outline Panel, select the asset or group you want to rename.
2.  Click the **right mouse button** and select "**Rename**" from the context menu.
3.  Enter the new name and press Enter to confirm.

### 4. **Delete Assets**

#### Operation
-   **Right-Click Menu Delete**: In the Outline list, select the asset or group you want to delete, right-click → "Delete."
-   **Keyboard Delete Key**: In the Outline list, select the asset or group you want to delete, then press the `Delete` key on your keyboard.

#### ⚠️ Important Notes
-   Deleting a group typically also deletes all child objects under that group.
-   Deleting a parent object also deletes all its child objects.
-   Deletion is irreversible — please confirm carefully.

## 💡 Best Practices

### 1. **Meaningful Naming**
-   Use descriptive names for all groups and assets (e.g., "Robot_Arm_Group," "Table_01") and avoid default names (e.g., "Group," "Untitled").

### 2. **Logical Hierarchy Organization**
-   Establish parent-child hierarchies based on physical connections and logical relationships. For example, a gripper is a child of the robotic arm's end effector.
-   Group related objects together to reduce clutter in the Outline Panel and facilitate management.

### 3. **Regular Cleanup**
-   Delete temporary objects or groups that are no longer needed to keep the scene tidy.

## 📝 Summary

OrcaLab's "Outline Panel" is the core tool for scene organization and management. Through operations such as **adding groups, adjusting hierarchy, renaming, and deleting**, you can efficiently manage large numbers of assets in complex scenes, thereby improving scene building and simulation debugging efficiency.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [How to select and edit objects in the scene?](FAQ-list/065-how-to-select-and-edit-objects-in-scene.md)