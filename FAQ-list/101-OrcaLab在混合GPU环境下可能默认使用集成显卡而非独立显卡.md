## GPU 适配器选择

OrcaLab 在混合 GPU 环境（如 AMD CPU + NVIDIA 独显笔记本）下，可能默认使用集成显卡而非独立显卡。本文档说明如何手动指定 GPU 适配器。

### 自动选择逻辑

当未手动指定 GPU 时，引擎按以下优先级自动选择：

1. **独立显卡**（任何厂商，如 NVIDIA、AMD 独显、摩尔线程等）
2. **NVIDIA 或 AMD 设备**（包括集成显卡）
3. **枚举到的第一个设备**（兜底）

> 在 AMD CPU + NVIDIA 独显的笔记本上，由于 Vulkan 驱动枚举顺序，AMD 集显可能排在 NVIDIA 独显之前，
> 导致自动选择逻辑优先选中 AMD 集显。此时需要手动指定 GPU。

---

### 方式一：配置文件（推荐，持久生效）

在工作目录的 `.orcalab/config.toml` 或用户配置 `~/Orca/OrcaLab/config.toml` 中添加：

```toml
[orcalab]
# 强制指定 GPU 适配器名称（子串匹配，不区分大小写）
force_adapter = "NVIDIA"

# 当匹配到多个 GPU 时，选择第几个（默认 0，即第一个）
# adapter_index = 0
```

**常见值：**

| 值 | 匹配范围 |
|----|---------|
| `"NVIDIA"` | 所有 NVIDIA GPU |
| `"RTX 4090"` | 特定型号 |
| `"AMD"` | 所有 AMD GPU（含集显和独显） |
| `"MTT"` | 摩尔线程 GPU |

---

### 方式二：命令行参数（临时生效，单次启动）

```bash
# 强制使用 NVIDIA GPU
orcalab --force-adapter=NVIDIA

# 强制使用特定型号
orcalab --force-adapter="RTX 4090"

# 匹配多个 GPU 时选择第二个
orcalab --force-adapter=RTX --adapter-index=1

# 使用摩尔线程 GPU
orcalab --force-adapter=MTT
```

---

### 参数对照表

不同层面使用不同的参数命名：

| 层面 | 适配器名称 | 适配器索引 |
|------|-----------|-----------|
| 配置文件 (TOML) | `force_adapter = "NVIDIA"` | `adapter_index = 0` |
| Python 命令行 | `--force-adapter=NVIDIA` | `--adapter-index=0` |
| 引擎命令行 | `--forceAdapter NVIDIA` | `--adapterIndex 0` |

> 引擎命令行参数由 Python 端自动转换，用户无需直接使用。

---

### 其他引擎 GPU 参数

以下参数仅支持在配置文件中设置：

| 配置键 | 默认值 | 说明 |
|--------|--------|------|
| `vsync` | `true` | 垂直同步。关闭（`false`）可能在混合 GPU 笔记本上导致卡死 |
| `lock_fps` | `0` | 帧率限制，`0` 表示跟随屏幕刷新率 |

---

### 注意事项

1. `force_adapter` 是**子串匹配、不区分大小写**的。例如 `"NVIDIA"` 可以匹配 `"NVIDIA GeForce RTX 4090"`，`"RTX"` 可以匹配所有包含 RTX 的设备
2. 如果 `force_adapter` 匹配不到任何设备，引擎会回退到自动选择逻辑
3. 命令行参数优先级高于配置文件
4. 关闭 VSync 在混合 GPU 笔记本上可能导致卡死，建议保持默认开启
