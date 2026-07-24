# What are the components of the OrcaLab interface?

## Question
How is the OrcaLab user interface laid out? What are the functions of each module?

## Answer

OrcaLab features a modular user interface design that supports flexible layouts. The default interface is divided into **three layers (top, middle, bottom) with five core modules**, providing users with a complete simulation development environment.

## 🖥️ Overall Interface Layout



### Interface Structure Overview
```
┌─────────────────────────────────────────┐
│                Menu Bar                 │  ← Top Layer
├─────────────┬─────────────┬─────────────┤
│   Outline   │   Viewport   │    Edit     │  ← Middle Layer
├─────────────┴─────────────┴─────────────┤
│              Assets Panel               │  ← Bottom Layer
└─────────────────────────────────────────┘
```

## 📋 Menu Bar Module

### 🔧 Top Information Area
```
Left Control Buttons:
├── Hide Button [-]     - Minimize window
├── Maximize Button [□] - Toggle fullscreen/windowed
└── Close Button [×]     - Exit program

Center Information Display:
└── Version Number [26.1.2] - Current OrcaLab version
```



### 🛠️ Function Menu Area
```
Left Menu:
├── File
│   ├── Open Layout (Ctrl+O)
│   ├── Save Layout (Ctrl+S)
│   ├── Save As (Ctrl+Shift+S)
│   ├── New Layout (Ctrl+N)
│   └── Exit
├── Edit
│   ├── Undo (Ctrl+Z)
│   └── Redo (Ctrl+Shift+Z)
└── Help
    └── About OrcaLab
```

### ⚙️ Toolbar Area
```
Center Tool Buttons:
├── Move Tool [↔] (Shortcut: 1)  - Move selected object
├── Rotate Tool [↻] (Shortcut: 2) - Rotate selected object
└── Scale Tool [⤢] (Shortcut: 3) - Scale selected object

Right Simulation Control:
├── Run Simulation [▶] - Start simulation
└── Stop Simulation [⏹] - End simulation
```

## 🗂️ Outline & Camera Panel

### Mode Switching
```
Mode Switch:
├── Outline Mode - Manage scene object hierarchy
└── Camera Mode - Manage and switch view cameras
```



### 🌳 Outline Mode Functions
```
Asset Management:
├── Display hierarchical structure of all scene objects
├── Support group creation and management
├── Asset renaming and deletion
├── Drag to adjust hierarchical relationships
└── Quick object selection and location

Operations:
├── Right-click menu - Add group, delete, rename
├── Left-click selection - Select object (synchronized to viewport)
├── Drag operation - Adjust parent-child relationships
└── Delete key - Quick delete selected object
```

### 📷 Camera Mode Functions
```
Camera Management:
├── List all available cameras
├── Switch between different camera views
├── Add custom cameras
└── Manage camera parameters

Default Cameras:
├── Main View Camera - Default 3D perspective
├── Orthographic Cameras - Front, side views, etc.
└── Free Camera - User-defined perspectives
```



## 👁️ Viewport (Core Area)

### 3D Viewport Functions
```
Main Functions:
├── Real-time 3D scene rendering and display
├── Object selection and visual feedback
├── Real-time simulation result display
├── Interactive scene editing
└── Multiple rendering mode support
```



### Viewport Controls
```
Mouse Operations:
├── Left-click - Select object
├── Right-click drag - Rotate view
├── Scroll wheel - Zoom view
└── Middle-click drag - Pan view

Keyboard Operations:
├── Right-click + W/S - Forward/Backward
├── Right-click + A/D - Move Left/Right
├── Right-click + Q/E - Move Up/Down
├── Right-click + Z - Focus on selected object
└── F3 - Reset object position (simulation mode)
```

### View Modes
```
Rendering Modes:
├── Standard Rendering - Photorealistic rendering
├── Wireframe Mode - Display mesh structure
├── Material Preview - Material effect display
└── Physics Debug - Display physics information
```

## ✏️ Edit Panel

### Transform Property Editing
```
Position:
├── X Position - World coordinate X direction
├── Y Position - World coordinate Y direction
└── Z Position - World coordinate Z direction

Rotation:
├── X Rotation - Rotation angle around X axis
├── Y Rotation - Rotation angle around Y axis
└── Z Rotation - Rotation angle around Z axis

Uniform Scale:
└── Scale Ratio - Uniform scale factor
```



### Edit Operations
```
Numeric Input:
├── Click input field to enter precise values
├── Use keyboard up/down arrows to fine-tune
└── Press Enter to confirm changes

Slider Adjustment:
├── Hover mouse to display slider arrows
├── Drag arrows to adjust values in real-time
└── Preview changes in real-time

Batch Editing:
├── Multi-select objects for simultaneous editing
├── Apply relative changes
└── Reset to default values
```

## 📦 Assets & Terminal Panel

### Mode Switching
```
Assets Mode:
└── Manage and use subscribed assets

Terminal Mode:
└── Display simulation program runtime information
```

### 📋 Assets Mode Functions
```
Asset Management:
├── Display all subscribed assets
├── Support fuzzy search filtering
├── Display asset detailed information
├── Drag assets into the scene
└── Open Asset Library entry

Operations:
├── Search box - Quick asset filtering
├── Asset preview - Hover to show information
├── Drag to add - Drag to viewport for use
├── Info copy - Copy asset information
└── Open Asset Library - Jump to Asset Library website
```



### 💻 Terminal Mode Functions
```
Information Display:
├── Simulation program launch information
├── Runtime process log output
├── Error and warning information
├── Performance statistics
└── Program exit status

Management Functions:
├── Clear terminal output
├── Copy terminal content
├── Search log information
└── Export log files
```



## 🎨 Interface Personalization

### Layout Adjustment
```
Supported Features:
├── Drag to adjust panel sizes
├── Hide/show specific panels
├── Save custom layouts
└── Restore default layout

Quick Operations:
├── Double-click panel title - Maximize panel
├── Right-click panel - Show panel menu
└── Drag panel borders - Adjust size
```

### Theme Settings
```
Visual Options:
├── Dark theme / Light theme
├── Font size adjustment
├── Interface zoom ratio
└── Custom color schemes
```

## 🔄 Workflow Integration

### Typical Usage Flow
```
1. Menu Bar → Create or open project
2. Assets Panel → Search and add assets
3. Viewport → Build and edit scene
4. Outline Panel → Manage scene hierarchy
5. Edit Panel → Precisely adjust properties
6. Menu Bar → Run simulation program
7. Terminal Panel → Monitor runtime status
8. Menu Bar → Save project results
```

### Efficiency Tips
```
Shortcut Usage:
├── Ctrl+S - Quick save layout
├── 1/2/3 - Switch edit tools
├── Delete - Delete selected object
└── F3 - Reset simulation state

Multi-Panel Collaboration:
├── Outline selection + Edit panel adjustment
├── Assets Panel search + Viewport addition
├── Viewport operation + Terminal monitoring
└── Camera switching + Scene editing
```

OrcaLab's modular interface design fully considers the simulation development workflow. Each module has a clearly defined role while maintaining good interactive collaboration, providing users with an efficient development environment.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)