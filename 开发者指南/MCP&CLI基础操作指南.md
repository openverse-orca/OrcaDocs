# OrcaLab MCP 与 CLI 使用指南

## 概述

OrcaLab 提供两种调用方式：

- **MCP (Python SDK)**：通过 `fastmcp` 库异步调用，适合编写自动化脚本
- **CLI (命令行)**：通过 `orcalab-cli` 直接执行，适合快速调试和手动操作

两者功能完全一致，CLI 是对 MCP 函数的封装。

***

MCP使用指南

## 环境准备

### 1. 启动 OrcaLab

OrcaLab 需要先启动，MCP 服务才能连接。
在桌面环境中运行 OrcaLab 应用程序

### 2. 接入 MCP

####

1. Cursor  & Trae
   进入MCP设置，加入如下配置：
   ![MCP配置](../img/MCP\&CLI基础操作指南/MCP配置.png)
   {
   "mcpServers": {
   "orcalab\_mcp": {
   "url": "<http://localhost:12345/mcp>"
   }
   }
   }
2. Claude Code
   直接输入： claude mcp add --transport http  orcalab\_mcp <http://localhost:12345/mcp>

### 3. MCP 使用

\`\`注意：MCP & CLI 服务需要开启Orcalab才可以使用，使用方式：

1. MCP 接入 Cursor & Trae  & Claude Code，可以通过对话直接调用控制Orcalab
2. orcalab-cli 可直接在命令行中操作

MCP 也可以通过代码接口快速访问：

1. 不带参数调用示例

![MCP脚本无参数调用](../img/MCP\&CLI基础操作指南/MCP脚本无参数调用.png)

```python
import asyncio
from fastmcp import Client

client = Client("http://localhost:12345/mcp")

async def call_tool():
    async with client:
        
        ## 列出所有工具接口
        all_tools = await client.list_tools()

        ## 函数调用
        result = await client.call_tool("start_simulation", {})
        print(result)
asyncio.run(call_tool())
```

<br />


2\. 带参数调用示例

![MCP脚本有参数调用](../img/MCP\&CLI基础操作指南/MCP脚本有参数调用.png)

```python
import asyncio
from fastmcp import Client

async def duplicate_actor():
    async with Client("http://localhost:12345/mcp") as client:
        result = await client.call_tool("duplicate_actors", {
            "actor_paths": ["/humanoid_industrial_robot_1"]
        })
        print(result.data)

asyncio.run(duplicate_actor())
```

**运行**：

```bash
python test_single.py
```

**输出**：

```
{"success": true, "message": "成功复制 1 个Actor"}
```

#### CLI的使用

```bash
# CLI 通常随 OrcaLab 一起安装，在 conda 环境中使用
conda activate orcalab

# 测试连接
orcalab-cli -h
orcalab-cli get_all_actors
```

具体使用模板：
function可以替换为下面可用函数列表所有函数，有参数函数使用json包装。

**无参数函数示例：**

![CLI无参数调用](../img/MCP\&CLI基础操作指南/CLI无参数调用.png)

```bash
orcalab-cli function   # 无参数函数
```

**有参数函数示例：**

![CLI有参数调用](../img/MCP\&CLI基础操作指南/CLI有参数调用.png)

```bash
orcalab-cli function --json '{"actor_path":"/Actor",...}'  #有参数函数，参数需要放到json里面
```

注意还有一些其他参数，基本使用默认即可。

示例：

```bash
orcalab-cli get_asset_map 
orcalab-cli get_viewport_png --json '{"index":0}'
orcalab-cli duplicate_actors --json '{"actor_paths":["/humanoid_industrial_robot_1"]}'
```

***

## 常用函数速查

| 功能          | 函数名                              |
| ----------- | -------------------------------- |
| 获取所有 Actor  | `get_all_actors`                 |
| 获取 Actor 变换 | `get_actor_transform`            |
| 设置 Actor 变换 | `set_actor_transform`            |
| 添加 Actor    | `add_actor`                      |
| 删除 Actor    | `delete_actor`                   |
| 复制 Actor    | `duplicate_actors`               |
| 获取选择        | `get_selection`                  |
| 设置选择        | `set_selection_and_active_actor` |
| 清空选择        | `clear_selection`                |
| 获取资产列表      | `get_asset_map`                  |
| 获取资产信息      | `get_asset_info`                 |
| 启动仿真        | `start_simulation`               |
| 停止仿真        | `stop_simulation`                |
| 获取仿真状态      | `get_simulation_state`           |
| 批量删除        | `delete_actors`                  |
| 批量设置变换      | `set_actors_transform`           |
| 获取视口信息      | `get_viewport_camera_info`       |
| 获取截图        | `get_viewport_png`               |
| 获取引擎信息      | `get_engine_info`                |
| 保存布局        | `save_layout`                    |
| 加载布局        | `load_layout`                    |

***

## 常见问题

### 1. Actor 路径不存在

```
复制Actor失败: Actor does not exist.
```

**解决**：先用 `get_all_actors` 确认路径。

### 2. 函数名错误

```
Unknown tool: 'set_selection'
```

**解决**：使用正确的函数名 `set_selection_and_active_actor`。

### 3. 布局加载失败

```
布局文件不存在: /home/orcatest/OrcaSim/my_layout
```

**解决**：使用绝对路径加载布局。

***

