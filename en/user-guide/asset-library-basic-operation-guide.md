# Asset Library Basic Operation Guide


## Page Overview

After downloading and installing the OrcaLab client, click the [Open Asset Library] button to open the Asset Library management webpage. The left side of the page is the Asset Management tab bar, and the right side is the content panel.

 ```bash
  # 1. Enter the OrcaLab conda environment

  conda activate orcalab

  #  Re-enter OrcaLab

  orcalab
  ```

![](img/asset-library-basic-guide/open-asset-library.png)
![](img/asset-library-basic-guide/assets.png)

### Asset Management
- Search: Supports searching all assets in the Asset Center by image reference or text description.
- Asset Center: Contains 6 categories — Industrial Assets, Lifestyle Assets, Service Assets, Sensor Assets, Robot Assets, and Other Assets.
- Tool Center: Includes 2 tools — AI Asset Generation and Robot Adaptation.
- Personal Center: Subscribed assets.
- Account Management: View account information and log out.
### Content
- Displays the content of each tab in Asset Management.




## Feature Guide

### Search
Provides two search methods: reference image and text description.

![](img/asset-library-basic-guide/assets.png)

### Asset Center
There are 6 categories in total: Industrial Assets, Lifestyle Assets, Service Assets, Sensor Assets, Robot Assets, and Other Assets. You can browse and subscribe to desired assets in the corresponding categories. Supports searching for asset packages or assets by keyword input, and sorting asset packages in the Asset Center by name or by size.

![](img/asset-library-basic-guide/asset-center.png)

#### Asset Package Details & Viewing
An asset package is a collection of one or more assets and is the basic unit of subscription in the Asset Library. An asset package contains basic information such as author, project, number of included assets, and total size.
- [Details] displays basic asset package information, asset description, version notes, and included asset files. Operations such as [Subscribe/Unsubscribe], [Return to Drafts], and [Delete] are available. [Return to Drafts] and [Delete] are only available for asset packages authored by the current account.

<img src="img/asset-library-basic-guide/details-this-author.png" width="37%"> <img src="img/asset-library-basic-guide/details-other-authors.png" width="38.3%">

- [**+**] expands to show the assets within the asset package. [**-**] collapses the assets within the asset package.

<img src="img/asset-library-basic-guide/expand.png" width="77%">

#### Asset Subscription & Usage
[Subscribe] downloads the asset package to the local OrcaLab asset file directory. After subscribing, OrcaLab will automatically download and update that version of the asset on the next launch. Once OrcaLab restarts, the assets will appear in the [Asset Library] panel at the bottom and will be ready to use. Subscribed asset packages will also sync to the Personal Center.

- Step 1: Subscribe to assets: Subscribe to assets in the Asset Library.

<img src="img/asset-library-basic-guide/subscribe.png" width="50%">

- Step 2: Use subscribed assets: Restart OrcaLab to use the assets

 ```bash
  # 1. Enter the OrcaLab conda environment

  conda activate orcalab

  #  Re-enter OrcaLab

  orcalab
  ```
   After restarting OrcaLab, [Syncing asset packages...] will download newly subscribed asset packages and update already subscribed ones. For asset packages subscribed with the [Scene] tag, the assets in the package come with a layout. After syncing is complete, they will appear in the [Select Scene] list in the next step. Using [Load Default Layout] will open and display the asset scene layout from that package in the viewport. You can modify the default scene layout or drag assets from the client's bottom asset list into the viewport. The modified layout can be saved via [File → Save Layout].

   <img src="img/asset-library-basic-guide/syncing-asset-package.png" width="40.5%"> <img src="img/asset-library-basic-guide/select-scene.png" width="36%">

   <img src="img/asset-library-basic-guide/scene-asset-package.png" width="40.5%"> <img src="img/asset-library-basic-guide/scene-layout-modify.png" width="40.5%">

