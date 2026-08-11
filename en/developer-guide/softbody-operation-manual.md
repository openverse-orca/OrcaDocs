# Softbody Operation Manual

## 1. Preparation

### 1.1 Asset Library Configuration
- Asset library link: [https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)
- Asset Center → Subscribe to the following assets:
  - `NurisingHome_Softbody`
  - `G1_omnipicker`

![NurisingHome_Softbody asset](../img/routi/NurisingHome_Softbody.png)
![G1_omnipicker asset](../img/routi/G1_omnipicker.png)

### 1.2 Create Conda Environment

```bash
conda create -n orcalab python=3.12
pip install -i https://test.pypi.org/simple/ orca-link==26.7.1.2
pip install -i https://test.pypi.org/simple/ orca-xpbd==26.7.1.16
```

![Environment configuration](../img/routi/environment.png)

### 1.3 Download Teleoperation Code

Clone the specified branches of the following three repositories in the same directory:
- OrcaGym cloth_dev
- OrcaManipulation dev
- OrcaPlayground cloth_dev

![OrcaGym cloth_dev asset](../img/routi/orcagym_cloth_dev.png)
![OrcaManipulation dev asset](../img/routi/OrcaManipulation_dev.png)
![OrcaPlayground cloth_dev asset](../img/routi/orcaplayground_cloth_dev.png)
---

## 2. Pico Setup

### 2.1 Download the Installation Package

Download the `PicoController.apk` installer to your computer.

Package path (replace `<repo-root>` with your local clone path):
```
<repo-root>/OrcaManipulation/src/examples/超市场景青龙机器人数采案例/pico安装包
```

![Pico installer](../img/routi/pico_install.png)

### 2.2 Connect the Pico Device

1. Turn on the Pico and connect it to the computer with a USB cable
2. Copy the apk installer to the Pico directory

![Pico device connection](../img/routi/pico.png)

### 2.3 Install the APK Package

View the installer directory in the VR view, use the right-hand controller to press the **A button**, and confirm the installation of the apk package.

### 2.4 Enable Developer Mode

1. In the VR view, go to: **Settings → About → Software Version Number**
2. Use the confirm key **A button** to press continuously **6-7 times** to bring up Developer Mode

![Developer Mode](../img/routi/开发者.png)

> **Pico setup is now complete**

---

## 3. Usage in OrcaLab

### 3.1 Launch OrcaLab

1. In a terminal, activate the conda environment used by OrcaLab:
   ```bash
   conda activate orcalab
   ```

2. Launch OrcaLab:
   ```bash
   orcalab
   ```

![OrcaLab interface](../img/routi/orcalab.png)

3. Enter the `NursingHome_4cloth` scene

![NursingHome_4cloth scene](../img/routi/NursingHome_4cloth.png)

---

## 4. Data Collection

### 4.1 Install ADB Tools

Run in an Ubuntu terminal:

```bash
sudo apt install android-tools-adb android-tools-fastboot
```

### 4.2 Configure Pico ↔ PC Communication

1. Connect the Pico device to the PC with a USB data cable
2. Run the adb command in a terminal:

```bash
adb reverse tcp:8001 tcp:8001
```

![ADB port configuration](../img/routi/8001.png)

### 4.3 Launch the VR Control Program

1. Make sure `OrcaGymCtrl` is opened in VR
2. Turn on the VR, select **Library** at the bottom
3. Find and launch `OrcaGymCtrl` in the library (this project uses the Ultra4 version)

![OrcaGymCtrl](../img/routi/orcagymctrl.png)

> **Note**: After VR startup, you will be prompted to set a safety boundary. You can reset it or keep the existing boundary.

After launching `OrcaGymCtrl`, a 3D interface will appear:
- A red / blue / green 3D coordinate axis on the left
- A series of red text in the middle

This interface is normal. VR teleoperation must remain in this interface at all times.

![VR interface](../img/routi/vr.png)

### 4.4 Start the Simulation

1. Drag the `G1_omnipicker` asset into the scene
2. In the outline panel on the left, rename the robot to `g1_omnipicker_usda` and drag it under the `Group`

![Rename robot](../img/routi/g1.png)

3. Click the **green start button** in the upper-right corner
4. Select **No simulation program (manual start)**

![Start simulation](../img/routi/启动.png)

### 4.5 Launch the Data Collection Script

1. Activate the conda environment of the Python data collection project:
   ```bash
   conda activate <your-data-collection-env-name>
   ```

2. Enter the data collection script directory and launch:
   ```bash
   cd <repo-root>/OrcaManipulation/src/examples/dataCollection_cloth/RunCloth
   ```

3. Set environment variables and run the simulation:
   ```bash
   export DEBUG="${DEBUG:-0}"
   export XPBD_RELEASE_BUILD="${XPBD_RELEASE_BUILD:-1}"
   export CLOTH_DEBUG="${CLOTH_DEBUG:-0}"
   export COLLECT_DATA="${COLLECT_DATA:-0}"
   export REPLAY="${REPLAY:-0}"
   export CLOTH_NO_REALTIME="${CLOTH_NO_REALTIME:-0}"
   export XPBD_UI="${XPBD_UI:-1}"
   export MAX_MACRO_FRAMES="${MAX_MACRO_FRAMES:-20000}"
   export PBD_GRPC_SBT_ROTATION="${PBD_GRPC_SBT_ROTATION:-from_quat}"
   export LEVEL="${LEVEL:-NursingHome}"
   export AGENT="${AGENT:-g1_omnipicker}"
   export MJC_PREFIX="${MJC_PREFIX:-Group_g1_omnipicker_usda}"

   bash run_cloth_robot_p23c.sh
   ```

> **Note**: The simulation must be ready; SceneManager connects to `localhost:50051` by default. If OrcaLab uses a different port, make sure it is consistent with the code or port mapping.

![Data collection script running](../img/routi/仿真.png)

### 4.6 Controller Operation Guide (Start Collection)

#### Robot Arm Reset / Enter Grasp Mode
Press the **left stick, then right stick** in sequence. The robot arm in the simulation becomes movable and the robot enters grasp operation mode.

#### Start / End a Trajectory Recording
Left controller grip key (`L_GRIPBUTTON`): toggles between "Not Started → Collecting → Ended" states; used to start and end the HDF5 recording for this episode (data is kept on task success, discarded on failure).

#### Grippers & Dual-Arm Control
| Controller | Button | Function |
|------|------|------|
| Left controller | X, Y, left trigger | Control left gripper |
| Right controller | A, B, right trigger | Control right gripper |
| Left controller | Left Transform | Control left arm OSC pose |
| Right controller | Right Transform | Control right arm OSC pose |

> **Important**: Make sure to master the grip key to correctly start and stop recording.
