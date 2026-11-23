# Definition of Done

> The criteria that decide whether this project can be closed, and the record of the closing judgement.
> §1 is filled in during initial setup; §4 only at closing.

## 1. Completion Criteria

| D-ID | Category | Criterion | Judgement method / evidence | Status | Handling | Reason | Approver | Approval date | Related ID | Update date |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| D-001 | Functional requirements | All 12 must functions meet the acceptance criteria in §9 of their story details (`project/01_management/stories/`) and pass the client's UAT | Story §9 checklist results in ST + UAT result report signed off by the client | not judged | | | | | F-001–F-012 | 2026-11-23 |
| D-002 | Functional requirements | F-013 (should) is delivered within the scope settled by QA-004, or its deferral to a later phase is approved | UAT result for E-05-S02, or an approved deferral record | not judged | | | | | F-013 | 2026-11-23 |
| D-003 | Non-functional requirements (quality & performance) | 仕切, receivables and 完納奨励金 match manual calculation with a ¥0 difference on the agreed test cases | Reconciliation sheets from IT/ST and the UAT parallel run (overview KPI #2) | not judged | | | | | NFR-005 | 2026-11-23 |
| D-004 | Non-functional requirements (quality & performance) | Security test passed: TLS on all traffic, hashed passwords, role-based access checked on screen and in the database, audit log of every change to trades and money | ST security test report | not judged | | | | | NFR-004 | 2026-11-23 |
| D-005 | Non-functional requirements (quality & performance) | Daily backup is configured and a restore test has passed before go-live; operations monitoring covers the early-morning session | Restore test record + monitoring setup checklist | not judged | | | | | NFR-002, NFR-007 | 2026-11-23 |
| D-006 | Non-functional requirements (quality & performance) | The paper fallback procedure for network outages, with later back-entry, is documented and rehearsed before go-live | Operations manual section + rehearsal record | not judged | | | | | NFR-003 | 2026-11-23 |
| D-007 | Non-functional requirements (quality & performance) | The client confirms compliance with 卸売市場法 and the market's 業務規程, and the handling of participants' personal data | Written confirmation from the client | not judged | | | | | NFR-006 | 2026-11-23 |
| D-008 | Non-functional requirements (quality & performance) | Main list and entry screens respond within about 3 s (target settled by QA-002) | Response-time measurement in ST | not judged | | | | | NFR-001 | 2026-11-23 |
| D-009 | Documents & deliverables | Phase ①: the 要件定義書 and screen list are approved by the client (M-02). Phases ②–④: screen, API and DB specifications, the full source code and the operations manual are delivered, in Japanese | Deliverables list with delivery dates + client approval record for phase ① | not judged | | | | | overview §1, §3 | 2026-11-23 |
| D-010 | Testing & acceptance | UT/IT/ST are completed by Sun* with a test result report; the client runs a 3-week UAT in parallel with the paper ledgers, no critical or major defects remain open, and the client accepts (M-06) | Test result report + UAT defect list + client acceptance | not judged | | | | | overview §4 | 2026-11-23 |
| D-011 | Testing & acceptance | During the parallel run, no trade breaching the 業務規程 is recorded without an approved exception, and 100% of the day's trades are recorded on the same day | Audit log review + paper ledger comparison (overview KPI #1, #3) | not judged | | | | | overview §2 | 2026-11-23 |
| D-012 | Operational transition & handover | Production runs on the client's Vercel and Supabase accounts with backups (M-07); master data is migrated; floor training for both roles is done; 2 weeks of hypercare are completed | Release record + migration check + training attendance + hypercare report | not judged | | | | | overview §4 | 2026-11-23 |
| D-013 | Contract & billing | The acceptance certificate for phase ① is received, and the acceptance certificate for phases ②–④ is received after hypercare; invoicing is complete | Acceptance certificates + issued invoices | not judged | | | | | overview §1 | 2026-11-23 |

## 2. Category Guidelines

| Category | What it covers | In scope? |
| --- | --- | --- |
| Functional requirements | Whether the functions in `function-list.md` are complete and accepted | yes |
| Non-functional requirements (quality & performance) | Whether the `non-function-list.md` targets are met | yes |
| Documents & deliverables | Whether the contracted deliverables have been handed over | yes |
| Testing & acceptance | Test completion and the client's acceptance | yes |
| Operational transition & handover | Handover to operations, manuals, training | yes — limited to the operations manual, training and 2 weeks of hypercare; ongoing maintenance is a separate contract (overview §4) |
| Contract & billing | Acceptance certificate, invoicing, contract closing | yes — fixed price per phase: an acceptance certificate per phase (overview §1) |

## 3. Status Definitions & the Flow for Unmet Criteria

> **Fixed definitions — never rewrite this section.** This skill applies them; changing them is out of scope.

**Statuses**: `not judged` / `met` / `partially met` / `not met`.

**Flow for unmet and partially met criteria**:

1. Propose the handling — **address and meet it** / **waive it (out of scope)** / **defer it to the next phase** — with the reason, as a draft needing confirmation.
2. Take it through the approver for that subject in `stakeholders.md` §3 and record the review and approval status.
3. Finalize status / handling / reason / approver / approval date / update date **only for approved rows**. Unapproved rows stay on hold as "awaiting approval".
4. When an important decision arises, prompt the user to record it in `decision.md` (never edit that file from here).

## 4. Overall Closing Judgement

| Item | Content |
| --- | --- |
| Overall achievement rate | <!-- met ÷ total; filled in at closing --> |
| Waived items | <!-- count --> |
| Deferred items | <!-- count --> |
| Final approver | |
| Approval date | |
| Overall comment | |

## 5. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-23 | pm-define-dod skill | Created (initial setup): 6 categories in scope, D-001–D-013 confirmed by the PM |
