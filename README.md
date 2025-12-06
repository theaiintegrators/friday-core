<p align="left">
  <a href="https://github.com/theaiintegrators">
    <img src="https://img.shields.io/badge/Friday-Ecosystem-4B8BF5" />
  </a>
  <img src="https://img.shields.io/badge/status-active-success" />
  <img src="https://img.shields.io/badge/python-3.9%20|%203.10%20|%203.11-blue" />
  <img src="https://img.shields.io/badge/license-MIT-yellow" />
  <img src="https://img.shields.io/badge/docs-in%20progress-lightgrey" />
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen" />
</p>

# 📦 friday-core  
_Modular orchestration engine for enterprise-grade multi-agent AI workflows_

Friday Core provides the foundational building blocks for constructing **deterministic, evaluable, and observable multi-agent systems**, inspired by modern patterns found in:

- **Microsoft Agent Framework**  
- **LangGraph-style orchestration**  
- **OpenAI Model Context Protocol (MCP)**  
- **Agent-to-Agent (A2A) message passing**  
- **LangSmith / DeepEval evaluation workflows**  
- **LangFuse-style observability pipelines**  

It is the core runtime that powers the Friday ecosystem.

---

# 🌟 Why friday-core Exists

Most “agent frameworks” today focus on demos rather than production reliability.

Enterprise AI teams require:

- deterministic execution  
- strongly defined agent interfaces  
- reproducible workflows  
- structured evaluation gates  
- production-ready observability  
- modular components that can run on cloud or on-prem  
- graph-based routing, not ad-hoc function chains  

Friday Core fills this gap by offering a **minimal, extensible orchestration engine** suitable for real systems.

---

# ✨ Features

- **Deterministic Orchestrator** — predictable multi-agent execution  
- **Event-Based Routing** — clear next-step logic  
- **Simple Agent Interface** — plug-and-play behaviours  
- **Evaluation Hooks** — integrate DeepEval, LangSmith-style checks  
- **Observability Hooks** — emit LangFuse-compatible traces  
- **Enterprise Architecture** — modular, testable, vendor-neutral  

---

# 🏛 Architecture Overview

Friday Core splits responsibilities cleanly:

### **Orchestrator**  
Drives the event loop and executes agents in the correct order.

### **Agent**  
Implements behaviour through a minimal run interface.

### **Event**  
Typed message object passed between agents.

### **Router**  
Determines next agent using deterministic logic.

### **Evaluation Hooks**  
Optional validators inserted between steps.

### **Observability Hooks**  
Outputs structured traces & metrics.

```
   ┌────────┐      ┌────────┐
   │ Agent A│◀────►│ Agent B│
   └───▲────┘      └───▲────┘
       │               │
       ▼               ▼
   ┌────────────────────────┐
   │      Orchestrator      │
   │  (Event Loop + Router) │
   └────────────────────────┘
```

---

# 📚 Repository Structure

```
friday-core/
  ├── friday/
  │     ├── orchestrator.py
  │     ├── agent.py
  │     ├── router.py
  │     ├── event.py
  │     ├── exceptions.py
  │     ├── evaluation_hooks/
  │     └── observability_hooks/
  ├── examples/
  ├── tests/
  └── README.md
```

---

# 🚀 Quick Start Example

```python
from friday import Orchestrator, Agent, Event

class AgentA(Agent):
    def run(self, event: Event):
        return Event(content="Output from A", next="agent_b")

class AgentB(Agent):
    def run(self, event: Event):
        return Event(content="Output from B", next=None)

agents = {
    "agent_a": AgentA(),
    "agent_b": AgentB()
}

orchestrator = Orchestrator(agents=agents)
result = orchestrator.run("start")
print(result)
```

---

# 🔌 Extensions

### **Evaluation**
```python
orchestrator.with_evaluation(my_evaluator)
```

### **Observability**
```python
orchestrator.with_observability(langfuse_client)
```

---

# 📦 Installation

```bash
pip install friday-core   # coming soon
```

---

# 🧪 Roadmap

- A2A routing patterns  
- MCP tool integration  
- Built-in evaluation templates  
- LangFuse auto-enrichment  
- Workflow visualisation  
- YAML-defined pipelines  
- Friday CLI  

---

# 🔭 Vision

Friday Core aims to make AI workflows **predictable**, **testable**, and **observable** —  
suitable for real enterprise production systems, not just prototypes.

---

# 📄 License

MIT License
