# fmeda-builder — Example

**What this skill produces:** An ISO 26262-5 Hardware Safety Analysis (FMEDA) xlsx enumerating failure modes per HW element, allocating safety mechanisms from the upstream TSC, applying diagnostic coverage percentages, and deriving formula-driven hardware safety metrics (SPFM, LFM, PMHF) with auto-verification against per-ASIL thresholds.

**Typical input shape:** Upstream TSC xlsx (from `tsc-builder`) for safety-mechanism allocations plus a HW Bill of Materials JSON listing components with base failure rates (FIT), package-level grouping, and safety-relevant classification (safety-related vs QM).

**Expected output:** `<item>-fmeda.xlsx` — multi-tab workbook (Title, Element Catalog, FMEDA Worksheet with editable DC%, SPFM, LFM, PMHF, Dashboard, ASIL Targets, Traceability) where SUMIF + IF formulas propagate DC% and base-rate edits straight into the SPFM/LFM/PMHF metric tabs and Pass/Fail flags against the ASIL target row.

**Sample I/O:** Input a TSC stub for an EPB controller + 64-row HW BOM JSON → Output `EPB-fmeda.xlsx` with 184 failure modes enumerated, SPFM = 99.2% (ASIL D target ≥ 99%, PASS), LFM = 90.4% (ASIL D target ≥ 90%, PASS), PMHF = 8.7 FIT (ASIL D target < 10 FIT, PASS).

**Run:** Trigger by phrasing, e.g. "Build the FMEDA for the EPB controller from the TSC and BOM".
