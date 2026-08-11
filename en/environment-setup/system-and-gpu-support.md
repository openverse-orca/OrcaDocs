# System and GPU Support

This page describes the operating systems, graphics cards, and other hardware requirements supported by OrcaLab to help you verify environment compatibility before installation.

## 1. Supported Operating Systems

### 1.1 Windows

| OS | Support | Notes |
| --- | --- | --- |
| Windows 11 | ✅ Officially recommended | Best performance and stability |
| Windows 10 | ✅ Supported | Keep the system up to date |

### 1.2 Linux

| OS | Support | Notes |
| --- | --- | --- |
| Ubuntu 22.04 LTS | ✅ Officially recommended | High stability, best compatibility |
| Ubuntu 24.04 LTS | ✅ Supported | Newer version, better hardware support |
| UOS V20 | ✅ Supported | Domestic OS adaptation |

### 1.3 System Architecture

```
x86_64 (64-bit) architecture
```

---

## 2. GPU Support

### 2.1 NVIDIA RTX Series (Recommended)

OrcaLab recommends NVIDIA RTX series GPUs, **RTX 3060 or above required**.

| GPU Series | Supported Models | Recommended Driver | Notes |
| --- | --- | --- | --- |
| RTX 50 Series | RTX 5090, 5080, 5070, etc. | ≥ 550.00 | 5080/5070 verified on Windows 11; 5090 and same-architecture models theoretically compatible but untested |
| RTX 40 Series | RTX 4090, 4080, 4070, 4060, etc. | ≥ 535.00 | 4080 (Win11), 4070 (Win11/Ubuntu 22.04/24.04), 4060 (Ubuntu 24.04) verified; 4090 etc. untested |
| RTX 30 Series | RTX 3090, 3080, 3070, 3060 | ≥ 470.00 | ⚠️ Only 3090 (Windows 10) verified; 3080/3070/3060 theoretically compatible but untested; 30 series may be limited in high-performance scenarios |

> ⚠️ **Note**: Same-series models not listed above are theoretically compatible but have not been officially tested. If you encounter issues, please contact technical support.

#### Checking NVIDIA GPU Information

```bash
# View GPU model
lspci | grep VGA

# View NVIDIA driver version
nvidia-smi

# View CUDA version
nvcc --version
```

### 2.2 AMD Series

| GPU Model | Support | Notes |
| --- | --- | --- |
| AMD Radeon RX 9070 XT | ✅ Tested | Requires AMD-SMI version 26.2.1+fc0010cf6a or above |
| Other AMD GPUs | ❓ Untested | Not officially tested; compatibility not guaranteed |

#### Checking AMD GPU Information

```bash
# View AMD GPU information
lspci | grep -i amd

# View AMD-SMI version
amd-smi version
```

---

## 3. Hardware Requirements

### 3.1 Recommended Configuration

| Component | Requirement |
| --- | --- |
| CPU | Intel i7 / AMD Ryzen 7 or above |
| Memory | 32GB or above |
| Storage | 100GB+ available space (for asset storage) |
| GPU | NVIDIA RTX 40/50 series (verified: 4060/4070/4080/5070/5080) or AMD Radeon RX 9070 XT |

### 3.2 Minimum Configuration

| Component | Requirement |
| --- | --- |
| CPU | Intel i5 / AMD Ryzen 5 |
| Memory | 8GB |
| Storage | 50GB+ available space |
| GPU | NVIDIA RTX 4060 or above (verified); RTX 3060-3080 theoretically compatible but untested; AMD Radeon RX 9070 XT |

---

## 4. System Environment Requirements

### 4.1 Python Environment

```bash
# Managed via Miniconda
Python 3.12 (recommended version)
```

### 4.2 System Library Dependencies (Linux)

```bash
# Required system libraries
libx265-dev          # Video codec library
build-essential      # Build toolchain
```

### 4.3 Network Requirements

- Stable network connection for downloading assets
- Access to PyPI mirror sources
- Access to the asset library service

### 4.4 Permission Requirements

```bash
# Linux requires sudo privileges to install system dependencies
sudo apt update
sudo apt install libx265-dev
```

```bash
# Windows requires CMD administrator privileges
```

---

## 5. Pre-installation Checks

### 5.1 System Compatibility Check

```bash
# Check OS version
lsb_release -a            # Linux
winver                    # Windows

# Check system architecture
uname -m                  # Should display x86_64

# Check available space
df -h                     # Linux

# Check memory
free -h                   # Linux
```

### 5.2 Environment Preparation Checklist

- [ ] Windows 10/11 or Ubuntu 22.04/24.04 LTS or UOS V20
- [ ] x86_64 architecture
- [ ] NVIDIA RTX 4060 or above (verified: 3090/4060/4070/4080/5070/5080) or AMD Radeon RX 9070 XT
- [ ] Appropriate GPU driver version
- [ ] sudo / administrator privileges
- [ ] Stable network connection
- [ ] Sufficient storage space

---

## 6. Virtualization Environment Notes

### 6.1 Virtual Machine Usage

> ⚠️ **Running in a virtual machine is not recommended**
> - GPU passthrough configuration is complex
> - Significant performance loss
> - Compatibility issues may occur

If you need to connect to a virtual machine remotely, **Sunshine + Moonlight** is recommended as a high-performance remote desktop solution.

### 6.2 Container Support

Docker support is limited:
- Requires GPU container runtime
- Complex graphical interface configuration
- Direct physical machine installation is recommended

---

## 7. Related Links

- [Linux Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [Windows Installation Guide](environment-setup/windows-installation-guide-v1.0.md)
- [FAQ: What operating systems does OrcaLab support](FAQ-list/005-what-operating-systems-does-orcalab-support.md)
