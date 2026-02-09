## AI Usage Checklist (Betarena)

### Before starting any task

* [ ] Repo opened at root (Claude can see `docs/ai/*`)
* [ ] I pasted the **canonical Claude prompt**
* [ ] I know whether this task is **read-only** or **write-capable**
* [ ] If write-capable → I have *not* approved writes yet

---

### Mandatory workflow (always)

* [ ] Claude located **existing patterns** (file paths shown)
* [ ] Claude proposed a **plan + list of files**
* [ ] Changes are **minimal diffs**
* [ ] No refactors or redesigns unless explicitly requested
* [ ] Tests added/updated **only if behavior changed**
* [ ] Verification checklist provided

---

### Data safety (CRITICAL)

* [ ] No writes to Firestore / Postgres / Redis unless I explicitly said **“writes approved”**
* [ ] Verification steps are **read-only** by default
* [ ] No migrations, seeds, backfills, workers, invalidations run
* [ ] If writes were approved:

  * [ ] Target environment stated (emulator / staging / prod)
  * [ ] Rollback plan stated

---

### Repo rules respected

* [ ] `docs/ai/CONTEXT.md` followed
* [ ] Playbook version pinned (v1.0.5)
* [ ] No frontend rules applied to backend repos
* [ ] No backend logic added to frontend repos

---

### Before opening a PR

* [ ] Scope is tight and reviewable
* [ ] Dangerous paths (data writes) reviewed by another dev
* [ ] No secrets / PII logged
* [ ] Commit message reflects *what* changed, not *everything*

---

### Red flags (STOP if any)

* ❌ Claude guessed infra/env details
* ❌ Claude suggested running dev servers touching real data
* ❌ Claude proposed refactors “for cleanliness”
* ❌ Claude suggested migrations/seeds without approval

If any red flag appears → **stop and reassess**.

---

### Rule of thumb

> **If you didn’t explicitly ask for it, Claude shouldn’t do it.**

---