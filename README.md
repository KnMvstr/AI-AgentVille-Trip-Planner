# AgentsVille Trip Planner

An AI-powered travel planning system that generates personalized day-by-day itineraries for the city of AgentsVille. The project demonstrates advanced LLM reasoning techniques using the OpenAI API.

## Features

- **Role-Based Prompting** — Specialized travel planner agent persona
- **Chain-of-Thought Reasoning** — Step-by-step itinerary planning
- **ReAct Prompting** — Thought → Action → Observation cycles for iterative refinement
- **Feedback Loops** — Self-evaluation using tools to detect and fix plan issues

## Project Structure

```
AgentVille Trip Planner/
├── project_starter.ipynb   # Main notebook — walkthrough and implementation
├── project_lib.py          # Utility classes and helpers (ChatAgent, Interest, etc.)
├── requirements.txt        # Python dependencies
└── README.md
```

## Setup

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Configure your API key

The notebook uses the OpenAI API (or a compatible endpoint such as Vocareum). Set your key in one of two ways:

**Option A — Environment variable (recommended):**

```bash
# .env file
OPENAI_API_KEY=your-key-here
```

**Option B — Directly in the notebook:**

Edit the `api_key` line in the *Initial Setup* cell of `project_starter.ipynb`.

### 3. Run the notebook

Open `project_starter.ipynb` in VS Code or Jupyter and run the cells in order.

## Workflow Overview

| Step | Description |
|------|-------------|
| 1 | Define vacation details (`VacationInfo` Pydantic model) |
| 2 | Review simulated weather and activity schedule data |
| 3 | `ItineraryAgent` — generates an initial day-by-day plan in one LLM call |
| 4 | Evaluate the itinerary (city, dates, cost accuracy, hallucination check, weather suitability) |
| 5 | Define tools: `calculator_tool`, `get_activities_by_date_tool`, `run_evals_tool`, `final_answer_tool` |
| 6 | `ItineraryRevisionAgent` — refines the plan via ReAct loop until all constraints are met |
| 7 | Generate a narrative trip summary |

## Models

The project defaults to `gpt-4.1-mini`. You can switch models via the `MODEL` variable in the notebook:

| Model | Notes |
|-------|-------|
| `gpt-4.1` | Strongest reasoning |
| `gpt-4.1-mini` | Default — good balance of speed and cost |
| `gpt-4.1-nano` | Fastest and cheapest |

## Requirements

- Python 3.10+
- An OpenAI API key (or compatible endpoint)
