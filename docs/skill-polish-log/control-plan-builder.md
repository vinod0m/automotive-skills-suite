# Polish log — control-plan-builder

## 2026-06-18 (W25 POLISH, first pass)

**Tracking issue:** none open (issue tracker empty this run; selected via priority chain)
**Mode:** POLISH · **Severity:** low (one cosmetic factual fix applied)
**In-place fix applied:** yes — sample-size figure corrected (see below)

### Selection rationale
No open issues exist, so selection fell through the priority chain to
"least-recently-touched builder." A large group of builders is tied at the
2026-05-01 baseline. The tie was broken toward `control-plan-builder` because it
is one of this week's stated PLAN targets (W24 recap: "control-plan") and had not
yet received a documented quality pass, making it the most defensible non-random
pick among the tied set.

### What's good
- **Frontmatter is valid and complete.** Required fields `name` and `description`
  are both present; `description` is 601 chars, comfortably under the 1024-char
  ceiling. The trigger phrasing ("Control Plan, AIAG control plan, production
  control document, or manufacturing process control") is concrete and unambiguous.
- **Generator runs clean and matches its contract.** `scripts/generate_control_plan.py`
  executed against `examples/sample_control_plan_input_esc.json` produces a valid
  13-tab workbook; tab names match the schema docstring (`00_Title_Page` …
  `12_References`) exactly, and the in-body "Output structure (13 tabs)" table
  agrees row-for-row.
- **Schema/example/generator are aligned.** The example input exposes
  `[process_steps, characteristics, gages, reaction_plans, spc_settings,
  mistake_proofing]` and the generator consumes each. No orphan fields.
- **Color-coding and taxonomy are internally consistent.** Critical=Red,
  Significant=Orange, Standard=Light-yellow is stated identically in the "Color
  coding" section and implemented in the style constants (`RED`, `ORANGE`,
  `LIGHT_YELLOW`). The control-method taxonomy in the body matches
  `references/control_method_taxonomy.md`.

### What to fix
- **[APPLIED] Sample-count mismatch (cosmetic, factual).** The "Sample Control Plan"
  section claimed the ESC ECU example has "8 process steps and **18** characteristics."
  The actual `sample_control_plan_input_esc.json` contains 8 process steps and
  **15** characteristics (confirmed by both direct JSON count and the generator's
  own run summary: `"characteristics": 15`). Corrected "18" -> "15" in SKILL.md and
  re-zipped the `.skill`. Regenerated the workbook from the patched archive to
  confirm nothing broke.

### Suggested (non-blocking) edits for a future pass
- **Illustrative special-class examples vs. counts.** The narrative names Critical
  (placement, solder), Significant (FCT, firmware), Standard (label) as exemplars,
  while the generator reports the full sample as critical=7 / significant=6 /
  standard=2. The prose is clearly illustrative, not a tally, so it was left as-is;
  a future pass could add "(exemplars)" to remove any chance of misreading.
- **`mistake_proofing` sample depth.** The example carries a single poka-yoke entry.
  Adding one more would exercise the Mistake-Proofing Catalog tab more fully for
  demo purposes — content judgement, not a fix.

### Rationale for the in-place change
The "18 -> 15" edit qualifies as a small, obvious, unambiguous factual fix: the
number is mechanically verifiable against the shipped example and was simply wrong.
That is exactly the class of change POLISH permits in-place. All other observations
are content-judgement calls and were logged, not applied.

### Net assessment
Healthy skill, now factually consistent with its own sample. The 🟡 staleness flag
in STATUS.md is date-based, not quality-based — the file had not been edited since
the 2026-05-01 baseline. This review gives the quality domain a documented pass and
clears the W24/W25 control-plan target.
