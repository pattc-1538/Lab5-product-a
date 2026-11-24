# Stakeholders

> Organization, approval flow and escalation. The `Assigned effort (capacity)` column in §2 is the input
> `pm-plan-schedule` (SCH) uses for date calculation.

## 1. Client Organization

| Role | Name | Affiliation | Contact | Authority |
| --- | --- | --- | --- | --- |
| Project owner | 佐藤 健一 (fictional) | 卸売業者, representative director | Slack | Final approval of scope/specification changes and of deliverable acceptance |
| Point of contact | 鈴木 美咲 (fictional) | 卸売業者, operations section | Slack | Day-to-day contact, first review of deliverables, coordination of UAT |
| Market rules owner | 高橋 誠 (fictional) | Market management office (開設者), operations chief | Slack | Provides and confirms the 業務規程 (permissions, fees, payment deadlines, 完納奨励金) |

## 2. Sun\* Organization

| Role | Name | Affiliation | Contact | Authority | Assigned effort (capacity) |
| --- | --- | --- | --- | --- | --- |
| PL / BrSE | Trần Thị Chăm Pa | Sun* Vietnam | Slack | Requirements, specifications, client bridging | 38 person-days total (BrSE) |
| PM | TBD | Sun* Vietnam | Slack | Schedule, cost, quality and escalation | 18 person-days total |
| Back-end developer | TBD | Sun* Vietnam | Slack | Implementation | 57 person-days total |
| Front-end developer | TBD | Sun* Vietnam | Slack | Implementation | 25 person-days total |
| QA | TBD | Sun* Vietnam | Slack | Test design and execution | 33 person-days total |
| Designer | TBD | Sun* Vietnam | Slack | UI design | 6 person-days total |

> The unit follows the contract type in `overview.md` §1: lab/SES = person-days per month;
> fixed-price = total assigned person-days for the project.

## 3. Decision-Making & Approval Flow

| Subject | Proposed by | Reviewed by | Approved by | Notes |
| --- | --- | --- | --- | --- |
| Scope / specification change | Sun* PL/BrSE | Client point of contact + Sun* PM | Client project owner | Changes to the 業務規程 rules are also confirmed by the market rules owner |
| Deliverable acceptance | Sun* PM | Client point of contact (5 business days) | Client project owner | Approval flow and 5-business-day review confirmed (QA-002) |

## 4. Escalation Flow

| Level | Trigger | Contact | Response time |
| --- | --- | --- | --- |
| 1 | An issue or delay within the team | Sun* PL/BrSE ↔ client point of contact | Within 1 business day |
| 2 | A delay or issue affecting a milestone | Sun* PM ↔ client project owner | Same business day |
| 3 | Contract-level impact (cost, scope, deadline) | Sun* division manager ↔ client executive | Within 2 business days |

## 5. Contact & Communication Channels

| Purpose | Channel | Frequency | Participants |
| --- | --- | --- | --- |
| Day-to-day contact | Slack | As needed | Client contact, Sun* PL/BrSE, PM |
| Regular progress meeting | Google Meet | Weekly | Client contact, Sun* PL/BrSE, PM |

> The same answer feeds "communication channels" and "ticket management tool" in `overview.md` §3.
> Never interview for it twice.

## 6. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-23 | pm-plan-project skill | Created: client organization roles, Sun* team (capacity from the v2 estimate, 177 MD), approval flow, escalation, channels |
| 2026-11-24 | project-manager | Client organization filled from QA-001 (fictional names); approval flow and escalation confirmed (QA-002) |
