# OrcaLab 安装指南

## 一、系统要求

### 1.1 操作系统

- **推荐系统**：Ubuntu 22.04 LTS，Ubuntu 24.04 LTS

### 1.2 前置依赖

- **Miniconda**：需要提前安装最新版本的 Miniconda
- **网络要求**：需要稳定的网络连接
- **系统权限**：需要 sudo 权限安装系统依赖

### 1.3 硬件要求

- 建议配备 NVIDIA 显卡（RTX 40/50 系列）
- 建议驱动版本：≥535.00（RTX 40系列）或 ≥550.00（RTX 50系列）

---

## 二、安装步骤

### 2.1 安装 Miniconda

```bash
# 下载 Miniconda 安装脚本
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# 运行安装脚本
bash Miniconda3-latest-Linux-x86_64.sh

# 按照提示完成安装，重启终端或执行：
source ~/.bashrc
```

### 2.2 配置 PyPI 镜像源

为了加快下载速度，建议配置清华 PyPI 镜像源：

```bash
# 创建 pip 配置目录
mkdir -p ~/.pip

# 配置清华源
cat > ~/.pip/pip.conf << EOF
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host = pypi.tuna.tsinghua.edu.cn
EOF
```

### 2.3 创建 Conda 环境

```bash
# 创建名为 orcalab 的 Python 3.12 环境
conda create -n orcalab python==3.12

# 激活环境
conda activate orcalab
```

### 2.4 安装 OrcaLab

```bash
# 从 PyPI 安装 OrcaLab
pip install orca-lab
```

### 2.5 启动 OrcaLab

```bash
# 首次启动（会自动安装依赖）
orcalab

# 如果首次启动失败，安装 x265 后再次启动
sudo apt install libx265-dev
orcalab
```

**注意**：

- 首次运行 `OrcaLab` 会自动安装 Python 依赖包
- 第二次运行才会进入软件界面

---

## 四、检查安装环境及版本

安装完成后，可以通过以下方式验证：

```bash
# 1. 检查 Python 环境
python --version  # 应显示 Python 3.12.x

# 2. 检查 OrcaLab 版本
pip show orca-lab

# 3. 检查系统依赖
dpkg -l | grep libx265

# 4. 启动软件
orcalab
```

--- 
## 五、OrcaLab升级方法
有升级包可用时
```bash
# 需要添加 --upgrade 参数
pip install --upgrade orca-lab
```

---

## 六、OrcaLab卸载方法

如果需要卸载 OrcaLab：

```bash
# 1. 退出 conda 环境
conda deactivate

# 2. 删除 conda 环境
conda env remove -n orcalab
```


---

## 七、常见问题排查

### 7.1 安装问题

#### 问题：pip 安装失败，下载速度慢

**解决方案**：

1. 检查网络连接
2. 确认已配置清华 PyPI 镜像源（参考 2.2 节）
3. 验证镜像源是否可用

```bash
# 测试镜像源连接
curl https://pypi.tuna.tsinghua.edu.cn/simple/
```

#### 问题：conda 环境激活失败

**解决方案**：

```bash
# 初始化 conda
conda init bash
source ~/.bashrc

# 或手动激活
source ~/miniconda3/etc/profile.d/conda.sh
conda activate orcalab
```

### 7.2 运行问题

#### 问题：软件启动后无法连接服务器

**解决方案**：

- 检查网络连接
- 确认防火墙设置
- 使用离线启动模式（如果已下载资产）

 ![](img/install/offline-login.jpg) 

---

## 八、技术支持

如遇到问题，请：

1. 查看本文档的"常见问题排查"部分
2. 检查终端错误信息
3. 联系技术支持团队

