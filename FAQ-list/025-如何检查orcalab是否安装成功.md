# 如何检查OrcaLab是否安装成功？

## 问题
安装OrcaLab后，我如何验证它是否已经成功安装并在我的系统上正常运行？

## 回答

安装OrcaLab后，您可以通过以下几种方式来验证其安装状态和运行情况，以确保所有必要的组件都已正确配置。

## 📋 验证步骤

### 1. **检查Python环境**

首先，确认您正在使用为OrcaLab创建的Conda环境，并且其中的Python版本正确。

```bash
# 激活 OrcaLab 的 Conda 环境
conda activate orcalab

# 检查 Python 版本
python --version
# 期望输出：Python 3.12.x
```

### 2. **检查OrcaLab包是否安装**

验证`orca-lab`这个Python包是否已安装到您的Conda环境中。

```bash
# 激活 OrcaLab 的 Conda 环境
conda activate orcalab

# 检查 orca-lab 包信息
pip show orca-lab
```

#### 期望输出
如果安装成功，您会看到类似以下的输出，其中包含版本、作者、许可证等信息：

```
Name: orca-lab
Version: X.Y.Z  # 您的OrcaLab版本
Summary: High-fidelity physics AI simulation system
Home-page: https://www.songying.ai/
Author: SongYing Tech
License: Proprietary (for non-commercial use)
Location: /home/your_user/miniconda3/envs/orcalab/lib/python3.12/site-packages
Requires: ...
Required-by: ...
```

如果显示`WARNING: Package(s) not found: orca-lab`，则表示`orca-lab`包未成功安装。

### 3. **检查系统依赖**

如果OrcaLab在首次启动时提示需要安装`libx265-dev`，您应该验证该系统库是否已成功安装。

```bash
dpkg -l | grep libx265
```

#### 期望输出
您应该看到至少一行以`ii`开头的输出，表示`libx265-dev`已安装。例如：

```
ii  libx265-dev:amd64                       3.5-2build1                         amd64        x265, an H.265/HEVC encoder - development files
```

### 4. **启动OrcaLab客户端**

这是最直接的验证方法。尝试启动OrcaLab客户端，观察是否能正常进入主界面。

```bash
# 激活 OrcaLab 的 Conda 环境
conda activate orcalab

# 启动 OrcaLab
orcalab
```

#### 期望行为
1. 终端显示`正在同步资产包...`，并可能下载和更新一些资产。
2. 弹出"选择场景"对话框。
3. 您可以选择一个场景和布局，然后点击"打开"。
4. OrcaLab的GUI主界面正常显示，没有报错。


### 5. **运行快速入门仿真示例**

尝试运行一个OrcaLab提供的快速入门仿真示例，例如四轮底盘小汽车仿真，以验证所有核心功能是否正常。

#### 步骤
1. 从GitHub克隆`OrcaPlayground`仓库：
   ```bash
   git clone https://github.com/openverse-orca/OrcaPlayground.git
   cd OrcaPlayground
   conda activate orcalab
   pip install -r requirements.txt
   ```
2. 登录资产库订阅`OrcaPlaygroundAssets`。
3. 在`OrcaPlayground`目录下启动OrcaLab：
   ```bash
   orcalab
   ```
4. 在OrcaLab客户端中，添加资产`hummer_h2_usda_1`到布局中。
5. 点击界面右上角的"运行"按钮 [▶]，选择`run_ackerman`仿真程序并启动。
6. 如果小汽车模型正常加载，并且您可以使用WASD键控制其移动，则说明安装和基本功能正常。


## ⚠️ 常见问题与排查

### Q: `orcalab`命令找不到？
A: 确保您的Conda环境已激活（`conda activate orcalab`），并且OrcaLab已成功安装到该环境中。

### Q: 启动OrcaLab后，出现错误弹窗或闪退？
A: 1. 检查终端输出的错误信息，通常会提供线索。
   2. 确保所有系统依赖（如`libx265-dev`）都已安装。
   3. 检查NVIDIA显卡驱动版本是否满足要求。
   4. 尝试重新安装OrcaLab或Conda环境。

### Q: 资产包同步失败或卡住？
A: 检查网络连接，确保可以访问资产库服务器。确保足够的磁盘空间。

### Q: 示例仿真程序无法运行？
A: 检查`OrcaPlayground`项目的依赖是否安装完整 (`pip install -r requirements.txt`)，并确保已订阅`OrcaPlaygroundAssets`。

通过上述验证步骤，您可以全面确认OrcaLab是否已成功安装并具备完整的功能。

## 相关链接
- [OrcaLab安装指南](环境准备/Ubuntu系统安装OrcaLab指南_v1.0.md)
- [OrcaLab快速入门仿真示例](环境准备/OrcaLab快速入门仿真示例_v1.0.md)
