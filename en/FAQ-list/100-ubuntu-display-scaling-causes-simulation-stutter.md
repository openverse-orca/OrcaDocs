# Ubuntu display scaling causes simulation stutter — what to do?

## Question
On Ubuntu, when I set the system display scaling to a non-integer value (such as 125%, 150%, or 175%), running OrcaLab and executing a simulation results in OrcaLab's display resolution being much higher than the monitor's physical resolution, causing the simulation to become very choppy with a significant drop in rendering framerate.

## Answer
This is a known issue at the Ubuntu system level. Ubuntu's fractional scaling feature sets the actual rendering resolution higher than the monitor's physical resolution at the system level, which causes a significant increase in OrcaLab's rendering load, thereby affecting simulation framerate and smoothness.

## 🔍 Symptoms
- When using fractional scaling (125%, 150%, 175%, etc.), OrcaLab's actual rendering resolution is higher than the monitor's physical resolution
- Increased rendering load causes simulation stutter and framerate drops
- When using integer scaling (100%, 200%, 300%), OrcaLab's resolution matches the monitor and runs smoothly

## 🛠️ Solutions

### 1. **Use Integer Scaling (Recommended)**

#### Steps
1. Open Ubuntu System Settings
2. Go to "Displays" settings
3. Adjust the Scale to an integer value:
   - **100%** (default)
   - **200%** (suitable for high-resolution monitors)
   - **300%** (suitable for ultra-high-definition monitors)
4. Save settings and restart OrcaLab

#### Recommended Configurations
- For 1080p (1920x1080) monitors: use 100%
- For 4K (3840x2160) monitors: use 200%
- For 5K and above monitors: use 200% or 300%

### 2. **Adjust Monitor Resolution (Alternative)**

If you really need larger interface elements, consider:
1. Lowering the monitor resolution by one level (e.g., from 4K to 2K)
2. Keeping the scaling at 100%
3. This gives you larger interface elements without affecting OrcaLab performance

### 3. **Temporarily Switch Scaling**

If you need fractional scaling in certain applications, you can:
1. Use fractional scaling for daily use
2. Temporarily switch to integer scaling before running OrcaLab
3. Switch back after using OrcaLab

## 💡 Technical Notes
- Ubuntu's fractional scaling works by "rendering larger then shrinking the display"
- This causes OrcaLab's actual rendering resolution to be higher than the monitor's physical resolution
- The specific calculation of rendering resolution is controlled by the Ubuntu system at a low level and OrcaLab cannot intervene
- Higher rendering resolution means more pixels to process, significantly increasing rendering load
- This is a limitation at the Ubuntu system level that OrcaLab cannot directly resolve

## 📝 Summary
To get the best OrcaLab performance experience, **it is strongly recommended to use integer scaling ratios (100%, 200%, or 300%) on Ubuntu**. This ensures OrcaLab's rendering resolution matches the monitor's physical resolution, resulting in a smooth simulation experience.

## Related Links
- [How to improve simulation speed?](FAQ-list/084-how-to-improve-simulation-speed.md)
- [What hardware configuration is required for OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [Which Ubuntu LTS version is better: 22.04 or 24.04?](FAQ-list/018-which-ubuntu-lts-version-is-better-2204-or-2404.md)
