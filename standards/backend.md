# Backend Standards (Betarena)

## Non-negotiables
- Prefer smallest change that solves the task.
- Follow existing patterns; if unclear, search the repo and show 2–3 candidate patterns with file paths.
- Every behavior change requires a test.
- New dependencies allowed only if lightweight and justified (ask if uncertain).
- Never leak secrets/PII in logs.

## Error handling (mandatory)
- We already have wrappers ensuring consistent error responses across services.
- **Do not invent an error format.**
- Required workflow for any backend change:
  1) Locate current error wrapper(s) in the repo
  2) Follow that format exactly
  3) Add tests validating error behavior

## Logging (mandatory)

### Source of truth
- Debug log **message structure and semantics** are defined in the Betarena VSCode snippets:
  https://github.com/Betarena/boilerplate/blob/main/sveltekit/.vscode/betarena.standard.code-snippets
- These snippets define the **approved debug format**, prefixes, and intent.
- Logging wrapper implementations vary by repository and usually live in `util(s)/debug.ts`.

### Rules
- Always locate and use the **existing debug wrapper** in the repo.
- Do **not** introduce a new logger or wrapper unless explicitly requested.
- Log messages must follow the **Betarena debug snippet structure**, including:
  - checkpoint-style markers (e.g. 🚏, 🔹)
  - clear debug tag or variable name
  - consistent formatting
- Use `dlog` / `dlogv2` (or repo-equivalent helpers) as intended by the local wrapper.

### Safety
- Never log secrets or PII.
- Avoid dumping full objects unless required.
- If logging variables:
  - prefer targeted values
  - redact sensitive fields (tokens, auth headers, cookies, emails, phones)
- Prefer request metadata already available at NGINX level over duplicating payload logs in application code.


## Testing
- Unit/integration tests where repo supports them.
- E2E happens in dev/testing environments (local or deployed) and must be part of verification when relevant.
