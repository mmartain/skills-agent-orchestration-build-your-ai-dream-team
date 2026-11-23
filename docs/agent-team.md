# Agent team

I will build Mona's Project Pulse dashboard with the following custom agent team. GitHub Copilot CLI in this Codespace will orchestrate the work.

| Agent | Target model | Responsibility | Definition |
|---|---|---|---|
| **Orchestrator** | Claude Opus 5.5 (copilot) | Coordinates the Planner, Coder, and Designer; turns the implementation plan into ordered phases, delegates explicit file scopes, and verifies the integrated result. It does not implement the dashboard directly. | [.github/agents/orchestrator.agent.md](../.github/agents/orchestrator.agent.md) |
| **Planner** | Claude Opus 5.5 (copilot) | Researches the repository and requirements, identifies dependencies and edge cases, and produces a practical implementation plan with file assignments and validation expectations. | [.github/agents/planner.agent.md](../.github/agents/planner.agent.md) |
| **Coder** | GPT-5.5 (copilot) | Implements the dashboard code and runnable-app support, following repository patterns and validating behavior with clear, testable changes. | [.github/agents/coder.agent.md](../.github/agents/coder.agent.md) |
| **Designer** | Gemini 3.7 Flash (copilot) | Shapes the dashboard's UI/UX, accessibility, responsive layout, visual hierarchy, interaction flow, and Project Pulse styling within assigned files. | [.github/agents/designer.agent.md](../.github/agents/designer.agent.md) |

## How the team builds Project Pulse

GitHub Copilot CLI in this Codespace acts as the orchestration interface. The Orchestrator starts by asking the Planner to research the repository and create a phased implementation plan with clear file ownership, dependencies, risks, and validation criteria.

The Orchestrator then assigns work in phases. The Designer establishes the dashboard's visual hierarchy, responsive layout, accessibility, and styling, while the Coder implements the application structure and behavior. These specialists run in parallel only when their file scopes and dependencies do not overlap; otherwise, the Orchestrator sequences their work to avoid conflicts.

Finally, the Orchestrator verifies that the integrated dashboard is consistent and reports the result. Git operations remain controlled by the learner, as none of the custom agents stage, commit, or push changes.
