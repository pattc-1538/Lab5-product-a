# Schedule

> The plan baseline. Actual progress against it is recorded in `progress.md` (owned by `pm-report-project`).
> Assumptions and constraints belong in `overview.md` — never write them here.
> **The WBS goes down to the Story level only.** Tasks live in `task-list.md` (owned by `pm-create-tasks`).

## 1. Master Schedule (by phase)

> One row per work item in `overview.md` §4. Client-side phases stay listed, so dependencies stay visible.
> `overview.md` does not exist yet (PLAN not run); the phase list below was confirmed with the PM in the SCH interview
> on 2026-11-23 and should be carried into `overview.md` §4 when PLAN runs.

| Phase | Performed by | Start date (planned) | End date (planned) | Main deliverables | Related milestone ID |
| --- | --- | --- | --- | --- | --- |
| Requirements definition (Discovery) | Joint | 2026-12-01 | 2026-12-22 | 要件定義書, screen list, settled 業務規程 / money rules, answered Q&A | M-01, M-02 |
| Basic design | Sun* | 2026-12-23 | 2027-01-08 | UI design (tablet floor screens + components), DB design, dev/stg/prod environments, login + 2-role permission base | M-03 |
| Development & unit testing | Sun* | 2027-01-11 | 2027-04-07 | Source code for F-001–F-013 with unit tests | M-04 |
| Integration & system testing | Sun* | 2027-04-08 | 2027-04-19 | IT/ST results, money-calculation reconciliation against manual calculation (NFR-005) | M-05 |
| Data migration | Joint | 2027-04-08 | 2027-04-12 | Initial master data imported from paper ledgers (CSV) | M-05 |
| Documentation & training | Sun* | 2027-04-15 | 2027-04-19 | Operations manual, paper fallback procedure for network outage, training session | M-05 |
| Acceptance testing (UAT) | Client (Sun* supports) | 2027-04-20 | 2027-05-14 | UAT results, parallel run with paper ledgers | M-06 |
| Production release | Sun* | 2027-05-17 | 2027-05-17 | Production deployment, backup configuration | M-07 |

## 2. Milestones

| M-ID | Milestone | Planned date | Completion condition | Related phase |
| --- | --- | --- | --- | --- |
| M-01 | Kickoff | 2026-12-01 | Kickoff meeting held; Q&A list (Q-01, Q-02, Q-03, Q-07 first) sent to the client | Requirements definition (Discovery) |
| M-02 | Requirements sign-off | 2026-12-22 | Client approves 要件定義書 and screen list after a 5-business-day review | Requirements definition (Discovery) |
| M-03 | Basic design complete | 2027-01-08 | UI design, DB design, environments and permission base ready | Basic design |
| M-04 | Development complete | 2027-04-07 | All 13 stories implemented and unit tested | Development & unit testing |
| M-05 | System test complete / UAT start | 2027-04-19 | IT/ST passed, money reconciliation matches, master data migrated, users trained | Integration & system testing |
| M-06 | UAT passed | 2027-05-14 | Client accepts after a 3-week parallel run with paper ledgers | Acceptance testing (UAT) |
| M-07 | Production go-live | 2027-05-17 | System live in production with backups configured | Production release |

## 3. WBS (Epic / Story)

> **Epic = function group, Story = function.** Never split an Epic by phase, and never add Task rows.
> Story IDs inherit their parent Epic (`E-01` → `E-01-S01`).

