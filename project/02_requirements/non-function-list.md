# Non-Functional Requirements

> Categories that do not apply to this project are marked **out of scope** with a reason rather than being
> filled in mechanically. Numeric targets are only written in once the user has approved them.
> Compatibility targets recorded here are authoritative for `pm-plan-test` (TEST) §3.1.

## 1. Requirements

| NFR-ID | Category | Requirement | Target value | Priority | How it is verified | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| NFR-001 | Performance | List and entry screens respond quickly enough for use on the sales floor | Within about 3 s (confirmed QA-002, 2026-11-24) | should | Measured during ST | |
| NFR-002 | Availability | The system is available during market hours, including the early-morning session | About 99% during market hours excluding planned maintenance; RPO 24 h (confirmed QA-002, 2026-11-24) | must | Operations monitoring | An outage mid-session stops sales |
| NFR-003 | Operability | A paper fallback procedure exists for network outages, with later back-entry into the system | Procedure documented and rehearsed before go-live | must | Review of the operations manual | Port-side network may be unstable |
| NFR-004 | Security | TLS for all traffic, hashed passwords, role-based access, audit log of every change to trades and money | — | must | Security test during ST | Money and settlement data |
| NFR-005 | Calculation accuracy | 仕切, receivables and 完納奨励金 follow the 業務規程 rounding rules and match manual calculation | Zero difference on the agreed test cases | must | Parallel-run comparison against manual results | |
| NFR-006 | Laws & regulations | Comply with 卸売市場法 and the market's 業務規程; handle participant personal data under the personal information protection law | — | must | Client-side legal confirmation | Whether a regulation applies is for the client to confirm |
| NFR-007 | Data management | Daily backup of all data | Trade data retained 7 years (confirmed QA-002, 2026-11-24) | must | Restore test before go-live | |

> All numeric targets were confirmed by the client in QA-002 (2026-11-24).

## 2. Out of Scope

| Category | Reason |
| --- | --- |
| Internationalization | Users are market staff in Japan; Japanese only |
| Scalability | A single mid-size market; no large-scale growth expected |

## 3. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-04 | pm-gather-requirements skill | Created NFR-001–NFR-007 (numeric targets as drafts pending QA-002) |
| 2026-11-24 | project-manager | NFR-001/002/007 targets confirmed (QA-002) |