- [Unsubscribe] cancels the subscription to an asset package. After unsubscribing, it will synchronously disappear from the Personal Center and the [Asset Library] panel after OrcaLab restarts.

<img src="img/asset-library-basic-guide/unsubscribe.png" width="40.5%">

### Tool Center

#### AI Asset Generation Tool

**Generate Assets**
Supports generating USDZ-format 3D assets via [Image Reference] or [Text Description]. Currently, each user has 5 usage attempts per day, shared across both methods.

![](img/asset-library-basic-guide/ai-generate-assets.png)
Parameter introduction [generally keep defaults]:
- Separate Mesh: Split a model's mesh into multiple independent model files or assets
- Auto-generate LOD: Automatically generate multi-level detail meshes for the model
- Smooth Mesh: Apply smoothing to the model's mesh surface
- Smooth Strength: Controls the degree of "Smooth Mesh" processing. The two work together
- Use Hub CLI: Specifies using the Hub command-line tool for model processing (i.e., ap processing)

Upload a reference image or text description, click [Start Generating Asset], and do not refresh the page during generation to obtain the 3D asset.




#### Robot Adaptation Tool

This tool addresses the challenges users face when working with the ORCA physics AI simulation platform — the need to convert robot URDF models to MJCF and perform relatively complex and specialized adaptation work before teleoperation data collection and data augmentation can proceed smoothly on the ORCA platform. This process is complex, time-consuming, and the workflow is not reusable. Therefore, this tool was developed to simplify the adaptation workflow, improve robot adaptation efficiency, and enable users to quickly get started and smoothly perform subsequent robot operation and training tasks on the platform. This tool not only resolves issues encountered during URDF-to-MJCF conversion — such as empty material names and invalid value ranges — but also automatically configures position and motor actuators for robot joints.

**Page Layout**

From left to right: History, Toolbar, and Results Display Panel.

- History: Saves and displays user-imported and modified robot models along with corresponding parameter changes. [Right-click] to rename or delete.
- Toolbar: Used for uploading URDF/MJCF folders, displaying basic robot information, performing property adjustments, and outputting results.
- Results Display Panel: Displays the imported robot. ① View Controls: Left-click — rotate view, Shift + left-click — pan view, mouse wheel — zoom view. ② Simulation Run: Click [Run] to start simulation and control the robot via Control panel. [Reset] resets Control parameters to zero.

<img src="img/asset-library-basic-guide/JQRSPYM.png" width="40.5%">

<img src="img/asset-library-basic-guide/JQRSPLSJVCMM1.png" width="19.5%"> <img src="img/asset-library-basic-guide/JQRSPLSJVCMM2.png" width="20.5%">

**Upload File**

Supports click-to-upload or drag-and-drop upload of robot model URDF/MJCF folders or compressed archives.

**Basic Information**

- Robot Name: Auto-detected and populated robot name.
- Movement Type: Required, Biped/Chassis.
- End Effector: Required, Gripper/Dexterous Hand.

**Property Adjustment**

**Robot Structure**:
Displays the robot's tree structure. Supports deleting and editing joints; adding, editing, and deleting actuators.

<img src="img/asset-library-basic-guide/JQRSPJQRJG.png" width="40.5%">

**Material Configuration**
- AI Global Material Configuration: One-click material replacement based on AI recommendations.
- Local Material Configuration: Double left-click to select a part, then adjust material type (Plastic, Metal, Wood, Rubber), basic properties (Color, Metalness, Roughness), and texture maps.

<img src="img/asset-library-basic-guide/JQRSPYJGHCZ.png" width="20.5%"> <img src="img/asset-library-basic-guide/JQRSPJBGHCZ1.png" width="20.5%">


**Dynamics Configuration**

① Single Joint: Enables AI classification of joints and automatic actuator assignment for joints.

