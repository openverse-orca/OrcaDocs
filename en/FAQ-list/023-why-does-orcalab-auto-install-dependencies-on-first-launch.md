# Why does OrcaLab auto-install dependencies on first launch?

## Question
When launching OrcaLab for the first time, why does it show "Syncing asset packages..." and automatically install Python dependency packages and download assets? What is this process doing?

## Answer

OrcaLab performs automatic dependency installation and asset package synchronization on first launch to ensure the completeness and currency of the software environment, providing users with an **out-of-the-box** simulation experience.

## 📋 Automatic Dependency Installation

### 1. **Purpose**
- **Ensure Python Environment Completeness**: As a Python application, OrcaLab may depend on some packages that were not fully installed or are dynamically loaded during `pip install orca-lab`.
- **Dynamic Libraries & Plugins**: May need to install Python modules, plugins, or bindings closely related to OrcaLab's core functionality that may not be automatically completed during standard `pip` installation.
- **Version Matching**: Ensure all dependency package versions are compatible with the OrcaLab client core program.

### 2. **Trigger Mechanism**
- On first run, the OrcaLab client checks its runtime environment. If it detects missing necessary dependencies, or certain dependency versions do not meet requirements, it automatically triggers the installation process.

### 3. **Processing Flow**
- **Check Dependencies**: Scan the current Python environment for modules and versions required by OrcaLab.
- **Download & Install**: Through internal package management mechanisms, download and install missing or outdated Python packages from PyPI or pre-configured sources.
- **Update Environment Variables**: May need to update some Python paths or environment variables to ensure newly installed dependencies can be correctly referenced.

### 4. **Important Notes**
- **Network Connection**: This process requires a stable network connection to download dependency packages.
- **Permissions**: Ensure the current user has permission to install new Python packages in the Conda environment.
- **Time**: Depending on network speed and the number of dependencies needed, this process may take anywhere from a few minutes to over ten minutes.

## 📦 Automatic Asset Package Synchronization

### 1. **Purpose**
- **Provide Out-of-the-Box Resources**: Ensure users can immediately access necessary 3D models, scenes, robots, and other assets after launching OrcaLab, without manual downloads.
- **Keep Assets Up to Date**: Automatically sync the latest versions of subscribed asset packages, ensuring users have the most current assets with the latest fixes or features.
- **Personalized Assets**: Download custom asset packages that users have subscribed to in the Asset Library.

### 2. **Trigger Mechanism**
- **First Launch**: When the OrcaLab client starts, it checks the local asset library against user subscription information. If local assets are missing or versions are outdated, synchronization is triggered.
- **Every Launch**: Each time OrcaLab starts, it performs a sync check with the online Asset Library. If new subscriptions or updates to existing subscriptions are detected, downloads are automatically triggered.
- **Asset Library Subscription Updates**: After subscribing to or unsubscribing from assets on the Asset Library webpage, synchronization is triggered on the next OrcaLab launch.

### 3. **Processing Flow**
- **Connect to Asset Library**: The OrcaLab client connects to the online Asset Library service.
- **Authentication**: Authenticates using the user's login credentials.
- **Compare Inventories**: Compares the local asset list with the online subscription list and version information.
- **Download/Update**: Downloads new asset packages and updates subscribed packages with outdated versions.
- **Local Extraction/Installation**: Extracts downloaded asset packages to OrcaLab's local asset directory.



### 4. **Important Notes**
- **Network Connection**: Asset packages are usually large and require a good network environment. Unstable networks may cause download failures or interruptions.
- **Disk Space**: Ensure sufficient local disk space to store downloaded asset packages.
- **Download Speed**: If asset package download speed is slow, check your network or try a different network environment.
- **Force Restart**: After subscribing to new assets on the Asset Library webpage, OrcaLab needs to be **closed and restarted** to trigger the asset download sync.

## 📝 Summary

OrcaLab's automatic dependency installation and asset package synchronization on first launch is an **intelligent design** aimed at providing users with a convenient, up-to-date experience. This process is a critical step to ensure the software **runs properly** and **has the required resources**. If issues are encountered during this process, you typically need to check your network connection, disk space, and user permissions.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What to do if pip install OrcaLab download is slow?](FAQ-list/022-what-to-do-if-pip-install-download-is-slow.md)
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)