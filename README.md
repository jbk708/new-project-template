# {Project Name}

One-sentence description of what this project does.

## Starting a New Project

This template is set up for ticket-driven work with Claude.

### With Claude Code (CLI)
1. Clone or copy this template into a new repo.
2. Edit `README.md` (this file) with the project name and description.
3. Fill in `TICKETS.md` with the initial backlog.
4. Fill in the placeholders in `.claude/agents/` once the stack is chosen — see `.claude/agents/README.md`.
5. Run `claude` in the project root.
6. Ask Claude to read `CLAUDE.md` and start on `T1`.

### With Claude (web / cowork)
1. Share `CLAUDE.md` and `TICKETS.md` with the agent.
2. Reference the active ticket by ID (e.g. `T1`).
3. Approve the plan, then let Claude implement following the workflow.

## Layout
- `CLAUDE.md` — agent rules, principles, workflow, formats
- `TICKETS.md` — ticket backlog (open + done)
- `README.md` — this file
- `.claude/agents/` — six-agent pipeline (team-lead, planner, SWE, QA, deployer, diagnostics)

## Setup

<!-- Replace with real build/test commands once the stack is chosen. -->

```sh
# install
# build
# test
```
