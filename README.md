# OpenCode Config

Personal [OpenCode](https://opencode.ai) configuration — global coding conventions and custom agent definitions.

## Agents

| Agent | Description |
|-------|-------------|
| **plan** | Plans a software engineering task by exploring the codebase, clarifying ambiguities, and producing a structured implementation plan. |
| **build** | Implements a plan by writing code, running tests, linting, and committing changes. |
| **execute** | Implements a single, fully-specified file or component change. Called by the build agent to parallelise independent tasks. |
| **review** | Reviews code changes for quality, readability, and maintainability. Accepts a PR number to review a remote GitHub PR. |
| **coach** | Evaluates agent performance during a session and proposes targeted improvements to the agent's system prompt. |
