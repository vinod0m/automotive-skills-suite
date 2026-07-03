# aspice-gap-analysis-builder — Example

**What this skill produces:** An ASPICE gap analysis xlsx (10 tabs) that compares current process capability (from an assessment) against target capability levels — covering current state, target-state definition, per-process gap identification, severity classification (Show-stopper / Major / Minor), effort estimation, quick wins, and major initiatives to feed an improvement roadmap.

**Typical input shape:** The upstream assessment workbook (e.g. an `aspice-assessment-builder` output) plus a JSON per `scripts/generate_aspice_gap_analysis.py` giving, per in-scope process, the process ID/name, current CL (from the assessment), target CL, and target justification.

**Expected output:** `<project>-aspice-gap-analysis.xlsx` — multi-tab workbook where CL deltas and missing process attributes are enumerated per process, each gap carries a severity and effort estimate, and quick-wins vs major-initiatives tabs prioritize the remediation roadmap.

**Sample I/O:** Input an assessment showing SWE.1 at CL1 with a target of CL3 → Output `BrakeECU-aspice-gap-analysis.xlsx` listing the CL1→CL3 delta, the missing PA2.1/PA3.1 attributes, a Major severity, an effort estimate, and placement on the major-initiatives tab.

**Run:** Trigger by phrasing, e.g. "Do an ASPICE gap analysis to CL3 for the brake ECU software processes" — then `python scripts/generate_aspice_gap_analysis.py <assessment.xlsx> <input.json> <output.xlsx>`.

**Paired reviewer:** `aspice-gap-analysis-checklist-reviewer` — audits the gap inventory for target-CL justification, severity consistency, and effort/priority completeness.
