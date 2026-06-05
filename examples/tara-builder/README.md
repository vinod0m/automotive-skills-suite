# tara-builder — Example

**What this skill produces:** An ISO/SAE 21434 Clause 15 Threat Analysis and Risk Assessment (TARA) xlsx with assumptions, asset inventory, STRIDE-coverage threat catalog, impact / feasibility analysis, risk-determination matrix, treatment decisions, and derived cybersecurity goals — audit-ready for ISO/SAE 21434 concept-phase work products and UN R155 type-approval evidence.

**Typical input shape:** Item definition (system identity, cybersecurity-relevant assets), threat scenarios per STRIDE category, impact ratings (safety / financial / operational / privacy), feasibility ratings (elapsed time, expertise, knowledge, window of opportunity, equipment), and an existing-controls inventory.

**Expected output:** `<item>-tara.xlsx` — multi-tab workbook (Assumptions, Assets, STRIDE Threat Catalog, Impact, Feasibility, Risk Matrix, Treatment, Derived CS Goals, Traceability) with risk value auto-computed from impact × feasibility lookup and CAL-level color coding.

**Sample I/O:** Input a body-control ECU asset list (12 assets) + 28 threat scenarios → Output `BCM-tara.xlsx` with 28 threats rated, 9 high-risk items flagged, and 6 cybersecurity goals derived for hand-off to `cs-goals-builder`.

**Run:** Trigger by phrasing, e.g. "Build a TARA for the body control module — 12 assets and 28 STRIDE threats".
