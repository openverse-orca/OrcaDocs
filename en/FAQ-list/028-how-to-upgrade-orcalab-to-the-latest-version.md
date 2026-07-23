# How to upgrade OrcaLab to the latest version?

## Question
As a continuously iterating software product, how can I upgrade my OrcaLab client to the latest version?

## Answer

Upgrading OrcaLab to the latest version is a relatively simple process, primarily done through the `pip` package manager within OrcaLab's Conda environment. This ensures you always enjoy the latest features, performance optimizations, and bug fixes.

## 📋 Upgrade Steps

### 1. **Activate the OrcaLab Conda Environment**

Before performing any OrcaLab-related operations, always ensure you have activated the Conda environment created for it.

```bash
conda activate orcalab
```

### 2. **Run the Upgrade Command**

Use the `pip install --upgrade` command to upgrade the `orca-lab` package.

```bash
pip install --upgrade orca-lab
```

#### Command Breakdown
- `pip install`: pip's install command.
- `--upgrade`: This flag tells pip to upgrade the `orca-lab` package to the latest version if already installed. If not installed, it will install it.
- `orca-lab`: The name of the package to upgrade.

#### Example Output
If the upgrade is successful, you will see output similar to the following:

```
(orcalab) user@host:~$ pip install --upgrade orca-lab
Collecting orca-lab
  Downloading orca_lab-X.Y.Z-py3-none-any.whl (xx.x MB)
Requirement already satisfied: ...
Installing collected packages: orca-lab
  Attempting uninstall: orca-lab
    Found existing installation: orca-lab A.B.C
    Uninstalling orca-lab-A.B.C:
      Successfully uninstalled orca-lab-A.B.C
Successfully installed orca-lab-X.Y.Z
```

Where `A.B.C` is the old version number and `X.Y.Z` is the latest version number.

### 3. **Verify the Upgrade**

After upgrading, you can check the OrcaLab version number to confirm the upgrade was successful.

```bash
pip show orca-lab
```

Ensure the "Version" field displays the latest version number.

### 4. **Restart the OrcaLab Client**

To ensure the new version and dependencies take effect, be sure to close any running OrcaLab client after upgrading, then restart it.

```bash
orcalab
```

## ⚠️ Important Notes

### 1. **Network Connection**
- The upgrade process requires downloading new versions of packages from PyPI, so a stable network connection is needed.
- If the download speed is slow, check your PyPI mirror configuration.

### 2. **Conda Environment**
- Be sure to run the upgrade command in the correct Conda environment. Running it in the system Python environment may cause confusion.

### 3. **Compatibility**
- Generally, OrcaLab upgrades are backward compatible. However, to be safe, it is recommended to back up important project files and custom configurations before upgrading.
- Sometimes new versions may have new requirements for hardware drivers or system dependencies; pay attention to official update logs.

### 4. **Asset Package Sync**
- After upgrading the OrcaLab client, the first launch may automatically trigger an asset package sync and update process to ensure local assets are compatible with the latest version, or to download new assets.

### 5. **Special Upgrade Situations**
- **Major Version Upgrades**: If OrcaLab releases a major version upgrade (e.g., from 1.x to 2.x), additional steps beyond `pip upgrade` may be required, such as updating the Conda environment's Python version or installing new system dependencies. Be sure to consult the official upgrade guide.
- **Dependency Conflicts**: If the upgrade process indicates dependency conflicts, you can try uninstalling the old version first and then installing the new one, or installing the new version in a fresh Conda environment.

## 💡 Best Practices

### Regularly Check for Updates
- Follow OrcaLab's official release channels (such as GitHub repository, official website news) for the latest version information.
- Periodically run `pip install --upgrade orca-lab` to keep the software up to date.

### Back Up Important Data
- Before performing any major software update, get into the habit of backing up project files, layouts, and custom configurations.

### Clean Up Old Versions
- If you encounter upgrade issues or want to ensure a clean environment, you can completely uninstall the old version of the `orca-lab` package first, then install the latest version.
  ```bash
  pip uninstall orca-lab
  pip install orca-lab
  ```

By following these steps and recommendations, you can smoothly and safely upgrade OrcaLab to the latest version.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [How to check if OrcaLab is installed successfully?](FAQ-list/025-how-to-check-if-orcalab-is-installed-successfully.md)
- [What to do if pip install OrcaLab download is slow?](FAQ-list/022-what-to-do-if-pip-install-download-is-slow.md)