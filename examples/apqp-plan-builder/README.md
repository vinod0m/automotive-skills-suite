# apqp-plan-builder — Example

**What this skill produces:** An audit-ready AIAG APQP 5-phase Master Plan xlsx (15 tabs) covering program definition, the cross-functional team, all five APQP phases (Plan & Define, Product Design, Process Design, Product & Process Validation, Feedback & Assessment) with standard deliverable checklists, phase gate reviews, special/critical characteristics, a risk register, open items, and schedule — per IATF 16949 supplier requirements.

**Typical input shape:** A JSON conforming to `scripts/generate_apqp_plan.py`. Mandatory fields are `program.name` and `program.customer`; optional blocks cover part number and vehicle program, supplier and key dates (SOP/EOP/peak volume), team roles and phase ownership, deliverable overrides, milestones, gate reviews, special characteristics (SC/CC), risks, and open items. Omitted fields auto-populate AIAG-standard defaults.

**Expected output:** `<program>-apqp-plan.xlsx` — multi-tab workbook where each of the five phases carries its deliverables with owner and status, gate reviews list exit criteria, and the special-characteristics, risk, and schedule tabs are cross-linked to the program definition.

**Sample I/O:** Input `program.name = "ESC Control Module APQP"`, `customer = "Phoenix Motors"`, part `WS-4521-A` on the Falcon XLT 2027 → Output `ESC-Control-Module-apqp-plan.xlsx` with the five AIAG phases populated, five gate reviews, an SC/CC tab, and a risk register seeded with capacity/design/schedule items.

**Run:** Trigger by phrasing, e.g. "Build an APQP master plan for the ESC control module program" — then `python scripts/generate_apqp_plan.py <input.json> <output.xlsx>`.

**Paired reviewer:** `apqp-plan-checklist-reviewer` — audits the workbook against the AIAG APQP Manual and IATF 16949 for deliverable completeness, gate-review coverage, and characteristic traceability.
