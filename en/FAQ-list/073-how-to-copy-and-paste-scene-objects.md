# How to copy and paste scene objects?

## Question
When building scenes in OrcaLab, I may need to create multiple identical instances of an object, or copy an object from one group to another. How can I efficiently copy and paste objects in the scene?

## Answer

The OrcaLab client typically provides standard Copy and Paste functionality, which is crucial for quickly creating repeated scene elements, organizing scene content, and improving scene building efficiency.

## 📋 Copying and Pasting Scene Objects

### 1. **Select the Object to Copy**

-   In OrcaLab's **3D Viewport**, left-click the object, or select the object's name in the **Outline Panel** to select it.
-   You can hold the `Ctrl` key (or `Shift` key) to select multiple objects.

### 2. **Copy Operation**

#### Method 1: Using the Menu Bar
-   In the top menu bar of the OrcaLab client interface, click the "Edit" menu.
-   Select "**Copy**" from the dropdown menu.

#### Method 2: Using Keyboard Shortcuts (Recommended)
-   After selecting the object, press the **`Ctrl + C`** shortcut on your keyboard.

### 3. **Paste Operation**

#### Method 1: Using the Menu Bar
-   In the top menu bar of the OrcaLab client interface, click the "Edit" menu.
-   Select "**Paste**" from the dropdown menu.

#### Method 2: Using Keyboard Shortcuts (Recommended)
-   Press the **`Ctrl + V`** shortcut on your keyboard.

#### Paste Result
-   After pasting, the new object instance typically appears **near the original object's position** or directly **on top of the original object**. This is to allow you to immediately see the newly pasted object and move it.
-   In the "Outline Panel," the newly pasted object will also appear, with a name typically carrying a suffix (such as `_copy` or a number) indicating it is a duplicate.

### 4. **Adjust the New Object's Position**

-   After pasting, you may need to immediately move the newly generated object to avoid overlapping with the original.
-   Use the Move tool (shortcut `1`) or adjust its `Position` property in the "Edit Panel" to move it to the desired location.

## 💡 Various Applications of Copy & Paste

### 1. **Quickly Generate Repeated Elements**
-   For example, if you need to create multiple trees, boxes, chairs, etc., copy and paste is the most efficient method.

### 2. **Copy Entire Groups**
-   Select a group in the Outline Panel, then copy and paste to duplicate the entire group and all its children at once.
-   For example, duplicating a complete desk-and-chair set.

### 3. **Copy an Object Under a Different Parent**
-   First copy an object.
-   Then select a new parent object in the Outline Panel.
-   After pasting, the new object instance may become a child of the new parent object (specific behavior may vary by OrcaLab's implementation; sometimes it may be pasted directly to the world root). If it doesn't become a child, you can manually drag to adjust the hierarchy.

### 4. **Back Up Scene Elements**
-   Before making important modifications, you can duplicate key objects or groups as backups and temporarily hide them, just in case.

## ⚠️ Important Notes

### 1. **Memory Usage**
-   Copy and paste creates new object instances. If there are many complex objects in the scene, frequent or large-scale copying may increase memory usage and affect performance.

### 2. **Uniqueness**
-   Copy and paste creates **independent instances** of objects. This means modifying one copy's properties does not affect the original.
-   However, in some advanced scenarios, you may need to "reference" rather than "copy" objects. Whether OrcaLab currently supports "instancing" or "referencing" mechanisms — please consult its advanced development documentation.

### 3. **Paste Position**
-   The default position of pasted objects may be very close to or overlapping with the original. Be sure to move them promptly.

### 4. **Scope of Copied Properties**
-   The copy operation typically copies the object's geometry, materials, Transform properties, and directly associated components. However, some more complex properties or script bindings may not be fully copied.

## 📝 Summary

OrcaLab's Copy (`Ctrl + C`) and Paste (`Ctrl + V`) functionality is an indispensable efficiency tool in scene building. Through them, you can quickly duplicate individual objects or entire groups, greatly simplifying the creation of repetitive elements and scene organization. After pasting, be sure to adjust the new object's position to avoid overlap.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to select and edit objects in the scene?](FAQ-list/063-how-to-select-and-edit-objects-in-scene.md)
- [How to use Undo and Redo?](FAQ-list/072-how-to-use-undo-and-redo.md)