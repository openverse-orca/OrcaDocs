## GPU Adapter Selection

In mixed GPU environments (such as AMD CPU + NVIDIA discrete GPU laptops), OrcaLab may default to using the integrated GPU instead of the discrete GPU. This document explains how to manually specify the GPU adapter.

### Automatic Selection Logic

When no GPU is manually specified, the engine auto-selects with the following priority:

1. **Discrete GPU** (any vendor, such as NVIDIA, AMD discrete GPU, Moore Threads, etc.)
2. **NVIDIA or AMD devices** (including integrated GPUs)
3. **First enumerated device** (fallback)

> On laptops with AMD CPU + NVIDIA discrete GPU, due to the Vulkan driver enumeration order, the AMD integrated GPU may appear before the NVIDIA discrete GPU,
> causing the auto-selection logic to preferentially select the AMD integrated GPU. In this case, you need to manually specify the GPU.

---

### Method 1: Configuration File (Recommended, Persistent)

Add the following to `.orcalab/config.toml` in the working directory or `~/Orca/OrcaLab/config.toml` in the user config:

```toml
[orcalab]
# Force specify GPU adapter name (substring match, case-insensitive)
force_adapter = "NVIDIA"

# When multiple GPUs match, select which one (default 0, i.e., the first)
# adapter_index = 0
```

**Common values:**

| Value | Match Scope |
|----|---------|
| `"NVIDIA"` | All NVIDIA GPUs |
| `"RTX 4090"` | Specific model |
| `"AMD"` | All AMD GPUs (including integrated and discrete) |
| `"MTT"` | Moore Threads GPU |

---

### Method 2: Command Line Arguments (Temporary, Single Launch)

```bash
# Force use of NVIDIA GPU
orcalab --force-adapter=NVIDIA

# Force use of a specific model
orcalab --force-adapter="RTX 4090"

# Select the second GPU when multiple match
orcalab --force-adapter=RTX --adapter-index=1

# Use Moore Threads GPU
orcalab --force-adapter=MTT
```

---

### Parameter Reference Table

Different layers use different parameter names:

| Layer | Adapter Name | Adapter Index |
|------|-----------|-----------|
| Config File (TOML) | `force_adapter = "NVIDIA"` | `adapter_index = 0` |
| Python CLI | `--force-adapter=NVIDIA` | `--adapter-index=0` |
| Engine CLI | `--forceAdapter NVIDIA` | `--adapterIndex 0` |

> Engine CLI parameters are automatically converted by the Python layer; users do not need to use them directly.

---

### Other Engine GPU Parameters

The following parameters can only be set in the configuration file:

| Config Key | Default | Description |
|--------|--------|------|
| `vsync` | `true` | Vertical sync. Turning it off (`false`) may cause freezing on mixed GPU laptops |
| `lock_fps` | `0` | Framerate limit; `0` means follow the screen refresh rate |

---

### Notes

1. `force_adapter` uses **substring matching and is case-insensitive**. For example, `"NVIDIA"` can match `"NVIDIA GeForce RTX 4090"`, and `"RTX"` can match all devices containing RTX
2. If `force_adapter` does not match any device, the engine falls back to auto-selection logic
3. Command line arguments take priority over configuration file settings
4. Turning off VSync on mixed GPU laptops may cause freezing; it is recommended to keep it enabled by default
