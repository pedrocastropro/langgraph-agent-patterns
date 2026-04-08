# LangGraph Agent Patterns

Executable repository demonstrating the fundamental patterns for building agents with LangGraph — from the prebuilt helper to manual construction with state, memory, and routing.

## Architecture

```
01 create_react_agent     Prebuilt agent (2 nodes: agent + tools)
        │
02 StateGraph manual      Same agent built from scratch
        │
03 MemorySaver            In-session memory via thread_id
        │
04 conditional_edges      Deterministic router → specialized nodes
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

Run them in order — each one builds on the previous.

| # | Notebook | What it demonstrates |
|---|----------|---------------------|
| 01 | `create_agent` | `create_react_agent` prebuilt + 1 custom tool |
| 02 | `state_graph` | Same graph built manually with `StateGraph` + `TypedDict` + Reducers |
| 03 | `memory_saver` | `MemorySaver` — multi-turn memory via `thread_id` |
| 04 | `conditional_edges` | Deterministic intent router → 3 specialized nodes |

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
    ├── 01_create_agent.ipynb
    ├── 02_state_graph.ipynb
    ├── 03_memory_saver.ipynb
    └── 04_conditional_edges.ipynb
```
