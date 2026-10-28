<p align="center">
  <b>中文</b> | <a href="README.md">English</a>
</p>

<p align="center">
  <img src="assets/posim_logo.png" alt="POSIM Logo" width="600">
</p>

<h3 align="center">POSIM — 面向社交媒体舆情演化与治理的多智能体仿真框架</h3>

<p align="center">
  <em>"所有模型都是错误的，但其中一些是有用的。" — George E. P. Box</em>
</p>

<p align="center">
  <a href="https://www.python.org/downloads/"><img src="https://img.shields.io/badge/python-3.8+-blue.svg" alt="Python 3.8+"></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT"></a>
  <a href="https://pytorch.org/"><img src="https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg" alt="PyTorch"></a>
  <a href="https://openai.com/"><img src="https://img.shields.io/badge/LLM-OpenAI_Compatible-412991.svg" alt="LLM"></a>
</p>

---

<h2 align="center">
  🌐 <a href="https://DeepCogLab.github.io/posim/">https://DeepCogLab.github.io/posim/</a> 🌐
</h2>

<p align="center">
  <a href="https://DeepCogLab.github.io/posim/">
    <img src="https://img.shields.io/badge/🏠_项目主页-DeepCogLab.github.io/posim-blue?style=for-the-badge&logoColor=white" alt="项目主页">
  </a>
</p>

<p align="center">
  🌐 <a href="https://DeepCogLab.github.io/posim/">主页</a>  | 
  🐛 <a href="https://github.com/DeepCogLab/posim/issues">Issues</a>
</p>

---

## 📖 目录

