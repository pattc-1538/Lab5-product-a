# Requirements Q&A — List of Items for Customer Confirmation

> This is a list of items that could not be settled on the spot during the requirements definition
> (pm-gather-requirements) interview, for the customer to confirm. We apologize for the imposition and would
> be grateful if you could fill in the "Answer" column.

## 1. Items for Confirmation

| QA-ID | Subject | Question | Status | Raised on | Answer | Answer date | Respondent |
| --- | --- | --- | --- | --- | --- | --- | --- |
| QA-001 | system-overview §2 | Regarding your current operations, could you confirm whether the following understanding is correct, and correct anything that differs?<br>(1) Because trades are recorded by phone, fax and handwritten ledgers, the day's trades cannot be seen in real time and transcription or settlement errors occur.<br>(2) Whether a buyer is permitted to trade (e.g. who may buy directly from the wholesaler) is checked by staff, so a trade that breaches your operating rules (業務規程) could slip through.<br>(3) The on-time-payment incentive (完納奨励金) is calculated by hand from payment records, which takes effort and can lead to errors or disputes. | Answered | 2026-11-04 | Confirmed as written (fictional client; answered by the PL acting as client). | 2026-11-24 | Client role (PL on behalf) |
| QA-002 | non-function-list NFR-001/002/007 | Regarding system performance and availability, could you confirm or correct the following proposed targets?<br>(1) List and entry screens respond within about 3 seconds.<br>(2) The system is available during market hours, including the early-morning session, at about 99% excluding planned maintenance, and data loss on failure is limited to at most 24 hours.<br>(3) For how many years must trade and payment records be retained? | Answered | 2026-11-04 | Confirmed: about 3 s; about 99% during market hours excluding planned maintenance; RPO 24 h; trade data retained 7 years (Japanese tax-record practice). | 2026-11-24 | Client role (PL on behalf) |

## 2. Revision History

| Date | Updated by | Content |
| --- | --- | --- |
| 2026-11-04 | pm-gather-requirements skill | Raised QA-001 |
| 2026-11-04 | pm-gather-requirements skill | Raised QA-002 |
| 2026-11-24 | project-manager | QA-001, QA-002 answered (fictional client; PL answered as the client) |
