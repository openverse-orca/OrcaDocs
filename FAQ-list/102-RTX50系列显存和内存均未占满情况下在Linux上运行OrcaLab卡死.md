# RTX 50系列笔记本显存和内存均未占满情况下在 Linux 上运行 OrcaLab 卡死怎么办？

## 问题

**典型场景：**

- 硬件：i9 + RTX 5070 笔记本（NVIDIA 50 系列移动端显卡）
- 系统：Ubuntu 24.04，X11 桌面
- 驱动：NVIDIA 590（或更新版本）
- 现象：运行 OrcaLab 约 10 秒后软件未响应/卡死

**关键特征：**

- 显存（VRAM）和内存（RAM）均未占满
- 显卡日志（dmesg / nvidia-smi）没有任何报错
- 卡死前无明显异常，进程未崩溃，窗口无响应

## 原因

这是 **NVIDIA RTX 50 系列笔记本显卡在 Linux + Vulkan 上的已知驱动问题**，并非 OrcaLab 本身的 Bug。

在混合 GPU 笔记本（Intel/AMD 核显 + NVIDIA 独显）上，PRIME（核显输出 + 独显渲染）模式下，Vulkan 渲染可能出现 display fence 永不信号化、reverse prime commit 死锁等底层问题，导致渲染管线卡死。该问题在 RTX 5060/5070/5080/5090 移动版上均有报告。

## 解决方案

### 方案一：BIOS 中设置为 dGPU only（推荐）

进入笔记本 BIOS，将显卡工作模式从"混合（Hybrid/Optimus）"改为 **dGPU only（独显直连）**，关闭核显，让独显直接输出。

**操作步骤：**

1. 重启笔记本，进入 BIOS（通常按 F2/Del）
2. 找到显卡/GPU 相关设置项（常见名称：`GPU Mode`、`Graphics Device`、`Display Mode`）
3. 将模式从 `Hybrid` / `Optimus` 改为 `dGPU only` / `Discrete Only` / `Ultimate`
4. 保存并重启

**各品牌设置位置参考：**

| 品牌 | 设置位置 |
|------|---------|
| ASUS ROG | BIOS → Advanced → GPU Mode → Ultimate |
| Lenovo Legion | BIOS → Config → Display → Graphics Device → Discrete |
| Dell/Alienware | BIOS → Display → Advanced → Graphics = Discrete |
| MSI | BIOS → Advanced → Graphics Adapter = Discrete |

### 方案二：配置 OrcaLab 强制使用独显（临时生效，单次启动）

若 BIOS 不支持独显直连，或不想全局关闭核显，可参考 [OrcaLab 在混合 GPU 环境下可能默认使用集成显卡而非独立显卡](101-OrcaLab在混合GPU环境下可能默认使用集成显卡而非独立显卡.md) 强制 OrcaLab 使用 NVIDIA GPU：

```bash
orcalab --force-adapter=NVIDIA
```

> ⚠️ **注意**：方案二仅解决 GPU 选择问题，无法绕过 RTX 50 系列在 Vulkan + PRIME 模式下的驱动 Bug。如方案二仍卡死，必须采用方案一。

## 副作用处理

### ROG 笔记本独显直连后亮度无法调节

部分 ASUS ROG 笔记本切换到 dGPU only 后，会出现屏幕亮度无法调节的问题。这是 Linux 内核对独显直连模式下背光控制的支持问题，可通过修改一行系统配置修复：

```bash
# 编辑 GRUB 配置
sudo nano /etc/default/grub

# 在 GRUB_CMDLINE_LINUX_DEFAULT 中添加参数
# 例如改为：
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia.NVreg_RegistryDwords=RMUsePfaMobilePanelBrightnessControl=1"

# 更新 GRUB
sudo update-grub

# 重启
sudo reboot
```

> 不同机型修复参数可能不同，请自行搜索 `ROG 独显直连 亮度` 或参考 [ASUS Linux 官方文档](https://asus-linux.org/)。

## 验证是否生效

切换到 dGPU only 后，可通过以下命令确认：

```bash
# 1. 确认核显已被关闭（应只显示 NVIDIA 独显）
lspci | grep -iE "vga|3d"

# 2. 确认 Vulkan 使用的是 NVIDIA 设备
vulkaninfo --summary | grep -i "device name"

# 3. 启动 OrcaLab 并观察是否仍卡死
orcalab
```

## 相关链接

- [NVIDIA 开发者论坛：RTX 50 系列随机渲染卡死 Bug 报告](https://forums.developer.nvidia.com/t/bug-report-random-rendering-freezes-in-proton-games-on-rtx-50-series-cards-recovers-after-alt-tab-window-refocus/374825)
- [NVIDIA 开发者论坛：RTX 5060 移动版 display fence 死锁 Bug 报告](https://forums.developer.nvidia.com/t/hard-system-freeze-display-fence-never-signals-in-reverse-prime-commit-work-deadlock-rtx-5060-laptop-gb206-amd-igpu-open-modules-595-80-and/375478)
- [OrcaLab 混合 GPU 适配器选择指南](/FAQ-list/101-OrcaLab在混合GPU环境下可能默认使用集成显卡而非独立显卡.md)
- [OrcaLab 安装与系统要求](../环境准备/系统及显卡支持.md)
