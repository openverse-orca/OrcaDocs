# How to save and load custom layouts?

## Question
I built a complex simulation scene in OrcaLab and adjusted the placement and configuration of objects. How can I save my custom layout for future use? And how do I load a previously saved layout file?

## Answer

In OrcaLab, the scene setup and configuration you create (including object placement, position, rotation, scale, hierarchy, etc.) can be saved as a **layout file**. This allows you to reuse complex scenes you've created, avoid repetitive work, and facilitate project management and collaboration.

## 📋 Saving a Custom Layout

### Step 1: Complete Scene Setup and Configuration

-   In the OrcaLab client, complete your scene setup according to your needs, including:
    -   Adding assets (3D models, robots, environments, etc.).
    -   Adjusting object position, rotation, scale (Transform properties).
    -   Setting object physical properties (such as mass, friction, etc.).
    -   Creating groups and organizing scene hierarchy.
    -   Configuring lights and cameras.

### Step 2: Open the "File" Menu

-   In the upper-left corner of the OrcaLab client interface, click the "File" menu.

### Step 3: Select "Save Layout" or "Save As"

#### 1. **Save Layout (Ctrl+S)**
-   If you have previously saved the current layout, selecting "Save Layout" will overwrite the existing file, saving the current scene state to the original file.
-   **Shortcut**: `Ctrl + S`.

#### 2. **Save As (Ctrl+Shift+S)**
-   If this is your first time saving the layout, or you want to save the current layout as a new file (without overwriting the original), select "Save As."
-   A file save dialog will appear.
-   **Choose Save Path**: Navigate to the directory where you want to save the layout file.
-   **Enter File Name**: Name your layout file, e.g., `my_robot_assembly_line.json`.
-   **Select File Type**: Ensure the file type is correct (typically `.json` or a specific layout file format).
-   **Click "Save"**.
-   **Shortcut**: `Ctrl + Shift + S`.

## 📋 Loading a Custom Layout

### Step 1: Launch the OrcaLab Client

-   Start the OrcaLab client normally and enter the scene selection interface.

### Step 2: Select a Base Scene (Optional but Recommended)

-   In the "Select Scene" dialog, you can choose a base scene (such as `orcalab_day`), then select "Empty Layout" to load a clean environment as the foundation.
-   Click "Open" to enter the client interface.

### Step 3: Open the "File" Menu

-   In the upper-left corner of the OrcaLab client interface, click the "File" menu.

### Step 4: Select "Open Layout"

-   In the dropdown menu, select "Open Layout."
-   A file selection dialog will appear.

### Step 5: Select and Load the Layout File

-   Navigate to the directory where you previously saved the custom layout file.
-   Select the layout file you want to load (e.g., `my_robot_assembly_line.json`).
-   Click "Open."



### Step 6: Verify Layout Loading

-   After successful loading, your previously saved scene layout, object configurations, etc., will be re-presented in the 3D viewport.

## 💡 Layout Files & Asset Packages

-   **Layout File**: Typically a lightweight text file (such as JSON format) that records the **position, rotation, scale of objects in the scene, as well as their hierarchical relationships and references to asset paths**.
-   **Asset Packages**: A layout file itself does not contain 3D model geometry data, textures, or other binary information — it only records **references** to these assets. Therefore, before loading a layout file, it is very important to ensure that all asset packages referenced in the layout file have been subscribed to and downloaded locally through the Asset Library.

## ⚠️ Important Notes

### 1. **Asset Dependencies**
-   If assets referenced in the layout file have not been downloaded locally or have been deleted, OrcaLab may display warnings or errors about missing assets when loading the layout, resulting in an incomplete scene.
-   Ensure all required asset packages are subscribed and synced locally.

### 2. **File Format**
-   OrcaLab layout files typically use the `.json` format. Do not casually modify the content of layout files unless you fully understand their structure.

### 3. **Version Compatibility**
-   There may be differences in layout file compatibility between different versions of the OrcaLab client. It is recommended to use the latest client version to load layouts.

### 4. **Abnormal Situations**
-   If the layout file is corrupted or contains incorrect asset path references, loading may fail. In this case, you can try creating a new empty layout and manually rebuilding the scene.

## 📝 Summary

OrcaLab provides convenient custom scene layout management through the "Save Layout" and "Open Layout" functions under the "File" menu. This allows users to efficiently reuse and share complex simulation environments. When loading a layout, be sure to ensure all referenced assets are available locally.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/059-what-are-the-components-of-the-orcalab-interface.md)
- [How to use subscribed assets in OrcaLab?](FAQ-list/047-how-to-use-subscribed-assets-in-orcalab.md)