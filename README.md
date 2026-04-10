# LangGraph Agent Patterns

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![LangGraph](https://img.shields.io/badge/LangGraph-framework-1C3C3C?logo=langchain&logoColor=white)](https://langchain-ai.github.io/langgraph/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-412991?logo=openai&logoColor=white)](https://platform.openai.com/)
[![Jupyter](https://img.shields.io/badge/Jupyter-notebooks-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

Executable repository demonstrating the fundamental patterns for building agents with LangGraph — from the prebuilt helper to manual construction with state, memory, and routing.

## Architecture

```
Level 1 — Foundations
├── N1A  create_react_agent       Prebuilt agent (2 nodes: agent + tools)
├── N1B  StateGraph manual        Same agent built from scratch
├── N1C  MemorySaver              In-session memory via thread_id
└── N1D  conditional_edges        Deterministic router → specialized nodes

Level 2 — Patterns
├── N2A  State & Routing          MessagesState · Command API · LLM routing · Prompt chaining
├── N2B  HITL · Streaming         interrupt_before · stream modes · SQLite checkpointer
└── N2C  Architectural Patterns   Orchestrator-Worker · Evaluator-Optimizer

Level 3 — Multi-Agent
├── N3A  Subgraph & Supervisor    Subgraph as node · LLM-coordinated specialists
├── N3B  Swarm & Send API         Decentralized handoffs · Dynamic map-reduce fan-out
└── N3C  Long-term Memory         Store · cross-thread / cross-user persistence
```

## Prerequisites

**Python 3.10+** and an **OpenAI API key**.

### 1. Create a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure your API key

```bash
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY
```

### 4. Register the Jupyter kernel

```bash
python -m ipykernel install --user --name langgraph-patterns --display-name "LangGraph Patterns"
```

## Notebooks

Run them in order — each level builds on the previous.

### Level 1 — Foundations

| # | Notebook | What it demonstrates |
|---|----------|---------------------|
| N1A | `N1A_create_agent` | `create_react_agent` prebuilt + 1 custom tool |
| N1B | `N1B_state_graph` | Same graph built manually with `StateGraph` + `TypedDict` + Reducers |
| N1C | `N1C_memory_saver` | `MemorySaver` — multi-turn memory via `thread_id` |
| N1D | `N1D_conditional_edges` | Deterministic intent router → 3 specialized nodes |

### Level 2 — Patterns

| # | Notebook | What it demonstrates |
|---|----------|---------------------|
| N2A | `N2A_state_routing` | `MessagesState` · `Command` API · LLM routing with structured output · Prompt chaining with validation |
| N2B | `N2B_hitl_streaming_memory` | `interrupt_before` (HITL) · Streaming (`updates` / `messages`) · `SqliteSaver` persistent memory |
| N2C | `N2C_patterns_advanced` | Orchestrator-Worker (parallel decomposition) · Evaluator-Optimizer (iterative quality loop) |

### Level 3 — Multi-Agent

| # | Notebook | What it demonstrates |
|---|----------|---------------------|
| N3A | `N3A_subgraph_supervisor` | Subgraph as a node (compiled graph reused inside another) · Supervisor pattern with LLM coordinator + specialist agents |
| N3B | `N3B_swarm_send_api` | Swarm — decentralized handoffs via `Command(goto=)` · Send API — dynamic fan-out to parallel workers (map-reduce) |
| N3C | `N3C_long_term_memory` | `Store` — cross-thread, cross-user memory · namespaces · combining checkpointer (short-term) with store (long-term) |

### Running

```bash
jupyter lab --notebook-dir=notebooks
```

Select the **"LangGraph Patterns"** kernel in each notebook. The first cell in every notebook installs dependencies automatically via `%pip install`.

## Project structure

```
.
├── .env.example          # API key template
├── .gitignore
├── requirements.txt      # All dependencies
├── README.md
└── notebooks/
    ├── N1A_create_agent.ipynb
    ├── N1B_state_graph.ipynb
    ├── N1C_memory_saver.ipynb
    ├── N1D_conditional_edges.ipynb
    ├── N2A_state_routing.ipynb
    ├── N2B_hitl_streaming_memory.ipynb
    ├── N2C_patterns_advanced.ipynb
    ├── N3A_subgraph_supervisor.ipynb
    ├── N3B_swarm_send_api.ipynb
    └── N3C_long_term_memory.ipynb
```
