# Polish log — dfmea-builder.skill

## 2026-05-27 (W22 #5 POLISH pass)

**Mode:** read-only review (no edits to .skill applied)
**Tracker:** issue #12

### What's good

- **Frontmatter clean.** `name` and `description` both present; description is 672 chars
  (well under the 1024 hard cap, plenty of headroom for future trigger phrasings).
- **Description trigger surface is broad and concrete.** Covers the exact deliverable
  (AIAG-VDA 2019 Design FMEA workbook), the methodology distinction (7-step process,
  Action Priority lookup, NOT RPN multiplication), the visible outputs (12-tab xlsx,
  color-coded AP cells), and a "use this instead of freeform" assertion. Should fire
  reliably on "DFMEA", "Design FMEA", "AIAG-VDA", and adjacent phrasings.
- **AIAG-VDA 2019 alignment is correct.** The replacement of classical RPN by the
  Action Priority lookup is the headline change in the 2019 harmonized edition, and
  the SKILL.md flags it prominently in both the description and the body.
- **Body is well-structured.** Clear "When to use" list, JSON input example, 7-step
  walkthrough mapped to specific tabs, scripts invocation, analyst review checklist,
  output structure table (tabs 00–11), AP formula spelled out, common pitfalls.
- **Bundled references are appropriate.** Severity / Occurrence / Detection tables
  plus the AP lookup table plus a methodology doc — exactly the AIAG-VDA reference
  set an analyst would expect to consult while filling out the worksheet.
- **Examples directory has a realistic seed.** `sample_dfmea_input_esc.json` (ESC ECU)
  matches the example file path referenced in the SKILL.md body — no broken link.

### What to fix

Nothing critical. A few low-priority polish items noted for a future pass (NOT
applied this run per the "small and shipped" rule):

- **Description could optionally add casual trigger phrasings** in the style of
  fsc-builder and hara-builder (e.g., "even casual phrasings like 'I need a design
  FMEA for this ECU' or 'analyze the failure modes of my design'"). Current
  description trips on the literal terms but a casual phrase like "what could go
  wrong with this design" might miss. Low priority — most real users will say DFMEA
  explicitly. Defer.
- **AP rule in body is a simplified prose summary**, not the full AIAG-VDA Table P.1.
  The bundled `references/action_priority_table.md` carries the authoritative table,
  so this is acceptable — the body is teaching intuition, not the contract. No fix.
- **"Lessons Learned cross-reference" in description vs "Lessons Learned & Crossref"
  in the tab listing** — a minor naming inconsistency but both phrasings convey the
  same concept and the description form reads more naturally in prose. Defer.

### Severity

**Low.** No blocking issues; no required frontmatter missing; no description
overflow; no broken file references; no methodology errors. Skill is in
production-ready shape. Re-touch only if a downstream classifier flags a miss
on the casual-phrase trigger surface.

### Suggested edits

None applied this pass. If a future pass wants to extend the description with
casual triggers, it must stay under 1024 chars total (currently 672, so ~350 chars
of headroom remain).
