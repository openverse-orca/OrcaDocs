# How to install OrcaLab on multiple computers?

## Question
I have multiple computers (e.g., a desktop and a laptop), and I want to use OrcaLab on different machines. How should I install and sync OrcaLab across multiple devices?

## Answer

You can install OrcaLab independently on multiple computers that meet the system and hardware requirements. Since OrcaLab is a single-user desktop application, it needs to be installed separately on each computer. The key is how to **synchronize your project files and assets**.

## 📋 Multi-Device Installation Steps

### 1. **Install OrcaLab Independently on Each Computer**

- **Environment Setup**: Ensure each computer meets OrcaLab's system requirements and hardware configuration (especially having an NVIDIA RTX graphics card).
- **Operating System**: Install Ubuntu 22.04 LTS or 24.04 LTS on each computer.
- **Miniconda**: Install Miniconda on each computer separately.
- **Conda Environment**: Create a dedicated Conda environment for OrcaLab.
- **Install OrcaLab**: Run `pip install orca-lab` to install the client.
- **Launch & Asset Sync**: On first launch, wait for asset package synchronization to complete.

### 2. **Sync Project Files & Code**

For your own simulation projects (such as `.orcalab/config.toml`, layout files, Python scripts, custom assets, etc.), using a **version control system** is strongly recommended for synchronization.

#### Recommended Approach: Git + GitHub/GitLab
- **Principle**: Initialize your OrcaLab project directory as a Git repository and push it to a remote repository (such as GitHub, GitLab). Clone the repository on the other computer.
- **Steps**:
  1. **Initialize Git Repository** (in your project directory):
     ```bash
     cd /path/to/your/OrcaLab_Projects/MySimulationProject
     git init
     git add .
     git commit -m "Initial commit of OrcaLab project"
     ```
  2. **Link Remote Repository**:
     ```bash
     git remote add origin https://github.com/your_username/MySimulationProject.git
     git push -u origin master
     ```
  3. **Clone Repository on Another Computer**:
     ```bash
     git clone https://github.com/your_username/MySimulationProject.git
     cd MySimulationProject
     ```
  4. **Sync Updates**:
     - After working on one computer, commit and push to remote: `git add . && git commit -m "Update feature X" && git push`
     - Before working on another computer, pull the latest code first: `git pull`
- **Advantages**:
  - **Version History**: Clear project version management.
  - **Conflict Resolution**: Git provides powerful conflict resolution mechanisms.
  - **Data Security**: Remote repository serves as backup, preventing local data loss.

#### Alternative: Cloud Storage / File Sync Tools
- **Principle**: Use cloud storage services (such as Google Drive, Dropbox, OneDrive) or sync tools (such as Syncthing) to automatically sync project files.
- **Operation**:
  1. Place the OrcaLab project directory in the cloud storage sync folder.
  2. Ensure the corresponding client is installed and configured on both computers for synchronization.
- **Advantages**: Simple and easy to use; non-technical users can get started quickly.
- **Disadvantages**:
  - **No Version History**: Difficult to trace file history; accidental deletions are hard to recover.
  - **Conflict Handling**: Sync tools have weaker file conflict handling and may require manual resolution.
  - **Slow Large File Sync**: For large asset files, synchronization may take a long time.

### 3. **Asset Package Synchronization**

OrcaLab's asset packages are bound to your user account. Assets you subscribe to in the Asset Library will be **automatically downloaded and synced when you log into the OrcaLab client and it starts up**.

- **Principle**: When the OrcaLab client starts, it detects all assets subscribed under your account and automatically downloads them locally.
- **Operation**:
  1. Launch the OrcaLab client on each computer and **log in with the same account**.
  2. Wait for the client to complete the "Syncing asset packages..." process.
- **Advantages**: No need to manually copy large asset files; OrcaLab manages this automatically.
- **Notes**:
  - **Network Bandwidth**: Asset packages are typically large; the first sync may take considerable time and bandwidth.
  - **Disk Space**: Ensure each computer has sufficient disk space to store asset packages.
  - **Sync Trigger**: When subscribing to new assets or asset updates occur, you need to close and restart the OrcaLab client.

## 💡 Best Practices

### 1. **Unified Account**
- Use **the same OrcaLab account** on all devices to sync subscribed assets.

### 2. **Git for Project Code Management**
- Use Git for version management and synchronization of small text files such as custom Python scripts, configuration files (`.orcalab/config.toml`), and scene layout files.

### 3. **Separate Data Storage**
- Raw simulation data (such as VR-collected data) is typically large and not suitable for Git sync. Consider storing it separately on cloud storage, external hard drives, or NAS.

### 4. **Avoid Simultaneous Editing**
- Try to avoid modifying the same project file on two computers simultaneously, as this easily leads to version conflicts.
- Develop the habit of "pull first, then modify, then commit."

### 5. **System Environment Consistency**
- Try to maintain consistency across computers in Ubuntu system version, Conda environment, Python version, and installed dependencies to reduce compatibility issues.

## 📝 Summary

Installing and using OrcaLab on multiple computers is feasible. The key lies in using **Git for project code synchronization** and relying on **OrcaLab's automatic asset sync mechanism** to manage resources. With a sound strategy, you can efficiently switch between different devices.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [How to check if OrcaLab is installed successfully?](FAQ-list/025-how-to-check-if-orcalab-is-installed-successfully.md)
- [What is the Asset Library and how to use it?](FAQ-list/044-what-is-the-asset-library-and-how-to-use-it.md)