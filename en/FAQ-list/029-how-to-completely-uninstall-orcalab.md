# How to completely uninstall OrcaLab?

## Question
I no longer need to use OrcaLab, or I need to reinstall it. How can I thoroughly uninstall OrcaLab from my system, including its Conda environment, Python packages, and related configuration files?

## Answer

Completely uninstalling OrcaLab primarily involves removing its Conda environment, Python packages, and related configuration files and caches. By following the steps below, you can thoroughly remove OrcaLab from your system.

## 📋 Uninstall Steps

### 1. **Exit the Conda Environment**

Before removing the Conda environment, you must first exit the currently active Conda environment.

```bash
conda deactivate
```

### 2. **Remove the OrcaLab Conda Environment**

This is the core step of uninstalling OrcaLab, which will remove all Python packages and related dependencies created for OrcaLab.

```bash
conda env remove -n orcalab
```

#### Command Breakdown
- `conda env remove`: Conda's command for removing environments.
- `-n orcalab`: Specifies the environment name to remove as `orcalab`.

### 3. **Clean Conda Cache (Optional, Recommended)**

Conda caches downloaded packages and indexes locally. Cleaning these caches can free up disk space.

```bash
conda clean --all
```

#### Command Breakdown
- `--all`: Cleans all types of caches, including package cache, tarball files, and unused files.

### 4. **Remove OrcaLab-Related Configuration Files and Caches (Optional, Recommended)**

OrcaLab may generate some configuration files and caches in the user home directory or project directories. Removing them ensures all traces are completely cleared.

#### Find and Remove Configuration Files in Project Directories
If you created OrcaLab configuration files in a project directory (e.g., `OrcaPlayground`), you need to manually delete them.

```bash
# Enter your project directory
cd /path/to/your/OrcaPlayground

# Remove the .orcalab directory
rm -rf .orcalab
```

#### Find and Remove OrcaLab Configuration and Cache in User Home Directory
OrcaLab may create some configuration and cache directories under your user home directory (`~`). Specific locations may vary by version; common possible paths include:
- `~/.orcalab/`
- `~/.config/orcalab/`
- `~/.cache/orcalab/`

You can try to find and remove them:

```bash
# Find possible directories (adjust based on actual situation)
find ~ -maxdepth 2 -type d -name "*orcalab*"

# After confirming, delete them (be very careful to confirm they are OrcaLab-related directories)
# rm -rf ~/.orcalab
# rm -rf ~/.config/orcalab
# rm -rf ~/.cache/orcalab
```

#### Example: Delete the `.orcalab` folder under the `/home/hpb/my-mcp-server/OrcaDocs` project directory
```bash
rm -rf /home/hpb/my-mcp-server/OrcaDocs/.orcalab
```

### 5. **Remove Asset Packages (Optional)**

Asset packages downloaded by OrcaLab are typically stored in a specific local directory. If you want to completely free up this space, you can delete them. This directory is usually located in your user home directory or the Conda environment installation directory; the specific location may need to be found through OrcaLab's logs or configuration.

**Recommendation**: If unsure, you can temporarily keep the asset packages, or only delete the Conda environment first, then manually delete asset files later if needed.

### 6. **Restart Your Computer (Recommended)**

After completing all the above operations, restarting your computer can clear all residual memory usage and processes, ensuring a thorough uninstall.

## ⚠️ Important Notes

### 1. **Use `rm -rf` with Caution**
- The `rm -rf` command is extremely destructive and will forcefully delete files and directories without prompting. Be absolutely sure you are deleting OrcaLab-related files and directories to avoid accidentally deleting important system files.

### 2. **Back Up Important Data**
- Before performing any thorough uninstall, be sure to back up all important project files, custom scripts, layout files, etc.

### 3. **Confirm Environment Name**
- Ensure that `orcalab` in `conda env remove -n orcalab` is the correct Conda environment name you created for OrcaLab. If you used a different name, replace it accordingly.

### 4. **System Dependencies**
- System dependencies installed by OrcaLab (such as `libx265-dev`) will not be automatically removed by uninstalling Conda. If you no longer need these libraries, you can manually remove them using `sudo apt remove libx265-dev`.

## 📝 Summary

Thoroughly uninstalling OrcaLab requires removing its Conda environment, related Python packages, and all configuration files and caches. Please operate with caution and carefully verify paths before executing deletion commands.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What is Miniconda? Why is it needed?](FAQ-list/020-what-is-miniconda-and-why-is-it-needed.md)
- [What to do if conda environment creation fails?](FAQ-list/021-what-to-do-if-conda-environment-creation-fails.md)