# OrcaLab支持哪些操作系统？

## 问题
OrcaLab可以在哪些操作系统上运行？对系统版本有什么具体要求？

## 回答

目前，OrcaLab **仅支持Linux操作系统**，特别是Ubuntu的特定版本。

## 支持的操作系统

### 🐧 Linux系统要求

#### ✅ 官方推荐系统
```bash
# 首选系统版本
Ubuntu 22.04 LTS (Jammy Jellyfish)
Ubuntu 24.04 LTS (Noble Numbat)
```

#### 系统选择建议
- **Ubuntu 22.04 LTS**：稳定性更高，兼容性最佳
- **Ubuntu 24.04 LTS**：较新版本，性能可能更优



### 🚫 不支持的操作系统

#### Windows系统
- ❌ Windows 10/11 不支持
- ❌ Windows Server 不支持  
- ❌ WSL (Windows Subsystem for Linux) 支持度有限

#### macOS系统
- ❌ macOS Intel 不支持
- ❌ macOS Apple Silicon 不支持

#### 其他Linux发行版
- ❌ CentOS/RHEL 未官方测试
- ❌ Fedora 未官方测试
- ❌ Debian 可能兼容但未官方支持

## 系统环境要求

### 📋 基础要求

#### 系统架构
```
x86_64 (64位) 架构
```

#### 内核要求
```bash
# 检查内核版本
uname -r
# 推荐 5.15+ (Ubuntu 22.04) 或 6.8+ (Ubuntu 24.04)
```

#### 权限要求
```bash
# 需要sudo权限安装系统依赖
sudo apt update
sudo apt install libx265-dev  # 示例系统依赖
```

### 🔧 必需软件组件

#### Python环境
```bash
# 通过Miniconda管理
Python 3.12 (推荐版本)
```

#### 系统库依赖
```bash
# 必需的系统库
libx265-dev          # 视频编解码库
build-essential      # 编译工具链
```

#### 网络要求
- 稳定的网络连接用于下载资产
- 能够访问PyPI镜像源
- 能够访问资产库服务

## 硬件兼容性

### 💻 GPU要求（重要）

#### 推荐显卡
```
NVIDIA RTX 40系列：
- RTX 4090, 4080, 4070, 4060等
- 驱动版本：≥535.00

NVIDIA RTX 50系列：
- RTX 5090, 5080等最新型号  
- 驱动版本：≥550.00
```

#### 检查显卡信息
```bash
# 查看显卡型号
lspci | grep VGA

# 查看NVIDIA驱动版本
nvidia-smi

# 查看CUDA版本
nvcc --version
```

### 🖥️ 系统要求

#### 推荐配置
```
CPU：Intel i7/AMD Ryzen 7 以上
内存：16GB 以上
硬盘：100GB+ 可用空间（用于资产存储）
```

#### 最低配置
```
CPU：Intel i5/AMD Ryzen 5
内存：8GB
硬盘：50GB+ 可用空间
```

## 安装前检查

### 🔍 系统兼容性检查

```bash
# 检查系统版本
lsb_release -a

# 检查系统架构
uname -m  # 应显示 x86_64

# 检查可用空间
df -h

# 检查内存
free -h

# 检查显卡
lspci | grep -i nvidia
```

### 📦 环境准备检查清单

- [ ] Ubuntu 22.04/24.04 LTS
- [ ] x86_64架构
- [ ] NVIDIA RTX显卡
- [ ] 合适的驱动版本
- [ ] sudo权限
- [ ] 网络连接稳定
- [ ] 充足的存储空间

## 虚拟化环境支持

### 💡 虚拟机使用
**⚠️ 不推荐在虚拟机中运行**
- GPU直通配置复杂
- 性能损失显著
- 可能出现兼容性问题

### 🐳 容器化支持
**Docker支持有限**
- 需要GPU容器运行时
- 图形界面配置复杂
- 建议直接物理机安装

## 未来系统支持计划

### 🔮 可能支持的系统
根据用户需求，未来可能考虑支持：
- Windows版本（通过WSL2或原生支持）
- macOS版本（Apple Silicon适配）
- 更多Linux发行版

### 📢 获取更新信息
- 关注官方发布公告
- 查看GitHub仓库更新
- 参与社区讨论

## 系统选择建议

### 🎯 新手用户
推荐**Ubuntu 22.04 LTS**：
- 长期支持版本
- 社区支持丰富
- 稳定性最佳

### 🚀 高级用户
可尝试**Ubuntu 24.04 LTS**：
- 更新的软件包
- 更好的硬件支持
- 更新的内核特性

### 🔧 系统管理员
建议配置：
- 使用LTS版本确保稳定性
- 定期更新系统补丁
- 监控硬件兼容性

## 常见问题

### Q: WSL2可以运行OrcaLab吗？
A: WSL2支持度有限，特别是GPU加速可能存在问题，建议使用原生Linux系统。

### Q: 能否在云服务器上运行？
A: 需要带GPU的云服务器实例，且能够运行图形界面程序。

### Q: 系统语言必须是英文吗？
A: 不强制要求，但建议使用英文环境避免编码问题。

选择合适的操作系统是成功运行OrcaLab的第一步，确保系统环境满足要求将为后续的使用提供良好基础。

## 相关链接
- [OrcaLab安装指南](环境准备/Ubuntu系统安装OrcaLab指南_v1.0.md)
- [常见问题排查](环境准备/Ubuntu系统安装OrcaLab指南_v1.0.md)