Click Classify to automatically classify joints by body part based on the Movement Type and End Effector type selected in Basic Information, and automatically add position and motor actuators to joints. If a joint is classified incorrectly, long-press the left mouse button on that data row and drag it to the desired type above. Click [Edit] to navigate to [Robot Structure] and modify the selected joint and actuator parameters.

<img src="img/asset-library-basic-guide/JQRSPDLX1.png" width="40.5%">
<img src="img/asset-library-basic-guide/JQRSPDLX3.png" width="40.5%">


① Parallel Joints: Create rigid body connection constraints, joint coupling constraints, tendons, etc. Whether the corresponding configuration takes effect can be verified and controlled in the control list after running simulation on the right side.

- Rigid Body Connection Constraint: Used to create rigid body connection constraints, commonly used for gripper rigid body connections. body1: left-click to select; body2: right-click to select; anchor: Ctrl + right-click to select (more precise anchor placement yields better control).

<img src="img/asset-library-basic-guide/JQRSPGTLJ1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPGTLJ2.png" width="40.5%">

- Joint Coupling Constraint: Used to create joint coupling constraints, commonly used for gripper and dexterous hand joint coupling.

<img src="img/asset-library-basic-guide/JQRSPGJLD1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPGJLD2.png" width="40.5%">

- Tendon: Used to create tendons and configure actuators for tendons to uniformly control coupled joints. Actuator types can be general, position, or motor.

<img src="img/asset-library-basic-guide/JQRSPJJ1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPJJ2.png" width="40.5%">

③ Exclude Collision: Create collision exclusions. Parts with rigid body connection constraints automatically add collision exclusions.

<img src="img/asset-library-basic-guide/JQRSPPCPZ1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPPCPZ2.png" width="40.5%">

**Initial Pose Configuration**

Adjust joint initial poses. Double-click the table to navigate to Robot Structure and adjust the control range of the corresponding joint.

Initial pose saving supports two options (choose one). **Save to XML Only**: Save the adjusted pose to XML for permanent modification of the pose state; **Save to Data Collection Config Only**: Save the adjusted initial pose state to the data collection configuration file for defining the initial pose during data collection, without modifying the model's initial state.

<img src="img/asset-library-basic-guide/JQRSPCSWZ1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPCSWZ2.png" width="40.5%">

**Sensor Configuration**

Used to create, edit, and delete camera sensors. [View] displays the camera's line of sight and view frustum. [Edit], combined with the coordinate axes and translate/rotate functions in Basic Information, enables camera translation and rotation modifications.

<img src="img/asset-library-basic-guide/JQRSPXJ2.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPXJ3.png" width="40.5%">

**Other Configuration**

Create sites for marking positions. The data collection configuration file requires the grasp point defined for the gripper or dexterous hand.

<img src="img/asset-library-basic-guide/JQRSPsite1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPsite2.png" width="40.5%">


**Result Output**

- Export XML: Export the modified XML file.

<img src="img/asset-library-basic-guide/JQRSPDC1.png" width="40.5%">

- Export Model: Export the entire model file.

<img src="img/asset-library-basic-guide/JQRSPDC2.png" width="40.5%">

- Upload Model: Upload the model to Personal Center for subscription.

<img src="img/asset-library-basic-guide/JQRSPSCMX.png" width="40.5%">

- Export Config File: Export the data collection configuration file for data collection. The left and right arm end effectors are the gripper or dexterous hand grasp marker sites defined in [Other Configuration]. The left and right hand drive joints are the joints selected for drive control.

<img src="img/asset-library-basic-guide/JQRSPDCSC1.png" width="40.5%"> <img src="img/asset-library-basic-guide/JQRSPDCSC2.png" width="40.5%">


### Account Management

Account Management supports viewing account information and logging out.

Click [Account Name] to view account information and perform operations such as linking third-party accounts. Click the [Logout] button to log out of the account.

<img src="img/asset-library-basic-guide/account-info-view-and-logout.png" width="77%">


