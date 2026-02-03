# Company AI Playbook

This repository is the **single source of truth** for how we design, build, test, and ship software.

It exists to:
- Keep engineering decisions consistent across repos
- Prevent drift between backend and frontend
- Ensure AI (Claude) produces predictable, minimal, correct diffs
- Speed up onboarding of new developers

This repo contains **rules, not code**.

---

## How this repo is used

- Docs in this repo are **copied or synced** into each code repo under:

docs/ai/

- Each code repo treats `docs/ai/CONTEXT.md` as authoritative.
- If a rule exists here, **Claude must follow it**.
- If a rule changes, it must be updated here first.

---

## Structure


> company-ai-playbook/
> ├── README.md
> ├── architecture.md
> ├── testing.md
> ├── security.md
> ├── release.md
> └── standards/
> ├── backend.md
> └── frontend.md


---

## Rules of engagement

- This repo is **opinionated by design**
- Changes should be rare and intentional
- When in doubt: prefer **consistency over cleverness**
- Small diffs beat rewrites

---

## Ownership

- One owner maintains this repo
- Review changes carefully: every edit here affects *all* projects
- Target maintenance time: ~30 minutes/week

---

## For AI (Claude)

When working in any code repo:
1. Read `docs/ai/CONTEXT.md`
2. Follow the standards defined here
3. Prefer the smallest possible change
4. Never introduce new dependencies without approval
5. Never redesign UI unless explicitly asked


