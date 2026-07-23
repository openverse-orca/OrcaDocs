# How to check if my GPU driver meets the requirements?

## Question
OrcaLab has specific NVIDIA graphics driver version requirements. How can I check the currently installed NVIDIA driver version on my system and ensure it meets OrcaLab's requirements?

## Answer

Checking the NVIDIA graphics driver version is a relatively simple process. You can use the command-line tool `nvidia-smi` to view driver information and compare it with OrcaLab's recommended requirements.

## 📋 Check Steps

### Step 1: Open a Terminal
On your Ubuntu system, open a terminal window. You can do this with the shortcut `Ctrl + Alt + T`, or by searching for "Terminal" in the application menu.

### Step 2: Run the `nvidia-smi` Command
Enter the following command in the terminal and press Enter:

```bash
nvidia-smi
```

### Step 3: Analyze the Output
The `nvidia-smi` command displays detailed information about the current NVIDIA graphics card, including driver version, CUDA version, GPU model, power consumption, temperature, and more. The main line you need to focus on is **"Driver Version"**.

#### Sample Output
```
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.67                 Driver Version: 550.67       CUDA Version: 12.4     |
|-----------------------------------------+----------------------+----------------------+ 
| GPU  Name              Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC | 
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. | 
|=========================================+======================+======================| 
|   0  NVIDIA GeForce RTX 4090       On   | 00000000:01:00.0 Off |                  N/A | 
|  0%   32C    P8    18W / 450W |      8MiB / 24564MiB |      0%      Default | 
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                              Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+
```

#### Key Information
In the sample output above, you can see `Driver Version: 550.67`. This is the NVIDIA driver version currently installed on your system.

### Step 4: Compare with OrcaLab Requirements
According to OrcaLab's installation guide, the driver version requirements are as follows:
- **RTX 40 Series**: Recommended driver version **≥ 535.00**
- **RTX 50 Series**: Recommended driver version **≥ 550.00**

Compare the driver version from your `nvidia-smi` output with the above requirements:
- **If your driver version meets the requirements**: No additional action is needed; you can proceed directly with OrcaLab installation.
- **If your driver version is below the requirements**: You need to update the NVIDIA graphics driver. See the next step.

## 🔄 Updating NVIDIA Graphics Drivers

If your driver version does not meet the requirements, you can update the driver using one of the following methods.

### 1. **Through Ubuntu's "Software & Updates"**
This is the most recommended and simplest method, especially for beginners.

#### Steps
1. Open the "Software & Updates" application.
2. Switch to the "Additional Drivers" tab.
3. The system will automatically detect and list available NVIDIA driver versions.
4. Select the recommended or latest proprietary driver version (typically `nvidia-driver-xxx`, where `xxx` is the version number; choose one greater than or equal to OrcaLab's required version).
5. Click "Apply Changes"; the system will download and install the driver.
6. After installation is complete, **restart your computer**.



### 2. **Install the Latest Driver via PPA**
If you need the latest driver version, you can install it through NVIDIA's official PPA (Personal Package Archive).

#### Steps
```bash
# 1. Add the NVIDIA PPA
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update

# 2. Find available driver versions
# Note: You may need to adjust based on your GPU model and required version number
apt search nvidia-driver

# 3. Install a specific driver version (e.g., install version 550)
sudo apt install nvidia-driver-550

# 4. Restart your computer
sudo reboot
```

### 3. **Download and Install from the NVIDIA Website**
This method is typically more complex and prone to issues. It is not recommended unless other methods have failed.

#### Steps
1. Visit the NVIDIA official driver download page.
2. Select your GPU model and Linux operating system.
3. Download the `.run` file.
4. **Switch to text mode (TTY) from the graphical interface** and disable the graphical interface.
5. Run the downloaded `.run` file for installation.
6. Re-enable the graphical interface and restart.

**⚠️ Warning**: Manually installing NVIDIA drivers may cause system instability or prevent you from entering the graphical interface. Proceed with caution and back up important data before installation.

## 📝 Post-Installation Verification

After updating the driver, be sure to run the `nvidia-smi` command again to verify that the new driver version has been successfully installed and meets OrcaLab's requirements.

## 💡 Common Issues & Troubleshooting

### Q: `nvidia-smi` command not found?
A: This may mean the NVIDIA driver is not installed at all, or the installation is incomplete. Follow the steps above to reinstall the driver.

### Q: Cannot enter the graphical interface after installing a new driver?
A: This is usually due to a failed driver installation or system conflict. You can try:
   - Entering recovery mode and uninstalling the most recently installed NVIDIA driver.
   - Trying installation again through "Software & Updates."
   - Checking whether your GPU model is supported by the latest driver.

### Q: The driver version meets requirements, but OrcaLab still reports errors?
A: The driver version is just one requirement. Please check:
   - Whether the CUDA version is compatible.
   - Whether the Miniconda and Python environments are correctly configured.
   - Whether other OrcaLab system dependencies (such as `libx265-dev`) are installed.

Ensuring your NVIDIA graphics driver version meets OrcaLab's requirements is a key step in guaranteeing stable software operation and optimal performance.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [Which Ubuntu LTS version is better: 22.04 or 24.04?](FAQ-list/018-which-ubuntu-lts-version-is-better-2204-or-2404.md)