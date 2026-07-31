# Does OrcaLab support multi-user collaboration?

## Question
Does OrcaLab support multiple users working together on the same project or scene simultaneously? If so, how? If not, what are the future plans?

## Answer

The current version of OrcaLab (Lightweight Edition) **does not directly support real-time multi-user online collaboration**. It is primarily designed as a single-user desktop application focused on personal learning, teaching, and small research projects.

## 🚫 Current Multi-User Collaboration Limitations

### 1. **Single-User Desktop Application**
- The OrcaLab client runs as standalone installable software on the user's local computer.
- Each OrcaLab instance runs independently with no direct real-time synchronization mechanism between them.

### 2. **Project Management Approach**
- Project files (such as scene layout files, custom scripts) are primarily stored on the local file system.
- Collaboration requires manual coordination through **file sharing** or **version control systems** (such as Git).

### 3. **Asset Library Indirect Collaboration**
- The Asset Library itself supports multi-user upload and subscription of assets, but not real-time sharing.
- Users can subscribe to assets uploaded by others but cannot modify the same asset or scene in real-time.

## ✅ Indirect Collaboration Methods

Although direct support is unavailable, you can achieve "indirect" collaboration through the following methods:

### 1. **Version Control Systems (e.g., Git)**
- **Method**:
  1. Place the OrcaLab project directory (including `.orcalab/config.toml`, layout files, custom scripts, etc.) under Git repository management.
  2. Team members work locally and synchronize code and configuration through Git commits, pulls, merges, etc.
- **Advantages**:
  - Effectively manage project history and versions.
  - Resolve conflicts and ensure code consistency.
  - Suitable for collaboration at the script and configuration file level.

### 2. **File Sharing**
- **Method**:
  1. Use shared folders (such as NFS, SMB) or cloud storage (such as OneDrive, Google Drive, Dropbox) to synchronize project files.
  2. Agree on work scope to avoid conflicts from simultaneous modification of the same file.
- **Advantages**: Simple and easy, suitable for small teams and non-real-time collaboration.

### 3. **Asset Library Sharing**
- **Method**:
  1. Team members can upload self-built public assets to the OrcaLab online Asset Library.
  2. Other members can subscribe to these assets and use them in their own OrcaLab instances.
- **Advantages**: Convenient for sharing reusable 3D models and components.

### 4. **Meeting Sharing**
- **Method**:
  1. Use screen sharing tools (such as Zoom, Tencent Meeting) for remote collaboration.
  2. One person operates OrcaLab while other members watch and provide guidance.
- **Advantages**: Real-time communication and guidance; suitable for design reviews, problem discussions, and similar scenarios.

## 🔮 Future Multi-User Collaboration Plans (OrcaStudio Enterprise Edition)

Although the OrcaLab Lightweight Edition does not directly support it, its higher-tier product — **OrcaStudio Enterprise Edition** — typically considers or already provides more powerful collaboration features to meet enterprise application needs.

### 🚀 Possible OrcaStudio Enterprise Edition Collaboration Features
- **Real-Time Online Collaboration**: Multiple users can simultaneously connect to the same simulation server for real-time interaction and modification in a shared 3D environment.
- **Cloud Deployment**: Deploy the simulation environment in the cloud; users access it over the network for cross-region collaboration.
- **Permission Management**: Fine-grained user permission control to ensure project security and orderliness.
- **Session Management**: Support for multiple collaboration sessions, facilitating work isolation for team members.
- **Version Control Integration**: Tighter integration with version control systems to simplify collaboration workflows.

## 💡 Summary

For OrcaLab (Lightweight Edition), collaboration is primarily achieved through indirect methods such as **version control systems (like Git)** and **file sharing**. If you have strong requirements for real-time multi-user collaboration and intend to use it for commercial projects, consider or upgrade to the OrcaStudio Enterprise Edition, which will provide more professional solutions.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)