# 01 — Individual Problem Scan

Chủ đề: **Y tế** — trải nghiệm thật với app đặt lịch khám của Bệnh viện Đại học Y Hà Nội.

Vai trò: bệnh nhân trực tiếp dùng app để đặt lịch khám (và quan sát người nhà đi khám cùng).

## Scan rộng

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Tốn thời gian | Sau khi khám xong tại BV, phải chờ đợi để chụp X-quang — đây là bước khó chịu nhất trong cả quy trình | Bệnh nhân đặt lịch qua app | Xảy ra ở mọi lần khám cần chỉ định cận lâm sàng, thời gian chờ không được báo trước |
| 2 | Tốn thời gian | Sau khi khám, phải chờ đợi để xét nghiệm máu, tương tự bước chụp X-quang | Bệnh nhân đặt lịch qua app | Diễn ra cùng lượt khám, nối tiếp ngay sau bước chờ X-quang |
| 3 | Lặp lại | Dù đã đặt lịch khám online trước (chọn giờ buổi tối, chọn bác sĩ theo khoa), vẫn phải xếp hàng lại nhiều lần trong viện: đăng ký, chờ khám, chờ cận lâm sàng | Bệnh nhân, người nhà đi cùng | Lặp lại ở mọi lần đi khám, không phải sự cố một lần |
| 4 | AI có thể tốt hơn | App không báo thời gian chờ thực tế hoặc số thứ tự, nên bệnh nhân ngồi chờ mà không biết còn bao lâu tới lượt | Bệnh nhân dùng app | Không có ước tính hay cập nhật trạng thái nào trong lúc chờ |
| 5 | AI có thể tốt hơn | App chỉ hỗ trợ tìm bác sĩ/đặt khám theo khoa thủ công, chưa có gợi ý hay dự đoán khoa phù hợp dựa trên triệu chứng | Bệnh nhân chưa chắc nên khám khoa nào | Người dùng phải tự chọn khoa; app chỉ dừng ở chức năng "khám bệnh", không có bước gợi ý trước đó |
| 6 | Pain từ người khác | Người nhà đi cùng khám cũng gặp đúng vấn đề chờ đợi kéo dài này mỗi lần đi viện | Người nhà bệnh nhân | Ai đi khám cùng cũng phản ánh cùng một điểm nghẽn, không riêng cá nhân tôi |

Ghi chú: 6 problems đều xuất phát từ cùng một trải nghiệm thật (dùng app BV Đại học Y Hà Nội để đặt lịch khám), nhưng mỗi dòng là một điểm nghẽn/quan sát riêng biệt trong quy trình, không phải lặp lại cùng một ý.

## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Chờ đợi cận lâm sàng (X-quang + xét nghiệm máu) sau khi khám, không rõ thời gian chờ | Bottleneck rõ nhất, khó chịu nhất, lặp lại ở mọi lần khám, ảnh hưởng cả bệnh nhân lẫn người nhà | Chưa có số phút chính xác — mới ở mức cảm nhận "khá lâu", cần hỏi thêm người khác ở Phase 4 để có baseline |
| 2 | Đặt lịch online xong vẫn phải xếp hàng lại nhiều lần trong viện (đăng ký, khám, cận lâm sàng) | Cho thấy quy trình online và tại viện chưa liên thông, ảnh hưởng ngay từ lúc vào viện | Chưa rõ nguyên nhân là do quy trình bệnh viện hay do giới hạn của app |
| 3 | App thiếu gợi ý/dự đoán chọn khoa theo triệu chứng, chỉ hỗ trợ tìm bác sĩ thủ công | Vấn đề độc lập, rõ actor, có thể so sánh Rule/Workflow/Agent (gợi ý khoa dựa trên mô tả triệu chứng) | Chưa chắc mức độ sai khoa xảy ra thường xuyên thế nào, cần validate thêm |

## Problem Card #1 — Chờ đợi cận lâm sàng sau khi khám

**Problem 1 câu:**
Sau khi khám xong tại BV Đại học Y Hà Nội, bệnh nhân đặt lịch qua app phải chờ đợi chụp X-quang và xét nghiệm máu mà không biết trước thời gian chờ, đây là bước khó chịu nhất trong cả quy trình khám.

**Actor:**
Bệnh nhân dùng app đặt lịch khám của Bệnh viện Đại học Y Hà Nội (và người nhà đi khám cùng).

**Thời điểm / bối cảnh:**
Sau khi khám xong với bác sĩ, khi bác sĩ chỉ định làm thêm cận lâm sàng (chụp X-quang, xét nghiệm máu) trước khi có kết luận/điều trị tiếp theo.

**Current workflow:**

```text
1. Mở app, đặt lịch khám vào buổi tối
2. Tìm bác sĩ theo khoa (tự chọn thủ công)
3. Đến viện đúng giờ hẹn, xếp hàng đăng ký
4. Khám với bác sĩ
5. Bác sĩ chỉ định cận lâm sàng: chụp X-quang, xét nghiệm máu
6. Xếp hàng chờ chụp X-quang — không rõ thời gian chờ
7. Xếp hàng chờ xét nghiệm máu
8. Quay lại gặp bác sĩ để có kết luận / điều trị tiếp theo
```