| WBS ID | Type | Name | Related F-ID | Start date (planned) | End date (planned) | Related milestone ID | Dependencies |
| --- | --- | --- | --- | --- | --- | --- | --- |
| E-01 | Epic | Master data (= FG-01) | | 2027-01-11 | 2027-01-28 | M-04 | Basic design complete (M-03) |
| E-01-S01 | Story | Participant management | F-001 | 2027-01-11 | 2027-01-15 | M-04 | |
| E-01-S02 | Story | Shipper management | F-002 | 2027-01-18 | 2027-01-18 | M-04 | |
| E-01-S03 | Story | Item master | F-003 | 2027-01-19 | 2027-01-19 | M-04 | |
| E-01-S04 | Story | 業務規程 parameter settings (fees, deadlines, 完納奨励金 rates, channel × tier permission matrix) | F-004 | 2027-01-20 | 2027-01-27 | M-04 | E-01-S01 |
| E-01-S05 | Story | User account management | F-005 | 2027-01-28 | 2027-01-28 | M-04 | |
| E-02 | Epic | Receiving (= FG-02) | | 2027-01-29 | 2027-02-03 | M-04 | E-01 |
| E-02-S01 | Story | Receiving & listing (上場) | F-006 | 2027-01-29 | 2027-02-03 | M-04 | E-01-S02, E-01-S03 |
| E-03 | Epic | Sales (= FG-03) | | 2027-02-15 | 2027-02-25 | M-04 | E-02 |
| E-03-S01 | Story | 相対取引 recording (includes the shared trade-permission check) | F-007 | 2027-02-15 | 2027-02-24 | M-04 | E-02-S01, E-01-S04 |
| E-03-S02 | Story | せり result recording | F-008 | 2027-02-25 | 2027-02-25 | M-04 | E-03-S01 (shared permission check) |
| E-04 | Epic | Settlement & receivables (= FG-04) | | 2027-02-26 | 2027-03-11 | M-04 | E-03 |
| E-04-S01 | Story | 仕切 (shipper settlement) | F-009 | 2027-02-26 | 2027-03-02 | M-04 | E-03-S01, E-03-S02 |
| E-04-S02 | Story | Receivables & payment recording | F-010 | 2027-03-03 | 2027-03-08 | M-04 | E-03-S01, E-03-S02 |
| E-04-S03 | Story | 完納奨励金 calculation | F-011 | 2027-03-09 | 2027-03-11 | M-04 | E-04-S02, E-01-S04 |
| E-05 | Epic | Inquiry & reporting (= FG-05) | | 2027-03-12 | 2027-03-16 | M-04 | E-03 |
| E-05-S01 | Story | Trade inquiry | F-012 | 2027-03-12 | 2027-03-12 | M-04 | E-03-S01, E-03-S02 |
| E-05-S02 | Story | Trade result reports | F-013 | 2027-03-15 | 2027-03-16 | M-04 | E-05-S01 |

**Cross-cutting notes**: Requirements, basic design (incl. environments and the login/permission base), IT/ST,
data migration, documentation & training, UAT and release are carried as §1 phase rows, not Epics. Project
management and BrSE bridging run across the whole period. Story dates come from the LAB-1 **v2** estimate shown to
the client (`output/product-a/product-a-estimate-261104-v2.json`, 177 MD most likely) with one full-time person per
role: each story lasts max(FE, BE) of its estimate lines and Epics run in sequence. Exceptions confirmed by the PM on
2026-11-23 from the story details: E-01-S01 = 5 days (licensing procedures), E-01-S04 = 6 days (license
requirements and license kind), E-02-S01 = 4 days (lot cancellation and freshness grades from the item master;
photos of hand-marks are out of scope as in the proposal). E-03-S01 = 8 days already includes the exception flow
(estimate line 5.1d). The 13 stories end on 2027-03-16; **2027-03-17…04-07 (15 working days) is schedule buffer**
inside the development phase, so the milestones M-04…M-07 shown to the client stay unchanged. Basic design needs
about 11 BE days against a 9-day window: project setup and environments (estimate line 2.2, 2 BE days) start in the
last days of the requirements phase, as they do not depend on the requirements.
Sun* days exclude 2026-12-29…2027-01-03, 2027-02-04…2027-02-12, 2027-04-30 and 2027-05-01; UAT (client)
excludes the Japanese holidays 2027-04-29 and 2027-05-03…05-05; the release day is a working day in both
countries. Hùng Kings' Day 2027 (around 2027-04-16) is not yet excluded and must be confirmed. F-013 scope is
still pending customer confirmation. Additions found while writing the story details and absorbed by the buffer
(checked on 2026-11-23, story dates unchanged): invoices in E-04-S02 (about 0.5 day) and past-lot inquiry
in E-05-S01 (about 0.5 day), 1 working day in total against the 15-day buffer.

## 4. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-23 | pm-plan-schedule skill | Created (Case A): 8 phases, 7 milestones, 5 Epics / 13 Stories from function-list F-001–F-013 |
| 2026-11-23 | pm-plan-schedule skill | Re-planned: E-01-S01 2→5 days and E-01-S04 7→9 days (scope added in story details); development end and later phases shifted by 5 working days; M-04 2027-04-07, M-05 2027-04-19, M-06 2027-05-14, M-07 2027-05-17 (moved out of Golden Week); Vietnamese 04-30/05-01 and Japanese GW holidays excluded |
| 2026-11-23 | pm-plan-schedule skill | Re-based on the v2 estimate (177 MD) shown to the client: development stories now take 40 working days (was 56) and end on 2027-03-16; the remaining 15 working days to M-04 are buffer, so M-04…M-07 are unchanged. E-01-S04 6 days, E-03-S01 8 days (incl. exception flow 5.1d), E-02-S01 4 days without photos. Project setup (2.2) starts at the end of the requirements phase |
| 2026-11-23 | pm-plan-schedule skill | Buffer check: about 1 working day of additions from the story details (E-04-S02 invoices, E-05-S01 past-lot inquiry) is absorbed by the 15-day buffer; dates and milestones unchanged |
