# item-definition-builder — Example

**What this skill produces:** An audit-ready ISO 26262-3 Clause 5 Item Definition xlsx (11 tabs) capturing item scope and classification, function enumeration, the boundary diagram, external interfaces, operating modes, HW/SW/mechanical allocation, and initial assumptions — the foundation artifact that feeds the HARA.

**Typical input shape:** A JSON conforming to `scripts/generate_item_definition.py`. Mandatory fields are `item.name`, at least one entry in `functions`, and ideally `scope_description`; optional blocks cover non-functional requirements, boundary (in/out/adjacent), interfaces (counterpart, direction, data type, integrity protection), operating modes with entry/exit conditions, allocations, assumptions, and references. Omitted fields default to empty.

**Expected output:** `<item>-item-definition.xlsx` — multi-tab workbook where each tab maps directly to an ISO 26262-3 Clause 5 sub-clause, with functions, interfaces, and operating modes cross-referenced and an assumptions tab ready for HARA hand-off.

**Sample I/O:** Input `item.name = "Electronic Stability Control"` with functions (yaw control, brake intervention), boundary and sensor/actuator interfaces → Output `ESC-item-definition.xlsx` with an 11-tab structure, the function list flagged for criticality, and an assumptions tab seeding the downstream HARA.

**Run:** Trigger by phrasing, e.g. "Create the ISO 26262 item definition for the ESC" — then `python scripts/generate_item_definition.py <input.json> <output.xlsx>`.

**Paired reviewer:** `item-def-checklist-reviewer` — audits the workbook for scope/boundary consistency, interface completeness, and Clause 5 coverage before it feeds the HARA.
