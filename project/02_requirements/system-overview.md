# System Overview

> The service/product view: what is being built, why, and what it is meant to achieve.
> KPIs and success criteria are **out of scope** here — they live in `project/01_management/overview.md`
> §2 and are owned by `pm-plan-project` (PLAN).

## 1. Service Overview

Product A is a web-based operations system for Sakura Bay Fish Market JSC (fictional), a mid-size fish wholesale market at a fishing port (産地市場 — buys directly from fishing boats). It records negotiated bilateral trades (相対取引) and auction sessions (せり), enforces who may trade with whom under the market's own operating rules (業務規程), and calculates the on-time-payment incentive (完納奨励金). Only internal staff operate the system; the other market participants are managed as data.

| Item | Value |
| --- | --- |
| Target platform | Web |
| Primary users | Market management office and 卸売業者 staff (data entry and operation). 仲卸 / 売買参加者 / 買出人 do not log in — they are managed as participant data |
| Where the data is mastered | Entered in this system (current operations are fully manual: phone, fax, handwritten ledgers) |

## 2. Background & Problems

| # | Current problem | Impact |
| --- | --- | --- |
| 1 | Trades are managed manually by phone, fax and handwritten ledgers | *Hypothesis (needs client confirmation, QA-001):* the day's trades cannot be seen in real time, and transcription and settlement errors occur |
| 2 | The market has just issued its own operating rules (業務規程) under the 2020 revision of 卸売市場法, and generic "auction market" systems do not fit them | No tool enforces the market's own rules |
| 3 | The two legal permission tiers among the four participant types (who may buy from whom, through which channel) are checked by people | *Hypothesis (needs client confirmation, QA-001):* trades that breach the 業務規程 can slip through |
| 4 | *Hypothesis (needs client confirmation, QA-001):* 完納奨励金 is calculated by hand from payment records | *Hypothesis (needs client confirmation, QA-001):* labour-intensive and error-prone, leading to disputes with buyers |

> Rows 1–3 (problem column) are taken from the client brief. Everything marked *Hypothesis* is inferred from
> general characteristics and must not be treated as confirmed before the client answers QA-001.

## 3. Objectives & Value Delivered

| # | Objective | Value delivered | Related problem # |
| --- | --- | --- | --- |
| 1 | Digitize the recording of 相対取引 and せり trades, including the freshness grade and market hand-marks entered by staff | The management office and 卸売業者 see the day's trades as they happen; fewer settlement errors | 1 |
| 2 | Hold the 業務規程 rules (permission tiers, fees, payment deadlines) in the system as parameters | The system follows this market's own rules; a rule change is a parameter change | 2 |
| 3 | Check trading permission at the moment a trade is entered | Trades that breach the 業務規程 are blocked before they are recorded | 3 |
| 4 | Calculate 完納奨励金 automatically from payment data | Less manual calculation and a verifiable basis when buyers query the amount | 4 |

## 4. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-04 | pm-gather-requirements skill | Created §1–§3 from context.txt; §2 hypotheses pending QA-001 |
