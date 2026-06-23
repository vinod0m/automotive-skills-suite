# 5-why-builder — Example

**What this skill produces:** An audit-ready 5-Why root cause analysis xlsx (8 tabs) covering the problem definition, a hierarchical 5-Why tree with multiple cause branches, consolidated root causes with supporting evidence, a corrective action per root cause (owner / due date / verification), and a post-action effectiveness check — with formula-driven status tracking.

**Typical input shape:** A measurable problem statement, the why-chain branches (Why 1 → Why 5, multiple branches allowed), candidate root causes with evidence, and corrective actions with owners and due dates.

**Expected output:** `<problem>-5why.xlsx` — multi-tab workbook with the problem-definition tab, the branching 5-Why tree, root causes cross-referenced to evidence, a corrective-action tracker, and a verification tab (baseline / target / actual).

**Sample I/O:** Input "Coolant leak at fitting on 3 field units" with two why-branches → Output `Coolant-Leak-5why.xlsx` with a 2-branch tree resolving to 2 root causes (under-torqued fitting; missing torque-audit step), each with a corrective action and an effectiveness-verification row.

**Run:** Trigger by phrasing, e.g. "Do a 5-Why root cause analysis on the coolant leak".

**Paired reviewer:** `5-why-checklist-reviewer` — audits this workbook (run `python scripts/generate_checklist.py <5why.xlsx> <output_checklist.xlsx>`).
