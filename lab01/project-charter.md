# Project charter: Realtime Quiz platform

| Field   | Value                            |
| ------- | -------------------------------- |
| Version | 1.0 (draft for sponsor approval) |
| Date    | 2026-09-29                       |
| Sponsor | Head of the IT department        |
| PM      | Supervising Lecturer             |

## 1. Purpose and justification

Currently, instructors in the IT department face high manual grading workloads and lack an interactive mechanism for real-time student evaluation during lectures. The Realtime Quiz platform is an internal web application that allows lecturers to create multiple-choice quizzes and host live timed sessions with instant leaderboard and feedback updates over WebSocket. Students participate simultaneously via a simple 6-character access code on their mobile or laptop browsers without friction. This initiative eliminates tedious manual marking, boosts active classroom participation, and ensures full departmental ownership of student data. A complete financial and operational justification is provided in business-case.md.

## 2. Objectives and success criteria

| #   | Objective (what will be true)                                     | Success criterion (number + week)                                      |
| --- | ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| O1  | Deliver core MVP functionality for authoring and live quizzing    | 100% of Must features operational with 0 blocking defects by week 7    |
| O2  | Conduct a live pilot session in a real lecture environment        | 50 active student participants completing the quiz session by week 14  |
| O3  | Maintain responsive real-time broadcast delivery during sessions  | Broadcast latency <= 500 ms at 95th percentile measured in week 14     |
| O4  | Support high concurrent session capacity on target VPS resources  | 20 concurrent sessions of 100 participants on 2 vCPU / 2 GB by week 12 |
| O5  | Maintain rigorous code quality and automated testing standards    | Automated line coverage >= 80% with green CI on all merges by week 13  |

## 3. High-level scope

In scope:
- User authentication and role management module (instructor, student, and guest access)
- Quiz authoring web interface for creating and configuring multiple-choice questions
- Real-time session execution engine with authoritative server-side countdown timers
- Instant scoring calculation engine and real-time live leaderboard broadcast
- Session analytics dashboard and report export module generating CSV and PDF formats
- Real-time notification system for quiz events and question transitions

Out of scope:
- Native mobile applications for iOS or Android platforms
- Open-ended and free-text question formats (only multiple choice supported)
- Built-in live audio or video streaming and conferencing features
- Direct bidirectional LMS gradebook integration and synchronization
- Multi-node distributed clustering and multi-server scaling architecture

## 4. Milestones

| Week | Milestone                                              | Ends process group |
| ---- | ------------------------------------------------------ | ------------------ |
| 1    | Charter approved, team formed                          | Initiating         |
| 4    | Quiz authoring and account management completed        | Executing          |
| 6    | Live session core and WebSocket communication verified | Executing          |
| 7    | MVP demo (all Must features demonstrated live)         | Executing          |
| 10   | Analytics dashboard and results export completed       | Executing          |
| 12   | Testing, hardening, and 100-user load test green       | Executing          |
| 14   | Pilot with 50 students, closure                        | Closing            |

## 5. Budget summary

Effort:
- Student developers: 4 students x 14 weeks x 8 h/week = 448 h
- Project manager: 1 PM x 14 weeks x 3 h/week = 42 h
- Total effort: 490 h

Cash:
- Linode VPS hosting: 4 months x 25 USD = 100 USD
- Custom domain registration: 15 USD
- Development & deployment testing tools: 60 USD
- Contingency reserve: 25 USD (14.3% of base cash expenses)
- Total cash budget: 200 USD

## 6. Assumptions

- All 4 student team members contribute 8 hours per week consistently across the 14-week semester.
- Campus Wi-Fi and network infrastructure allow WebSocket traffic or reliably support the SockJS fallback mechanism.
- The Linode VPS hosting environment at gicitc.com remains available with continuous network connectivity.
- The supervising lecturer is available for 3 hours each week for architectural guidance, progress reviews, and phase gate decisions.

## 7. Constraints

- Strict project duration: The project must complete within exactly 14 weeks starting 2026-09-29.
- Hard cash budget cap: Total financial expenditure cannot exceed 200 USD under any circumstances.
- Data governance: All student assessment records must remain within the internal database and campus-controlled hosting without external third-party storage.
- Single-node hardware constraint: The software must operate reliably on a single virtual server instance with 2 vCPU and 2 GB RAM.

## 8. High-level risks

- Campus network proxy blocking WebSocket connections (mitigated by configuring STOMP with SockJS fallback).
- Timer synchronization drift between student browsers and the server (mitigated by authoritative server timestamp validation under 200 ms drift).
- Feature scope creep impacting MVP completion (mitigated by strict feature freeze on Could/Should items until the week 7 MVP demo passes).

## 9. Project manager authority

- The PM has authority to reassign tasks among team members, select internal libraries, and adjust work schedules within the 490 person-hour allocation and 200 USD cash limit.
- Any change to the project scope (especially Must features), milestone delivery dates (MVP demo in week 7 or pilot in week 14), or request for budget expansion beyond 200 USD requires formal written approval from the Sponsor.

## 10. Approval

Sponsor: Head of the IT Department  Date: 2026-09-29  
PM:      Supervising Lecturer       Date: 2026-09-29  
