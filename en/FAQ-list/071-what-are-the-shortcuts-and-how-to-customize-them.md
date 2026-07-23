# What are the keyboard shortcuts and how to customize them?

## Question
What common keyboard shortcuts does the OrcaLab client provide? Can I modify or customize these shortcuts according to my usage habits to improve operational efficiency?

## Answer

The OrcaLab client provides a series of built-in keyboard shortcuts for quickly executing common operations such as view control, object transformation, and file management. Mastering these shortcuts can significantly improve your work efficiency.

## 📋 Common Shortcuts Reference

### 1. **View Navigation Shortcuts**

These shortcuts typically require holding the **right mouse button** and are used for freely roaming and observing the scene in the 3D viewport.

| # | Function | Shortcut | Notes |
|------|------------|----------------|------------------------|
| 1 | Move Forward | Right Mouse Button + W | Move forward along camera direction |
| 2 | Move Backward | Right Mouse Button + S | Move backward along camera direction |
| 3 | Move Left | Right Mouse Button + A | Pan left along camera |
| 4 | Move Right | Right Mouse Button + D | Pan right along camera |
| 5 | Move Down | Right Mouse Button + E | Move down along world Z axis |
| 6 | Move Up | Right Mouse Button + Q | Move up along world Z axis |
| 7 | Rotate View | Right Mouse Button (hold) | Rotate view around camera center |
| 8 | Focus Object | Right Mouse Button + Z | Quickly focus on selected object |

### 2. **Object Operation Shortcuts**

These shortcuts quickly switch between the "Move," "Rotate," and "Scale" tools for transforming selected objects.

| # | Function | Shortcut | Notes |
|------|----------|--------|------------------------------|
| 9 | Move Object | 1 | Activate move tool; drag to transform |
| 10 | Rotate Object | 2 | Activate rotate tool; drag to transform |
| 11 | Scale Object | 3 | Activate scale tool; drag to transform |
| 12 | Reset Object Position in Simulation Mode | F3 | Reset object position to pre-simulation state |

### 3. **File Management Shortcuts**

These shortcuts correspond to the "File" operations in the menu bar.

| # | Function | Shortcut | Notes |
|------|----------|----------------|--------------------|
| 13 | Open Layout | Ctrl + O | Open a local layout file |
| 14 | Save Layout | Ctrl + S | Save the current scene layout |
| 15 | Save As | Ctrl + Shift + S | Save the layout as a new file |
| 16 | New Layout | Ctrl + N | Create a new empty layout |

### 4. **Edit Operation Shortcuts**

These shortcuts correspond to the "Edit" operations in the menu bar.

| # | Function | Shortcut | Notes |
|------|----------|-------------|----------|
| 17 | Undo | Ctrl + Z | Undo the previous operation |
| 18 | Redo | Ctrl + Shift + Z | Redo the undone operation |

### 5. **Other Shortcuts**

| # | Function | Shortcut | Notes |
|------|------------|--------|------------------------------|
| 19 | Select Object | Left Mouse Button | Select an object in the viewport |
| 20 | Exit OrcaLab | ESC key (in scene selection interface) | Cancel or exit in the Select Scene dialog |

## 📋 Shortcut Customization

As a lightweight simulation system, the OrcaLab client **may not directly provide a user interface for shortcut customization**. This means you may not be able to directly modify shortcut bindings through a settings menu as you would in some large 3D modeling software or game engines.

#### 💡 Potential Customization Approaches (Advanced Development)

If OrcaLab opens up deeper customization capabilities in the future, or if you engage in advanced development, the following customization methods may be available:
-   **Modify Configuration Files**: In some applications, shortcut configurations are stored in editable configuration files (such as JSON, XML, or TOML files). You can try looking for OrcaLab's configuration files (typically in `~/.orcalab/` or the installation directory) to see if there are relevant shortcut configuration items.
-   **Write Plugins or Scripts**: If OrcaLab provides scripting or plugin interfaces, you may be able to write scripts to override or rebind certain shortcut behaviors.
-   **Operating System Level Modification**: On Linux systems, some desktop environments allow users to remap keyboard keys at the system level. However, this affects the entire system and is not recommended for application-specific modifications only.

## 📝 Summary

OrcaLab provides a rich set of built-in shortcuts covering core functionality including view navigation, object operations, and file management. These shortcuts are an effective way to improve operational efficiency. Currently, the client may not directly support shortcut customization through the user interface, and users need to familiarize themselves with and adapt to the default shortcuts. If you have strong customization needs, you can follow OrcaLab's future version updates or explore its advanced development interfaces.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [How to move and rotate the view in the 3D viewport?](FAQ-list/064-how-to-move-and-rotate-view-in-3d-view.md)