# VR遥操作与数据采集操作指南

松应OrcaLab使用VR遥操进行数据采集任务，需遵循特定流程配置硬件连接、启动程序。以下为详细操作指南，包含VR遥操作与数据采集的步骤、参数说明及常见问题解决方案。

---

## 一、数据采集软件硬件环境准备
 - **OrcaGym OrcaManipulation** 开源代码库下载
 - **VR操作设备** （如Pico Ultra 4配套手柄）
 - **场景资源** 订阅
 
### 1.1 从github获取OrcaManipulation代码仓库。

```bash
git clone https://github.com/openverse-orca/OrcaManipulation.git
# 进入项目目录
cd OrcaPlayground

# 激活 OrcaLab 的 conda 环境（根据你的环境名称调整）
conda activate orcalab  # 激活你创建的 OrcaLab 环境名称

# 安装项目依赖
pip install -r requirements.txt
```

### 1.2 VR遥操作设备准备

VR遥操作需先完成硬件连接与软件初始化，数据采集时，通过手柄控制机械臂执行任务并采集数据。

**步骤1** ：安装 `PicoController.apk` 程序(apk包所在目录：OrcaManipulation/src/examples/超市场景青龙机器人数采案例/pico安装包/）
 - 使用 USB 线将 Pico 连接电脑，并开机。
 - 将`PicoController.apk` 复制到PICO设备目录中 
![](img/pico_install.png)
 - 佩戴VR设备，在 VR 视角中，找到文件管理器，查看安装包目录，使用右手手柄点击 **A 键**，确认安装刚刚下载的 apk 包。

**步骤2** ：打开VR设备开发者模式
 - 在 VR 视角中，点击：  **设置 → 关于本机 → 软件版本号**， 使用确认键 **A 键** 对着软件版本号。 连续点击 **6–7 次**，调出开发者模式。  
 - 打开调试开关。
![](img/pico_usb.jpg)
**步骤3**：启动VR端OrcaGymCtrl程序 
 - 开启VR设备，选择底部的「资源库」（Pico Ultra 4设备直接在资源库中查找“OrcaGymCtrl”）。
 ![Pico设备资源库界面](img/pico_gym_controller.png)
 - VR启动后会提示设置安全边界，可选择“重设边界”或“保持原有边界”（默认配置）。
 - 启动OrcaGymCtrl后，会进入3D程序界面：左侧显示三维红蓝绿坐标轴，中间有红色文字启动OrcaGymCtrl后，会进入3D程序界面：左侧显示三维红蓝绿坐标轴，中间有红色文字。**后续VR遥操作需始终保持此界面激活**。
 ![Pico设备资源库界面](img/pico_OrcaGymCtrl.png)

**步骤4** ：安装adb工具
在Ubuntu终端中执行以下命令，安装Android调试工具（adb）
 ```bash
sudo apt install android-tools-adb android-tools-fastboot
```
 **步骤5**：建立PICO与PC的通信连接
- 使用USB数据线连接Pico设备与PC。
- 执行以下命令反向映射端口（确保通信正常）：
    
```bash
 adb reverse tcp:8001 tcp:8001
```
- ⚠️**注意**：每次重启PC或断开PICO的USB连接后，需重新执行此命令。执行成功会提示“start successful”；若已执行过该命令，再次执行可能无输出，属于正常现象。

 ### 1.3 场景资产包准备 

 以下内容，以 `青龙机器人` + `超市场景` 为例，展示一个数据采集场景任务，必需要准备的机器人资产和场景资产。
  
 **订阅相关资产**

1. 资产库链接: https://simassets.orca3d.cn/

2. 资产中心 → 订阅 **ShopScene_Scaning**
![](img/shop_scan.png)

1. 资产中心 → 订阅 **openloong**
![](img/openloong.png)

  
## 二、遥操作数据采集

完成以上准备工作后，以 `青龙机器人` + `超市场景` 为例，添加布局后，开始数据采集任务。

 - **确认PICO 连接正常**：
   - 启动OrcaGymCtrl后，会进入3D程序界面：左侧显示三维红蓝绿坐标轴；
   - adb 端口连接成功。
 - **资产包订阅成功**：个人中心有已订阅`ShopScene_Scaning`、`openloong`资产包，

  
  ### 2.1 打开 OrcaLab 中的场景与布局

1. 终端进入 OrcaLab 安装的 conda 环境：
```bash
#激活orcalab conda环境
conda activate orcalab
```
2. 执行命令启动 OrcaLab：
```bash
#启动OrcaLab
orcalab
```
3. 启动过程中会自动下载已订阅的资产，请等待下载与同步完成。
![](img/shop_download.png)

4. 资产下载完成后，在选择场景弹框中，选择 **shop 场景** ，选择默认布局。
![](img/shop_select.png)

5. 在 OrcaLab 客户端菜单栏中，选择 **打开布局**，加载 `shop_openloong.json` 文件。
```bash
#布局JSON 文件路径（注：布局文件定义了机器人初始位置及姿态）
  ~/OrcaManipulation/src/examples/超市场景青龙机器人数采案例/shop_openloong.json
```
![](img/shop_layout.png)

6.shopScense示例场景的yaml文件已配置为example.yaml，如需详细了解配置参数含义，请参考第三章节 数据采集任务配置文件说明
```bash
#example.yaml文件路径
~/OrcaManipulation/src/examples/dataCollection
```
![](img/shop_example1.png)

### 2.2 启动仿真

1. 点击界面右上角 **绿色启动按钮**
2. 选择 **无仿真程序（手动启动）**
![](img/shop_sim1.png)

### 2.3 开启数采脚本

1. 激活数采脚本所需 conda 环境：
```bash
conda activate orcalab
```

2. 进入数采脚本目录并启动
```bash
cd ~/OrcaManipulation/src/examples/dataCollection
#启动数据采集脚本,确保example.yaml文件中资产版本配置正确
python data_collection_tele.py
```
![](img/run_shop_scan.png)

### 2.4 VR遥操作开始数据采集

1. **机械臂复位** 进入抓取模式
   - 依次按压 **左摇杆**、**右摇杆**
   - 仿真环境中机械臂可移动，机器人进入抓取操作模式
![](img/vr_hand.png)

2. **手柄功能映射**

   - **左手手柄**
     - **Y 键长按**：左手抓取
     - **X 键**：左手放开

   - **右手手柄**
     - **B 键长按**：右手抓取
     - **A 键长按**：右手放开

3. **数据采集及存储**
   
   - 参考下图采集云币运行输出，updata_scence时，按一次左手柄扳机，开始数据采集状态。
   - 根据任务提示，抓取目标物体，放在篮子中。
   - 抓取完成后，再按一次左手柄扳机，保存采集的数据，并提示保存的目录，如数据失败，则进入下一个任务。  
    
![](img/PICO_l_save.png)



## 三、数据采集任务配置文件说明
详细解析任务配置示例yaml文件中的各个字段含义，并指导从零开始配置一个属于你自己的场景任务配置文件。
适用于第一次使用 OrcaLab 进行任务配置,需要自行搭建场景并完成数据采集任务的用户。

### 3.1 配置文件核心模块说明
| 模块分类 | 模块名称 | 核心作用 | 关键说明 |
|----------|----------|----------|----------|
| 基础信息 | level_name | 场景名称标识 | 用于日志记录、数据集区分、任务回放，建议使用业务语义名称（如pharmacy_pick） |
| 基础信息 | type | 任务类型定义 | 支持pick_and_place（抓取放置）、scan_qr（二维码扫描），决定task模块配置结构 |
| 动态物体 | actor | 动态加载物体配置 | 定义任务中随机生成的物体（药品/瓶子/盒子等）的名称、路径、关节、随机规则 |
| 场景灯光 | light | 灯光参数配置 | 控制场景灯光的数量、位置、随机策略，增强数据多样性 |
| 任务逻辑 | task | 任务目标配置 | 与顶层type保持一致，定义任务目标物体/区域及放置位点 |

### 3.2 配置字段详细说明
| 字段分类 | 具体字段 | 配置示例/格式 | 关键注意事项 |
|----------|----------|---------------|--------------|
| 基础信息 | level_name | level_name: "example" | 字符串格式，需唯一标识场景 |
| 基础信息 | type | type: "pick_and_place" | 仅支持pick_and_place/scan_qr |
| actor模块 | names | names: ["A", "B", "C", "D", "E"] | 数组格式，与spawnable一一对应 |
| actor模块 | spawnable | spawnable: ["assets/.../prefabs/kps/pipalu"] | 指向资产库prefab路径，路径错误会导致物体无法生成 |
| actor模块 | joints | joints: [...] | 定义物体根关节/可控关节，用于位姿控制 |
| actor模块 | joints_dof | joints_dof: [6, 6, 6, 6, 6] | 1=单自由度/3=球形关节/6=刚体关节，数量需与joints一致 |
| actor模块 | random.qpos | qpos: true | true=关节位置随机化/false=固定 |
| actor模块 | random.nums | nums: [1, 5] | 数组格式，定义actor生成数量范围（1~5个） |
| actor模块 | random.six_dof.center | center: [2.47, -2.33, 1.24] | 世界坐标系下的随机中心点 |
| actor模块 | random.six_dof.bound_position | bound_position: [[-0.1, 0.1], [-0.1, 0.1], [0, 0]] | XYZ方向偏移范围，最小值=最大值则该维度固定 |
| actor模块 | random.six_dof.bound_rotation | bound_rotation: [[0, 0], [0, 0], [0, 1]] | 绕XYZ轴旋转范围（弧度） |
| light模块 | names | names: ["spotlight1"] | 灯光实例名称，数组格式 |
| light模块 | spawnable | spawnable: ["prefabs/spotlight"] | 灯光prefab路径 |
| light模块 | random.position/rotation | position: false<br>rotation: false | 是否启用位置/旋转随机 |
| light模块 | random.center/bound_position/bound_rotation | center: [0, 0, 0]<br>bound_position: [[-1, 1], [-1, 1], [0, 2]]<br>bound_rotation: [[0, 3.14159], [0, 3.14159], [0, 3.14159]] | 同actor模块six_dof规则 |
| light模块 | random.nums | nums: [1, 1] | 每次生成的灯光数量 |
| light模块 | random.cycle | cycle: 20 | 每20个任务更新一次灯光配置 |
| task模块 | type | type: "pick_and_place" | 必须与顶层type一致 |
| task模块 | goal.name | name: "MedicineChest" | 目标物体/区域名称 |
| task模块 | goal.site | site: "MedicineChest_site" | 场景中定义的放置位点，不存在则任务失败 |

### 3.3 新场景配置步骤
| 步骤分类 | 具体步骤 | 操作说明 | 关键注意事项 |
|----------|----------|----------|--------------|
| 前期准备 | 明确任务类型 | 选择pick_and_place/scan_qr | 决定后续配置字段结构 |
| 前期准备 | 验证资产路径 | 确认所有spawnable路径有效 | 路径错误会导致物体/灯光无法生成 |
| 核心配置 | 配置actor参数 | 填写names、spawnable、joints、joints_dof | joints_dof数量需与joints一致 |
| 核心配置 | 设置actor随机规则 | 配置random下qpos、nums、six_dof | 随机范围过大会导致物体穿模/掉落 |
| 核心配置 | 配置light参数 | 填写names、spawnable及随机规则 | cycle参数可提升数据多样性 |
| 核心配置 | 配置task目标 | 填写type、goal.name、goal.site | 确认site在场景中真实存在 |
| 验证测试 | 小规模验证 | 将nums设为[1,1]测试配置 | 先验证再扩大随机范围 |

### 3.4 常见配置错误与排查
| 错误类型 | 错误描述 | 排查建议 |
|----------|----------|----------|
| 资产加载 | spawnable路径错误 | 核对资产库prefab路径，确保路径无拼写错误 |
| 加载失败 | joints与joints_dof数量不一致 | 检查两个字段的数组长度，保持一一对应 |
| 物体异常 | 随机范围过大 | 缩小six_dof的bound_position/bound_rotation范围 |
| 任务失败 | site名称不存在 | 确认场景中存在该site名称，或修正goal.site配置 |



## 📖 更多信息

- OrcaManipulation 主仓库：https://github.com/openverse-orca/OrcaManipulation
- OrcaManipulation详细说明：查看 `README.md`



   

   
