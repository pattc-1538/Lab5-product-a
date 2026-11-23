# Project Overview

> The management view of the project: contract, organization, way of working and constraints.
> The service/product view (background, problems, objectives) lives in
> `project/02_requirements/system-overview.md` and is owned by `pm-gather-requirements` (REQ).

## 1. Basic Information

| Item | Value |
| --- | --- |
| Project name | Product A — Sakura Bay Fish Market operations system（さくら湾水産市場 業務支援システム） |
| Project code | product-a |
| Client name | Sakura Bay Fish Market JSC (fictional) |
| Contract type | Fixed-price per phase: ① requirements definition fixed-price (18 MD); ② design through ④ testing & go-live quoted as fixed-price after ① is complete |
| Contract period | 2026-12-01 – 2027-05-31 (go-live 2027-05-17 + 2 weeks of hypercare) |
| Project type | New build (current operations are fully manual: phone, fax, handwritten ledgers) |

## 2. KPI & Success Criteria

| KPI | Target | How it is measured | Measured by |
| --- | --- | --- | --- |
| Trades breaching the 業務規程 recorded without an approved exception | 0 cases | Audit log review over the 3-week UAT parallel run | Sun* (report), client (confirm) |
| Difference between system and manual calculation of 仕切, receivables and 完納奨励金 | ¥0 on the agreed test cases | Reconciliation during IT/ST and the UAT parallel run (NFR-005) | Sun* (IT/ST), client (UAT) |
| Share of the day's trades recorded in the system on the same day | 100% | Comparison of paper ledgers with the system during the parallel run | Client |

**Success criteria**: The system goes live on 2027-05-17. After the 3-week parallel run, the market retires the paper ledgers and uses the system as the single source for trades, 仕切, receivables and 完納奨励金, with every trade checked against the 業務規程 permissions.

## 3. Way of Working

| Item | Value |
| --- | --- |
| Development method | Waterfall in 4 phases: ① requirements definition → ② design & foundation → ③ development → ④ testing & go-live |
| Sprint length | — (not agile) |
| Communication channels | Slack (day to day) + weekly progress meeting on Google Meet |
| Ticket management tool | GitHub Issues (pattc-1538/Lab2-product-a) |
| Language of deliverables | Japanese |

## 4. Scope & Role Split

| Work item | Performed by | Notes |
| --- | --- | --- |
| Requirements definition | Joint (Sun* leads) | Fixed-price phase ①. The client provides the full 業務規程 and answers the Q&A; Sun* writes the 要件定義書 and screen list; the client approves (M-02) |
| Basic design | Sun* | Incl. environments and the login/permission base |
| Development & implementation | Sun* | 13 functions F-001–F-013 |
| UT / IT | Sun* | |
| ST | Sun* | Incl. reconciliation against manual calculation (NFR-005) |
| UAT | Client (Sun* supports) | 3-week parallel run with the paper ledgers. The client provides the acceptance criteria and makes the acceptance decision |
| Production infrastructure setup | Sun* (on the client's accounts) | Vercel and Supabase accounts are held in the client's name and paid by the client; Sun* is granted access to set them up |
| Data migration | Joint | Master data only (participants, shippers, items, 業務規程 values): the client supplies the data from the paper ledgers, Sun* imports it. Migration of past trade data is out of scope |
| Operation & maintenance | Sun* (hypercare only) | 2 weeks of hypercare after go-live are in scope. Ongoing maintenance (about 2 person-days/month) is a separate contract, settled after phase ① |

> Express what Sun\* does **not** handle in the "Performed by" column. Do not add a separate
> "out of scope" subheading.

## 5. Constraints

| Category | Constraint |
| --- | --- |
| Technical | Next.js / Vercel / Supabase, the same stack as the prototype. Floor screens run on tablets. The port-side network may be unstable, so a paper fallback with later back-entry is required (NFR-003). Assumes one market with one 卸売業者 (Q-20; several wholesalers = scenario S2, +16 MD) |
| Budget & resources | Fixed price: phase ① 18 MD; whole project most likely 177 MD (optimistic 146 / pessimistic 200, v2 estimate). Running cost about USD 45/month for Vercel and Supabase, paid by the client |
| Schedule | Go-live 2027-05-17, outside the Japanese Golden Week. The price of phases ②–④ is fixed only after phase ① is complete |
| Other | The full text of the market's 業務規程 has not been received yet. A change to a number in the 業務規程 is a parameter change; a change to the structure of a rule is a software change handled as a change request |

## 6. Requirements to Uphold (D/C/Q/S)

| Category | Memo |
| --- | --- |
| Delivery (D) | Go-live on 2027-05-17 after a 3-week parallel run; the date avoids the Golden Week and needs the 業務規程 values before data migration |
| Cost (C) | Stay within the fixed price per phase (177 MD most likely); named risks are covered by the 23 MD pessimistic margin |
| Quality (Q) | Highest priority: money calculations must match manual calculation to the yen, and every trade must be checked against the 業務規程 permissions |
| Scope (S) | 13 functions as proposed; anything beyond (electronic auction, buyer login, several wholesalers, accounting/bank integration, photos of hand-marks, etc.) goes through a change request |

**Trade-off allocation (14 pts total)**: D = 4 / C = 3 / Q = 5 / S = 2 (confirmed by the PM on 2026-11-23)

## 7. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-23 | pm-plan-project skill | Created; §1–§6 filled from the LAB-1 v2 proposal and the PLAN interview (Blocks A–F) |
