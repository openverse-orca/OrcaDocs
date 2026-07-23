# What to do if the network is interrupted during installation?

## Question
If I encounter a network interruption while installing OrcaLab or its dependencies (such as Miniconda, Python packages, asset packages), how should I handle it?

## Answer

Network interruptions are a common challenge during installation. OrcaLab's installation and asset synchronization depend on a stable network connection. When the network is interrupted, you need to take appropriate measures to resume the installation process.

## 📋 Strategies for Handling Network Interruptions

### 1. **Confirm Network Status**

#### Symptoms
- Terminal shows `Connection timed out`, `Name or service not known`, `Temporary failure in name resolution`, or other network-related errors.
- Download progress stops with no response for a long time.

#### Troubleshooting Methods
- **Check Physical Connection**: Ensure the network cable is securely connected and wireless network is connected.
- **Test Network Connectivity**:
  ```bash
  ping www.baidu.com  # Test public network connectivity
  ping 114.114.114.114 # Test if DNS resolution is working
  ```
- **Check Router/Modem**: Restart your router or modem; the device may be faulty.
- **Check ISP Service**: Contact your Internet Service Provider to confirm whether there is a regional network outage.

### 2. **Handling Conda/Pip Download Interruptions**

Conda and Pip both have some degree of resume capability or retry mechanisms, but the specific behavior depends on when the interruption occurred.

#### Symptoms
- `conda create` or `pip install` commands hang or report errors.
- Downloaded package files are incomplete.

#### Solutions
- **Retry the Command**: After the network recovers, you can usually directly run the previous `conda create` or `pip install` command again. Conda and Pip will attempt to resume from where they left off or re-download the missing parts.
  ```bash
  conda create -n orcalab python==3.12 # Retry creating the environment
  pip install orca-lab # Retry installing the package
  ```
- **Clear Cache**: If repeated retries still fail, the cache files may be corrupted. Try clearing the Conda/Pip cache, then retry.
  ```bash
  conda clean --all
  pip cache purge
  ```
- **Switch Mirror Source**: If download speed is still slow after network recovery, or problems are frequent, consider switching to another domestic mirror source.

### 3. **Handling OrcaLab Asset Package Sync Interruptions**

The OrcaLab client automatically syncs asset packages on startup. If this process stops due to a network interruption:

#### Symptoms
- The client gets stuck on the "Syncing asset packages..." screen.
- Asset download failure messages appear.

#### Solutions
- **Wait for Network Recovery**: After the network returns to normal, restart the OrcaLab client. The client will automatically re-detect and attempt to sync asset packages.
  ```bash
  # Exit the OrcaLab client (if stuck, you may need to force-close the terminal)
  # Then restart
  conda activate orcalab
  orcalab
  ```
- **Check Disk Space**: Ensure sufficient disk space is available to complete the download.

### 4. **Handling System Dependency Installation Interruptions (apt)**

If the network is interrupted while using `sudo apt install` to install system dependencies (such as `libx265-dev`):

#### Symptoms
- `apt install` command reports errors.
- Software package download failure messages appear.

#### Solutions
- **Update Package List**: After network recovery, first update the package list to ensure the latest package information is obtained.
  ```bash
  sudo apt update
  ```
- **Fix Interrupted Installation**: Attempt to repair potentially corrupted software package dependencies.
  ```bash
  sudo apt install -f
  ```
- **Reinstall**: Run the previous installation command again.
  ```bash
  sudo apt install libx265-dev
  ```

## 💡 Preventive Measures

### 1. **Stable Network Environment**
- When installing and launching OrcaLab for the first time, try to choose a stable, high-speed network environment.

### 2. **Configure Mirror Sources**
- Pre-configure domestic mirror sources for Conda and PyPI to effectively reduce installation interruptions caused by slow network access.

### 3. **Step-by-Step Installation**
- Follow the installation guide steps precisely, completing the installation of Miniconda, Conda environment, OrcaLab package, and system dependencies step by step. When problems occur, it's easier to identify which stage has the issue.

### 4. **Patience & Retry**
- After a network interruption, give the network some time to recover, then try retrying the operation. Many download tools and package managers have built-in retry mechanisms.

## 📝 Summary

Network interruptions are a potential issue when installing OrcaLab, but can usually be resolved smoothly through **checking network status, retrying installation commands, clearing caches, and configuring mirror sources**. The key is patience and following the correct troubleshooting steps.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What to do if pip install OrcaLab download is slow?](FAQ-list/022-what-to-do-if-pip-install-download-is-slow.md)
- [What to do if conda environment creation fails?](FAQ-list/021-what-to-do-if-conda-environment-creation-fails.md)