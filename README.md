# 🧠 Coder Buddy – Agentic AI Engineer for Data & ML Projects

Coder Buddy is an agentic AI coding assistant built with **LangGraph** that behaves like a small multi‑agent engineering team.  
From a single natural language request, it plans, designs, and implements complete, working projects — file by file — using real developer workflows.

It is designed to be especially useful for **data engineers, data scientists, ML engineers, and AI engineers** who want to go from idea → running prototype quickly for data and AI workloads.

---

## 🌟 What Coder Buddy Can Do

Given a prompt like:

- “Create a batch data pipeline API that exposes transformed metrics.”
- “Set up a simple experiment scaffolding for a regression model with training, evaluation, and prediction endpoints.”
- “Build a small web UI to explore and filter a dataset.”

Coder Buddy will:

1. Understand your high‑level requirement.
2. Design the project architecture (files, folders, tech stack).
3. Implement the code directly into your project directory.

Today, it can already generate complete examples such as:

- A to‑do list web application (HTML, CSS, JavaScript).
- A calculator web application (HTML, CSS, JavaScript).
- A blog API using FastAPI and SQLite, which mirrors patterns used in data/ML APIs (request validation, persistence, basic CRUD).

You can easily adapt the same workflow for:

- Data ingestion & transformation services
- Analytics and reporting backends
- ML/AI experiment runners and serving layers

---

## 🏗️ Architecture Overview

Coder Buddy uses a **multi‑agent architecture** orchestrated with LangGraph.

- **Planner Agent**  
  - Interprets natural language prompts into a structured project plan.  
  - Defines features, technology stack, and overall file/folder layout (e.g., `data/`, `models/`, `api/`, `tests/`).

- **Architect Agent**  
  - Breaks the plan into concrete engineering tasks with **file‑scoped instructions**.  
  - Specifies exactly what each file should contain (ETL steps, API routes, model training logic, utilities, etc.).

- **Coder Agent**  
  - Executes the tasks, writes code into real files, and respects the existing project structure.  
  - Reads from and writes to disk using tools, so it can extend or refactor existing projects rather than hallucinate paths.

<div style="text-align: center;">
  <img src="resources/coder_buddy_diagram.png" alt="Coder Agent Architecture" width="90%"/>
</div>

The workflow is coordinated by a **LangGraph state graph**, which routes information and control between agents in an explicit, debuggable way (ideal for production‑style data and AI workflows).

---

## 🧰 Tech Stack

- **Language & Orchestration**
  - Python
  - LangGraph (agent orchestration and state graph)
  - LangChain for LLM integration and structured outputs

- **Model Backend**
  - Groq LLMs, configured via `GROQ_API_KEY` environment variable.

- **Configuration & Tooling**
  - `python-dotenv` for environment configuration (`.env`)
  - `uv` as the Python project and environment manager for fast, reproducible installs

This stack mirrors what many modern data/ML/AI teams use for building agentic systems, internal tools, and rapid prototypes.

---

## 🚀 Getting Started

### 1. Prerequisites

- **Python** (3.10+ recommended)
- **uv** – a fast Python package and project manager.  
  Follow the official installation guide here: https://docs.astral.sh/uv/getting-started/installation/
- A **Groq account** and API key: https://console.groq.com/keys

### 2. Installation & Setup

Clone the repository, then inside the project folder:

```bash
# Create and activate a virtual environment using uv
uv venv
source .venv/bin/activate  # On Windows, use: .venv\Scripts\activate


Install dependencies (managed via pyproject.toml):

bash
uv pip install -r pyproject.toml
Create a .env file in the project root and add the environment variables following .sample_env:

bash
GROQ_API_KEY="your_groq_api_key_here"
# Add any other configuration keys required by the project
💡 Pro Tip: Using a .env file keeps secrets out of source control and is the recommended practice for API keys.

3. Run Coder Buddy
Start the application:

bash
python main.py
🎉 You're ready! You can now give Coder Buddy natural language prompts, and it will plan and implement projects directly into your working directory.
