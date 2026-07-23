# What is libx265-dev? Why is it needed?

## Question
The OrcaLab installation guide mentions that if the first launch fails, you may need to install `libx265-dev`. What is `libx265-dev`? Why does OrcaLab need it?

## Answer

`libx265-dev` is a development library that contains the **development files (header files, static libraries, etc.) for the x265 video encoder**. x265 is an open-source H.265/HEVC (High Efficiency Video Coding) encoder. OrcaLab needs it most likely because its **recording, streaming, or internal video processing functionality** depends on H.265 encoding capabilities.

## 📋 `libx265-dev` Overview

### 1. **What is H.265/HEVC**
- **H.265**, also known as **HEVC (High Efficiency Video Coding)**, is a high-efficiency video coding standard.
- It is the successor to H.264, designed to provide higher compression efficiency at the same video quality (typically saving about 50% bitrate), thereby reducing file size or bandwidth requirements.

### 2. **The x265 Encoder**
- **x265** is an open-source H.265/HEVC video encoder.
- It is widely used in various video processing scenarios, including video recording, live streaming, transcoding, etc.

### 3. **`libx265-dev`**
- `libx265-dev` is the **development package** for the `x265` encoder.
- It contains the header files and library files needed by compilers when compiling or linking programs. This means that if OrcaLab or one of its components needs to **dynamically compile** or **link** against x265 encoding functionality at runtime, this `dev` package is required.

## 🎯 Why OrcaLab Needs It

As simulation software, OrcaLab may depend on H.265 encoding capabilities in the following scenarios, thus requiring `libx265-dev`:

### 1. **Video Recording**
- OrcaLab may offer the ability to record the simulation process as video. To generate high-quality, compact video files, H.265 may be chosen as the encoding format.
- For **real-time recording** or **background encoding**, `libx265-dev` is needed to ensure the encoder module works properly.

### 2. **Remote Streaming**
- If OrcaLab supports real-time streaming of simulation visuals to other devices (such as remote desktop, web client), H.265 is an ideal choice for low latency and high image quality.
- In this process, OrcaLab may need to use `libx265-dev` to build its video stream encoding module.

### 3. **Internal Video Processing**
- Certain advanced features, such as data augmentation, scene pre-processing, or post-processing, may involve encoding or decoding video frames.
- `libx265-dev` provides the necessary encoding capabilities for these internal processes.

### 4. **Python Bindings or Plugins**
- OrcaLab may call the underlying x265 encoder through Python bindings (such as `ffmpeg-python` or other custom bindings).
- These bindings require the development header files and library files provided by `libx265-dev` when compiling.

## 🛠️ Steps to Install `libx265-dev`

If OrcaLab's first launch fails and prompts about a missing library, you can run the following command in the terminal to install it:

```bash
sudo apt install libx265-dev
```

- `sudo`: Execute the command with administrator privileges, as this is a system-level library installation.
- `apt install`: Ubuntu's package manager command for installing software packages.

After installation, try launching OrcaLab again.

## ⚠️ Important Notes

### 1. **System Permissions**
- Installing system development libraries requires `sudo` privileges.

### 2. **Network Connection**
- The `apt install` command needs to download packages from Ubuntu's software repositories, so a stable network connection is required.

### 3. **Installation Timing**
- The installation guide recommends installing "if the first launch fails," which typically means this dependency is not mandatory in all cases, or OrcaLab attempts dynamic linking and only prompts for installation after failure. However, it may also mean the dependency is only needed when certain specific features are invoked.

### 4. **Alternatives**
- In some cases, if only H.265 video playback is needed, installing `libx265` (the runtime library) rather than `libx265-dev` (the development library) would suffice. But OrcaLab explicitly requires the `dev` version, indicating it needs the development files.

## 📝 Summary

`libx265-dev` is a system library providing the development files for the H.265 video encoder. OrcaLab needs it to support its internal video recording, streaming, or video processing features. On Ubuntu systems, it can be installed with the `sudo apt install libx265-dev` command.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)