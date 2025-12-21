# Agent Development Kit (ADK)

## What is ADK

Agent Development Kit (ADK) is a framework for building coordinated AI systems composed of multiple agents.

Instead of a single model handling everything, ADK enables:

- **Specialized agents → Coordinated execution → One outcome**

Each agent has a clear responsibility, and ADK manages how they work together.

---

## Orchestration 🎼

Orchestration is the control layer that defines how agents execute and interact.

ADK allows you to specify:

- Execution order
- Parallel or sequential runs
- Iteration and refinement
- Shared access to outputs

### Example: Content Creation Workflow

| Agent           | Responsibility      |
|-----------------|------------------|
| Script Writer   | Generates text     |
| Visual Designer | Suggests visuals   |
| Formatter       | Produces final output |

This turns independent agents into a predictable workflow.

---

## Multi-Agent Composition

Agents are typically organized under a root agent that manages execution.

```yaml
root_agent:
  workflow:
    - script_writer
    - visual_designer
    - formatter
The root agent defines structure; sub-agents focus on their tasks.

Model Foundation ⚙️
ADK is model-agnostic and deployment-agnostic.

You can use different models or environments while ADK consistently manages:

Agent coordination

Execution flow

State handling

Runtime events

Models generate outputs; ADK manages behavior.

Output Keys 🔑
Agents often need to consume outputs produced by other agents.
ADK enables this through output keys, which act as shared state.

yaml
Copy code
output_key: generated_content
Flow:

One agent writes to the key

Other agents read from the same key

This enables collaboration without re-generating data.

Interaction Interfaces
ADK supports multiple ways to interact with agents:

CLI – local testing and fast iteration

bash
Copy code
adk run .
Web UI – interactive demos (chat, voice, video)

API Server – REST endpoints for application integration

Python API – programmatic execution in backend services

Agent Types
LLM Agent
An agent backed by an LLM and optional tools.
Used for writing, analysis, or research.

Workflow Agents
Workflow agents control how agents run:

Sequential – agents run one after another

Parallel – agents run at the same time

Loop 🔁 – agents iterate for refinement

yaml
Copy code
LoopAgent:
  max_iterations: 3
Custom – combinations of the above for complex workflows

Runtime Services 🧠
Session – active execution lifecycle

Memory – persistent state across sessions

Artifacts – stored outputs (text, images, documents)

Runner & Events
Runner
Executes the root agent, coordinates sub-agents, and manages flow.

Events
Every meaningful action emits an event:

Agent start or finish

Tool calls and responses

Events provide visibility and control during execution.

System View
text
Copy code
User
 → Runner
 → Root Agent
 → Sub-Agents
 → Shared State (output keys)
 → Memory / Artifacts
 → Events
