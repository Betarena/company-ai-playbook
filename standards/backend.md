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
- We use a shared custom logging wrapper (typically `utils/debug.ts`).
- No formal log levels enforced today — still keep logs meaningful and minimal.
- Request bodies:
  - Allowed when necessary for debugging, but:
    - never log secrets/PII
    - redact sensitive fields
    - avoid dumping full objects if a summary is enough
  - Note: NGINX can log request metadata already; prefer NGINX for broad request logging.

## Testing
- Unit/integration tests where repo supports them.
- E2E happens in dev/testing environments (local or deployed) and must be part of verification when relevant.
