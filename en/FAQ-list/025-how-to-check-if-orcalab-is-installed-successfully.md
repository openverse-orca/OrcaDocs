# How to check if OrcaLab is installed successfully?

## Question
After installing OrcaLab, how can I verify that it has been successfully installed and is running properly on my system?

## Answer

After installing OrcaLab, you can verify its installation status and operation in several ways to ensure all necessary components are correctly configured.

## 📋 Verification Steps

### 1. **Check Python Environment**

First, confirm you are using the Conda environment created for OrcaLab and that the Python version is correct.

```bash
# Activate the OrcaLab Conda environment
conda activate orcalab

# Check Python version
python --version
# Expected output: Python 3.12.x
```

### 2. **Check if the OrcaLab Package is Installed**

Verify that the `orca-lab` Python package is installed in your Conda environment.

```bash
# Activate the OrcaLab Conda environment
conda activate orcalab

# Check orca-lab package information
pip show orca-lab
```

#### Expected Output
If installation was successful, you will see output similar to the following, including version, author, license, and other information:

```
Name: orca-lab
Version: X.Y.Z  # Your OrcaLab version
Summary: High-fidelity physics AI simulation system
Home-page: https://www.songying.ai/
Author: SongYing Tech
License: Proprietary (for non-commercial use)
Location: /home/your_user/miniconda3/envs/orcalab/lib/python3.12/site-packages
Requires: ...
Required-by: ...
```

If you see `WARNING: Package(s) not found: orca-lab`, it means the `orca-lab` package was not successfully installed.

### 3. **Check System Dependencies**

If OrcaLab prompted you to install `libx265-dev` on first launch, you should verify that this system library has been successfully installed.

```bash
dpkg -l | grep libx265
```

#### Expected Output
You should see at least one line beginning with `ii`, indicating that `libx265-dev` is installed. For example:

```
ii  libx265-dev:amd64                       3.5-2build1                         amd64        x265, an H.265/HEVC encoder - development files
```

### 4. **Launch the OrcaLab Client**

This is the most direct verification method. Try launching the OrcaLab client and observe whether it successfully enters the main interface.

```bash
# Activate the OrcaLab Conda environment
conda activate orcalab

# Launch OrcaLab
orcalab
```

#### Expected Behavior
1. The terminal displays `Syncing asset packages...` and may download and update some assets.
2. A "Select Scene" dialog appears.
3. You can select a scene and layout, then click "Open".
4. The OrcaLab GUI main interface displays normally without errors.


### 5. **Run the Quick Start Simulation Example**

Try running one of OrcaLab's quick-start simulation examples, such as the four-wheel chassis car simulation, to verify that all core features are working properly.

#### Steps
1. Clone the `OrcaPlayground` repository from GitHub:
   ```bash
   git clone https://github.com/openverse-orca/OrcaPlayground.git
   cd OrcaPlayground
   conda activate orcalab
   pip install -r requirements.txt
   ```
2. Log in to the Asset Library and subscribe to `OrcaPlaygroundAssets`.
3. Launch OrcaLab from the `OrcaPlayground` directory:
   ```bash
   orcalab
   ```
4. In the OrcaLab client, add the asset `hummer_h2_usda_1` to the layout.
5. Click the "Run" button [▶] in the upper-right corner, select the `run_ackerman` simulation program, and start it.
6. If the car model loads properly and you can control its movement using the WASD keys, the installation and basic functionality are working correctly.


## ⚠️ Common Issues & Troubleshooting

### Q: `orcalab` command not found?
A: Ensure your Conda environment is activated (`conda activate orcalab`) and that OrcaLab has been successfully installed into that environment.

### Q: After launching OrcaLab, an error dialog appears or it crashes?
A: 1. Check the terminal output for error messages, which usually provide clues.
   2. Ensure all system dependencies (such as `libx265-dev`) are installed.
   3. Check that the NVIDIA graphics driver version meets the requirements.
   4. Try reinstalling OrcaLab or the Conda environment.

### Q: Asset package sync fails or gets stuck?
A: Check your network connection to ensure the Asset Library server is accessible. Also ensure sufficient disk space is available.

### Q: Example simulation program won't run?
A: Check that the `OrcaPlayground` project dependencies are fully installed (`pip install -r requirements.txt`) and that you have subscribed to `OrcaPlaygroundAssets`.

Through the above verification steps, you can comprehensively confirm whether OrcaLab has been successfully installed and has full functionality.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)