# OrcaLab Installation Guide

## 1. System Requirements

### 1.1 Operating System and Hardware Requirements

- **Reference**: [System and GPU Support](/environment-setup/system-and-gpu-support.md)

### 1.2 Prerequisites

- **Miniconda**: Requires the latest version of Miniconda to be installed beforehand
- **Network Requirements**: A stable network connection is required
- **System Permissions**: sudo privileges are required to install system dependencies
- **User Registration**: See the User Registration & Management section to complete user registration

### 1.3 ORCALab Latest Version: 26.7.1
 - The installation command in Section 2.3 downloads the latest version by default. You may also install a specific version: pip install orca-lab==xx.x.x

---

## 2. Installation Steps

### 2.1 Install Miniconda

```bash
# Download the Miniconda installation script
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Run the installation script
bash Miniconda3-latest-Linux-x86_64.sh

# Follow the prompts to complete installation, then restart the terminal or run:
source ~/.bashrc
```


### 2.2 Create a Conda Environment

```bash
# Create a Python 3.12 environment named orcalab
conda create -n orcalab python==3.12

# Activate the environment
conda activate orcalab
# Upon successful activation, the conda environment name appears in parentheses, e.g.: (orcalab) 123@E-AX:~/orcalab
```

### 2.3 Install OrcaLab

```bash
# Install OrcaLab — Tsinghua or Aliyun mirror recommended. Default source installation requires a VPN and may be slow
pip install orca-lab -i https://pypi.tuna.tsinghua.edu.cn/simple
# You may also install a specific version: orca-lab==xx.x.x
```

### 2.4 Launch OrcaLab

```bash
# First launch (dependencies will be installed automatically)
orcalab
```

**Note**:

- The first run of `OrcaLab` will automatically install Python dependency packages
- The second run will enter the software interface

---

## 3. Verifying the Installation Environment & Version

After installation, you can verify with the following:

```bash
# 1. Check Python environment
python --version  # Should display Python 3.12.x

# 2. Check OrcaLab version
pip show orca-lab

# 3. Check system dependencies
dpkg -l | grep libx265

# 4. Launch the software
orcalab
```

---
## 4. Upgrading OrcaLab
When an upgrade package is available:
```bash
# The --upgrade flag is required. You may also specify a version: orca-lab==xx.x.x
pip install --upgrade orca-lab
```

---

## 5. Uninstalling OrcaLab

If you need to uninstall OrcaLab:

```bash
# 1. Exit the conda environment
conda deactivate

# 2. Remove the conda environment
conda env remove -n orcalab
```


---

## 6. Common Troubleshooting

### 6.1 Installation Issues

#### 6.1.1 Issue: pip installation fails, slow download speed

**Solution**:

1. Check network connection
2. Confirm the Tsinghua PyPI mirror is configured (refer to Section 2.2)
3. Verify the mirror is accessible

```bash
# Test mirror connection
curl https://pypi.tuna.tsinghua.edu.cn/simple/
```

#### 6.1.2 Issue: conda environment activation fails

**Solution**:

```bash
# Initialize conda
conda init bash
source ~/.bashrc

# Or manually activate
source ~/miniconda3/etc/profile.d/conda.sh
conda activate orcalab
```

### 6.2 Runtime Issues

#### 6.2.1 Issue: Running ORCA Lab on a virtual machine shows low framerate

**Solution**:



#### 6.2.2 Issue: Software cannot connect to server after launching

**Solution**:

- Check network connection
- Verify firewall settings
- Use offline launch mode (if assets have already been downloaded)

 ![](../img/install/offline-login.jpg)

---

## 7. Technical Support

If you encounter issues, please:

1. Refer to the "Common Troubleshooting" section of this document
2. Check terminal error messages
3. Scan the QR code to contact the technical support team

![](../img/install/chat_scode.png)

---