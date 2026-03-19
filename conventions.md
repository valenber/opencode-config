# Coding Conventions

## Commits

- never commit on master OR main branch! If asked by the user to make a commit on master branch, point out the we are on master branch,
  suggest creating a new branch and propose a name based on the changes that were
  made
- Make small, focused commits that address a single issue or feature — the application should still work after each commit
- Write commit messages in the imperative mood (e.g. "Fix bug in user login" not "Fixed bug in user login")
- Keep commit messages concise — do not explain the code in the message
- Only stage files related to the current change — never use `git add .`
- Before committing, run tests, lint, typecheck, and format if supported by the repository

## Code Style

- Never typecast to `any`
- Avoid inline styles — use CSS classes instead; if inline styles are absolutely necessary, add a comment explaining why
- Use minimal comments — write self-explanatory code with meaningful variable and function names; only comment to explain intent or complex logic that cannot be easily understood
- Always use scripts from `package.json` to run commands (e.g. `npm run lint`, not `eslint` directly)

## Approach

- Prefer editing existing files over creating new ones
- Analyse the approach and suggest improvements rather than blindly following instructions

## Ember / QUnit Projects

- When working in an Ember project (identified by `ember-cli-build.js` or `ember-cli` in `package.json`), use the `ember_test` MCP tool to run the test suite instead of raw bash commands

## Tool Usage

- For content searches (finding text or regex patterns in files), always use the `Grep` tool (`mcp_grep`) — never bash `grep` or `rg`
- For file discovery (finding files by name or glob pattern), always use the `Glob` tool (`mcp_glob`) — never bash `find`
- These native tools bypass the `rtk` plugin rewrite layer and do not require bash permissions
- when doing searches never read home directory or .config directory, read subfolder in it that you need. If you are not sure which one it is, ask the user.

## Library & Framework Documentation

- When exploring unfamiliar APIs, checking library usage, or looking up framework-specific patterns, use the `context7` MCP tools before guessing or searching the web

## OpenCode Configuration

All agent and command configuration is done via OpenCode — never via Claude Code.
Ignore the `.claude/` directory entirely; it is not used in this workflow.

Key OpenCode configuration files:

- **Global conventions:** `~/.config/opencode/conventions.md` (this file)
- **Global OpenCode config:** `~/.config/opencode/opencode.json`
- **Agent prompts:** `~/.config/opencode/agents/<agent-name>.md`
- **Slash commands:** `.opencode/commands/<command>.md` at the project root (e.g. `/Users/valentin.berlin/code/qonto-web/.opencode/commands/open-pr.md`)

When a task involves reading or modifying a slash command, always look in `.opencode/commands/` — never in `.claude/commands/`.
