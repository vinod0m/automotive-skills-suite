# Polish log — 5-why-builder

## 2026-06-23 (POLISH, autonomous)

**Selected via:** weekly-target issue #27 (least-recently-touched builder; no skill-bug/reviewer-finding issues open; zero true orphans).

**What's good:**
- Frontmatter valid — `name` and `description` both present; description is 524 chars (well within the 1024 limit).
- Description is specific and trigger-rich (mentions "5-Why", "root cause method", "problem tree", 8-tab xlsx output) — good activation surface.
- Archive is complete: SKILL.md + example input JSON + generate/recalc/office scripts.
- Reviewer pairing confirmed: `5-why-checklist-reviewer` exists and references the 5why workbook consistently.

**What to fix:**
- (med) No `examples/5-why-builder/README.md` existed — FIXED this run by adding the 5-line stub per repo convention.
- (low) SKILL.md body ends with a stray trailing `---` (dangling horizontal rule after the last paragraph). Cosmetic only; left as-is this run because editing requires repackaging the .skill zip and the risk outweighs the benefit for a non-functional artifact. Captured as a follow-up.

**Suggested edits (future):**
- Drop the trailing `---` in SKILL.md on the next pass that already needs to repackage the archive.
- Consider naming the output convention explicitly in SKILL.md (e.g. `<problem>-5why.xlsx`) to match sibling builders' docs.

**Severity:** low–med (one shipped doc fix; one cosmetic follow-up).
