# Function List

> The scope of what will be built. `pm-plan-schedule` (SCH) turns the function groups into WBS Epics and the
> functions into Stories, and writes the resulting story IDs back into "Related WBS ID".
> Per-function details (use cases, I/O, business rules) belong under `functions/` and are owned by the
> downstream `requirement-analysist` — leave "Detail document" blank or `TBD` here.

## 1. Function Groups

| FG-ID | Function group | Description |
| --- | --- | --- |
| FG-01 | Master data | Participants, shippers, items, 業務規程 parameters and user accounts |
| FG-02 | Receiving | Incoming catch from boats registered as lots for sale |
| FG-03 | Sales | Recording trades through the two channels, 相対取引 and せり, with a permission check |
| FG-04 | Settlement & receivables | 仕切 to shippers, buyer receivables and payments, 完納奨励金 |
| FG-05 | Inquiry & reporting | Looking up trades and producing required reports |

## 2. Functions

| F-ID | FG-ID | Function name | Summary | Priority | Target roles | Related WBS ID | Detail document |
| --- | --- | --- | --- | --- | --- | --- | --- |
| F-001 | FG-01 | Participant management | Register 仲卸 / 売買参加者 / 買出人 with their permission tier and approval status | must | ROLE-001 | E-01-S01 | TBD |
| F-002 | FG-01 | Shipper management | Register fishers / 漁協 who consign catch, for use in 仕切 | must | ROLE-001 | E-01-S02 | TBD |
| F-003 | FG-01 | Item master | Fish species, packing units and freshness grades | must | ROLE-001 | E-01-S03 | TBD |
| F-004 | FG-01 | 業務規程 parameter settings | Fees, payment deadlines, 完納奨励金 rates and the channel × tier permission matrix, each with an effective date | must | ROLE-001 | E-01-S04 | TBD |
| F-005 | FG-01 | User account management | Login accounts for market and wholesaler staff | must | ROLE-001 | E-01-S05 | TBD |
| F-006 | FG-02 | Receiving & listing (上場) | Create lots from incoming catch, with staff-entered freshness grade and market hand-marks | must | ROLE-002 | E-02-S01 | TBD |
| F-007 | FG-03 | 相対取引 recording | Record a negotiated trade and check the buyer's permission at entry | must | ROLE-002 | E-03-S01 | TBD |
| F-008 | FG-03 | せり result recording | Record the winning buyer and price per lot and check permission (result recording only, no electronic bidding) | must | ROLE-002 | E-03-S02 | TBD |
| F-009 | FG-04 | 仕切 (shipper settlement) | Settle with the shipper: sales amount minus fees | must | ROLE-002 | E-04-S01 | TBD |
| F-010 | FG-04 | Receivables & payment recording | Bill 買受代金 to buyers, record payments received, track overdue amounts | must | ROLE-002 | E-04-S02 | TBD |
| F-011 | FG-04 | 完納奨励金 calculation | Calculate the incentive per period for buyers who paid in full by the deadline | must | ROLE-002, ROLE-001 | E-04-S03 | TBD |
| F-012 | FG-05 | Trade inquiry | View trades for the day and for a period | must | ROLE-001, ROLE-002 | E-05-S01 | TBD |
| F-013 | FG-05 | Trade result reports | Reports required by 卸売市場法 / 業務規程 (scope pending customer confirmation) | should | ROLE-001 | E-05-S02 | TBD |

## 3. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-04 | pm-gather-requirements skill | Created FG-01–FG-05 and F-001–F-013 |
| 2026-11-23 | pm-plan-schedule skill | Filled "Related WBS ID" for F-001–F-013 (E-01-S01…E-05-S02) |
