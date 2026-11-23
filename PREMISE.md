# PREMISE — Backlog LAB-5 khác bản LAB-4 ở đâu

Bản gốc: bộ spec LAB-4 nộp ngày 2026-11-22 (`specs/_index.md`, SPEC-PA-001, SPEC-PA-101〜106, SPEC-PA-201〜205).
Chi tiết từng thay đổi nằm trong story tương ứng ở [`project/01_management/stories/`](project/01_management/stories/) (mục §5, §10).

## 1. Spec thêm / bỏ / sửa so với LAB-4

| # | Spec (mã/file LAB-4) | Thêm/Bỏ/Sửa | Trước → sau | Vì sao | Issue bị ảnh hưởng |
| --- | --- | --- | --- | --- | --- |
| P1 | SPEC-PA-105 業務規程パラメータ (`business-rules/screen-specification/PA_BUSINESS_RULE_PARAMS_SPEC.md`) | Thêm | 4 tab (手数料・税率 / 取引権限 / 種別区分 / 許可・承認要件) → 6 tab, thêm **支払期限** (ngày chốt + số ngày) và **完納奨励金率** (tỷ lệ theo tháng) → [story-E-01-S04 §5](project/01_management/stories/story-E-01-S04-business-rule-parameter-settings.md) | Hở phát hiện khi break: function-list F-004, tên story trong WBS và estimate LAB-1 dòng 3.4a đều có hai tham số này, nhưng SPEC-PA-105 chưa thiết kế; market-rule-catalog ghi "chưa thiết kế (F-010, F-011)". E-04-S02/S03 cần tra tham số theo ngày | #25, #26, #27, #93, #95 (và #70, #77 dùng tham số) |
| P2 | SPEC-PA-105 | Sửa | 変更理由 chỉ bắt buộc ở tab 手数料・税率 → **bắt buộc ở mọi tab** | Chốt khi break E-01-S04: lịch sử thay đổi phải giải thích được khi có tranh chấp (story §4) | #28, #29, #94, #95 |
| P3 | SPEC-PA-101 上場 (`receiving/screen-specification/PA_LOT_LISTING_SPEC.md`) | Thêm | Không có thao tác sửa/hủy lô → **hủy lô chưa bán kèm lý do** (không xóa, R-09) | SPEC-PA-101 §6 để ngỏ "lô nhập sai có cần hủy không"; 10 người nhập đồng thời nên khó tránh nhập sai | #96, #97 |
| P4 | SPEC-PA-101 | Sửa | Hạng độ tươi là CHECK cố định A/B/C → **lấy từ danh mục hạng độ tươi** (một danh sách chung, E-01-S03) | function-list F-003 ghi danh mục mặt hàng quản lý hạng độ tươi; SPEC-PA-101 §6 tự ghi "nếu chợ dùng thang khác thì chuyển thành danh mục" (Q-05) | #18〜#22, #42, #43 |
| P5 | SPEC-PA-101 | Sửa | `lot_no` 4 chữ số đánh liên tục → **đặt lại theo từng ngày chợ** (L-0001 mỗi ngày, duy nhất theo ngày chợ + số lô) | Hở khi break: 4 chữ số liên tục hết số sau khoảng 3 năm với ~10 lô/ngày | #41, #42 |
| P6 | SPEC-PA-101, SPEC-PA-102 | Sửa | 市場日 / 取引日 nhập ngày bất kỳ → **hôm nay đến 7 ngày trước**; ngày giao dịch không sớm hơn ngày chợ của lô | Nhập bù khi mất mạng (NFR-003) cần ngày quá khứ, nhưng ngày bất kỳ dễ nhập nhầm | #42, #49, #56 |
| P7 | SPEC-PA-101 | Sửa | Số lượng 1 số lẻ cho mọi đơn vị → **kg 1 số lẻ, 箱 và 尾 số nguyên** | Không thể có 1,5 thùng hay 1,5 con | #42, #43 |
| P8 | SPEC-PA-106 仕切 (`shipper-settlement/screen-specification/PA_SHIKIRI_SETTLEMENT_SPEC.md`) | Thêm | API hủy 仕切 (API-STL-03) được nhắc nhưng không có tài liệu → **đưa vào phạm vi, viết ở basic design** | R-09 yêu cầu hủy 仕切 trước khi hủy giao dịch đã 仕切; thư mục `api-design/shipper-settlement/` chỉ có STL-01, STL-02 | #61, #101, #102 |
| P9 | SPEC-PA-106 | Sửa | Giao dịch 承認待ち được duyệt sau khi đã 仕切 "vào kỳ nào: chưa quyết (Q-22)" → **vào 仕切 kỳ sau**, màn hình 仕切 cảnh báo số giao dịch chờ | Chốt khi break E-03-S01 (Block 4) để không chặn thanh toán cho người gửi hàng | #63, #64 |
| P10 | SPEC-PA-106 | Sửa | 仕切日 nhập ngày bất kỳ → **từ ngày cuối kỳ đến hôm nay**; 差引支払額 âm được phép kèm cảnh báo; PDF bằng trang in của trình duyệt | Chốt khi break E-04-S01; tỷ lệ phí lấy theo 仕切日 nên ngày sai sẽ chọn sai tỷ lệ | #63, #64, #102 |
| P11 | (không có trong LAB-4) | Thêm | Màn hình せり (F-008), công nợ / thu tiền / 請求書 (F-010), 完納奨励金 (F-011), danh mục người gửi hàng, mặt hàng, tài khoản, tra cứu, báo cáo → **spec sẽ viết ở basic design** theo story | LAB-4 chỉ thiết kế 6 màn lõi; market-rule-catalog ghi "せり chưa có màn hình", "hạn thanh toán, 完納奨励金 chưa thiết kế" | #11, #18, #32, #53, #67, #74, #81, #87 |
| P12 | (không có trong LAB-4) | Thêm | **請求書** theo kỳ chốt (in / lưu PDF), cấn trừ 完納奨励金 vào 請求書 tháng sau | Chốt khi break E-04-S02: người mua chuyển khoản cần biết số tiền; proposal ghi cấn trừ vào kỳ sau (Q-07, Q-25) | #70, #71 |