- [💡 为什么选择 POSIM？](#-为什么选择-posim)
- [✨ 核心特性](#-核心特性)
- [🚧 项目进展](#-项目进展)
- [📊 数据集](#-数据集)
- [🏗️ 框架总览](#%EF%B8%8F-框架总览)
- [⚙️ 安装配置](#%EF%B8%8F-安装配置)
- [🚀 快速开始](#-快速开始)
- [🔌 扩展指南](#-扩展指南)
- [⚠️ 伦理声明](#%EF%B8%8F-伦理声明)
- [📄 许可证](#-许可证)
- [🖥️ 系统原型展示](#%EF%B8%8F-系统原型展示)

---

## 💡 为什么选择 POSIM？

社交媒体上的舆情事件——从消费纠纷到公共安全事件——可以在数小时内从局部讨论升级为全网热搜。成千上万用户涌入评论区，情绪在转发链条中不断升级，一位意见领袖的一条帖子就能重塑整个公共话语。对于政府机构、媒体组织和平台运营者而言，理解舆情如何形成、演化和引导，具有重要的实践意义。

然而，对这些动态进行真实社会实验面临根本性挑战：伦理约束阻止了对公共话语的刻意操控，每个事件都是独一无二且不可复现的。这正是**计算仿真**的价值所在——它提供了一个虚拟实验室，让研究者能够在可控环境中回放、分析和实验舆情场景。

传统仿真方法——传染病模型、阈值级联模型和经典基于智能体的建模（ABM）——各自捕捉了舆论动态的某些方面，但共同存在一个关键局限：**无法显式建模个体认知过程**。这些系统中的智能体是规则驱动的自动机，既不理解其接触的内容，也不会对其回应进行推理。大语言模型（LLM）带来了突破——语义理解和类人推理能力，但现有基于 LLM 的仿真方案大多将模型作为黑箱行为生成器——输入提示词、输出动作——未建模驱动真实人类行为的中间认知状态。

**POSIM**（**P**ublic **O**pinion **Sim**ulator，舆情仿真器）填补了这一空白。通过将 LLM 嵌入结构化认知架构（Social-BDI），POSIM 创建的智能体能够：

- **维护显式信念状态** — 每个智能体跟踪其身份、心理特质、事件观点和情绪激发等结构化、可检视的数据
- **产生完全可追溯的决策** — 每个行为都可以通过意图 → 欲望 → 信念链追溯到产生它的原因
- **展现涌现的集体行为** — 舆论生命周期模式、情绪极化和级联幂律从个体智能体交互中自发涌现，而非预设规则

POSIM 面向计算社会科学、舆情动力学、危机传播和基于 LLM 的多智能体系统的研究者。同时也可作为通过反事实仿真评估治理策略的决策支持工具。

---

## ✨ 核心特性

- 🧠 **Social-BDI 智能体架构** — 将 LLM 嵌入分层认知框架（感知 → 信念 → 欲望 → 意图 → 行为），融合情绪激发和认知偏差。三个认知子系统各由独立 LLM 调用驱动，行为决策链完全可追溯。
- ⏱️ **Hawkes 过程驱动时间引擎** — Hawkes 自激点过程统一外生事件冲击与内生用户交互，结合昼夜节律调制，以分钟级分辨率再现"爆发-持续-衰退"活跃模式。
- 🛡️ **三层递进验证** — 从个体行为机制校准 → 群体现象涌现 → 统计结果一致性，逐层建立仿真可信度。
- 🔌 **高度解耦模块化架构** — 智能体、仿真环境和评估模块通过标准接口通信——可独立替换认知架构、时间引擎或评估指标。

---

## 🚧 项目进展

POSIM 仍在持续开发中。我们目前正在基于 POSIM 开发完整的舆情仿真系统，后续会在系统稳定后尽快发布。同时，我们也正在开发 pip 包，欢迎关注本仓库以获取后续发布信息。

当前公开仓库包含核心仿真框架、脱敏后的运行脚本示例、轻量级样例数据、本地嵌入模型资源，以及 [`datasets/`](datasets/) 中脱敏后的危机事件数据集。更多系统组件将逐步发布。

---

## 📊 数据集

[`datasets/`](datasets/) 公开了 POSIM 使用的三个新浪微博舆情危机数据集：天价耳环（LE）、武大图书馆（WL）、西贝预制菜（XF）。每个数据集包含事件脉络、参与账号（共 5,360 个）、这些账号的全链路博文（原发、转发、评论，共 220,897 条），以及转发 / 评论 / 回复交互关系（共 206,202 条）。所有数据均经过脱敏处理。全量采集数据（157 万账号、452 万条记录）的获取方式见 [`datasets/FULL_CRAWL.md`](datasets/FULL_CRAWL.md)。字段说明、统计、脱敏流程和使用条款见 [`datasets/README.md`](datasets/README.md)。

---

## 🏗️ 框架总览

<p align="center">
  <img src="assets/framework_overview.png" alt="POSIM 框架总览" width="95%">
</p>
<p align="center"><b>图 1.</b> POSIM 总体架构。</p>

POSIM 由三大核心组件构成：

> **（1）Social-BDI 智能体** — 四层层次化信念系统（身份 → 心理 → 事件观点 → 情绪），LLM 驱动的欲望推理，以及多层级思维链意图规划。四种异质智能体类型（普通用户、意见领袖、媒体、政府）共享统一认知管线。
>
> **（2）仿真环境** — Hawkes 点过程时间引擎实现非平稳激活；虚拟社交媒体平台提供个性化推荐、三层社交网络和热搜话题。
>
> **（3）策略评估** — 干预器（事件注入、节点控制、平台策略）、仿真器（基于检查点的反事实轨迹）和评估器（跨行为、内容、拓扑三层的多维定量评估）。

### 🎭 四种异质智能体类型

| 类型                 | 角色                 | 行为特征                 | 典型表现               |
| -------------------- | -------------------- | ------------------------ | ---------------------- |
| 👤**普通用户** | 主要参与者           | 口语化、碎片化、情绪驱动 | 高激发下的冲动表达     |
| 🌟**意见领袖** | 关键中介（两级传播） | 独立见解、议程设置       | 显著影响下游用户信念   |
| 📰**媒体账号** | 信息采集与传播       | 正式、克制、及时         | 信息确认与议程框架     |
| 🏛️**政府**   | 官方立场与治理       | 低频但高权威             | 事件升级后产生关键影响 |

> 四种类型的行为模式**不是预设的**，而是通过 Social-BDI 管线自主涌现的。

---

## ⚙️ 安装配置

### 💻 系统要求

| 项目   | 最低要求 | 推荐配置                           |
| ------ | -------- | ---------------------------------- |
| Python | ≥ 3.8   | 3.10                               |
| CUDA   | —       | ≥ 11.0（本地嵌入加速）            |
| 内存   | 16 GB    | 32 GB+（大规模仿真）               |
| GPU    | —       | 推荐（sentence-transformers 加速） |

### 📦 安装步骤

```bash
git clone https://github.com/DeepCogLab/posim.git
cd posim

# 推荐使用 conda
conda create -n posim python=3.10
conda activate posim

pip install -r requirements.txt
```

### 📚 核心依赖

| 包名                      | 版本      | 用途                            |
| ------------------------- | --------- | ------------------------------- |
| `numpy`                 | ≥ 1.24.0 | 数值计算，Hawkes 过程强度采样   |
| `openai`                | ≥ 1.0.0  | LLM API 调用（OpenAI 兼容接口） |
| `pydantic`              | ≥ 2.0.0  | 配置验证与结构化数据管理        |
| `sentence-transformers` | ≥ 2.2.0  | 语义嵌入（推荐、去重、记忆）    |
| `torch`                 | ≥ 2.0.0  | 深度学习后端（嵌入模型推理）    |
| `matplotlib`            | ≥ 3.7.0  | 评估可视化                      |
| `neo4j`                 | ≥ 5.0.0  | 社交网络图数据库（可选）        |
| `websockets`            | ≥ 12.0   | 实时仿真监控                    |

---

## 🚀 快速开始

### 1️⃣ 配置

创建 `scripts/<event>/config.json`，最小示例：

```json
{
  "simulation": {
    "event_name": "my_event",
    "simulation_title": "My Simulation",
    "start_time": "2025-05-15T00:00",
    "end_time": "2025-05-17T00:00",
    "time_granularity": 10,
    "decision_mode": "ebdi"
  },
  "data": {
    "users_file": "data/users.json",
    "events_file": "data/events.json",
    "initial_posts_file": "data/initial_posts.json",
    "relations_file": "data/relations.json"
  },
  "llm": {
    "max_concurrent_requests": 30,
    "use_local_embedding_model": true,
    "local_embedding_model_path": "path/to/bge-small-zh-v1.5",
    "embedding_dimension": 512,
    "embedding_device": "cuda",
    "llm_api_configs": [
      {
        "name": "my-llm",
        "enabled": true,
        "base_url": "http://localhost:8000/v1/",
        "api_key": "not-needed",
        "model": "Qwen/Qwen2.5-14B-Instruct",
        "temperature": 0.7,
        "top_p": 0.9,
        "weight": 1.0
      }
    ]
  },
  "output": {
    "base_dir": "output"
  }
}
```

> **`decision_mode`**：`"ebdi"`（完整认知管线）| `"no_ebdi"` | `"cot"` | `"wo_belief"` | `"wo_desire"` | `"wo_intention"` | `"wo_hawkes"`
>
> **LLM**：支持任何 OpenAI 兼容 API（vLLM、Ollama、DeepSeek、OpenAI 等）。可配置多端点进行负载均衡和按用途路由。

### 2️⃣ 准备数据

每个仿真场景需要四个数据文件，放置于 `scripts/<event>/data/` 目录下：

| 文件                   | 内容           |
| ---------------------- | -------------- |
| `users.json`         | 用户画像       |
| `events.json`        | 外部事件序列   |
| `initial_posts.json` | 仿真初始帖子   |
| `relations.json`     | 用户关系       |

<details>
<summary><b>📋 数据格式说明</b></summary>

#### `users.json` — 用户对象数组

```json
[
  {
    "user_id": "123456",
    "username": "Alice",
    "agent_type": "citizen",
    "followers_count": 500,
    "following_count": 300,
    "verified": false,
    "description": "个人简介。",
    "raw_profile": {
      "gender": "女",
      "location": "北京",
      "verified_type": "普通用户"
    },
    "behavior_tendency": {
      "repost": 1,
      "long_comment": 2,
      "like": 5
    },
    "identity_description": "一段自然语言描述，概括该用户的身份和行为模式。",
    "psychological_beliefs": [
      "心理信念1。",
      "心理信念2。"
    ],
    "event_opinions": [
      {
        "time": "2025-05-15T12:00",
        "subject": "事件主题名称",
        "opinion": "该用户对事件的初始立场。",
        "reason": "持有该立场的原因。"
      }
    ]
  }
]
```

> `agent_type`：`"citizen"` / `"kol"` / `"media"` / `"government"`
> `behavior_tendency`：相对权重（整数），数值越大概率越高
> `identity_description` 和 `psychological_beliefs` 作为智能体初始信念状态，建议基于真实画像数据提炼自然语言描述

---

#### `events.json` — 事件对象数组

支持两种事件类型：

**`global_broadcast`** — 全平台广播（如突发新闻）：
```json
{
  "time": "2025-05-16T09:45",
  "type": "global_broadcast",
  "source": ["external"],
  "topic": "简短主题标签",
  "content": "注入所有智能体感知的详细事件描述。",
  "influence": 1.0
}
```

**`node_post`** — 指定用户发帖：
```json
{
  "time": "2025-05-16T13:34",
  "type": "node_post",
  "source": ["user_id_here"],
  "topic": "简短主题标签",
  "content": "帖子内容文本。",
  "influence": 1.0,
  "source_post": {
    "user_id": "user_id_here",
    "username": "用户名",
    "agent_type": "citizen",
    "time": "2025-05-16T13:34:00",
    "content": "帖子内容文本。"
  }
}
```

> `influence`：`[0, 1]` 区间浮点数，控制该事件对 Hawkes 过程的激励强度

---

#### `initial_posts.json` — 种子帖子对象数组

```json
[
  {
    "type": "post",
    "author": "用户名",
    "author_id": "123456",
    "content": "帖子内容文本。",
    "time": "2025-05-07 19:21:39",
    "keywords": "关键词1,关键词2"
  }
]
```

> `type`：`"post"`（原创帖）或 `"comment"`（评论）
> 这些帖子构成推荐系统的初始内容池

---

#### `relations.json` — 用户关系对象数组

```json
[
  {
    "follower_id": "111",
    "following_id": "222",
    "relation_type": "follow",
    "timestamp": 1746878497
  }
]
```

> `timestamp`：Unix 时间戳（秒），用于加权关系时效性

</details>

### 3️⃣ 运行仿真

创建运行脚本（如 `scripts/<event>/run.py`），加载配置并启动仿真：

```python
import asyncio, sys
from pathlib import Path

sys.path.insert(0, str(Path(__file__).parent.parent.parent))

from posim.config.config_manager import ConfigManager
from posim.llm.api_pool import APIPool
from posim.engine.simulator import Simulator
from posim.data.data_loader import DataLoader, parse_user_data
from posim.storage.database import SimulationDatabase

async def main():
    config = ConfigManager("scripts/<event>/config.json").config
    api_pool = APIPool(config.llm)
    data_loader = DataLoader(config.data)
    users = parse_user_data(data_loader.load_users())
    db = SimulationDatabase("scripts/<event>/output/simulation.db")
    simulator = Simulator(config, api_pool, users, data_loader, db)
    await simulator.run()

asyncio.run(main())
```

仿真输出保存在 `output/` 目录。

---

## 🔌 扩展指南

得益于高度解耦的模块化设计，POSIM 的核心组件可以通过标准接口独立替换和扩展。

<details>
<summary><b>➕ 添加新智能体类型</b></summary>

1. 在 `posim/agents/` 中继承 `BaseAgent` 创建新类
2. 在 `posim/prompts/` 中创建对应的角色提示模板（信念/欲望/意图）
3. 在仿真配置中注册新类型

</details>

<details>
<summary><b>🔄 替换认知架构</b></summary>

Social-BDI 的三个子系统通过结构化中间状态通信，可以独立替换：

- 信念子系统：`posim/agents/ebdi/belief/`
- 欲望子系统：`posim/agents/ebdi/desire/`
- 意图子系统：`posim/agents/ebdi/intention/`

只需保持相同的输入/输出格式即可。

</details>

<details>
<summary><b>⏱️ 更换时间引擎</b></summary>

在 `posim/engine/` 中实现新的时间引擎模块，遵循相同的强度计算和智能体采样接口。

</details>

<details>
<summary><b>📊 添加评估指标</b></summary>

在 `posim/evaluation/calibration/` 或 `posim/evaluation/mechanism/` 中添加新的评估器类，并在 `evaluator_manager.py` 中注册。

</details>

<details>
<summary><b>🔗 接入新的 LLM 服务</b></summary>

只需在 `llm_api_configs` 配置中添加新端点——框架使用统一的 OpenAI 兼容接口，无需修改代码。支持本地部署（vLLM、Ollama）、OpenAI 及其他云 API 服务。

</details>

---

## ⚠️ 伦理声明

> **本研究纯粹作为数据驱动的科学研究。所有事件的分析完全基于公开可用的数据，作者对任何涉及的事件、个人或组织不持有任何意见或立场。该仿真框架仅用于学术研究和方法验证。**

数据集收集自新浪微博平台的公开帖子，经脱敏处理后公开，仅限非商业学术研究使用（见 [`datasets/README.md`](datasets/README.md)）。

---

## 📄 许可证

本项目基于 [MIT 许可证](LICENSE) 开源。

---

## 🖥️ 系统原型展示

我们正在基于 POSIM 开发完整的舆情仿真系统。以下原型图展示了当前界面方向与分析流程。

<p align="center">
  <img src="assets/system_prototype_1.png" alt="POSIM 系统原型总览" width="95%">
</p>
<p align="center"><b>图 2.</b> POSIM 仿真系统原型界面。</p>

<p align="center">
  <img src="assets/system_prototype_2.png" alt="POSIM 系统原型分析视图" width="95%">
</p>
<p align="center"><b>图 3.</b> 仿真监控与分析原型界面。</p>

---

<p align="center">
  <i>有问题或建议？欢迎提交 <a href="https://github.com/DeepCogLab/posim/issues">Issue</a> 💬</i>
</p>
