# Post-mortem: CampusPay Wallet IT Project Failure

## 1. Timeline and sources

| # | When | Event | Source |
|---|------|-------|--------|
| 1 | Month 1 | University requests IT unit to build cashless payment app for canteen and library fines in one semester; Head of Finance agrees to sponsor via email without a formal charter. | Fictional case from Lab-01 instruction |
| 2 | Month 2 | Lead developer acts as dual PM and primary programmer; no formal project plan or requirement baseline is established. | Fictional case from Lab-01 instruction |
| 3 | Month 3 | IT conducts student survey; requirements expand uncontrollably to include campus bus tickets and parking payments without schedule or budget adjustments. | Fictional case from Lab-01 instruction |
| 4 | Month 4 | Development rushes to meet the arbitrary September launch date; unit testing is minimal and real physical card terminal integration testing is omitted. | Fictional case from Lab-01 instruction |
| 5 | Day 1 (Launch) | App launches campus-wide; canteen card terminals reject 40% of payment attempts immediately. | Fictional case from Lab-01 instruction |
| 6 | Days 2–3 | Canteen queues double across campus; system experiences severe operational disruptions; app is abruptly withdrawn after three days. | Fictional case from Lab-01 instruction |
| 7 | Month 9 (+5 months) | App relaunches after extensive redesign, stripped back down to original canteen payment scope only. | Fictional case from Lab-01 instruction |

## 2. Classification and organisation

- **Classification:** Started as a standalone **project** (temporary, targeted deliverable: cashless campus payments). However, uncontrolled expansion into transportation, ticketing, and parking transformed it into an uncoordinated **programme** of distinct initiatives without the necessary programme management structure, coordinated architecture, or oversight.
- **Structure and PM authority:** The organization operated under a **weak functional structure**. The project manager had virtually zero real authority, was compromised by dual roles (acting simultaneously as lead developer and PM), and had no mandate to refuse sponsor or stakeholder feature additions.
- **Sponsor, charter, PMO:** No formal signed project charter was ever authorized. The Head of Finance acted as a "phantom sponsor" (granting superficial email consent but attending zero reviews or steering gates). There was no PMO or governance committee to monitor delivery health.

## 3. Success criteria

- **Stated criteria:** The sole stated criterion was "launch in September"—a calendar deadline completely devoid of functional, performance, or quality metrics.
- **Missing measurable criteria:**
  - Transaction success rate: >= 99.5% payment authorization success on physical terminals.
  - Checkout response latency: Transaction processing completed in <= 2.0 seconds.
  - Concurrency throughput: Support for peak lunch-hour transaction volumes (e.g., 20 simultaneous transactions/minute/canteen).
- **Ignored wider dimensions:**
  - *Operations:* Canteen cashiers and terminal operators were never trained or consulted on hardware failure modes.
  - *Users:* Students were stranded at checkout counters with unusable wallets and doubled wait times.
  - *Business benefits:* Expected cost savings in cash handling turned into immediate brand embarrassment and customer dissatisfaction.
  - *Team:* The lead developer suffered extreme burnout attempting to single-handedly code features without QA support.

## 4. Process groups and knowledge areas

| Process group | What went wrong or was skipped |
|---|---|
| Initiating | No project charter or formal stakeholder identification took place; executive sponsorship remained informal without accountability. |
| Planning | Scope management plans, WBS, and risk assessments were omitted; hardware integration test plans were never drafted. |
| Executing | Development prioritized implementing superficial survey features over validating core transaction workflows with physical POS hardware. |
| Monitoring and controlling | Progress was tracked purely by calendar dates without objective performance indicators; the team fell into the "invisibility trap." |
| Closing | No pilot deployment, verification gate, or rollback procedure existed; withdrawal was forced by operational chaos on launch day. |

**Knowledge areas most responsible:**
1. **Scope Management:** Uncontrolled scope creep occurred when survey suggestions (bus tickets and parking) were accepted directly into development without formal change control, impact analysis, or budget revisions.
2. **Quality Management:** Total failure of verification and validation; the software was deployed to production without running integration tests on physical card terminals or verifying transaction error handling.
3. **Stakeholder & Governance Management:** Absence of active executive sponsorship; the sponsor never attended progress reviews to establish project priorities, defend scope boundaries, or validate readiness.

## 5. Ethics

- **Decision examined:** Releasing the CampusPay application campus-wide to students on September 1 despite knowing that physical terminal hardware integration had never been validated in a realistic operating environment.
- **Evaluation against PMI Code of Ethics:**
  - *Responsibility:* Violated. The team prioritized meeting a calendar deadline over their professional obligation to deliver a secure, functional, and reliable payment solution.
  - *Respect:* Violated. Disregarded the time and well-being of canteen staff and students who depended on the system for daily meals.
  - *Fairness:* Violated. Subjected students to financial distress and transaction failures after taking their money into digital accounts.
  - *Honesty:* Violated. Misrepresented project status as "ready for launch" to university administration while concealing that critical hardware verification was skipped.

## 6. What our project will do differently

| # | Commitment (We will ...) | Measured by | By week | Charter line |
|---|---|---|---|---|
| 1 | We will run a load test simulating 100 concurrent students over campus Wi-Fi before deploying to production | Load test report confirming 0 connection drops and broadcast latency <= 500 ms | Week 12 | Objective O4, Milestone Week 12 |
| 2 | We will hold a formally signed charter with a named sponsor who reviews and signs off on phase gates | Written signatures on charter and formal gate approval minutes | Week 1 | Milestone Week 1, Section 10 Approval |
| 3 | We will enforce an authoritative server countdown timer with active drift compensation | WebSocket clock synchronization drift maintained strictly under 200 ms | Week 14 | Objective O3, Section 8 High-Level Risks |
| 4 | We will freeze scope and reject all non-essential Could/Should features until the core MVP is proven | 100% of Must features demonstrated live with zero blocking defects | Week 7 | Objective O1, Milestone Week 7, Section 9 PM Authority |
| 5 | We will secure institutional student data privacy sign-off before conducting any live student testing | Approved data protection compliance memo signed by the Data Protection Officer | Week 13 | Milestone Week 14, Section 7 Constraints |
