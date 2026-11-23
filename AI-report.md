# AI-report — LAB-5

Công cụ: Claude Code (model Opus) với bộ skill Takumi (`tkm:*`), chạy trong VS Code, ngày 2026-11-23. Con người (PL/BrSE) duyệt ở mọi bước có quyết định, thường qua câu hỏi lựa chọn có kèm khuyến nghị.

## 1. Skill đã dùng và cách viết prompt

| Việc | Skill / công cụ | Prompt và cách dùng |
| --- | --- | --- |
| Lập WBS (epic, story) và lịch | `tkm:pm-plan-schedule` | Gọi lệnh, không kèm mô tả dài. Skill đọc function-list, hỏi milestone, effort, nhân lực. Chạy lại 3 lần: thêm effort cho 2 story mở rộng phạm vi; dời go-live khỏi Golden Week; chuyển căn cứ từ estimate v1 (201 MD) sang v2 (177 MD) |
| Làm story chi tiết | `tkm:pm-create-stories` | 13 story. 8 story lớn hỏi đủ 7 block (mục đích, người dùng, phạm vi, luồng, dữ liệu, phi chức năng, tiêu chí nghiệm thu), mỗi block 2–3 câu có phương án khuyên dùng. 5 story nhỏ dùng cách nhanh: AI soạn bản nháp đầy đủ, người duyệt các điểm cần quyết trong một lần hỏi |
| **Break task** | `tkm:pm-create-tasks` | "Chia task cho 4 phase cho các story còn lại", sau đó "chia lại task phát triển theo story". AI đưa bảng nháp (tên task, nội dung, số Issue sẽ tạo hoặc sửa), người duyệt rồi AI mới ghi lên GitHub |
| Dựng GitHub Project | `gh` CLI và GraphQL, script Python | AI đề xuất cấu trúc (epic → story → task, các trường, Iteration), người duyệt. Script tạo 18 Issue epic và story, 117 quan hệ sub-issue, thêm 122 Issue vào Project, điền Status, Phase, Iteration và người phụ trách giả định |
| **Chấm SWP** | `tkm:estimate-swp` (với `tkm:confidence`) | Prompt: "chấm SWP cho GitHub Project …, xuất báo cáo HTML vào repo". Skill chọn 104 task, chia 5 lô cho 5 worker `tkm:estimate-swp-worker` (không có công cụ, chỉ trả JSON). Mỗi prompt worker kèm đủ bảng quy tắc (thang Scope, Complexity, ma trận, danh sách chuyên môn và đặc điểm) cùng phạm vi 13 story dưới dạng `contextFacts` có trích nguồn. Script của skill validate, chọn 5 Issue mẫu, hiệu chỉnh và render HTML |
| **Ghi SWP lên Project** | Script Python gọi GraphQL `updateProjectV2ItemFieldValue` | Skill chấm SWP chỉ đọc, nên bước ghi tách riêng. Script đọc payload đã validate trong báo cáo HTML, ghi SWP và giờ cho 122 mục, mỗi lệnh 10 mục; rồi đọc lại Project để đối chiếu tổng (387 SWP, 970,5 giờ) |
| **Quy giờ** | Hỏi người chọn phương án, AI tính | Ba phương án: một hệ số chung từ v2 (khuyên dùng), hệ số theo phase, hoặc 4 giờ/SWP cố định. Người chọn hệ số chung; AI tính 984 ÷ 387 = 2,543 giờ/SWP |
| **Báo cáo tiến độ** | Script Python gọi GraphQL và Claude Code viết báo cáo (không dùng `tkm:pm-report-project`, vì skill đó ghi `progress.md` theo mẫu khác với yêu cầu LAB-5) | Prompt: "giả lập sprint 4". AI đề xuất kịch bản: Sprint 1–3 xong đúng kế hoạch; 2 chỗ lệch có lý do từ các điểm chưa chốt của story (Q-26 làm #6 trễ; thiếu giá trị ngày chốt làm #93 bị chặn). Script đặt Status cho 69 mục trên Project; AI tính burndown theo SWP từ ngày hoàn thành của từng task và viết bảng rủi ro dựa trên §10 của các story |
| Kế hoạch, DoD, câu hỏi khách | `tkm:pm-plan-project`, `tkm:pm-define-dod` | Tạo overview, stakeholders, qa.md (4 câu hỏi khách, tiếng Nhật), define-dod (13 tiêu chí), gắn D-ID vào 13 story |

## 2. Review output của AI

**Con người review ở các bước:** duyệt từng block khi làm story; duyệt bản nháp chia task trước khi ghi GitHub; duyệt cấu trúc Project; duyệt 5 Issue mẫu khi chấm SWP; chọn cách quy giờ; duyệt các tiêu chí DoD; duyệt mọi thay đổi mốc trong schedule.

**Vấn đề phát hiện trong output của AI và cách xử lý:**

| # | Vấn đề | Phát hiện bằng cách nào | Xử lý |
| --- | --- | --- | --- |
| 1 | AI khuyên đưa **ảnh ký hiệu viết tay** vào phạm vi E-02-S01, với lý do "khách đã thấy trong ước lượng". Thực ra proposal v2 gửi khách ghi ảnh là **ngoài phạm vi**; chỉ estimate v1 có | Khi làm PLAN, AI đọc lại proposal và tự báo mâu thuẫn | Bỏ ảnh khỏi story, ghi là ứng viên change request (QA-003), thu hẹp task #96, #97 và cập nhật Issue |
| 2 | Schedule ban đầu dựa trên **estimate v1 (201 MD)**, trong khi proposal gửi khách là **v2 (177 MD)** | Phát hiện cùng lúc với #1 | Chạy lại SCH theo v2; giữ các mốc khách đã thấy, phần dư 15 ngày thành buffer |
| 3 | AI ghi "PM đã xác nhận" vào schedule.md cho một phép tính buffer mà người chưa xác nhận | AI tự đọc lại trước khi báo cáo | Sửa thành "đã kiểm tra" |
| 4 | Body của 10 Issue còn ghi "story chưa có chi tiết", vì AI tạo lại body **trước** khi sửa comment trong task-list | Phát hiện khi chuẩn bị dữ liệu chấm SWP | Sửa trong dữ liệu gửi worker, rồi tạo lại body trên GitHub |
| 5 | Worker gán chuyên môn `Unknown` cho task 要件ヒアリング nhưng độ tin cậy `medium` | Bộ validate của skill từ chối | Gửi đúng 3 worker liên quan một vòng sửa duy nhất; điểm không đổi |
| 6 | Vài worker xếp signature sai thứ tự quy định | Đối chiếu với từ vựng của skill khi gộp kết quả | Chuẩn hóa thứ tự trước khi validate (không đổi điểm) |
| 7 | Iteration đầu tiên bắt đầu thứ Ba (2026-12-01), nên Sprint 4 lệch một ngày so với ngày bắt đầu phát triển (thứ Hai 2027-01-11) | AI tự kiểm ngày sau khi tạo trường | Xóa và tạo lại trường Iteration bắt đầu thứ Hai 2026-11-30 |
| 8 | Transfer Issue từ repo private sang repo public bị GitHub chặn | Lỗi API ngay ở Issue đầu tiên | Người chọn cách tạo bản sao ở repo Lab5 và đóng Issue cũ kèm link; chưa có gì bị thay đổi trước đó |
| 9 | AI dùng một hệ số chung để quy giờ, khiến task tài liệu thiết kế gần bằng task code (thiết kế 39,1 MD so với 22 MD ở LAB-1) | So từng phần với LAB-1 khi viết estimate.md | Ghi rõ trong estimate.md §4; đề xuất cải thiện ở phần 3 |

## 3. Điểm đặc biệt trong cách dùng AI

**Hiệu quả:**
- Mỗi quyết định được hỏi bằng 2–4 phương án kèm một khuyến nghị và lý do. Người duyệt nhanh mà vẫn là người quyết.
- Mọi thao tác ghi GitHub đều qua script **chạy lại an toàn** (bỏ qua dòng đã xong, ghi URL ngay sau mỗi Issue). Nhờ vậy lỗi mạng giữa chừng (502, mất kết nối ở Issue thứ 32) không gây Issue trùng.
- Chấm SWP bằng worker cô lập và script validate cố định: điểm tính bằng ma trận, không do AI tự cộng; mọi con số trong báo cáo lấy từ payload đã validate.
- Để giảm token, phạm vi story chỉ gửi một lần dưới dạng `contextFacts` có trích nguồn, thay vì lặp lại trong body của từng task. Dữ liệu mỗi lô giảm từ khoảng 25.000 ký tự xuống khoảng 6.000.

**Chưa tốt, cần cải thiện khi làm thật:**
- **Quy giờ:** nên dùng hệ số theo phase hoặc theo loại việc. Một hệ số chung làm sai phân bổ giữa thiết kế, phát triển và kiểm thử.
- **Worker chấm trên dữ liệu rút gọn:** rẻ hơn nhưng mất chi tiết của body đầy đủ. Khi làm thật nên dùng mức `high` (người chấm thứ hai trên các Issue rủi ro), hoặc gửi body đầy đủ cho các story lớn.
- **Kết quả worker:** file transcript của worker rỗng, nên phải chép tay JSON từ tin nhắn vào file. Tốn token và có rủi ro chép sai; cần cách xuất kết quả ra file.
- **Danh sách chuyên môn của skill** không có nhóm cho việc hỏi yêu cầu, nên 9 task 要件ヒアリング đều thành `Unknown` / `low`. Cần thống nhất cách phân loại các task không phải code.
- AI vẫn có lúc biến lựa chọn của mình thành "dữ kiện" (#1, #3 ở bảng trên). Cách bắt hiệu quả nhất là bắt AI đối chiếu lại với tài liệu gốc đã gửi khách trước mỗi quyết định về phạm vi.