**Bottleneck:**
Bước 6 — chờ chụp X-quang. Đây là bước bị đánh giá là khó chịu nhất, vì không có thông tin thời gian chờ hay số thứ tự nên bệnh nhân chỉ ngồi chờ thụ động.

**Impact:**
Lặp lại ở mọi lần đi khám cần cận lâm sàng, không phải sự cố một lần. Ảnh hưởng cả bệnh nhân và người nhà đi cùng. Thời gian chờ chính xác chưa đo được — mới ở mức cảm nhận "khá lâu"; cần khảo sát thêm người khác ở Phase 4 để có con số baseline đáng tin, thay vì tự ước lượng.

**Success metric:**
Chưa chốt số liệu cụ thể ở bước này. Hướng đo có thể là: (a) thời gian chờ trung bình từ lúc khám xong đến lúc có kết quả cận lâm sàng, (b) mức độ bệnh nhân biết trước thời gian chờ ước tính (có/không), thay vì chỉ nói "nhanh hơn".

**Non-AI alternative:**
Bảng hiển thị số thứ tự điện tử tại khu chụp X-quang/xét nghiệm, hoặc quy trình sắp lịch cận lâm sàng cố định theo khung giờ, có thể giảm một phần sự khó chịu mà không cần AI.

**AI hypothesis:**
AI/hệ thống có thể ước tính thời gian chờ dựa trên số lượng người đang xếp hàng và tốc độ xử lý trung bình, rồi hiển thị trên app để bệnh nhân chủ động sắp xếp thời gian, thay vì ngồi chờ không rõ thời điểm.

**Quick gut:**
Workflow.

### Draft current workflow

```text
CURRENT STATE

[1 Đặt lịch qua app: vài phút]
→ [2 Tìm bác sĩ theo khoa (thủ công)]
→ [3 Đăng ký tại viện, xếp hàng]
→ [4 Khám với bác sĩ]
→ [5 Chỉ định cận lâm sàng]
→ [6 Chờ chụp X-quang — không rõ thời gian]  <-- bottleneck
→ [7 Chờ xét nghiệm máu]
→ [8 Quay lại gặp bác sĩ để kết luận]
```

### Draft future workflow

```text
FUTURE STATE

[1 Đặt lịch qua app + chọn khoa có gợi ý theo triệu chứng]
→ [2 App hiển thị số thứ tự/thời gian chờ ước tính khi đăng ký]
→ [3 Khám với bác sĩ]
→ [4 Chỉ định cận lâm sàng]
→ [5 App báo thời gian chờ ước tính cho X-quang/xét nghiệm, bệnh nhân chủ động chờ hoặc quay lại đúng giờ]  <-- human vẫn tự quyết định chờ ở đâu
→ [6 Nhận kết quả + gặp bác sĩ kết luận]

Fallback: nếu ước tính thời gian sai lệch nhiều → quay về xếp hàng thủ công như hiện tại, nhân viên y tế vẫn kiểm soát thứ tự thực tế.
```

## Problem Cards #2 và #3 — tóm tắt

| Card | Actor | Bottleneck | Metric | Quick gut | Vì sao chưa chọn làm #1 |
|---|---|---|---|---|---|
| Xếp hàng lại nhiều lần dù đã đặt lịch online | Bệnh nhân, người nhà | Quy trình online và tại viện chưa liên thông (đăng ký, khám, cận lâm sàng đều phải xếp hàng riêng) | Số lần xếp hàng/lượt khám | Rule / Workflow | Chưa rõ do quy trình bệnh viện hay giới hạn app, phạm vi có thể rộng hơn 1 buổi lab |
| Thiếu gợi ý chọn khoa theo triệu chứng | Bệnh nhân chưa rõ nên khám khoa nào | App chỉ có tìm kiếm thủ công, không có bước gợi ý trước | Tỷ lệ chọn sai khoa / phải đặt lại lịch | Rule / Workflow | Chưa validate được tần suất chọn sai khoa xảy ra thật sự nhiều hay ít |

## Chọn card muốn pitch nhất

```text
Card #1 — Chờ đợi cận lâm sàng (X-quang + xét nghiệm máu) sau khi khám, không rõ thời gian chờ.
```

Vì sao:

```text
Đây là bottleneck cụ thể nhất, lặp lại ở mọi lần khám, có actor rõ (bệnh nhân + người nhà), và có thể so sánh được Non-AI (bảng số thứ tự điện tử) với hướng AI hỗ trợ (ước tính thời gian chờ).
```

Câu hỏi tôi muốn nhóm challenge:

```text
Nếu không đo được số phút chờ chính xác, nhóm có nên chọn bài này không, hay cần validate baseline trước? Việc "ước tính thời gian chờ" có nên là Rule (đếm số người xếp hàng) hay cần phức tạp hơn tới mức Agent?
```

---

*Day 02 — Individual Problem Scan (Nguyễn Xuân Hùng)*
