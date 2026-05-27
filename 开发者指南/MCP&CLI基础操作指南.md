# 🐋 OrcaLab MCP 与 CLI 使用指南

## 📋 概述

OrcaLab 提供两种调用方式：

- **🤖 MCP (Python SDK)**：通过 `fastmcp` 库异步调用，适合编写自动化脚本
- **💻 CLI (命令行)**：通过 `orcalab-cli` 直接执行，适合快速调试和手动操作

> 💡 两者功能完全一致，CLI 是对 MCP 函数的封装。

---

## 🔌 MCP 使用指南

### 一、环境准备

#### 1. 启动 OrcaLab

OrcaLab 需要先启动，MCP 服务才能连接。

> 🖥️ 在桌面环境中运行 OrcaLab 应用程序

#### 2. 接入 MCP        

**Cursor & Trae 配置：**

![MCP配置](../img/MCP\&CLI基础操作指南/MCP配置.png)

```json
{
  "mcpServers": {
    "orcalab_mcp": {
      "url": "http://localhost:12345/mcp"
    }
  }
}
```

**Claude Code 配置：**

```bash
claude mcp add --transport http orcalab_mcp http://localhost:12345/mcp
```

### 二、MCP 使用

> ⚠️ **注意**：MCP & CLI 服务需要开启 OrcaLab 才可以使用。

**方式一：通过通用Agent访问**
1. 🔗 MCP 接入 Cursor & Trae & Claude Code，可以通过对话直接调用控制 OrcaLab
2. ⌨️ `orcalab-cli` 可直接在命令行中操作

**方式二：通过代码接口快速访问**

**1. 不带参数调用示例**

![MCP脚本无参数调用](../img/MCP\&CLI基础操作指南/MCP脚本无参数调用.png)

```python
import asyncio
from fastmcp import Client

client = Client("http://localhost:12345/mcp")

async def call_tool():
    async with client:
        # 📋 列出所有工具接口
        all_tools = await client.list_tools()

        # 🚀 函数调用
        result = await client.call_tool("start_simulation", {})
        print(result)

asyncio.run(call_tool())
```

**2. 带参数调用示例**

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

**▶️ 运行：**

```bash
python test_single.py
```

**📤 输出：**

```json
{"success": true, "message": "成功复制 1 个Actor"}
```

---

## 💻 CLI 使用指南
### 一、环境准备
```bash
# 🌐 CLI 通常随 OrcaLab 一起安装，在 conda 环境中使用
conda activate orcalab

# ✅ 测试连接
orcalab-cli -h
orcalab-cli get_all_actors
```

### 二、具体使用示例

> `function` 可以替换为下面可用函数列表所有函数，有参数函数使用 JSON 包装。

**1. 无参数函数示例**

![CLI无参数调用](../img/MCP\&CLI基础操作指南/CLI无参数调用.png)

```bash
orcalab-cli function   # 无参数函数
```

**2. 有参数函数示例**

![CLI有参数调用](../img/MCP\&CLI基础操作指南/CLI有参数调用.png)

```bash
orcalab-cli function --json '{"actor_path":"/Actor",...}'  # 有参数函数，参数需要放到 JSON 里面
```

> 💡 注意还有一些其他参数，基本使用默认即可。

**一些其他示例：**

```bash
# 📦 获取资产地图
orcalab-cli get_asset_map

# 📸 获取视口截图
orcalab-cli get_viewport_png --json '{"index":0}'

# 📋 复制 Actor
orcalab-cli duplicate_actors --json '{"actor_paths":["/humanoid_industrial_robot_1"]}'
```

---

## 📚 常用函数速查

| 功能 | 函数名 | 说明 |
|------|--------|------|
| 📋 获取所有 Actor | `get_all_actors` | 列出场景中所有 Actor |
| 📍 获取 Actor 变换 | `get_actor_transform` | 获取指定 Actor 的位置/旋转/缩放 |
| ✏️ 设置 Actor 变换 | `set_actor_transform` | 修改指定 Actor 的变换属性 |
| ➕ 添加 Actor | `add_actor` | 向场景中添加新 Actor |
| ❌ 删除 Actor | `delete_actor` | 删除指定 Actor |
| 📋 复制 Actor | `duplicate_actors` | 复制一个或多个 Actor |
| 👆 获取选择 | `get_selection` | 获取当前选中的 Actor |
| 🎯 设置选择 | `set_selection_and_active_actor` | 设置当前选中的 Actor |
| 🧹 清空选择 | `clear_selection` | 清空当前选择 |
| 📦 获取资产列表 | `get_asset_map` | 获取项目资产目录 |
| ℹ️ 获取资产信息 | `get_asset_info` | 获取指定资产详细信息 |
| ▶️ 启动仿真 | `start_simulation` | 开始物理仿真 |
| ⏹️ 停止仿真 | `stop_simulation` | 停止物理仿真 |
| 📊 获取仿真状态 | `get_simulation_state` | 查询当前仿真运行状态 |
| 🗑️ 批量删除 | `delete_actors` | 同时删除多个 Actor |
| 📝 批量设置变换 | `set_actors_transform` | 同时修改多个 Actor 变换 |
| 🎥 获取视口信息 | `get_viewport_camera_info` | 获取相机参数 |
| 📸 获取截图 | `get_viewport_png` | 捕获视口图像 |
| ⚙️ 获取引擎信息 | `get_engine_info` | 查询引擎版本等信息 |
| 💾 保存布局 | `save_layout` | 保存当前场景布局 |
| 📂 加载布局 | `load_layout` | 加载已保存的场景布局 |

---

## ❓ 常见问题

###  1. Actor 路径不存在

```
复制Actor失败: Actor does not exist.
```

> 🔧 **解决**：先用 `get_all_actors` 确认路径。

###  2. 函数名错误

```
Unknown tool: 'set_selection'
```

> 🔧 **解决**：使用正确的函数名 `set_selection_and_active_actor`。

###  3. 布局加载失败

```
布局文件不存在: /home/orcatest/OrcaSim/my_layout
```

> 🔧 **解决**：使用绝对路径加载布局。

---

> 🐋 **OrcaLab** — 让仿真更简单
