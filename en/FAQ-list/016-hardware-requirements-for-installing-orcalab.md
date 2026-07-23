# What hardware configuration is required to install OrcaLab?

## Question
What hardware configuration does OrcaLab require? What are the minimum and recommended configurations?

## Answer

As a high-fidelity physics AI simulation system, OrcaLab has certain hardware requirements, especially regarding graphics card performance. Below are the detailed hardware configuration requirements:

## 🎮 Graphics Card Requirements (Critical)

### ✅ Recommended GPU Configurations
```
NVIDIA RTX 40 Series:
├── RTX 4090 (Recommended)    - Top-tier performance, smooth in large scenes
├── RTX 4080 (Recommended)    - High performance, suitable for complex simulations
├── RTX 4070 (Good)    - Mid-to-high performance, smooth for general use
└── RTX 4060 (Entry)    - Basic

NVIDIA RTX 50 Series:
├── RTX 5090 (Best)    - Latest top-tier performance
└── RTX 5080 (Excellent)    - Latest high-end performance

NVIDIA RTX 30 Series
```
**Note: RTX 30 series only supports 3060 and above models, and high-performance scenarios are limited.**

### 📋 Driver Version Requirements
```bash
RTX 30 Series: Driver version ≥ 470.00
RTX 40 Series: Driver version ≥ 535.00
RTX 50 Series: Driver version ≥ 550.00

# Check current driver version
nvidia-smi
```

### ⚠️ Unsupported GPUs
- ❌ Integrated graphics (Intel UHD, AMD APU)
- ❌ AMD discrete GPUs
- ❌ NVIDIA RTX 30 series and below
- ❌ NVIDIA GTX series

## 💻 CPU Configuration Requirements

### Recommended Configurations
```
Intel Processors:
├── Intel i9-13900K/14900K (Best)
├── Intel i7-13700K/14700K (Recommended)
└── Intel i5-13600K/14600K (Good)

AMD Processors:
├── AMD Ryzen 9 7900X/7950X (Best)
├── AMD Ryzen 7 7700X/7800X3D (Recommended)
└── AMD Ryzen 5 7600X (Good)
```

### Minimum Configuration
```
Intel i5-12400 or AMD Ryzen 5 5600X
6 cores / 12 threads or above
Base frequency ≥ 3.0GHz
```

### Performance Comparison
| CPU Level | Simulation Complexity | Multitasking Capability | Recommended Scenario |
|--------|-----------|-----------|----------|
| High-End (i9/R9) | Complex large scenes | Strong | Research-grade applications |
| Mid-Range (i7/R7) | Moderate complexity scenes | Fairly strong | Teaching & learning |
| Entry (i5/R5) | Basic simple scenes | Moderate | Getting started |

## 🧠 Memory Configuration Requirements

### Recommended Configuration
```
32GB DDR4-3200 or higher (Recommended)
- Supports large complex scenes
- Multiple simulations running in parallel
- Large asset loading
```

### Minimum Configuration
```
16GB DDR4-3200 (Standard)
- Moderate-scale scenes
- Single simulation running smoothly
- Basic asset management
```


```
8GB DDR4-2666 (Minimum)
- Small simple scenes
- Basic feature exploration
- May experience performance bottlenecks
```



## 💾 Storage Configuration Requirements

### Recommended Configuration
```
SSD Storage Solution:
├── System drive: 500GB+ NVMe SSD
├── Asset drive: 1TB+ SATA SSD
└── Data drive: 500GB+ SSD (optional)

Total storage: 2TB+
```

### Minimum Configuration
```
Hybrid Storage Solution:
├── System drive: 250GB SSD (required)
├── Asset drive: 500GB HDD (usable)
└── Total storage: 750GB+
```

### Storage Usage Analysis
```
Space allocation recommendations:
├── System & software: 100GB
├── OrcaLab Asset Library: 200-500GB
├── Simulation data: 100-300GB
├── User projects: 100-200GB
└── System reserve: 100GB
```

## 🌐 Network Requirements

### Bandwidth Requirements
```
Recommended bandwidth: 100Mbps+ (download)
Minimum bandwidth: 50Mbps (download)

Uses:
- Asset package downloads
- Software updates
- Cloud service connections
```

### Network Stability
- Low-latency connection (<50ms to Asset Library)
- Stable connection (avoid frequent disconnections)
- No strict firewall restrictions

## 📱 Peripheral Requirements

### VR Devices (Optional)
```
Supported VR devices:
└── Pico Ultra 4 + bundled controllers

Use: VR teleoperation & data collection
```

### Input Devices
```
Required:
├── Keyboard (supports standard shortcuts)
└── Mouse (three-button scroll wheel mouse recommended)

Recommended:
├── Mechanical keyboard (enhanced operation experience)
└── Gaming mouse (precise control)
```

## 🖥️ Monitor Requirements

### Recommended Configuration
```
Resolution: 2560×1440 (2K) or higher
Size: 27 inches or above
Refresh rate: 60Hz or above
Color: sRGB 99%+ (for design needs)
```

### Minimum Configuration
```
Resolution: 1920×1080 (1080p)
Size: 24 inches
Refresh rate: 60Hz
```

### Multi-Monitor Support
- Multi-monitor extension supported
- Dual monitors recommended for improved productivity
- Primary monitor for 3D view, secondary for tool panels



## ⚡ Performance Optimization Recommendations

### System Optimization
```bash
# Close unnecessary background programs
# Set high-performance power mode
# Regularly clean system junk files
# Keep drivers up to date
```

### BIOS Settings
```
Enable:
├── XMP/DOCP (memory overclocking)
├── PCIe 4.0 (if supported)
└── Virtualization technology

Disable:
├── Integrated graphics (if discrete GPU present)
└── Unnecessary onboard devices
```

## 🔍 Hardware Check Commands

```bash
# CPU information
lscpu | grep "Model name"
cat /proc/cpuinfo | grep "cpu cores"

# Memory information
free -h
dmidecode -t memory | grep -E "Size|Speed"

# Graphics card information
lspci | grep VGA
nvidia-smi

# Storage information
lsblk
df -h

# Network speed test
speedtest-cli
```

Choosing the right hardware configuration is the foundation for ensuring smooth OrcaLab operation. It is recommended to select the appropriate configuration based on your usage needs and budget.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [Common Troubleshooting](environment-setup/ubuntu-installation-guide-v1.0.md)