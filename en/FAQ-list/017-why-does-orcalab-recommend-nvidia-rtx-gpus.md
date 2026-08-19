# Why does OrcaLab recommend NVIDIA RTX graphics cards?

## Question
OrcaLab's installation guide explicitly recommends using NVIDIA RTX series graphics cards. What is the reason behind this? What is the impact of using other graphics cards?

## Answer

The core reason OrcaLab recommends NVIDIA RTX series graphics cards (RTX 3060 or above required) is their **powerful GPU computing capability** and **optimized support for specific NVIDIA technologies**, which is crucial for high-fidelity physics AI simulation. Verified models include RTX 3090, RTX 4060/4070/4080, and RTX 5070/5080; in addition, the AMD Radeon RX 9070 XT is also tested and supported.

## 🚀 Core Reasons

### 1. **GPU-Accelerated Physics Computation**
- **Physics Engine Acceleration**: OrcaLab's underlying physics engine can fully leverage the parallel computing power of NVIDIA GPUs to accelerate complex physics simulations such as collision detection, rigid body dynamics, and joint calculations.
- **Massive Parallel Computing**: GPUs have thousands of cores, making them ideal for processing large numbers of independent physics computation tasks, far exceeding the serial processing capability of CPUs.

### 2. **AI Training & Inference Performance**
- **CUDA Cores**: NVIDIA RTX graphics cards are equipped with a large number of CUDA cores, which are the foundation for deep learning training and inference. As an AI simulation system, the speed of AI algorithm execution directly affects OrcaLab's efficiency.
- **Tensor Cores**: RTX cards also contain Tensor Cores, specifically designed to accelerate matrix multiplication and tensor operations, which excel in deep learning models (especially Transformer models), further improving AI task performance.
- **DLSS/RTX Technology**: While DLSS is primarily used for game rendering, other components of the RTX technology stack may also accelerate specific computations or rendering effects in simulation.

### 3. **Real-Time Ray Tracing & Rendering**
- **RT Cores**: The ray tracing cores (RT Cores) in RTX graphics cards enable more realistic, physically accurate lighting, reflection, and shadow effects.
- **High-Quality Rendering**: This is crucial for OrcaLab's need to present high-fidelity 3D scenes, providing visual feedback closer to the real world and helping users more accurately evaluate simulation results.
- **Data Generation**: In certain AI training scenarios, synthetic images with realistic lighting effects need to be generated as training data, where the rendering capabilities of RTX graphics cards demonstrate their advantage.

### 4. **Stable Drivers & Ecosystem**
- **NVIDIA Drivers**: NVIDIA provides mature, stable GPU drivers for Linux systems, ensuring OrcaLab can fully leverage hardware performance while reducing compatibility issues.
- **CUDA Ecosystem**: The vast CUDA ecosystem includes rich development tools, libraries, and optimization practices, facilitating low-level optimization and feature extension by OrcaLab developers.

## ⚠️ Impact of Using Other Graphics Cards

### 1. **Integrated Graphics (Intel UHD Graphics)**
- **Insufficient Performance**: Integrated graphics lack dedicated video memory and powerful compute units, unable to support the high-performance physics simulation and 3D rendering required by OrcaLab.
- **Unable to Run**: OrcaLab may not launch at all, or even if it does, it will be severely sluggish with extremely low framerates, making effective operation impossible.

### 2. **AMD Graphics Cards**
- **Supported Model**: AMD Radeon RX 9070 XT has passed official testing (requires AMD-SMI version 26.2.1+fc0010cf6a or above).
- **Other Models Untested**: AMD GPUs other than the RX 9070 XT have not been officially tested; compatibility is not guaranteed. AMD's ROCm or OpenCL ecosystem may have performance bottlenecks.
- **Driver Requirements**: On Linux, ensure the AMD driver and AMD-SMI version meet the requirements; otherwise stability may be affected.

### 3. **Older NVIDIA Graphics Cards (GTX Series, RTX 20/30 Series)**
- **RTX 30 Series**: RTX 3090 verified (Windows 10); 3080/3070/3060 theoretically compatible but untested; 30 series may be limited in high-performance scenarios.
- **GTX and RTX 20 Series**: Lack the latest Tensor Cores and RT Cores, or have fewer cores. Performance is noticeably insufficient when handling complex scenes, large-scale AI training, or high-fidelity rendering, potentially causing simulation stutter and extended training times.
- **Driver Version Limitations**: Older cards may not support the latest driver versions, preventing the use of the latest optimizations.

## 📈 Summary

NVIDIA RTX series graphics cards provide OrcaLab with **powerful physics computation, AI training, and high-quality rendering capabilities** — key to ensuring a smooth and efficient simulation experience. Using non-compliant graphics cards will result in:

- **Performance Bottlenecks**: Slow, stuttering simulation execution.
- **Limited Functionality**: Some high-fidelity rendering or AI acceleration features cannot be enabled.
- **Compatibility Issues**: May cause software instability or failure to launch.

Therefore, to obtain the best OrcaLab experience, it is strongly recommended to equip your system with an NVIDIA RTX series graphics card meeting the recommended specifications.

## Related Links
- [System and GPU Support](environment-setup/system-and-gpu-support.md)
- [Linux Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [Windows Installation Guide](environment-setup/windows-installation-guide-v1.0.md)
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [What is the technical architecture of OrcaLab?](FAQ-list/013-what-is-the-technical-architecture-of-orcalab.md)