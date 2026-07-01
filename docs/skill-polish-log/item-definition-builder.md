# Polish log — item-definition-builder

## 2026-07-01 (POLISH, Wed)

**Selection reason:** No open issues. Priority fell to orphan builders — `item-definition-builder` is flagged 🔴 in STATUS.

**What's good:**
- Frontmatter is valid: `name` + `description` present; description is 333 chars (well under the 1024 limit).
- Clear 5-step workflow (interview → read refs → build JSON → generate → present/iterate).
- 11-tab output table maps explicitly to ISO 26262-3 Clause 5; "JSON is source of truth, xlsx is derived" is stated cleanly.
- Skill payload is complete: generator, recalc, office helper, 2 references, and a worked ESC example.

**What to fix:**
- **[med] Reviewer naming mismatch (root cause of the 🔴 flag).** The paired reviewer is `item-def-checklist-reviewer.skill`, but the builder base is `item-definition-builder`. Strict `<base>-checklist-reviewer.skill` matching therefore reports this builder as an orphan even though a reviewer exists. Same pattern affects `ppap-package-builder` ↔ `ppap-checklist-reviewer`.
- **[low] Staleness.** Last touched 2026-05-01 (61 days); content is still accurate, but it sits in the 🟡 stale bucket.

**Suggested edits (NOT applied this run — rename is a repo-structure change, out of scope for a small in-file polish):**
- Option A: rename `item-def-checklist-reviewer.skill` → `item-definition-checklist-reviewer.skill` (align reviewer to builder base). Cleanest, but breaks any external references to the old name and requires the reviewer's internal `name:` frontmatter to change too.
- Option B: add an alias/exception map to the STATUS generator so shortened-base pairs resolve. Lower blast radius, keeps filenames.
- Recommend Option B unless a human confirms no external consumers depend on the current reviewer filename.

**Severity:** med (cosmetic/reporting accuracy; no functional defect in the builder itself).

**Applied this run:** none — SKILL.md is clean; the only actionable item is a rename/generator-exception decision that needs a human call. Captured as a follow-up.
