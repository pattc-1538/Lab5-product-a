# Task breakdown — Product A

## 1. Nguyên tắc chia task

**Ba tầng trên GitHub Project** ([Product A — LAB-5](https://github.com/users/pattc-1538/projects/1)):

| Tầng | Là gì | Số lượng | Ví dụ |
| --- | --- | --- | --- |
| Epic | Một nhóm chức năng (FG) trong function-list. Không chia theo phase | 5 | #105 [Epic] E-01 Master data |
| Story (sub-issue của epic) | Một chức năng F-xxx, có story chi tiết với tiêu chí nghiệm thu | 13 | #106 [Story] E-01-S01 Participant management |
| Task (sub-issue của story) | Một việc của một phase cho story đó | 104 | #5 バックエンド実装・データ層 |

**Độ hạt (chia tới đâu thì dừng):**
- Mỗi story có task theo 4 phase: 要件ヒアリング (1), basic design (画面仕様書・API設計・DB設計, tối đa 3; story chỉ đọc dữ liệu thì không có DB設計), phát triển, ST (1).
- Phát triển mặc định chia **Backend + Frontend**. Story lớn hơn khoảng 3 ngày, hoặc có phần làm độc lập được, thì tách tiếp theo phần kỹ thuật, sao cho mỗi task khoảng 1–3 ngày và một người làm. Ví dụ E-01-S04 có 6 task phát triển: phần sửa code LAB-2 tách khỏi phần mới; E-03-S01 tách riêng hàm kiểm quyền dùng chung và luồng ngoại lệ.
- Dừng khi một task là một việc một người làm xong trong 1–3 ngày và có tiêu chí xong kiểm tra được. Không tách theo thao tác CRUD.

**Định nghĩa xong:**
- Task: các tiêu chí trong body Issue đã đạt, đã review, Status = Done.
- Story: mọi task con Done và đạt §9 của story chi tiết.
- Dự án: các tiêu chí D-001 đến D-013 trong [define-dod.md](project/01_management/define-dod.md). Mỗi story ghi D-ID liên quan ở §11.

**Các trường trên Project:**

| Trường | Cách dùng |
| --- | --- |
| Status | Todo / In Progress / In Review / Done |
| Phase | requirements / basic-design / development / testing |
| Iteration | Mỗi sprint 2 tuần, bắt đầu thứ Hai từ 2026-11-30. Sprint 4 (2027-01-11 → 01-24) là sprint phát triển đầu tiên |
| Assignee (assumed) | Người phụ trách giả định theo vai trò: BrSE (ヒアリング), Designer (画面仕様書), BE (API/DB設計, バックエンド), FE (フロントエンド), QA (ST), PM (epic, story) |
| SWP | Điểm SWP đã review (xem [estimate.md](estimate.md)). Story và epic là tổng của task con |
| Estimate (h) | SWP × 2,543 giờ, làm tròn 0,5 giờ |

## 2. Spec → issue

| Spec (LAB-4) | Epic | Issue / sub-issue | Phần spec chưa thành issue và vì sao |
| --- | --- | --- | --- |
| SPEC-PA-104 参加者・許可承認, SPEC-PA-203 (`participant-licensing/`) | #105 E-01 | Story #106 → #1〜#9 | — |
| (không có spec) F-002 người gửi hàng | #105 E-01 | Story #107 → #10〜#16 | Spec màn hình viết ở #11 (P11) |
| (không có spec) F-003 mặt hàng, hạng độ tươi | #105 E-01 | Story #108 → #17〜#23 | Spec viết ở #18 (P11) |
| SPEC-PA-105 業務規程パラメータ, SPEC-PA-204 (`business-rules/`) | #105 E-01 | Story #109 → #24〜#30, #92〜#95 | Hủy bản 予約 và bỏ hẳn một điều kiện cấp phép: khách xác nhận không cần (QA-013) |
| (không có spec) F-005 tài khoản | #105 E-01 | Story #110 → #31〜#37 | Đăng nhập và RLS là phần nền (estimate 2.4), chưa thành issue (dòng cuối bảng) |
| SPEC-PA-101 上場 (`receiving/`) | #111 E-02 | Story #112 → #38〜#44, #96, #97 | Ảnh ký hiệu viết tay: ngoài phạm vi, khách xác nhận không cần (QA-003) |
| SPEC-PA-102 相対取引入力, SPEC-PA-103 例外承認, SPEC-PA-201, SPEC-PA-202 (`sales-trading/`) | #113 E-03 | Story #114 → #45〜#51, #98〜#100 | — |
| (không có spec) F-008 せり | #113 E-03 | Story #115 → #52〜#58 | Spec viết ở #53 (P11) |
| SPEC-PA-106 仕切作成, SPEC-PA-205 (`shipper-settlement/`) | #116 E-04 | Story #117 → #59〜#65, #101, #102 | — |
| (không có spec) F-010 công nợ, thu tiền | #116 E-04 | Story #118 → #66〜#72, #103, #104 | Spec viết ở #67 (P11) |
| (không có spec) F-011 完納奨励金 | #116 E-04 | Story #119 → #73〜#79 | Spec viết ở #74 (P11) |
| (không có spec) F-012 tra cứu | #120 E-05 | Story #121 → #80〜#85 | — |
| (không có spec) F-013 báo cáo, công khai | #120 E-05 | Story #122 → #86〜#91 | Phạm vi đã chốt ở QA-004 |
| SPEC-PA-001 kiến trúc (`_common/PA_MARKET_OPS_DESIGN.md`) | — | Chưa có issue | Phần nền (khởi tạo dự án và môi trường, đăng nhập + RLS, audit log; estimate 2.2–2.5) là việc của phase basic design trong schedule §1, không thuộc story nào. Sẽ tạo issue khi bắt đầu basic design |
| (schedule §1) Chuyển dữ liệu, tài liệu và đào tạo, UAT, release, PM/BrSE | — | Chưa có issue | Là phase hoặc việc xuyên suốt, không gắn với story; giờ của chúng không nằm trong 387 SWP (xem estimate.md §3) |

## 3. Hạng mục chịu ràng buộc đặc thù: 完納奨励金

| Ràng buộc | Issue | Vì sao tách riêng |
| --- | --- | --- |
| Tính 完納奨励金 theo từng kỳ chốt, tiền chưa thuế × tỷ lệ tháng, làm tròn xuống ở tổng tháng (A2) | Story #119; #73 ヒアリング, #74〜#76 thiết kế, #77 BE tính và xác nhận, #78 FE kết quả và bảng kê, #79 ST | Là tiền nên phải khớp tính tay tới từng yên (NFR-005, D-003). Công thức đặc thù của chợ (đã chốt ở QA-007), cần story riêng để test riêng |
| Cờ "đã trả đủ đúng hạn" của từng kỳ | #103 (E-04-S02 BE thu tiền) | Đầu vào của 奨励金. Đặt ở công nợ vì xuất phát từ việc trừ nợ |
| Cấn trừ vào 請求書 tháng sau | #70, #71 (E-04-S02) | Proposal: cấn trừ, không trả tiền mặt (Q-25). E-04-S03 tính số, E-04-S02 áp vào công nợ |
| Tỷ lệ thưởng theo tháng, có ngày hiệu lực | #93, #95 (E-01-S04) | Tham số 業務規程: đổi tỷ lệ không cần sửa phần mềm. Spec LAB-4 chưa có (P1) |
| Sau khi đã xác nhận mà khoản thu bị hủy | #77 (cờ "cần tính lại", điều chỉnh tháng sau) | Tránh lệch giữa bảng kê đã đưa khách và công nợ |

## 4. Chỗ hở hoặc mâu thuẫn của spec LAB-4 phát hiện khi break

| Spec | Chỗ hở / mâu thuẫn | Xử lý |
| --- | --- | --- |
| SPEC-PA-105 | Không có tab hạn thanh toán và tỷ lệ 完納奨励金, trong khi F-004, WBS và estimate 3.4a có | Đã sửa thiết kế (PREMISE P1) |
| SPEC-PA-105 | 変更理由 chỉ bắt buộc ở một tab | Đã sửa thiết kế (PREMISE P2) |
| SPEC-PA-105 §6 | Chưa hỗ trợ hủy bản 予約 và bỏ hẳn điều kiện cấp phép | Giả định đã được khách xác nhận: không cần (PREMISE §3, QA-013) |
| SPEC-PA-101 §6 | Không có cách xử lý lô nhập sai | Đã sửa thiết kế (PREMISE P3) |
| SPEC-PA-101 | Hạng độ tươi cố định A/B/C, trong khi F-003 nói danh mục mặt hàng quản lý hạng độ tươi | Đã sửa thiết kế (PREMISE P4) và giả định (A4) |
| SPEC-PA-101 | Số lô 4 chữ số đánh liên tục sẽ hết số | Đã sửa thiết kế (PREMISE P5) |
| SPEC-PA-101 và estimate v1 4.1b | Spec không có ảnh, estimate v1 có, proposal v2 ghi ngoài phạm vi | Hướng đã chốt (PREMISE §3): không làm; khách xác nhận ở QA-003 |
| SPEC-PA-101, SPEC-PA-102 | Ngày chợ / ngày giao dịch cho nhập ngày bất kỳ | Đã sửa thiết kế (PREMISE P6) |
| SPEC-PA-103 / R-07 | Luồng ngoại lệ phụ thuộc Q-22 | Hướng đã chốt (PREMISE §3); khách xác nhận ở QA-006 |
| SPEC-PA-106 | API-STL-03 (hủy 仕切) được nhắc nhưng không có tài liệu | Đã sửa thiết kế (PREMISE P8); viết ở #61, làm ở #101 |
| SPEC-PA-106 D-3 | Giao dịch được duyệt sau khi đã 仕切 vào kỳ nào: "chưa quyết" | Đã sửa thiết kế (PREMISE P9) |
| market-rule-catalog | せり, công nợ, 完納奨励金 chưa có màn hình hay quy tắc | Tạo issue làm rõ: #53, #67, #74 (viết spec màn hình); giả định A1, A2 |
| market-rule-catalog R-03 | Cách tính phí ủy thác và làm tròn đang để tạm (Q-02) | Hướng đã chốt (PREMISE §3): giữ giá trị tạm làm chính thức (QA-008) |
| SPEC-PA-104 / Q-26 | Ngưng tư cách người tham gia và ngưng giấy phép có gộp làm một không | Hướng đã chốt (PREMISE §3): tách riêng (QA-009) |
| function-list F-013 | Phạm vi công khai và báo cáo chưa rõ | Hướng đã chốt (PREMISE §3): đã chốt ở QA-004 |
| Estimate v1 và schedule | Luồng ngoại lệ (v2 dòng 5.1d) không có trong bản v1 mà schedule dùng | Đã sửa (PREMISE §3: tính lại schedule theo v2) |