## 2. Giả định bổ sung

| # | Giả định | Chỗ spec/RFP để ngỏ | Ảnh hưởng tới issue/estimate |
| --- | --- | --- | --- |
| A1 | Hạn thanh toán = ngày chốt + số ngày; rơi vào ngày nghỉ ngân hàng thì lùi sang ngày làm việc kế tiếp | Cách tính hạn thanh toán chưa có trong RFP lẫn LAB-4 | #70 (cần lịch ngày nghỉ Nhật); giá trị cụ thể hỏi khách |
| A2 | 完納奨励金 xét theo từng kỳ chốt; tiền mua chưa thuế × tỷ lệ tháng; làm tròn xuống ở tổng tháng của từng người mua | Công thức thưởng (Q-07) | #77 (độ khó C3), #79; nếu khách dùng bậc thang thì +3〜5 MD (rủi ro estimate v2) |
| A3 | 中値 = mức giá có khối lượng giao dịch lớn nhất | Định nghĩa giá công bố (F-013, QA-004) | #89 |
| A4 | Hạng độ tươi là một danh sách chung cho cả chợ, khởi tạo A/B/C | Thang độ tươi thật (Q-05) | #20, #21; đổi thang chỉ là đổi dữ liệu |
| A5 | Khoảng 10 lô/ngày, 10 giao dịch 相対/ngày, tối đa 10 người nhập cùng lúc; 20〜50 người mua cấp 1; khoảng 20 tài khoản | Khối lượng giao dịch chưa có trong RFP | Kích thước test và hiệu năng (#42, #49, #97) |
| A6 | Tài khoản tạo bằng email mời, tự đặt lại mật khẩu qua email (Supabase Auth); mọi nhân viên có email công việc | Cách cấp tài khoản | #35, #36 |
| A7 | Tham số 業務規程 có hiệu lực từ ngày mai; một 市場管理者 tự phát hành, không cần người duyệt thứ hai | Quy trình đổi quy tắc | #28〜#30, #92〜#95 |
| A8 | CSV dùng UTF-8 có BOM; tra cứu tối đa 1 năm mỗi lần, 100 dòng/trang | Định dạng xuất | #83, #84 |

Các giả định trên chỉ lấp chỗ RFP và LAB-4 để ngỏ. Những gì RFP đã nêu rõ (2 vai trò đăng nhập, kiểm quyền khi nhập giao dịch, せり chỉ ghi kết quả, 13 chức năng) giữ nguyên.

## 3. Hướng đã chốt

| Vấn đề | Các phương án ở LAB-4 | Phương án chốt | Vì sao |
| --- | --- | --- | --- |
| Giao dịch sai quyền (R-07, Q-22) | Chặn cứng (code LAB-2) / ghi 承認待ち kèm lý do, 市場管理者 duyệt (ADR-005) | Ghi 承認待ち và duyệt; nếu khách trả lời Q-22 là "chặn tuyệt đối" thì bỏ phần này | Proposal điểm 03 đã hứa với khách; estimate v2 có dòng 5.1d (4 MD) |
| Sửa giao dịch nhập sai | Sửa trực tiếp giá/số lượng (estimate 5.1b) / hủy kèm lý do rồi nhập lại (SPEC-PA-102, R-09) | Hủy kèm lý do rồi nhập lại | Giữ lịch sử rõ ràng cho 仕切 và công nợ |
| Ảnh chụp ký hiệu viết tay | Có (estimate v1 dòng 4.1b) / không (SPEC-PA-101, proposal v2 mục ngoài phạm vi) | Không làm, ghi là ứng viên change request (QA-003) | Proposal gửi khách ghi rõ ngoài phạm vi |
| Tạo file PDF (仕切書, 請求書, bảng kê) | Server tạo PDF / trang in của trình duyệt | Trang in A4 của trình duyệt, người dùng lưu thành PDF | Vừa effort 6.1b (2 MD), phông tiếng Nhật hiển thị đúng |
| Căn cứ estimate | v1 201 MD (schedule ban đầu) / v2 177 MD (proposal gửi khách) | v2 177 MD | Khớp với con số đã báo khách; schedule tính lại, các mốc giữ nguyên, phần dư thành buffer |
| Ngày áp dụng tham số | Từ ngày mai (R-08, code LAB-2) / cho phép ngay hôm nay | Từ ngày mai | Tránh giao dịch trong cùng một ngày bị chia hai quy tắc |
