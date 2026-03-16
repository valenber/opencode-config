# Coding Conventions

## Commits
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
