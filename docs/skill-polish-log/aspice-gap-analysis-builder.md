# Polish Log — aspice-gap-analysis-builder

## 2026-07-02 (autonomous POLISH)

**Selected because:** least-recently-touched builder (last touched 2026-05-01) with no
existing polish-log entry; no open issues and no orphan builders this run.

**Smoke test:** `generate_aspice_gap_analysis.py IGNORED.xlsx examples/sample_gap_analysis_input.json out.xlsx`
→ exit 0, `{"status":"ok","tabs":10,"processes":2}`, workbook opens with all 10 expected
tabs (00_Title_Page … 09_References). Generation is healthy.

**What's good**
- Frontmatter well-formed (name + description present); description 514 chars (well under 1024).
- SKILL.md "Output (10 tabs)" table matches the 10 tabs the script emits, in order and by name.
- Sample input (`config`, `processes`, `gaps`) matches the keys the generator reads.
- Clean styling helpers, deterministic output, JSON status line for programmatic use.

**What to fix**
- **[med] The first CLI argument `<assessment.xlsx>` is required but never read.** The
  generator signature is `generate_gap_analysis(assessment_xlsx, input_json, output_xlsx)`
  and `main()` enforces `len(sys.argv) != 4`, yet `assessment_xlsx` is never opened. The
  smoke test above passed a nonexistent path and still succeeded, proving the arg is inert.
  Consequence: users must supply a file that is silently ignored; the Current State tab is
  actually built from the JSON `processes` array, not the assessment workbook.
- **[low] `load_workbook` is imported but unused** — a direct symptom of the dead
  assessment-read path.
- **[low] Doc/behavior mismatch:** SKILL.md tab 02 says "Read-only echo of assessment
  results," but Current State is populated from `data["processes"]` in the input JSON, not
  from the assessment xlsx.

**Suggested edits (deferred — not applied this run)**
Two coherent options, both cross-file and needing thought, so captured as follow-ups rather
than done blind:
  1. **Make it real:** load the assessment workbook and populate Current State (achieved CL
     per process) from it, keeping JSON for target definitions only. Update SKILL.md Step 1.
  2. **Make it honest:** drop the assessment arg (accept 3→2 positional args), remove the
     unused `load_workbook` import, and reword SKILL.md tab 02 + the usage line. Confirm the
     paired `aspice-gap-analysis-checklist-reviewer` does not probe for the assessment arg
     before changing the interface.

**Severity:** med (functional-interface inconsistency; output itself is valid).

**Applied this run:** none — behavior/interface change with doc + paired-reviewer coupling
is out of scope for a same-run safe edit. Logged only.
