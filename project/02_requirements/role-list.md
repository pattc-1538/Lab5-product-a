# Role List & Permission Matrix

## 1. User Roles

| ROLE-ID | Role name | Description | Typical user |
| --- | --- | --- | --- |
| ROLE-001 | Market administrator (市場管理者) | Maintains the participant register and their permission tier, sets the 業務規程 parameters, views reports | Market management office staff |
| ROLE-002 | Wholesaler staff (卸売業者 担当者) | Registers incoming lots (incl. freshness grade and hand-marks), records せり and 相対取引 trades, issues 仕切, records payments | 卸売業者 sales floor and office staff (one shared role) |

> 仲卸, 売買参加者 and 買出人 do not log in. They are held as participant data (with their permission tier) and are
> referenced when a trade is checked.

## 2. Permission Matrix (function × role)

> One column per role in §1, one row per function in `function-list.md`.
> Legend: ✅ = allowed / — = not allowed / △ = conditional (state the condition in Notes).

| F-ID | Function | ROLE-001 | ROLE-002 | Notes |
| --- | --- | --- | --- | --- |
| F-001 | Participant management | ✅ | △ | ROLE-002: view only (to see who may buy) |
| F-002 | Shipper management | ✅ | △ | ROLE-002: view only |
| F-003 | Item master | ✅ | △ | ROLE-002: view only |
| F-004 | 業務規程 parameter settings | ✅ | — | |
| F-005 | User account management | ✅ | — | |
| F-006 | Receiving & listing (上場) | △ | ✅ | ROLE-001: view only |
| F-007 | 相対取引 recording | △ | ✅ | ROLE-001: view only |
| F-008 | せり result recording | △ | ✅ | ROLE-001: view only |
| F-009 | 仕切 (shipper settlement) | △ | ✅ | ROLE-001: view only |
| F-010 | Receivables & payment recording | △ | ✅ | ROLE-001: view only |
| F-011 | 完納奨励金 calculation | △ | ✅ | ROLE-001: view only |
| F-012 | Trade inquiry | ✅ | ✅ | |
| F-013 | Trade result reports | ✅ | — | |

## 3. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-04 | pm-gather-requirements skill | Created ROLE-001–ROLE-002 and the permission matrix for F-001–F-013 |
