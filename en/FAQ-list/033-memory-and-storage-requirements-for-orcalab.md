# What are the memory and storage requirements for OrcaLab?

## Question
As simulation software, what specific requirements or recommendations does OrcaLab have for computer memory (RAM) and storage (hard drive) capacity and type?

## Answer

OrcaLab's memory and storage requirements primarily depend on the **complexity, scale, and quantity of assets** involved in your simulation tasks. Below are OrcaLab's detailed memory and storage requirements and recommendations.

## 🧠 Memory (RAM) Requirements

Memory is critical for OrcaLab's performance in running and loading scenes, assets, simulation data, and executing AI training. Insufficient memory can lead to performance degradation or even program crashes.

### 1. **Minimum Requirement: 16GB DDR4**
- **Recommended For**: Most personal learning, teaching, and moderate-scale simulation projects.
- **Capabilities**:
  - Smooth loading of moderately complex scenes and assets.
  - Single simulation tasks can run stably.
  - Can run the OrcaLab client alongside a small number of other applications.

### 2. **Recommended Configuration: 32GB DDR4 or Higher**
- **Best For**: Professional users who need to handle large complex scenes, conduct long-duration AI training, VR teleoperation data collection, or run multiple simulation instances simultaneously.
- **Capabilities**:
  - Stress-free loading of ultra-large-scale scenes and massive assets.
  - Supports complex AI algorithm training without memory bottlenecks.
  - Excellent multitasking performance with smooth switching.
  - Better utilization of GPU memory for improved overall performance.

### 💡 Memory Selection Recommendations
- **Frequency**: Choose DDR4-3200MHz or higher frequency memory to improve data transfer efficiency.
- **Channels**: Prioritize dual-channel memory for higher bandwidth.
- **Expandability**: Consider the number of memory slots on the motherboard to reserve space for future upgrades.

## 💾 Storage Requirements

Storage is used for the OrcaLab software itself, the Conda environment, Python dependencies, downloaded asset packages, simulation project files, and generated simulation data. Both storage **capacity and speed** are crucial.

### 1. **Minimum Capacity: 50GB Free Space**
- **Applicable Scenario**: Only for installing the OrcaLab client and the most basic Conda environment.
- **Limitations**:
  - Cannot store large amounts of asset packages and simulation data.
  - Will quickly run out of space, preventing downloads of new assets or saving of projects.

### 2. **Standard Configuration: 500GB+ SSD (Solid State Drive)**
- **Recommended For**: Most users; meets the needs of software installation, Conda environment, basic asset storage, and a small amount of simulation data.
- **Advantages**:
  - **Speed**: SSDs have far faster read/write speeds than HDDs, significantly accelerating OrcaLab startup time, scene loading speed, and asset access speed.
  - **Enhanced Experience**: Reduces wait times and improves work efficiency.

### 3. **Recommended Configuration: 1TB+ NVMe SSD + Additional Storage**
- **Best For**: Professional users who need to store large amounts of high-resolution assets, record extensive simulation videos, and conduct large-scale data collection and AI training.
- **Advantages**:
  - **Ultra-Fast Storage**: NVMe SSDs provide top-tier read/write speeds, further optimizing performance.
  - **Ample Space**: A 1TB or larger primary drive, combined with additional SATA SSDs or large-capacity HDDs as data drives, meets massive storage needs.

### 📊 Storage Capacity Allocation Recommendations
- **System Drive (SSD)**: 100-200GB (operating system, OrcaLab software, Conda environment)
- **Asset Storage Drive (SSD)**: 200-500GB+ (downloaded asset packages)
- **Project Data Drive (SSD/HDD)**: 100GB to several TB (your simulation project files, generated data, recorded videos, etc.)

### 💡 Storage Selection Recommendations
- **SSD First**: It is strongly recommended to install the operating system, OrcaLab software, and all assets on a **Solid State Drive (SSD)**. This will significantly improve software responsiveness and scene loading times.
- **NVMe SSD**: If budget allows, prioritize NVMe interface SSDs, whose speeds far exceed SATA SSDs.
- **HDD as Auxiliary Storage**: For archived data that doesn't need frequent access, or extremely large datasets, consider using traditional Hard Disk Drives (HDDs) as auxiliary storage.

## 📝 Summary

OrcaLab's memory and storage requirements are:
- **Memory**: At least 8GB, 16GB recommended, 32GB or higher for professional use.
- **Storage**: Minimum 50GB free space, 500GB+ SSD recommended as primary drive, 1TB+ NVMe SSD with additional storage for professional use.

Ensuring your computer is equipped with sufficient memory and high-speed storage will provide a smooth, efficient runtime environment for OrcaLab, avoiding poor experiences caused by hardware bottlenecks.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [What are the common reasons for OrcaLab startup failure?](FAQ-list/026-common-reasons-for-orcalab-startup-failure.md)