# Polish log — uds-services-builder.skill

## 2026-05-26 (autonomous POLISH run, W22 target #1 / issue #9, two-week carryover)

**Domain:** diagnostics · **Severity:** med · **Outcome:** small fix applied

### What's good
- SKILL.md cleanly structured: an Input JSON schema, a 13-tab Output contract
  enumerating service inventory / DID / RID / SecurityAccess / NRC / timing /
  memory layout, and a `python scripts/generate_uds.py input.json output.xlsx`
  Usage snippet. The 13-tab output mirrors what diagnostics teams actually
  hand to the OEM, so the workbook structure was already DoD-aligned before
  edits.
- Correctly scoped to ISO 14229-1 (protocol-neutral UDS), keeping the skill
  off ISO 14229-3 (CAN-TP) and ISO 14229-5 (DoIP) which would belong in
  separate skills.
- Inner zip is healthy: SKILL.md + `scripts/generate_uds.py` + `recalc.py` +
  a small `scripts/office/` helper package. No dead files.

### What to fix
1. **Trigger sentence was nearly empty (med).** The frontmatter `description`
   ended with the boilerplate "Use this skill when the user mentions uds
   services builder." — i.e. the classifier had nothing to match on except
   the literal skill name. UDS-relevant requests phrased with the actual
   vocabulary the field uses (DID catalog, SecurityAccess, NRC, P2/P2*/S3,
   programming session) were not going to route here reliably.
2. **No disambiguation against neighbour skills (med).** The repo also has
   `odx-builder`, `cdd-builder`, `dtc-catalog-builder` and `dem-config-builder`
   — all in the same broad neighbourhood. With a weak description the
   classifier could mis-route between them. Worth being explicit about who
   owns what.
3. **Service range and session names hidden in the body (low).** The 0x10-0x86
   range and the default / programming / extended session vocabulary appeared
   only in the body — surfacing them in the description gives the classifier
   harder anchors.

### Edits applied this run
- Rewrote the frontmatter `description` (now 953 chars, well under the 1024
  limit): expanded triggers to name DIDs, RIDs, SecurityAccess, NRC, the
  three session types, P2/P2*/S3 timing, the 0x10-0x86 service range, and
  three casual phrasings ('spec the diagnostics for this ECU', 'what DIDs
  does this ECU support', 'write up the UDS services'). Added an explicit
  sibling-skill redirect for ODX (odx-builder), CANdela (cdd-builder), DTC
  inventory (dtc-catalog-builder), and the AUTOSAR Dem runtime layer
  (dem-config-builder).
- Rewrote the `## Overview`-area body trigger sentence to match: same vocab,
  same sibling redirects, slightly shorter to avoid prose bloat.
- Body Inputs / Output / Usage sections left untouched — no refactor.

### Deferred (not done this run)
- The Output section currently flags `12. Validation Rules` as "Input
  validation and constraints" but doesn't say which constraints get checked —
  a one-line example would make the contract clearer. Cosmetic, low value,
  left for a future pass.
- Worth a symmetric pass on `uds-services-checklist-reviewer.skill` so the
  reviewer's description carries the same vocabulary; captured as a W23
  follow-up candidate.
- The Adaptive UDS / DoIP angle (ISO 14229-5) is not in scope for this skill
  and not in scope for this repo today — flag for product judgement, not for
  a polish pass.
