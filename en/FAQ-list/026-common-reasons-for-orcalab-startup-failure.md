# What are the common reasons for OrcaLab startup failure?

## Question
When launching the OrcaLab client, various failures may occur, preventing the software from starting normally or causing it to crash. What are the common reasons for OrcaLab startup failure? How can I troubleshoot and resolve them?

## Answer

OrcaLab startup failures have various causes, typically involving **environment configuration, hardware drivers, system dependencies, network connectivity, and software configuration**. Understanding these common causes can help you quickly locate and resolve issues.

## 📝 Common Startup Failure Causes & Troubleshooting

### 1. **Conda Environment Not Activated or Misconfigured**

#### Symptoms
- Terminal shows `orcalab: command not found`.
- Python environment-related errors.

#### Troubleshooting & Resolution
- **Confirm Conda Environment Is Activated**:
  ```bash
  conda activate orcalab
  ```
- **Check if the `orcalab` Package Is Installed**:
  ```bash
  pip show orca-lab
  ```
- **Reinitialize Conda**: If the `conda activate` command itself has issues, try `conda init bash` and `source ~/.bashrc`.

### 2. **Missing Python Dependencies or Version Mismatches**

#### Symptoms
- Terminal reports `ModuleNotFoundError`.
- Specific Python package version incompatibility messages.

#### Troubleshooting & Resolution
- **Check Dependencies of `pip show orca-lab`**: Confirm all `Required-by` packages are installed.
- **Reinstall Dependencies**:
  ```bash
  conda activate orcalab
  pip install -r requirements.txt # For OrcaPlayground projects
  # Or try reinstalling orca-lab
  pip install --upgrade --force-reinstall orca-lab
  ```
- **Review First-Launch Auto-Install Logs**: The first launch attempts to install dependencies; if that process fails, subsequent launches may also fail.

### 3. **NVIDIA Graphics Driver Issues**

#### Symptoms
- Crash on startup; terminal may show `CUDA`, `OpenGL`, or GPU-related errors.
- GPU not recognized.
- Blank screen or display corruption after launch.

#### Troubleshooting & Resolution
- **Check Driver Version**:
  ```bash
  nvidia-smi
  ```
  Ensure the driver version meets OrcaLab requirements (RTX 40 series ≥ 535.00, RTX 50 series ≥ 550.00).
- **Update Graphics Driver**: Install the latest stable NVIDIA driver through Ubuntu's "Software & Updates" or PPA.
- **Check CUDA Installation**: Usually included with the driver, but manual verification may sometimes be needed.

### 4. **Missing System Dependency Libraries**

#### Symptoms
- Terminal reports `Shared object not found`, `cannot open shared object file`.
- Especially `libx265-dev`.

#### Troubleshooting & Resolution
- **Install Missing System Libraries**:
  ```bash
  sudo apt install libx265-dev # If prompted as missing
  # Other potentially missing libraries — install based on error messages
  ```

### 5. **Network Connection Issues**

#### Symptoms
- Gets stuck at `Syncing asset packages...` during startup with no response for a long time.
- Network connection failure or asset download failure messages.

#### Troubleshooting & Resolution
- **Check Network Connection**: Ensure the network is stable and external websites are accessible.
- **Check PyPI and Conda Mirror Sources**: Ensure they are correctly configured and verify availability.
- **Check Asset Library Server Connection**:
  ```bash
  ping simassets.orca3d.cn
  ```

### 6. **Insufficient Disk Space**

#### Symptoms
- `No space left on device` or similar error messages.
- Asset package download failures.

#### Troubleshooting & Resolution
- **Check Disk Space**:
  ```bash
  df -h
  ```
- **Clean Up Unnecessary Files**: Delete large files, old Conda environments, pip cache, etc.

### 7. **OrcaLab Configuration or Cache Issues**

#### Symptoms
- Previously able to start normally, suddenly unable to launch.
- Specific scenes or layouts fail to load.

#### Troubleshooting & Resolution
- **Delete Cache**: Try deleting OrcaLab's cache files (specific locations may be at `~/.orcalab` or `~/.cache/orcalab`; consult documentation or logs for exact paths).
- **Reset Configuration**: If `config.toml` modifications caused issues, try using `orcalab --init-config` to regenerate a basic configuration.
- **Try Different Scenes/Layouts**: If a specific scene fails to load, the scene file may be corrupted or missing dependent assets.

### 8. **Permission Issues**

#### Symptoms
- `Permission denied` messages.
- Unable to create or write files.

#### Troubleshooting & Resolution
- **Check File/Directory Permissions**: Ensure OrcaLab's installation directory and relevant configuration and asset directories under the user home directory have read/write permissions.
- **Avoid Launching as Root**: It is generally not recommended to use `sudo orcalab` to launch.

### 9. **Port Conflict**

#### Symptoms
- `Address already in use` or other port binding errors.

#### Troubleshooting & Resolution
- **Find the Process Occupying the Port**:
  ```bash
  sudo lsof -i :<port_number>
  ```
- **Terminate the Conflicting Process**: If confirmed as an unrelated process, terminate it.
- **Restart Your Computer**: The simplest but effective method; clears all port occupations.

## 📝 Comprehensive Troubleshooting Flow

1. **Check Terminal Error Messages**: This is the most important first step; error messages usually clearly indicate the problem.
2. **Check Python Environment**: Confirm `conda activate orcalab` succeeds, and `python --version` and `pip show orca-lab` return normally.
3. **Check Graphics Driver**: Run `nvidia-smi` and confirm the driver version meets requirements.
4. **Check System Dependencies**: Install missing system libraries based on error messages.
5. **Check Network**: Test network connectivity to ensure assets and packages can be downloaded normally.
6. **Check Disk Space**: Ensure sufficient storage space is available.
7. **Retry After Each Fix**: After each fix, try restarting OrcaLab.

If you encounter issues you cannot resolve, it is recommended to submit complete error information, your system environment (Ubuntu version, GPU model, driver version), and operation steps to the technical support team.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [How to check if OrcaLab is installed successfully?](FAQ-list/025-how-to-check-if-orcalab-is-installed-successfully.md)