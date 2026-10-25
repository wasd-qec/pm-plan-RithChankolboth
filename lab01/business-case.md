# Business case: live quizzes for the IT department

## 1. Problem

Lecturers across the IT department currently spend excessive hours manually printing, distributing, marking, and recording paper-based multiple-choice quizzes. Furthermore, students receive feedback days or weeks after assessments, losing the educational benefit of timely reinforcement during lectures.

Assumptions:
- Number of lecturers conducting regular quizzes: 10 lecturers
- Manual marking time per lecturer per week: 1 hour
- Teaching weeks per academic year: 30 weeks
- Total manual grading time lost: 10 lecturers x 1 h/week x 30 weeks = 300 hours/year
- Notional value of academic time: 10 USD/hour (used to monetize teaching and development hours objectively)
- Annual cost of current manual grading: 300 h x 10 USD/h = 3,000 USD/year

## 2. Options

| Option | Description | One-off cost | Annual cost | Annual benefit |
|--------|-------------|--------------|-------------|----------------|
| A      | Do nothing (continue manual paper quizzes) | 0 USD | 0 USD | 0 USD |
| B      | Buy commercial SaaS licenses (Kahoot! EDU / Mentimeter) | 0 USD | 1,800 USD | 3,000 USD |
| C      | Build internal Realtime Quiz platform (charter budget) | 4,900 USD | 300 USD | 4,800 USD |

*Note on Option B pricing:* Standard educational tier assumed at 15 USD per lecturer per month (10 lecturers x 15 USD x 12 months = 1,800 USD/year), based on published benchmark academic pricing for commercial quiz software (Kahoot! 360 Edu, accessed October 2026).

*Note on Option C costs:* One-off effort includes 490 person-hours valued at 10 USD/hour = 4,900 USD. Annual cost represents Linode VPS hosting at 25 USD/month x 12 months = 300 USD/year. Annual benefit combines 3,000 USD/year marking time saved plus 1,800 USD/year commercial SaaS subscription fees avoided.

## 3. Comparison

| Option | Net annual benefit | Payback (years) | Sensitivity (6 lecturers) |
|--------|--------------------|-----------------|---------------------------|
| B      | 3,000 - 1,800 = 1,200 USD | 0.0 years (immediate) | Net benefit: 1,800 - 1,080 = 720 USD; Payback: 0.0 years |
| C      | 3,000 + 1,800 - 300 = 4,500 USD | 4,900 / 4,500 = 1.09 years | Net benefit: 1,800 + 1,080 - 300 = 2,580 USD; Payback: 4,900 / 2,580 = 1.90 years |

*Detailed cost lines, quantities, and spreadsheet formulas are provided in business-case.csv.*

## 4. Benefits not priced

- **Student pedagogical capstone value:** 4 undergraduate students obtain direct industry experience designing real-time WebSocket distributed applications, managing databases, and implementing automated CI/CD pipelines.
- **Institutional data sovereignty:** All student identities, scores, and assessment records remain strictly inside university-controlled VPS and database environments, completely eliminating third-party FERPA/privacy liabilities.
- **No participant or session quotas:** The department can support arbitrarily large class cohorts without incurring commercial "per-seat" or "tier-upgrade" penalties.
- **Permanent asset ownership:** The system becomes an internal digital asset that can be continuously customized, extended, and integrated into departmental workflows in subsequent years.

## 5. Risks per option

### Option A: Do nothing
1. **Prolonged faculty inefficiency:** Continued waste of 300 lecturer hours annually on repetitive grading tasks.
2. **Suboptimal learning engagement:** Missed pedagogical opportunities for interactive, immediate feedback during critical classroom lectures.

### Option B: Buy commercial SaaS
1. **Recurring cost increases:** SaaS vendors frequently increase educational subscription rates or change plan boundaries after institutional lock-in.
2. **Student data governance risks:** Third-party cloud providers process and store university student data outside campus control.
3. **Participant caps:** Low-tier SaaS plans restrict maximum room capacity (e.g. 50-100 participants), preventing large multi-section combined quiz sessions.

### Option C: Build internal Realtime Quiz platform
1. **Technical delivery and integration risks:** WebSocket proxy blocking or clock synchronization drift could jeopardize real-time execution (mitigated by SockJS fallback and authoritative server timers).
2. **Schedule delay during development:** Student teams might fall behind schedule if scope creeps into non-essential features (mitigated by strict MVP gating in week 7).
3. **Operational maintenance handover:** Post-launch system updates require documentation and IT staff handover (mitigated by clear Docker Compose scripts and operational runbooks).

## 6. Recommendation and review gate

**Recommendation: Implement Option C (Build Realtime Quiz platform).**  
Option C offers an attractive net annual benefit of 4,500 USD and achieves full payback within 1.09 years (or 1.90 years even under conservative adoption of only 6 lecturers). Unlike Option B, Option C avoids endless recurring license fees, guarantees complete student data privacy on campus, and provides substantial educational capstone experience for the engineering students.

**Review Gate:**  
A formal phase gate will occur at the **Week 7 MVP Demonstration**. If the student team fails to demonstrate all core Must features (quiz authoring, live WebSocket synchronization, and instant scoring) with zero blocking defects by week 7, the project will immediately pivot to **Option B** (purchasing SaaS licenses for the following semester), and the student effort will be redirected to an exploratory research evaluation.
