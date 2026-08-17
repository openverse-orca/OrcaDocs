# RTX 50 series freezes when running OrcaLab on Linux while VRAM and RAM are not fully occupied

## Problem

**Typical scenario:**

- Hardware: i9 + RTX 5070 laptop (NVIDIA 50 series mobile GPU)
- OS: Ubuntu 24.04, X11 desktop
- Driver: NVIDIA 590 (or newer)
- Symptom: OrcaLab becomes unresponsive/freezes after about 10 seconds

**Key characteristics:**

- VRAM and RAM are not fully occupied
- GPU logs (dmesg / nvidia-smi) show no errors
- No obvious anomaly before the freeze; process does not crash, window simply stops responding

## Cause

This is a **known driver issue with NVIDIA RTX 50 series laptop GPUs on Linux + Vulkan**, not a bug in OrcaLab itself.

On laptops with hybrid graphics (Intel/AMD iGPU + NVIDIA dGPU), when running in PRIME mode (iGPU output + dGPU rendering), the Vulkan rendering pipeline may encounter low-level issues such as display fence never signaling or reverse prime commit deadlock, causing the render pipeline to freeze. This issue has been reported on RTX 5060/5070/5080/5090 mobile editions.

## Solutions

### Option 1: Set dGPU only in BIOS (Recommended)

Enter the laptop BIOS and change the GPU operating mode from "Hybrid (Optimus)" to **dGPU only (discrete-only)**, disabling the integrated GPU so the discrete GPU outputs directly.

**Steps:**

1. Restart the laptop and enter BIOS (usually F2/Del)
2. Locate the GPU/graphics-related setting (common names: `GPU Mode`, `Graphics Device`, `Display Mode`)
3. Change the mode from `Hybrid` / `Optimus` to `dGPU only` / `Discrete Only` / `Ultimate`
4. Save and reboot

**Brand-specific BIOS locations:**

| Brand | Location |
|------|---------|
| ASUS ROG | BIOS → Advanced → GPU Mode → Ultimate |
| Lenovo Legion | BIOS → Config → Display → Graphics Device → Discrete |
| Dell/Alienware | BIOS → Display → Advanced → Graphics = Discrete |
| MSI | BIOS → Advanced → Graphics Adapter = Discrete |

### Option 2: Force OrcaLab to use the discrete GPU (Temporary, Single Launch)

If the BIOS does not support discrete-only mode, or you prefer not to globally disable the iGPU, refer to [OrcaLab may use integrated GPU instead of discrete GPU in hybrid GPU environments](101-orcalab-may-use-integrated-gpu-instead-of-discrete-gpu.md) to force OrcaLab to use the NVIDIA GPU:

```bash
orcalab --force-adapter=NVIDIA
```

> ⚠️ **Note**: Option 2 only resolves the GPU selection issue; it cannot bypass the driver bug in RTX 50 series under Vulkan + PRIME mode. If Option 2 still freezes, you must use Option 1.

## Side Effect Handling

### Brightness cannot be adjusted on ROG laptops after enabling dGPU only

Some ASUS ROG laptops experience an inability to adjust screen brightness after switching to dGPU only. This is a Linux kernel backlight control issue under discrete-only mode and can be fixed by modifying a single system configuration line:

```bash
# Edit GRUB configuration
sudo nano /etc/default/grub

# Add the parameter inside GRUB_CMDLINE_LINUX_DEFAULT
# For example:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia.NVreg_RegistryDwords=RMUsePfaMobilePanelBrightnessControl=1"

# Update GRUB
sudo update-grub

# Reboot
sudo reboot
```

> The fix parameter may differ across models. Search for `ROG dGPU only brightness` or refer to the [ASUS Linux official documentation](https://asus-linux.org/).

## Verifying the Fix

After switching to dGPU only, verify with the following commands:

```bash
# 1. Confirm the iGPU is disabled (should only show the NVIDIA dGPU)
lspci | grep -iE "vga|3d"

# 2. Confirm Vulkan is using the NVIDIA device
vulkaninfo --summary | grep -i "device name"

# 3. Launch OrcaLab and check whether it still freezes
orcalab
```

## Related Links

- [NVIDIA Developer Forum: Random rendering freeze bug report on RTX 50 series](https://forums.developer.nvidia.com/t/bug-report-random-rendering-freezes-in-proton-games-on-rtx-50-series-cards-recovers-after-alt-tab-window-refocus/374825)
- [NVIDIA Developer Forum: RTX 5060 mobile display fence deadlock bug report](https://forums.developer.nvidia.com/t/hard-system-freeze-display-fence-never-signals-in-reverse-prime-commit-work-deadlock-rtx-5060-laptop-gb206-amd-igpu-open-modules-595-80-and/375478)
- [OrcaLab hybrid GPU adapter selection guide](/FAQ-list/101-orcalab-may-use-integrated-gpu-instead-of-discrete-gpu.md)
- [OrcaLab installation and system requirements](/environment-setup/system-and-gpu-support.md)
