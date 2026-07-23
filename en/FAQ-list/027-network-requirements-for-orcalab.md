# What are the network requirements for OrcaLab?

## Question
OrcaLab requires a network connection during installation, startup, asset synchronization, and the use of certain features. What specific requirements does it have for the network environment? What is the impact if the network is poor?

## Answer

OrcaLab has clear requirements for the network environment. A stable network connection is crucial for its normal installation and efficient use, primarily in the areas of **dependency installation, asset synchronization, online service access, and remote VR teleoperation**.

## 📋 OrcaLab's Network Requirements

### 1. **Installation & Environment Setup Phase**

#### Purpose
-   **Download Miniconda**: Needs to download the installation script from the Miniconda official repository.
-   **Install Python Packages**: The `pip install orca-lab` command needs to download all Python dependency packages from PyPI or a configured mirror source.
-   **Install System Dependencies**: The `sudo apt install` command needs to download system libraries from Ubuntu software repositories.

#### Requirements
-   **Stable & Fast**: Needs a stable network connection with sufficient bandwidth to quickly download large files. Network interruptions can cause installation failures.
-   **Access to External Resources**: Must be able to access the PyPI official source or your configured domestic mirror source, as well as Ubuntu's software repositories.

### 2. **OrcaLab Client Startup Phase**

#### Purpose
-   **Online Service Verification**: The client may need to connect to OrcaLab's online services for user verification and authorization upon startup.
-   **Asset Package Synchronization**: The most critical step — the client connects to the Asset Library server to detect and download subscribed asset packages (typically containing many large 3D models and textures).

#### Requirements
-   **Stable Connection**: Ensure a stable network connection during client startup to prevent sync interruptions or freezes.
-   **High Bandwidth**: Asset packages are usually large; high bandwidth significantly reduces waiting time.
-   **Low Latency**: The lower the latency to the Asset Library server, the better, as it speeds up communication.


### 3. **Asset Library Web Access**

#### Purpose
-   **Browse/Search Assets**: Access the Asset Library webpage (`https://simassets.orca3d.cn/`) to browse, search, and subscribe to 3D assets.
-   **User Management**: Perform user registration, login, modify personal information, bind third-party accounts, and other operations.
-   **AI Asset Generation**: Use Text-to-3D and Image-to-3D features.

#### Requirements
-   **Normal Web Access**: Must be able to access external websites normally.
-   **HTTPS Connection**: Ensure your browser can securely connect to the Asset Library via the HTTPS protocol.

### 4. **VR Teleoperation Data Collection**

#### Purpose
-   **ADB Communication**: While ADB communication between Pico and PC is local network-based, remote VR teleoperation may require transmitting data or control commands to the cloud or a remote simulation server, requiring WAN connectivity.
-   **Pico Device Updates**: Firmware updates for the Pico VR device itself also require a network connection.

#### Requirements
-   **Low Latency**: For real-time teleoperation, a low-latency network connection (especially from the VR device to the simulation program) is crucial; high latency leads to poor operation experience and imprecise control.
-   **High Bandwidth**: If VR video streaming or large amounts of real-time data exchange are involved, high bandwidth is required.

### 5. **External Simulation Programs (Python Scripts)**

#### Purpose
-   **Download External Libraries**: If your Python simulation scripts need to dynamically download new Python libraries, a network connection is required.
-   **Cloud Service Interaction**: If scripts need to interact with cloud AI services, databases, or remote APIs, a network connection is required.

#### Requirements
-   Depends on the specific functionality of the script.

## ⚠️ Impact of Poor Network Conditions

1.  **Installation Failure or Excessive Duration**: Downloads of various dependencies and software get interrupted or are slow.
2.  **Slow OrcaLab Startup**: Extended asset package synchronization time causes slow client startup.
3.  **Limited or Broken Functionality**:
    -   Unable to access the Asset Library, subscribe to new assets, or use AI generation features.
    -   VR teleoperation latency is too high, affecting operation precision.
    -   Simulation features involving online services cannot function properly.
4.  **Data Loss or Corruption**: Network interruptions during asset synchronization may cause file corruption.
5.  **Poor User Experience**: Stuttering operations and sluggish response.

## 💡 Recommendations for Optimizing the Network Environment

### 1. **Prioritize Wired Connections**
-   For the PC host, use a wired Ethernet connection whenever possible. It is more stable, has lower latency, and higher bandwidth than wireless Wi-Fi.

### 2. **Configure Domestic Mirror Sources**
-   Configuring domestic mirror sources for Conda and PyPI (such as the Tsinghua TUNA source) can significantly improve package download speeds.

### 3. **Check Firewall & Proxy**
-   Ensure the firewall is not blocking OrcaLab or related services from accessing the network.
-   If using a proxy, ensure proxy settings are correct and stable.

### 4. **Ensure Sufficient Bandwidth**
-   If your home or office network bandwidth is insufficient, consider upgrading your broadband service.

### 5. **Reduce Network Usage**
-   When running OrcaLab or performing data synchronization, close other applications that consume significant network bandwidth (such as online video, download tools).

## 📝 Summary

OrcaLab has high requirements for network connection stability and speed, especially in installation, asset synchronization, and online services. Poor network conditions can lead to installation failures, slow startup, limited functionality, and degraded experience. By optimizing network connections, configuring mirror sources, and other measures, you can effectively improve OrcaLab's network usage experience.

## Related Links
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [What to do if pip install OrcaLab download is slow?](FAQ-list/022-what-to-do-if-pip-install-download-is-slow.md)
- [What to do if Asset Library access is slow?](FAQ-list/059-what-to-do-if-asset-library-access-is-slow.md)