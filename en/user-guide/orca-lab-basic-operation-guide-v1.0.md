# OrcaLab Basic Operation Guide

## Launching OrcaLab

`Note: Choose the appropriate launch method based on your operating system. Refer to the Environment Setup section for details.`

After launching, a [Syncing asset packages...] prompt will appear, automatically syncing newly subscribed asset packages and updating already subscribed ones.

Once asset package syncing is complete, the scene and layout selection interface appears. After selecting a scene and layout, click the [Open] button to enter the OrcaLab client interface. Click the [Cancel] button or press the [ESC key] to exit the OrcaLab launcher in the terminal.

<img src="img/client-basic-guide/asset-package-sync.png" width="40%" > <img src="img/client-basic-guide/select-scene.png" width="36%" >


The default selectable scenes are orcalab\_day (Daytime), orcalab\_night (Night), and previewthumbnail\_orcalab (Thumbnail Rendering). Users can subscribe to more scenes in the Asset Library for additional options.

Regarding layout options, [Load Default Layout] and [Empty Layout] have no difference for the three default scenes. For scenes users have subscribed to in the Asset Library, [Load Default Layout] includes interactive objects that come with the scene, while [Empty Layout] does not — you will need to add them manually.

<img src="img/client-basic-guide/daytime.png" width="36.5%" > <img src="img/client-basic-guide/night.png" width="40%" >

<img src="img/client-basic-guide/default-layout.png" width="38%" > <img src="img/client-basic-guide/empty-layout.png" width="39%" >



## GUI Interface

After launching the OrcaLab application, the backend application interface appears as shown below. OrcaLab supports flexible layout. The default layout is divided into three layers (top, middle, bottom) with five modules: Menu Bar, Outline Panel, Viewport Panel, Edit Panel, and Asset Panel.

<img src="img/client-basic-guide/gui-interface.png" width="77%" >


### Menu

The top-center [26.1.2] displays the OrcaLab version number. The three icons on the left side are Hide, Maximize, and Close.

The lower-left section contains File, Edit, and Help. The center section contains function buttons such as [Move], [Rotate], and [Scale]. The right section contains the [Run Simulation] and [Stop Simulation] buttons.

<table>
<tbody>
<tr class="odd">
<td>Menu Bar</td>
<td>Function</td>
<td></td>
<td>Shortcut</td>
<td></td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/version-number.png" style="width:0.64583in;height:0.26042in" /></td>
<td>Display version number and scene/layout name</td>
<td></td>
<td>--</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/hide.png" style="width:0.23958in;height:0.1875in" /></td>
<td>Hide</td>
<td></td>
<td>--</td>
<td></td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/maximize.png" style="width:0.1875in;height:0.27083in" /></td>
<td>Maximize</td>
<td></td>
<td>--</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/close.png" style="width:0.27083in;height:0.17708in" /></td>
<td>Close</td>
<td></td>
<td>--</td>
<td></td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/file.png" style="width:0.39583in;height:0.23958in" /></td>
<td>Open Layout</td>
<td>Select a locally saved layout file</td>
<td>ctrl+o</td>
</tr>
<tr class="odd">
<td></td>
<td>Save Layout</td>
<td>Save the edited layout file</td>
<td>ctrl+s</td>
</tr>
<tr class="even">
<td></td>
<td>Save As</td>
<td>Save the edited layout file as a new file</td>
<td>ctrl+shift+s</td>
</tr>
<tr class="odd">
<td></td>
<td>New Layout</td>
<td>Create a new layout file</td>
<td>ctrl+n</td>
</tr>
<tr class="even">
<td></td>
<td>Exit</td>
<td>Exit the application</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/edit-button.png" style="width:0.41667in;height:0.19792in" /></td>
<td>Undo</td>
<td>Undo the last action</td>
<td>ctrl+z</td>
</tr>
<tr class="even">
<td></td>
<td>Redo</td>
<td>Redo the undone action</td>
<td>ctrl+shift+z</td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/help-button.png" style="width:0.38542in;height:0.23958in" /></td>
<td>About OrcaLab</td>
<td><p>Display OrcaLab version, copyright, company homepage, GitHub</p>
<p>repository, and other information</p></td>
<td>--</td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/move-button.png" style="width:0.26042in;height:0.23958in" /></td>
<td>Move</td>
<td>Move the selected object along the X, Y, and Z axes</td>
<td>1</td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/rotate-button.png" style="width:0.26042in;height:0.21875in" /></td>
<td>Rotate</td>
<td>Rotate the selected object around the X, Y, and Z axes</td>
<td>2</td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/zoom-button.png" style="width:0.21875in;height:0.23958in" /></td>
<td>Scale</td>
<td>Scale the selected object around its center point</td>
<td>3</td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/view-pan.png" style="width:0.26042in;height:0.23958in" /></td>
<td>Pan View</td>
<td>Move the view up, down, left, and right</td>
<td>Right-click + a/d</td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/view-rotate.png" style="width:0.26042in;height:0.21875in" /></td>
<td>Rotate View</td>
<td>Rotate the view</td>

