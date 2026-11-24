# Estimate — Product A (SWP)

**Báo cáo HTML của skill:** [`reports/estimate-swp-product-a-lab5-20261123-135557.html`](reports/estimate-swp-product-a-lab5-20261123-135557.html)
(skill `tkm:estimate-swp`, mức xử lý `medium`, 104 task, hiệu chỉnh `accepted`, tạo lúc 2026-11-23 13:55 UTC).

Mọi con số dưới đây lấy từ payload kiểm toán nhúng trong báo cáo và từ các trường SWP, Estimate (h) trên [GitHub Project](https://github.com/users/pattc-1538/projects/1).

## 1. Issue mẫu skill chọn để kiểm

Skill tự chọn 5 Issue mẫu bằng thuật toán cố định (nhỏ nhất, trung vị, lớn nhất, lệch xa nhất, độ tin cậy thấp nhất). Mỗi Issue được hỏi hai vòng: mức khó, rồi điểm cụ thể.

| Issue | Skill chấm (Scope × Complexity → SWP) | Bạn chốt | Lý do |
| --- | --- | --- | --- |
| #13 DB設計（Shipper management）— nhỏ nhất | 1 × 1 → 1 | 1 (rất dễ) | Thiết kế một bảng, chỉ chốt nhẹ RLS và cách nạp CSV |
| #7 フロントエンド実装・参加者台帳 — trung vị | 3 × 1 → 4 | 4 (dễ) | Danh sách, lọc, chi tiết, form đăng ký là CRUD tiêu chuẩn |
| #103 バックエンド実装・入金と消し込み — lớn nhất | 3 × 3 → 6 | 6 (vừa) | Tự trừ nợ kỳ cũ nhất, đổi tay, tiền trả trước, hủy, cờ 完納: có cập nhật đồng thời nhưng vẫn trong một luồng |
| #34 DB設計（User account management）— lệch xa nhất | 1 × 1 → 1 | 1 (rất dễ) | Chủ yếu dựa vào bảng của Supabase Auth |
| #1 要件ヒアリング（Participant management）— độ tin cậy thấp nhất | 3 × 1 → 4 | 4 (dễ) | Story lớn (17 tiêu chí) nhưng chỉ cần hỏi 3 điểm chưa chốt |

**Không sửa Issue nào.** Lý do giữ nguyên: thứ tự tương đối giữa 5 Issue mẫu đúng với cảm nhận của PM; điểm cao nhất (6) rơi vào phần logic tiền, đúng là chỗ khó nhất. Vì không có Issue mẫu nào bị chỉnh, không có quy tắc nào lan sang các Issue cùng nhóm.

Trước khi tới bước duyệt, có một vòng sửa máy: worker gán nhóm chuyên môn `Unknown` cho 9 task 要件ヒアリング nhưng để độ tin cậy `medium`. Bộ validate của skill từ chối, và chính các worker đó sửa sang `low` / `AMBIGUOUS`; điểm không đổi.

## 2. Cách quy ra giờ

- **Cách chọn:** quy ước đổi SWP ra giờ bằng **một hệ số chung**, không ước giờ trực tiếp từng Issue.
- **Vì sao:** SWP đo độ rộng và độ khó; một hệ số chung giữ đúng thứ tự tương đối giữa các task. Hệ số lấy từ estimate v2 đã gửi khách, nên tổng giờ khớp với con số đã cam kết. Ước trực tiếp 104 task thì không nhất quán và không kiểm lại được.
- **Quy tắc:**
  1. Lấy MD của các dòng estimate v2 mà task trên Project bao phủ: requirements (18), thiết kế và nền tảng (22), 5 nhóm chức năng (75), IT/ST (8.1–8.2: 8). Tổng **123 MD = 984 giờ**.
  2. **Hệ số = 984 ÷ 387 SWP = 2,543 giờ/SWP.**
  3. Giờ của task = SWP × 2,543, làm tròn tới 0,5 giờ. Story và epic lấy tổng giờ của task con, không làm tròn lại.
  4. Không đưa vào hệ số 54 MD không có task trên Project: chuyển dữ liệu (3), tài liệu vận hành (3), đào tạo (3), UAT (8), hỗ trợ tăng cường (6), deploy (1), PM (15), BrSE (15).
- **Áp dụng nhất quán:** một script ghi SWP và giờ cho cả 122 mục cùng lúc từ payload đã validate; không chỉnh tay mục nào. Tổng 104 task là 970,5 giờ (thấp hơn 984 do làm tròn từng task).

## 3. Tổng theo epic

| Epic | Số issue (task) | Tổng SWP | Tổng giờ | Ghi chú |
| --- | --- | --- | --- | --- |
| #105 E-01 Master data | 41 | 140 | 350,0 | 5 story. E-01-S04 (43 SWP) lớn nhất do thêm 2 tab tham số (PREMISE P1) |
| #111 E-02 Receiving | 9 | 36 | 90,5 | Có thêm hủy lô (P3) |
| #113 E-03 Sales | 17 | 68 | 170,5 | Gồm luồng ngoại lệ (#98〜#100) |
| #116 E-04 Settlement & receivables | 25 | 103 | 259,5 | Gồm 完納奨励金 (27 SWP) và 請求書 (P12) |
| #120 E-05 Inquiry & reporting | 12 | 40 | 100,0 | #86 có độ tin cậy low (lúc chấm, phạm vi F-013 còn chờ khách; đã chốt ở QA-004 ngày 2026-11-24 nhưng chưa chấm lại) |
| **Tổng** | **104** | **387** | **970,5** | Độ tin cậy: high 12, medium 82, low 10. Không có đề xuất tách Issue |

## 4. So với estimate LAB-1

LAB-1 v2 (177 MD) tính requirements, thiết kế và kiểm thử chung cho cả dự án, chỉ phần phát triển tách theo nhóm chức năng. Bảng dưới so theo đúng cách chia đó. Số LAB-5 là giờ ÷ 8.

| Phần | LAB-1 (MD) | LAB-5 (MD) | Chênh | Vì sao |
| --- | --- | --- | --- | --- |
| Requirements (13 task 要件ヒアリング) | 18 | 12,8 | −5,2 | LAB-1 có workshop và duyệt tài liệu yêu cầu chung (dòng 1.1, 1.4); LAB-5 chỉ có task hỏi theo từng story, SWP thấp (1–5) |
| Thiết kế (37 task) | 22 | 39,1 | +17,1 | Một hệ số chung cho mỗi tài liệu thiết kế gần bằng số giờ của một task code (SWP 2–5). LAB-1 có 15 MD cho phần nền (2.2–2.5) chưa có issue. Đây là điểm yếu của cách quy đổi (xem AI-report) |
| Phát triển FG-01 / E-01 | 17 | 19,1 | +2,1 | Thêm thủ tục 許可/承認 (E-01-S01) và tab tham số (P1, P2) |
| Phát triển FG-02 / E-02 | 5 | 4,8 | −0,2 | Thêm hủy lô (P3), bỏ ảnh (PREMISE §3) |
| Phát triển FG-03 / E-03 | 14 | 9,8 | −4,2 | SWP của kiểm quyền và ngoại lệ chỉ ở mức C2–C3 (≤ 6 SWP mỗi task); estimate LAB-1 cho BE nhiều ngày hơn (5.1c, 5.1d) |
| Phát triển FG-04 / E-04 | 14 | 14,9 | +0,9 | Thêm 請求書 và hủy 仕切 (P8, P12) |
| Phát triển FG-05 / E-05 | 5 | 5,0 | 0 | Thêm tra cứu lô ngày cũ, bù lại phạm vi F-013 hẹp |
| Kiểm thử (13 task ST) | 28 | 15,9 | −12,1 | LAB-1 có 1 MD QA cho mỗi dòng chức năng (20 MD) cộng IT/ST (8 MD); LAB-5 gộp thành một task ST cho mỗi story |
| **Cộng phần có task** | **123** | **121,3** | **−1,7** | Bằng nhau theo cách tính hệ số; chênh do làm tròn 0,5 giờ |
| Phần không có task (chuyển dữ liệu, UAT, PM, BrSE…) | 54 | — | — | Nằm ở phase và việc xuyên suốt trong schedule §1 |
| **Tổng dự án** | **177** (v1: 201) | **175,3** nếu cộng 54 MD | — | Schedule đã chuyển từ v1 sang v2 (PREMISE §3) |
