# Reviewer Pairing Aliases (canonical registry)

The STATUS.md pairing check expects `<base>-checklist-reviewer.skill` (or `<base>-reviewer.skill`)
for every `<base>-builder.skill`. Two reviewer files use a shortened base and are **canonically
paired by alias** rather than by filename convention:

| Builder | Paired Reviewer (alias) | Rationale |
|---|---|---|
| `item-definition-builder.skill` | `item-def-checklist-reviewer.skill` | Reviewer shipped with shortened base `item-def`; internal frontmatter `name: item-def-checklist-reviewer` and external references (examples/, docs/) already use this name. Renaming would break the zip's internal directory name and any installed copies. |
| `ppap-package-builder.skill` | `ppap-checklist-reviewer.skill` | Reviewer covers the whole PPAP package under the shorter base `ppap`; same rename blast-radius argument applies. |

**Decision (2026-07-08, autonomous run, per issue #38 "rename or document alias"):** the alias path
is adopted as canonical. Any STATUS regeneration MUST honor this table. Do not rename these files
without a human decision — a rename requires repacking the .skill zip (internal directory +
frontmatter `name:`) and updating all external references, and would orphan installed copies.

New alias entries require a matching row here in the same commit that introduces the pairing.
