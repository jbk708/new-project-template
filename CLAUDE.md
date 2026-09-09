# Project Template

## Principles

### KISS — Keep It Simple
- Write the smallest code that solves the problem.
- No speculative features, flags, abstractions, or fallbacks.
- Three similar lines beat a premature abstraction.
- Delete unused code; don't preserve it "just in case."

### CRUD — One Job Per Unit
- Each function does one thing: **C**reate, **R**ead, **U**pdate, or **D**elete.
- No mixed read+write side effects in a single path.
- Pure where possible; push I/O to the boundaries.
- State changes are explicit and localized.

### Style
- Code speaks for itself — no comments explaining *what*.
- Comment only non-obvious *why* (constraints, invariants, gotchas).
- Names carry meaning. If a comment is needed, try a better name first.

### Secrets
- **Never** paste auth tokens, API keys, passwords, private keys, session cookies, OAuth/JWT tokens, `.env` contents, or any post-auth credential into the chat.
- If a secret is needed, reference it by name (e.g. `OPENAI_API_KEY`) and load it from the environment, a secrets manager, or a gitignored `.env` file.
- If a secret is accidentally shared, treat it as compromised: rotate immediately, then scrub history.
- Do not commit secrets. Add `.env`, `*.pem`, `*.key`, and credential files to `.gitignore` before first commit.

## Agents

A six-agent pipeline lives in `.claude/agents/` — see [`.claude/agents/README.md`](.claude/agents/README.md) for the roster, flow, and trigger threshold.

Start with `team-lead` for any change broader than a single-line fix. It dispatches Planner ⇄ SWE to reconcile a plan, blocks on your explicit go-ahead, then runs SWE → QA → Deployer.

The agents ship generic. Fill in the `{TEST_COMMAND}`, `{LINT_COMMANDS}`, `{DEPLOY_COMMANDS}`, and `{ACCESS_PATTERN}` placeholders once the stack is chosen, and grow each agent's `## Memory` section as the project teaches you things.

## Workflow (One Ticket Per PR)

1. **Branch** — `git checkout -b t{N}-short-description`
2. **Plan** — Read ticket, outline types/functions/tests, get approval.
3. **Tests** — Write failing tests first; define expected behavior.
4. **Implement** — Minimum code to pass tests.
5. **Simplify** — Lint, format, all tests green, no warnings.
6. **PR** — `gh pr create --title "T{N}: {Title}" --body '...'` then `gh pr merge --auto --squash --delete-branch`.
7. **Monitor** — `gh pr checks --wait`; rebase if needed. Auto-merge fires on green.

## Formats

### Commit
```
T{N}: {verb} {what changed}
```

### PR Title
```
T{N}: {Ticket title}
```

### PR Body
Use **single quotes** around `gh pr create --body` content to avoid shell interpolation.