<td>Right-click</td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/view-scale.png" style="width:0.21875in;height:0.23958in" /></td>
<td>View Forward/Backward</td>
<td>Move the view forward and backward</td>
<td>Mouse wheel / Right-click + w(s)</td>
</tr>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/distance-measurement.png" style="width:0.26042in;height:0.23958in" /></td>
<td>Distance Measurement</td>
<td>Measure distance between objects in the simulation environment. Hover over the start point to reactivate and modify the starting position</td>
<td>--</td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/angle-measurement.png" style="width:0.26042in;height:0.21875in" /></td>
<td>Angle Measurement</td>
<td>Measure angles between objects in the simulation environment. Hover over the start or turning point to reactivate and modify its position</td>
<td>--</td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/collision.png" style="width:0.21875in;height:0.23958in" /></td>
<td>Show/Hide Collision</td>
<td>Show or hide physics collisions and joints</td>
<td>--</td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/move-simulation-object.png" style="width:0.22917in;height:0.25in" /></td>
<td>Move Objects During Simulation</td>
<td>Move objects in the simulation environment while the simulation is running</td>
<td>F3</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="img/client-basic-guide/simulation-running.png" style="width:0.22917in;height:0.25in" /></td>
<td>Run Simulation</td>
<td></td>
<td>--</td>
<td></td>
</tr>
<tr class="even">
<td><img src="img/client-basic-guide/simulation-end.png" style="width:0.21875in;height:0.21875in" /></td>
<td>Stop Simulation</td>
<td></td>
<td>--</td>
<td></td>
</tr>
</tbody>
</table>


### Outline & Camera

This module is primarily used for managing objects and viewpoints in the viewport layout. The leftmost button toggles between [Outline] and [Camera]. [Outline] is used to manage objects and cameras in the viewport layout, while [Camera] is used to switch between different camera viewpoints.

![](img/client-basic-guide/outline.png)

![](img/client-basic-guide/camera.png)

Drag assets from the Asset Library into the viewport module to add objects and cameras. Added objects and cameras will simultaneously appear in the [Outline] list. The supported operations are as follows:

|    |        |                                   |                                    |
| -- | ------ | --------------------------------- | ---------------------------------- |
| Module | Function | Operation | |
| Outline | Asset Management | Add Group | Method 1: Right-click on empty area in Outline → [Add Group] |
|    |        |                                   | Method 2: Right-click on any asset in Outline list → [Add Group] |
|    |        | Delete Asset | Method 1: Right-click on asset/group in Outline list → [Delete] |
|    |        |                                   | Method 2: Left-click on asset/group in Outline list → press Delete key |
|    |        | Rename Asset | Right-click on asset/group in Outline list → [Rename] |
| Camera | View Switching | Click in the camera list to switch between the default camera and custom-added camera viewpoints in the viewport scene layout. | |
|    |        |                                   |                                    |


### Viewport

Used for displaying the scene layout.

<img src="img/client-basic-guide/view.png" width="77%" >

In the 3D viewport, keyboard and mouse operations enable viewing and navigation of the 3D environment. Common shortcuts are as follows:

|      |            |                         |
| --   | -----------| ------------------------|
| #  | Function | Shortcut |
| 1    | Move Forward | Right-click + w |
| 2    | Move Backward | Right-click + s |
| 3    | Move Left | Right-click + a |
| 4    | Move Right | Right-click + d |
| 5    | Move Down | Right-click + e |
| 6    | Move Up | Right-click + q |
| 7    | Rotate View | Right-click |
| 8    | Select Object | Left-click |
| 9    | Move Object | 1 |
| 10    | Rotate Object | 2 |
| 11    | Scale Object | 3 |
| 12    | Move object after changing position in simulation mode, re-run simulation | F3 |


To closely inspect an object in the 3D viewport, click the node in the Outline tree menu, or directly left-click the object in the viewport, then use "Right-click + z" to focus on that object.

### Edit

This module has the [Edit] function, which is primarily responsible for editing asset Transform properties (Position, Rotation, Uniform Scale).

<img src="img/client-basic-guide/edit.png" width="77%" >


[Edit] function: Select an asset in the Outline list or viewport, and the right-side [Edit Panel] will display the object's Transform information, including Position, Rotation, and Uniform Scale. You can click to directly enter numeric values for precise modification, or adjust parameters by sliding the arrows that appear when hovering over data bars.

<img src="img/client-basic-guide/outline-view-edit.png" width="77%" >


### Assets & Terminal

This module has two main functions: [Assets] and [Terminal]. [Assets] displays assets successfully subscribed to in the Asset Library. [Terminal] displays the simulation running process.

<img src="img/client-basic-guide/assets.png" width="77%" >
<img src="img/client-basic-guide/terminal.png" width="77%" >


[Assets] function: Displays subscribed assets. Supports fuzzy search of subscribed assets by including or excluding specific fields. Click the [Open Asset Library] button to open the Asset Library. When hovering over an item, the right side displays the item's name, path, metadata, and other related information. Click the [Copy] button below to copy this information.

[Terminal] primarily displays the simulation process and results, which can be cleared and copied.
