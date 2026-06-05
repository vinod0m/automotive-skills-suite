# cs-concept-builder — Example

**What this skill produces:** An ISO/SAE 21434 Cybersecurity Concept xlsx deriving Cybersecurity Requirements (CSRs) per cybersecurity goal across the six security properties (authentication, authorization, integrity, confidentiality, availability, non-repudiation), allocating Cybersecurity Assurance Level (CAL) per architectural element, and producing the Cybersecurity Implementation (CSI) hand-off table.

**Typical input shape:** Upstream CS Goals xlsx (from `cs-goals-builder`) plus a system block-diagram JSON listing architectural elements, trust boundaries, data flows, and asset classifications.

**Expected output:** `<item>-cs-concept.xlsx` — multi-tab workbook (CS Goals import, CSR Derivation tree per goal × property, CAL Allocation, Verification Method per CAL, CSI Hand-off, Traceability) with CSR-to-goal and CSR-to-element cross-references.

**Sample I/O:** Input CS Goals for a telematics ECU + block diagram (5 elements, 3 trust boundaries) → Output `Telematics-cs-concept.xlsx` with 24 CSRs derived across 6 properties, 5 elements at CAL 2–3, and 8 CSI hand-off rows.

**Run:** Trigger by phrasing, e.g. "Build the cybersecurity concept for the telematics ECU from the CS Goals workbook".
