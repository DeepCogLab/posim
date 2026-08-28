<p align="center">
  <a href="README_CN.md">中文</a> | <b>English</b>
</p>

<p align="center">
  <img src="assets/posim_logo.png" alt="POSIM Logo" width="600">
</p>

<h3 align="center">POSIM — A Multi-Agent Simulation Framework for Social Media Public Opinion Evolution and Governance</h3>

<p align="center">
  <em>"All models are wrong, but some are useful." — George E. P. Box</em>
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
    <img src="https://img.shields.io/badge/🏠_Project_Homepage-DeepCogLab.github.io/posim-blue?style=for-the-badge&logoColor=white" alt="Project Homepage">
  </a>
</p>

<p align="center">
  🌐 <a href="https://DeepCogLab.github.io/posim/">Homepage</a>  | 
  🐛 <a href="https://github.com/DeepCogLab/posim/issues">Issues</a>
</p>

---

## 📖 Table of Contents

- [💡 Why POSIM?](#-why-posim)
- [✨ Key Features](#-key-features)
- [🚧 Project Status](#-project-status)
- [🏗️ Framework Overview](#%EF%B8%8F-framework-overview)
- [⚙️ Installation](#%EF%B8%8F-installation)
- [🚀 Quick Start](#-quick-start)
- [🔌 Extension Guide](#-extension-guide)
- [⚠️ Ethical Statement](#%EF%B8%8F-ethical-statement)
- [📄 License](#-license)
- [🖥️ System Prototype](#%EF%B8%8F-system-prototype)

---

## 💡 Why POSIM?

Public opinion events on social media — from consumer disputes to public safety incidents — can escalate from a local discussion to a nationwide trending topic within hours. Thousands of users flood comment sections, emotions intensify through repost chains, and a single opinion leader's post can reshape the entire discourse. For government agencies, media organizations, and platform operators, understanding how public opinion forms, evolves, and can be guided is of critical practical importance.

However, conducting real-world social experiments on these dynamics faces fundamental challenges: ethical constraints prevent deliberate manipulation of public discourse, and each event is unique and irreproducible. This is where **computational simulation** becomes invaluable — it provides a virtual laboratory where researchers can replay, analyze, and experiment with public opinion scenarios in a controlled environment.

Traditional simulation approaches — epidemic models, threshold cascade models, and classic agent-based modeling (ABM) — each capture certain aspects of opinion dynamics, but share a critical limitation: **they cannot explicitly model individual cognitive processes**. Agents in these systems are rule-driven automatons that neither understand the content they encounter nor reason about their responses. Large language models (LLMs) offer a breakthrough with semantic understanding and human-like reasoning, yet most existing LLM-based simulations treat the model as a black-box behavior generator — prompt in, action out — without modeling the intermediate cognitive states that drive real human behavior.

**POSIM** (**P**ublic **O**pinion **Sim**ulator) bridges this gap. By embedding LLMs within a structured cognitive architecture (Social-BDI), POSIM creates agents that:

- **Maintain explicit belief states** — each agent tracks its identity, psychological traits, event opinions, and emotional arousal as structured, inspectable data
- **Produce fully traceable decisions** — every action can be traced back through the intention → desire → belief chain that produced it
- **Exhibit emergent collective behaviors** — opinion lifecycle patterns, emotional polarization, and cascade power laws arise spontaneously from individual agent interactions, without being programmed in

POSIM is designed for researchers studying computational social science, public opinion dynamics, crisis communication, and LLM-based multi-agent systems. It can also serve as a decision-support tool for evaluating governance strategies through counterfactual simulation.

---

## ✨ Key Features

- 🧠 **Social-BDI Agent Architecture** — LLMs embedded in a layered cognitive framework (Perception → Belief → Desire → Intention → Action) with emotional arousal and cognitive biases. Three cognitive subsystems powered by independent LLM calls, fully traceable decision chains.
- ⏱️ **Hawkes Process-Driven Temporal Engine** — Hawkes self-exciting point process unifying exogenous event shocks and endogenous user interactions with circadian rhythm modulation, reproducing realistic "outbreak–sustain–decay" activity patterns at minute-level resolution.
- 🛡️ **Three-Tier Progressive Validation** — From individual behavioral mechanism calibration → collective phenomenon emergence → statistical consistency, establishing simulation credibility layer by layer.
- 🔌 **Highly Decoupled Modular Architecture** — Agents, environment, and evaluation modules communicate through standard interfaces — swap the cognitive architecture, temporal engine, or evaluation metrics independently.

---

## 🚧 Project Status

POSIM is under active development. We are building a full simulation system on top of POSIM and will publish it as soon as it is ready. A pip package is also in development, so please follow this repository for release updates.

The current public repository includes the core simulation framework, sanitized run-script examples, lightweight sample data, and local embedding model assets. Full datasets and additional system components will be released gradually after review and anonymization.

---

## 🏗️ Framework Overview

<p align="center">
  <img src="assets/framework_overview.png" alt="POSIM Framework Overview" width="95%">
</p>
<p align="center"><b>Figure 1.</b> Overall architecture of POSIM.</p>

POSIM comprises three core components:

> **(1) Social-BDI Agents** — Four-layer hierarchical belief system (identity → psychology → event opinion → emotion), LLM-driven desire inference, and multi-level chain-of-thought intention planning. Four heterogeneous agent types (ordinary users, opinion leaders, media, governments) share the unified cognitive pipeline.
>
> **(2) Simulation Environment** — Hawkes point process temporal engine for non-stationary activation; virtual social media platform with personalized recommendation, three-layer social networks, and trending topics.
>
> **(3) Strategy Evaluation** — Intervenor (event injection, node control, platform policy), Simulator (checkpoint-based counterfactual trajectories), and Evaluator (multi-dimensional quantitative assessment across behavior, content, and topology layers).

### 🎭 Four Heterogeneous Agent Types

| Type                        | Role                                  | Behavioral Traits                      | Typical Manifestation                       |
| --------------------------- | ------------------------------------- | -------------------------------------- | ------------------------------------------- |
| 👤**Ordinary Users**  | Primary participants                  | Colloquial, fragmented, emotion-driven | Impulsive expression under high arousal     |
| 🌟**Opinion Leaders** | Key intermediaries (two-step flow)    | Independent views, agenda-setting      | Significant influence on downstream beliefs |
| 📰**Media Accounts**  | Information gathering & dissemination | Formal, restrained, timely             | Information confirmation & agenda framing   |
| 🏛️**Governments**   | Official stance & governance          | Low frequency, high authority          | Pivotal influence after event escalation    |

> All behavioral patterns emerge autonomously through the Social-BDI pipeline — they are **not** preset by rules.

---

## ⚙️ Installation

### 💻 System Requirements

| Item   | Minimum | Recommended                                      |
| ------ | ------- | ------------------------------------------------ |
| Python | ≥ 3.8  | 3.10                                             |
| CUDA   | —      | ≥ 11.0 (local embedding acceleration)           |
| RAM    | 16 GB   | 32 GB+ (large-scale simulation)                  |
| GPU    | —      | Recommended (sentence-transformers acceleration) |

### 📦 Setup

```bash
git clone https://github.com/DeepCogLab/posim.git
cd posim

# Recommended: use conda
conda create -n posim python=3.10
conda activate posim

pip install -r requirements.txt
```

### 📚 Core Dependencies

| Package                   | Version   | Purpose                                             |
| ------------------------- | --------- | --------------------------------------------------- |
| `numpy`                 | ≥ 1.24.0 | Numerical computation, Hawkes process sampling      |
| `openai`                | ≥ 1.0.0  | LLM API calls (OpenAI-compatible interface)         |
| `pydantic`              | ≥ 2.0.0  | Configuration validation & structured data          |
| `sentence-transformers` | ≥ 2.2.0  | Semantic embeddings (recommendation, dedup, memory) |
| `torch`                 | ≥ 2.0.0  | Deep learning backend (embedding inference)         |
| `matplotlib`            | ≥ 3.7.0  | Evaluation visualization                            |
| `neo4j`                 | ≥ 5.0.0  | Social network graph database (optional)            |
| `websockets`            | ≥ 12.0   | Real-time simulation monitoring                     |

---

## 🚀 Quick Start

### 1️⃣ Configure

Create `scripts/<event>/config.json`. A minimal example:

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

> **`decision_mode`**: `"ebdi"` (full cognitive pipeline) | `"no_ebdi"` | `"cot"` | `"wo_belief"` | `"wo_desire"` | `"wo_intention"` | `"wo_hawkes"`
>
> **LLM**: Supports any OpenAI-compatible API (vLLM, Ollama, DeepSeek, OpenAI, etc.). Multiple endpoints can be configured for load balancing and per-purpose routing.

### 2️⃣ Prepare Data

Each simulation scenario requires four data files under `scripts/<event>/data/`:

| File                   | Contents                       |
| ---------------------- | ------------------------------ |
| `users.json`         | User profiles                  |
| `events.json`        | External event sequence        |
| `initial_posts.json` | Seed posts at simulation start |
| `relations.json`     | User relationships             |

<details>
<summary><b>📋 Data Format Reference</b></summary>

#### `users.json` — Array of user objects

```json
[
  {
    "user_id": "123456",
    "username": "Alice",
    "agent_type": "citizen",
    "followers_count": 500,
    "following_count": 300,
    "verified": false,
    "description": "A brief self-introduction.",
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
    "identity_description": "One-paragraph natural language summary of the user's identity and behavior patterns.",
    "psychological_beliefs": [
      "Belief sentence 1.",
      "Belief sentence 2."
    ],
    "event_opinions": [
      {
        "time": "2025-05-15T12:00",
        "subject": "Event topic name",
        "opinion": "The user's initial stance on the event.",
        "reason": "Why the user holds this opinion."
      }
    ]
  }
]
```

> `agent_type`: `"citizen"` / `"kol"` / `"media"` / `"government"`
> `behavior_tendency`: relative weights (integers); higher = more likely
> `identity_description` and `psychological_beliefs` are used as the agent's initial belief state — provide natural language summaries based on real profile data

---

#### `events.json` — Array of event objects

Two event types are supported:

**`global_broadcast`** — Platform-wide push (e.g. breaking news):

```json
{
  "time": "2025-05-16T09:45",
  "type": "global_broadcast",
  "source": ["external"],
  "topic": "Short topic label",
  "content": "Detailed event description injected into all agents' perception.",
  "influence": 1.0
}
```

**`node_post`** — A specific user publishes a post:

```json
{
  "time": "2025-05-16T13:34",
  "type": "node_post",
  "source": ["user_id_here"],
  "topic": "Short topic label",
  "content": "Post content text.",
  "influence": 1.0,
  "source_post": {
    "user_id": "user_id_here",
    "username": "Username",
    "agent_type": "citizen",
    "time": "2025-05-16T13:34:00",
    "content": "Post content text."
  }
}
```

> `influence`: float in `[0, 1]`, controls how strongly this event excites the Hawkes process

---

#### `initial_posts.json` — Array of seed post objects

```json
[
  {
    "type": "post",
    "author": "Username",
    "author_id": "123456",
    "content": "Post content text.",
    "time": "2025-05-07 19:21:39",
    "keywords": "keyword1,keyword2"
  }
]
```

> `type`: `"post"` (original post) or `"comment"` (reply)
> These posts form the initial content pool for the recommendation system

---

#### `relations.json` — Array of user relationship objects

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

> `timestamp`: Unix timestamp (seconds); used to weight relationship recency

</details>

### 3️⃣ Run Simulation

Create a run script (e.g. `scripts/<event>/run.py`) that loads config and starts the simulator:

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

Simulation outputs are saved to the `output/` directory.

---

## 🔌 Extension Guide

Thanks to the highly decoupled modular design, POSIM's core components can be independently replaced and extended through standard interfaces.

<details>
<summary><b>➕ Add a New Agent Type</b></summary>

1. Inherit `BaseAgent` in `posim/agents/` to create a new class
2. Create corresponding role prompt templates in `posim/prompts/` (belief / desire / intention)
3. Register the new type in the simulation configuration

</details>

<details>
<summary><b>🔄 Replace the Cognitive Architecture</b></summary>

The three Social-BDI subsystems communicate through structured intermediate states and can be independently replaced:

- Belief subsystem: `posim/agents/ebdi/belief/`
- Desire subsystem: `posim/agents/ebdi/desire/`
- Intention subsystem: `posim/agents/ebdi/intention/`

Simply maintain the same input/output format.

</details>

<details>
<summary><b>⏱️ Switch the Temporal Engine</b></summary>

Implement a new temporal engine module in `posim/engine/`, following the same intensity computation and agent sampling interface.

</details>

<details>
<summary><b>📊 Add Evaluation Metrics</b></summary>

Add a new evaluator class in `posim/evaluation/calibration/` or `posim/evaluation/mechanism/`, and register it in `evaluator_manager.py`.

</details>

<details>
<summary><b>🔗 Connect a New LLM Service</b></summary>

Simply add a new endpoint in the `llm_api_configs` configuration — the framework uses a unified OpenAI-compatible interface, no code changes needed. Supports local deployments (vLLM, Ollama), OpenAI, and other cloud API services.

</details>

---

## ⚠️ Ethical Statement

> **This study is conducted purely as data-driven scientific research. All events are analyzed based entirely on publicly available data, and the authors hold no opinions or positions regarding any events, individuals, or organizations involved. The simulation framework is intended exclusively for academic research and methodological validation.**

Datasets are collected from publicly available posts on Sina Weibo. We plan to release them publicly after careful review and anonymization.

---

## 📄 License

This project is open-sourced under the [MIT License](LICENSE).

---

## 🖥️ System Prototype

We are developing a complete public opinion simulation system based on POSIM. The following prototype screens show the current direction of the interface and analysis workflow.

<p align="center">
  <img src="assets/system_prototype_1.png" alt="POSIM system prototype overview" width="95%">
</p>
<p align="center"><b>Figure 2.</b> Prototype view of the POSIM simulation system.</p>

<p align="center">
  <img src="assets/system_prototype_2.png" alt="POSIM system prototype analysis view" width="95%">
</p>
<p align="center"><b>Figure 3.</b> Prototype view of simulation monitoring and analysis.</p>

---

<p align="center">
  <i>Questions or suggestions? Feel free to open an <a href="https://github.com/DeepCogLab/posim/issues">Issue</a> 💬</i>
</p>
