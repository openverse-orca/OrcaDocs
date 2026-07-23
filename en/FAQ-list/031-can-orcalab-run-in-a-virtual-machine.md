# Can OrcaLab run in a virtual machine?

## Question
OrcaLab has high hardware requirements, particularly needing an NVIDIA RTX graphics card. Can I install and run OrcaLab in a virtual machine (such as VMware, VirtualBox)? What limitations or issues would there be?

## Answer

**Theoretically, OrcaLab can be installed in a virtual machine, but it is generally not recommended and will face significant limitations and performance issues.** As a simulation system requiring high-performance GPU acceleration, OrcaLab typically performs poorly in virtual machine environments.

## 🚫 Challenges of Running OrcaLab in a Virtual Machine

### 1. **GPU Passthrough Is Complex and Limited**
- **Performance Bottleneck**: Virtual machines typically cannot directly access the physical GPU; instead, access goes through a virtualization layer, causing significant GPU performance degradation or complete loss.
- **Complex Passthrough**: To allow a virtual machine to directly use the physical GPU (GPU Passthrough), support from both the host machine and virtualization software (such as VMware ESXi, Proxmox VE) is required. The configuration process is very complex and has strict requirements on hardware and system environment.
- **Single GPU Limitation**: Even if GPU passthrough is successfully implemented, one GPU can typically only be used exclusively by one virtual machine, making it impossible to share the GPU between host and guest.

### 2. **Severe Performance Loss**
- **CPU Virtualization Overhead**: The hypervisor introduces additional CPU overhead, affecting simulation computation and AI training efficiency.
- **Memory & Disk I/O**: Virtual machine memory and disk I/O performance is also typically lower than physical machines, affecting asset loading and data processing speed.

### 3. **Graphics Rendering Issues**
- **OpenGL Compatibility**: OrcaLab's GUI and 3D rendering depend on OpenGL. Virtual machine support for OpenGL virtualization may be incomplete or inefficient, leading to display anomalies, stuttering, or even inability to render.
- **Driver Issues**: NVIDIA drivers installed inside the virtual machine may not fully leverage the physical GPU's performance and may even cause compatibility issues.

### 4. **VR Device Compatibility**
- OrcaLab supports VR teleoperation data collection, but this requires low-latency direct interaction between the VR device and the system. A virtual machine environment may introduce significant latency or even fail to recognize the VR device.

## 💡 Alternatives & Recommendations

### 1. **Physical Machine Installation (Recommended)**
- **Best Choice**: Install OrcaLab directly on a physical Ubuntu machine. This is the recommended approach for the best performance and most stable experience.
- **Simple & Efficient**: Eliminates the complexity and performance loss introduced by virtualization.

### 2. **Dual Boot**
- **Approach**: Install both Windows and Ubuntu as a dual-boot system on your computer.
- **Advantages**: When you need to run OrcaLab, boot directly into Ubuntu to fully utilize hardware performance. Does not affect your daily Windows usage.
- **Operation**:
  1. Back up all important data.
  2. On the Windows system, shrink a partition to create installation space for Ubuntu.
  3. Create an Ubuntu bootable USB and install, being sure to select "Install alongside Windows."

### 3. **Cloud Computing / GPU Server**
- **Approach**: Rent a cloud server with a high-performance NVIDIA GPU (such as AWS EC2, Google Cloud, Azure).
- **Advantages**:
  - No need to purchase expensive hardware.
  - Can scale computing resources on demand.
  - Typically comes pre-installed with a compatible Linux system and GPU drivers.
- **Challenges**:
  - Requires some Linux server operation experience.
  - Remote desktop connections may introduce graphical latency.
  - Costs increase with usage time.

### 4. **WSL2 (Windows Subsystem for Linux 2) — Limited Support**
- **Approach**: Install WSL2 on a Windows system, and install Ubuntu and OrcaLab within WSL2.
- **Advantages**: No dual-boot needed; can run Linux applications directly within the Windows environment.
- **Limitations**:
  - **GPU Support**: WSL2's GPU support is currently primarily CUDA, but support for OpenGL graphical interface applications is still maturing and may have performance or compatibility issues.
  - **Graphical Interface**: Running OrcaLab's GUI requires WSL2 graphics support (WSLg), which may have latency or display anomalies.
  - **VR Devices**: WSL2's compatibility with VR devices is unclear; teleoperation may not be achievable.

## 📝 Summary

While running OrcaLab in a virtual machine is technically feasible, it is not an ideal choice due to **GPU virtualization difficulties, severe performance loss, and graphics compatibility issues**. To obtain the best user experience and simulation performance, it is strongly recommended to **install Ubuntu on a physical machine and run OrcaLab directly**, or consider alternatives such as **dual-boot** and **GPU cloud servers**.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [Why does OrcaLab recommend NVIDIA RTX graphics cards?](FAQ-list/017-why-does-orcalab-recommend-nvidia-rtx-gpus.md)