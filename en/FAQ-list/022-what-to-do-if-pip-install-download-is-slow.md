# What to do if pip install OrcaLab download is slow?

## Question
When following the OrcaLab installation guide and running the `pip install orca-lab` command, the download speed is very slow, causing the installation to take too long or fail. How can I resolve slow pip download speeds?

## Answer

Slow pip download speeds are usually caused by a slow network connection to the official PyPI source. By **configuring a domestic PyPI mirror**, you can significantly improve download speed.

## 🚀 Solution: Configure PyPI Mirror

PyPI (Python Package Index) is Python's official third-party library repository. Configuring a domestic mirror, such as the **Tsinghua University Open Source Software Mirror (TUNA)**, can dramatically speed up package downloads.

### 1. **Temporary Mirror Usage**

If you only need to install `orca-lab` this one time, you can temporarily specify a mirror using the `-i` or `--index-url` parameter.

```bash
pip install orca-lab -i https://pypi.tuna.tsinghua.edu.cn/simple
```

#### Pros
- Simple and quick, no configuration file modification required.

#### Cons
- Must be manually specified for each installation, easy to forget.
- Not suitable for situations requiring downloads from multiple sources simultaneously.

### 2. **Permanent Mirror Configuration (Recommended)**

By modifying pip's configuration file, you can permanently change the default source to a domestic mirror — configure once and forget.

#### Steps

1. **Create the pip config directory** (if it doesn't exist):
   ```bash
   mkdir -p ~/.pip
   ```
   - `~` represents your user home directory (e.g., `/home/your_username/`).
   - The `mkdir -p` command recursively creates directories, even if parent directories don't exist.

2. **Create or edit the `pip.conf` file**:
   Use a text editor (such as `nano` or `vim`) to open or create the `~/.pip/pip.conf` file.
   ```bash
   nano ~/.pip/pip.conf
   # Or use the cat command to write directly
   # cat > ~/.pip/pip.conf << EOF
   # [global]
   # index-url = https://pypi.tuna.tsinghua.edu.cn/simple
   # [install]
   # trusted-host = pypi.tuna.tsinghua.edu.cn
   # EOF
   ```

3. **Add the following content to the `pip.conf` file**:
   ```ini
   [global]
   index-url = https://pypi.tuna.tsinghua.edu.cn/simple
   [install]
   trusted-host = pypi.tuna.tsinghua.edu.cn
   ```
   - `index-url`: Specifies the default PyPI mirror URL.
   - `trusted-host`: Adds the mirror host to the trust list to avoid SSL certificate verification issues.

4. **Save and close the file**.

#### Pros
- Configure once, works permanently — all `pip install` commands will automatically use the mirror.
- More convenient and less error-prone.

#### Cons
- Requires modifying configuration files, which may be slightly more complex for beginners.

### 3. **Verify the Mirror is Working**

After configuration, you can try installing a small package to verify the mirror is working:

```bash
pip install requests
```

If the download speed is noticeably faster, the mirror configuration was successful.

## 💡 Other Optimization Suggestions

### 1. **Check Network Connection**
- Ensure your network connection is stable with sufficient bandwidth.
- Try restarting your router or switching network environments.

### 2. **Use VPN or Proxy**
- If you are on a corporate or school network, you may need to configure a VPN or proxy to access external resources, including PyPI mirrors.
- Consult your network administrator for detailed proxy settings.

### 3. **Clear pip Cache**
- Cache may cause some issues; try clearing the pip cache.
  ```bash
  pip cache purge
  ```

### 4. **Upgrade pip**
- Ensure your pip version is up to date; newer versions often have performance improvements and bug fixes.
  ```bash
  pip install --upgrade pip
  ```

## 📝 Summary

Slow pip download speed is a common issue. Configuring the **Tsinghua PyPI mirror** is the most effective way to resolve it. The **permanent configuration** approach is recommended for more convenient Python package installation in the future.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What to do if conda environment creation fails?](FAQ-list/021-what-to-do-if-conda-environment-creation-fails.md)