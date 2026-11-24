# Product A — Hệ thống hỗ trợ nghiệp vụ Chợ Thủy sản Vịnh Sakura (LAB-5)

- **Mã học viên:** pattc_1538
- **Đề:** Product A

## Tổng quan

- **Backlog break từ:** bộ spec LAB-4 nộp ngày **2026-11-22** (SPEC-PA-001, SPEC-PA-101〜106, SPEC-PA-201〜205).
- **PREMISE.md: có thay đổi** so với LAB-4: 12 thay đổi spec, 8 giả định bổ sung, 6 hướng đã chốt. Xem [PREMISE.md](PREMISE.md).
- **Số epic:** 5 epic, 13 story, 104 task. Tổng **387 SWP / 970,5 giờ** ([estimate.md](estimate.md)).
- **Sprint giả lập đã chạy:** Sprint 4 (2027-01-11 → 2027-01-24), sprint phát triển đầu tiên gồm 14 task của E-01 Master data. Hoàn thành 39/53 SWP; 14 SWP chuyển sang Sprint 5 ([progress-report.md](progress-report.md)).

## Link

| | |
| --- | --- |
| Repo | https://github.com/pattc-1538/Lab5-product-a |
| GitHub Project | https://github.com/users/pattc-1538/projects/1 |
| Báo cáo HTML chấm SWP | [`reports/estimate-swp-product-a-lab5-20261123-135557.html`](reports/estimate-swp-product-a-lab5-20261123-135557.html) |

Repo và Project đều public. ⚠ *Đã mở thử bằng cửa sổ ẩn danh: chưa kiểm tra.*

## Cấu trúc repo

| File / thư mục | Nội dung |
| --- | --- |
| `README.md` | File này: tổng quan, link, cấu trúc, ánh xạ spec → epic |
| `PREMISE.md` | Backlog khác LAB-4 ở đâu: thay đổi spec, giả định bổ sung, hướng đã chốt |
| `task-breakdown.md` | Nguyên tắc chia task, spec → issue, hạng mục 完納奨励金, chỗ hở của spec LAB-4 |
| `estimate.md` | Issue mẫu skill chọn, cách quy ra giờ, tổng theo epic, so với estimate LAB-1 |
| `progress-report.md` | Tiến độ Sprint 4 giả lập: trạng thái, burndown, rủi ro trễ |
| `AI-report.md` | Skill và prompt đã dùng, cách review output của AI, điểm đặc biệt |
| `reports/` | Báo cáo HTML của skill `tkm:estimate-swp` (có payload kiểm toán nhúng bên trong) |
| `project/01_management/` | Tài liệu quản lý dự án: overview, stakeholders, schedule (WBS), task-list (T-001〜T-104 ↔ Issue #1〜#104), define-dod, qa (câu hỏi khách) và `stories/` (13 story chi tiết mà body Issue trỏ tới) |
| `project/02_requirements/` | Yêu cầu: function-list, non-function-list, role-list, glossary, system-overview, qa |

## Spec → epic

| Spec (mã/file LAB-4, hoặc dòng PREMISE) | Epic trên Project (#số — tên) | Ghi chú |
| --- | --- | --- |
| SPEC-PA-104 `participant-licensing/…/PA_PARTICIPANT_LICENSE_SPEC.md`, SPEC-PA-203 | #105 — [Epic] E-01 Master data | Thủ tục 許可 (có xét duyệt) và 承認 (không xét duyệt) cho người tham gia |
| SPEC-PA-105 `business-rules/…/PA_BUSINESS_RULE_PARAMS_SPEC.md`, SPEC-PA-204; PREMISE P1, P2 | #105 — [Epic] E-01 Master data | Tham số có ngày hiệu lực; thêm tab hạn thanh toán và tỷ lệ 完納奨励金 |
| PREMISE P4, P11 (F-002, F-003, F-005, chưa có spec) | #105 — [Epic] E-01 Master data | Danh mục người gửi hàng, mặt hàng và hạng độ tươi, tài khoản |
| SPEC-PA-101 `receiving/…/PA_LOT_LISTING_SPEC.md`; PREMISE P3〜P7 | #111 — [Epic] E-02 Receiving | Hủy lô, số lô theo ngày chợ; ảnh ký hiệu viết tay ngoài phạm vi (QA-003) |
| SPEC-PA-102, SPEC-PA-103, SPEC-PA-201, SPEC-PA-202 `sales-trading/` | #113 — [Epic] E-03 Sales | Kiểm quyền dùng chung theo ngày giao dịch; luồng ngoại lệ chờ duyệt (khách xác nhận QA-006) |
| PREMISE P11 (F-008, chưa có spec) | #113 — [Epic] E-03 Sales | せり chỉ ghi kết quả, dùng chung kiểm quyền với 相対 |
| SPEC-PA-106 `shipper-settlement/…/PA_SHIKIRI_SETTLEMENT_SPEC.md`, SPEC-PA-205; PREMISE P8〜P10 | #116 — [Epic] E-04 Settlement & receivables | Hủy 仕切 (API-STL-03) đưa vào phạm vi |
| PREMISE P11, P12 (F-010, F-011, chưa có spec) | #116 — [Epic] E-04 Settlement & receivables | **Ràng buộc đặc thù 完納奨励金** (story #119); 請求書 theo kỳ chốt |
| PREMISE P11 (F-012, F-013, chưa có spec) | #120 — [Epic] E-05 Inquiry & reporting | Phạm vi công khai kết quả giao dịch đã chốt (QA-004) |
| SPEC-PA-001 `_common/PA_MARKET_OPS_DESIGN.md` | — (phase basic design) | Phần nền (khởi tạo dự án, đăng nhập + RLS, audit log) chưa có issue; xem task-breakdown.md §2 |
