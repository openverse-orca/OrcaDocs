# .orcalab/config.toml文件有什么作用？

## 问题
OrcaLab项目中经常会看到一个名为`.orcalab/config.toml`的文件。这个文件的具体作用是什么？它包含了哪些配置信息？

## 回答

`.orcalab/config.toml`文件是OrcaLab用于**配置和管理外部仿真程序**的核心文件。它允许用户将自定义的Python脚本或模块集成到OrcaLab的启动列表中，并定义这些程序的运行方式和参数。

## 📋 `.orcalab/config.toml`文件的作用

### 1. **定义外部仿真程序**
-   这是其最主要的作用。该文件以TOML（Tom's Obvious, Minimal Language）格式定义了一系列外部可执行的仿真程序。
-   这些程序会在OrcaLab客户端启动时，出现在"仿真程序"的选择列表中，供用户选择运行。

### 2. **参数化启动**
-   每个定义的外部程序都可以指定其执行命令（如`python`）和一系列命令行参数（`args`）。这使得用户可以灵活地传递配置、模式、文件路径等信息给外部脚本。

### 3. **统一管理**
-   将所有外部程序的配置集中管理在一个文件中，方便查看、修改和版本控制。

### 4. **项目隔离**
-   由于`config.toml`通常位于项目根目录下，因此每个OrcaLab项目可以拥有自己独立的外部程序配置，实现项目间的隔离和互不干扰。

## 📁 `.orcalab/config.toml`文件结构与内容

该文件主要包含一个`external_programs`部分，其下有`programs`数组，每个数组元素（即`[[external_programs.programs]]`块）定义一个外部程序。

### 示例文件内容
```toml
# .orcalab/config.toml 示例

[external_programs]

# 定义外部程序列表
[[external_programs.programs]]
name = "run_sim_loop"                  # 程序的唯一标识符
display_name = "空循环仿真"               # 在OrcaLab UI中显示的名称
command = "python"                     # 执行命令
args = ["-m", "orca_gym.examples.sim_loop"] # 命令行参数列表，这里以模块方式运行
description = "一个简单的空循环仿真，用于测试"

[[external_programs.programs]]
name = "run_ackerman"                   # 另一个程序的唯一标识符
display_name = "四轮底盘小汽车仿真"       # 在OrcaLab UI中显示的名称
command = "python"                     # 执行命令
args = ["-m", "examples.wheeled_chassis.run_ackerman"] # 命令行参数列表
description = "控制四轮底盘车辆进行物理仿真"

# 你可以在这里添加更多自定义的仿真程序
[[external_programs.programs]]
name = "my_custom_training"
display_name = "我的强化学习训练"
command = "python"
args = [
    "-m", 
    "my_project.train_script",
    "--env", "MyRobotEnv",
    "--epochs", "100",
    "--render"
]
description = "启动一个自定义的强化学习训练任务"
```

### 关键配置参数

| 参数           | 说明                                                                                                                                     |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | **唯一标识符**。用于OrcaLab内部查找和启动程序。必须与所有已配置程序的`name`和`display_name`都不重复。                                      |
| `display_name` | **显示名称**。在OrcaLab启动对话框的UI中显示给用户。必须与所有已配置程序的`name`和`display_name`都不重复。                                      |
| `command`      | **执行命令**。通常是`"python"`，也可以是其他可执行命令。                                                                                |
| `args`         | **命令行参数列表**。每个参数作为数组的一个元素，传递给`command`指定的命令。可以是模块路径（`-m`）或脚本文件路径，以及其他自定义参数。       |
| `description`  | **程序描述**。可选参数，在OrcaLab UI的工具提示中显示，帮助用户了解程序功能。                                                              |

## 💡 如何使用`.orcalab/config.toml`

### 1. **添加新的仿真程序**
-   如果您编写了一个新的Python仿真脚本，希望能在OrcaLab中直接启动，就需要在这个文件里添加一个新的`[[external_programs.programs]]`块。
-   参照示例，填写`name`、`display_name`、`command`和`args`。

### 2. **修改现有程序的参数**
-   您可以修改`args`中的参数来改变仿真程序的行为，例如调整训练的`epochs`数量，或切换`debug`模式。

### 3. **验证配置**
-   **确保唯一性**：`name`和`display_name`必须是唯一的，否则OrcaLab可能无法正确识别程序。
-   **路径正确**：`args`中的脚本路径或模块路径需要相对于`.orcalab/config.toml`所在的目录。
-   **重启客户端**：每次修改`config.toml`文件后，都必须**关闭并重新启动OrcaLab客户端**，以使更改生效。

### 4. **版本控制**
-   由于`config.toml`是项目的重要配置，建议将其纳入Git等版本控制系统进行管理，以便跟踪更改、协作和回溯。

## ⚠️ 注意事项

### 1. **TOML语法**
-   确保您遵守TOML文件的语法规范。错误的语法会导致文件无法解析，OrcaLab将无法加载您的外部程序。
-   TOML中，数组用`[]`表示，字符串用`""`表示。

### 2. **文件位置**
-   OrcaLab只会在其**当前工作目录**下查找`.orcalab/config.toml`。如果您在不同的项目目录下启动OrcaLab，它会加载相应项目目录下的`config.toml`。

## 📝 总结

`.orcalab/config.toml`文件是OrcaLab外部仿真程序的"注册表"。通过它，用户可以灵活地配置、管理和启动各种自定义的Python仿真脚本，从而扩展OrcaLab的功能，实现更复杂的机器人AI仿真任务。理解并正确编辑这个文件，是高级用户使用OrcaLab的关键。

## 相关链接
- [OrcaLab快速入门仿真示例](环境准备/OrcaLab快速入门仿真示例_v1.0.md#orcaLab-配置)
- [如何配置外部仿真程序？](FAQ-list/079-如何配置外部仿真程序.md)
- [什么是仿真程序？如何选择？](FAQ-list/077-什么是仿真程序如何选择.md)