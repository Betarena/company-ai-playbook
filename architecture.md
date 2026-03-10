# Architecture

Architecture guidelines and patterns for company projects.

## Scheduled Jobs / Cronicle

Some background tasks are executed via **Cronicle**.

Cronicle is used only when a scheduled job is the clearest and most maintainable implementation.

### Decision order

When implementing background or recurring tasks, prefer:

1. application logic (event-driven or request-driven)
2. database-native mechanisms (e.g. SQL triggers)
3. Cronicle scheduled jobs

Cronicle should only be used when:
- the task must run on a fixed schedule
- it cannot be reliably triggered by application events
- implementing it in code would create unnecessary complexity

### Rules

- Do not introduce new Cronicle jobs unless explicitly justified.
- Business logic should remain in application code, not hidden in scheduler configuration.
- Before modifying background logic, verify whether the process is triggered by:
  - application code
  - database triggers
  - Cronicle

### Documentation requirement

If a new scheduled job is introduced, document:
- job purpose
- schedule
- target service/repository
- failure impact
- how the job can be disabled
