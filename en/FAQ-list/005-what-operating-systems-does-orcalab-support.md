# What operating systems does OrcaLab support?

## Question
Which operating systems can OrcaLab run on? What are the specific system version requirements?

## Answer

Currently, OrcaLab supports Linux and Windows operating systems, with specific Ubuntu versions recommended for Linux.

## Supported Operating Systems

### 🐧 Linux System Requirements

#### ✅ Officially Recommended Systems
```bash
# Preferred system versions
Ubuntu 22.04 LTS (Jammy Jellyfish)
Ubuntu 24.04 LTS (Noble Numbat)
```

#### System Selection Recommendations
- **Ubuntu 22.04 LTS**: Higher stability, best compatibility
- **Ubuntu 24.04 LTS**: Newer version, potentially better performance

### 🪟 Windows System Requirements
```bash
# Preferred system versions
Windows 10/11
```
#### System Selection Recommendations
- Windows 11 is recommended as it offers better performance and stability.

### 🚫 Unsupported Operating Systems

#### Windows Systems
- ❌ Systems below Windows 10 — not officially tested
- ❌ Windows Server — not supported
- ❌ WSL (Windows Subsystem for Linux) — limited support

#### macOS Systems
- ❌ macOS Intel — not supported
- ❌ macOS Apple Silicon — not supported

#### Other Linux Distributions
- ❌ CentOS/RHEL — not officially tested
- ❌ Fedora — not officially tested
- ❌ Debian — may be compatible but not officially supported

## System Environment Requirements

### 📋 Basic Requirements

#### System Architecture
```
x86_64 (64-bit) architecture
```

#### Kernel Requirements
```bash
# Check kernel version
uname -r
# Recommended: 5.15+ (Ubuntu 22.04) or 6.8+ (Ubuntu 24.04)
```

#### Permission Requirements
```bash
# sudo privileges required to install system dependencies
sudo apt update
sudo apt install libx265-dev  # Example system dependency
```

### 🔧 Required Software Components

#### Python Environment
```bash
# Managed via Miniconda
Python 3.12 (recommended version)
```

#### System Library Dependencies
```bash
# Required system libraries
libx265-dev          # Video codec library
build-essential      # Compilation toolchain
```

#### Network Requirements
- Stable network connection for downloading assets
- Ability to access PyPI mirror sources
- Ability to access Asset Library services

## Hardware Compatibility

### 💻 GPU Requirements (Important)

#### Recommended Graphics Cards
```
NVIDIA RTX 40 Series:
- RTX 4090, 4080, 4070, 4060, etc.
- Driver version: ≥535.00

NVIDIA RTX 50 Series:
- RTX 5090, 5080 and other latest models
- Driver version: ≥550.00

NVIDIA RTX 30 Series:
- RTX 3090, 3080, 3070, 3060, etc.
- Driver version: ≥470.00
```
**Note: RTX 30 series only supports 3060 and above models, and high-performance scenarios are limited.**

#### Check Graphics Card Information
```bash
# View graphics card model
lspci | grep VGA

# View NVIDIA driver version
nvidia-smi

# View CUDA version
nvcc --version
```

### 🖥️ System Requirements

#### Recommended Configuration
```
CPU: Intel i7 / AMD Ryzen 7 or above
Memory: 16GB or above
Storage: 100GB+ free space (for asset storage)
```

#### Minimum Configuration
```
CPU: Intel i5 / AMD Ryzen 5
Memory: 8GB
Storage: 50GB+ free space
```

## Pre-Installation Check

### 🔍 System Compatibility Check

```bash
# Check system version
lsb_release -a

# Check system architecture
uname -m  # Should display x86_64

# Check available space
df -h

# Check memory
free -h

# Check graphics card
lspci | grep -i nvidia
```

### 📦 Environment Setup Checklist

- [ ] Ubuntu 22.04/24.04 LTS / Windows 11
- [ ] x86_64 architecture
- [ ] NVIDIA RTX graphics card
- [ ] Appropriate driver version
- [ ] sudo privileges
- [ ] Stable network connection
- [ ] Sufficient storage space

## Virtualization Environment Support

### 💡 Virtual Machine Usage
**⚠️ Running in a virtual machine is not recommended**
- GPU passthrough configuration is complex
- Significant performance loss
- Compatibility issues may arise

### 🐳 Containerization Support
**Docker support is limited**
- Requires GPU container runtime
- Graphical interface configuration is complex
- Direct physical machine installation is recommended

## Future System Support Plans

### 🔮 Potentially Supported Systems
Based on user demand, the following may be considered in the future:
- macOS version (Apple Silicon adaptation)
- More Linux distributions

### 📢 Getting Update Information
- Follow official release announcements
- Check GitHub repository updates
- Participate in community discussions

## System Selection Recommendations

### 🎯 New Users
Recommended: **Ubuntu 22.04 LTS** or **Windows 11**:
- Long-term support version
- Rich community support
- Best stability

### 🚀 Advanced Users
May try **Ubuntu 24.04 LTS**:
- Newer software packages
- Better hardware support
- Newer kernel features

### 🔧 System Administrators
Recommended configuration:
- Use LTS versions for stability
- Regularly update system patches
- Monitor hardware compatibility

## FAQ

### Q: Can OrcaLab run on WSL2?
A: WSL2 support is limited; GPU acceleration in particular may have issues. Using a native Linux system is recommended.

### Q: Can it run on cloud servers?
A: Requires a GPU-equipped cloud server instance capable of running graphical interface programs.

### Q: Does the system language need to be English?
A: Not strictly required, but using an English environment is recommended to avoid encoding issues.

Choosing the right operating system is the first step to successfully running OrcaLab. Ensuring the system environment meets requirements will provide a solid foundation for subsequent use.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [Common Troubleshooting](environment-setup/ubuntu-installation-guide-v1.0.md)