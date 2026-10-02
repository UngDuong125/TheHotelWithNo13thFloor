# 10 — Kế hoạch kiểm thử (QA)

## 1. Mục tiêu và phạm vi

- Đảm bảo game chạy ổn định trên Android (và Windows build).
- Đảm bảo **không softlock**, dữ liệu đúng, 5 kết thúc đạt được theo điều kiện.
- Đảm bảo trải nghiệm kinh dị, câu đố hợp lý, độ khó vừa phải.

## 2. Loại kiểm thử

| Loại | Mô tả | Khi nào |
|------|-------|---------|
| Smoke test | Mở game, vào Ca 1, thoát; chạy sau mỗi build | Mỗi build |
| Functional | Từng cơ chế, từng câu đố | Mỗi tính năng |
| Regression | Chạy lại ca đã xong sau khi sửa | Mỗi tuần |
| Pathing / Ending | Chơi theo đường để đạt từng kết thúc | Từ tuần 7 |
| Softlock | Cố tình bỏ lỡ vật phẩm/thứ tự lạ | Từ tuần 5 |
| Compatibility | Nhiều thiết bị và tỉ lệ màn hình | Tuần 8–9 |
| Performance | FPS, RAM, pin, dung lượng | Tuần 9 |
| Playtest | Người ngoài nhóm chơi, quan sát và khảo sát | Tuần 6, 9 |
| Accessibility | Cỡ chữ, giảm hiệu ứng, phụ đề | Tuần 9 |

## 3. Test case chức năng (mẫu)

| ID | Hạng mục | Bước | Kết quả mong đợi |
|----|----------|------|------------------|
| TC-001 | Save/Load | Chơi tới Ca 2, thoát, mở lại, Tiếp tục | Vị trí, đồng hồ, túi đồ, cờ giống trước khi thoát |
| TC-002 | Đồng hồ | Chuyển phòng, quan sát, giải đố | Thời gian tăng theo quy tắc; dừng khi hội thoại |
| TC-003 | Nút 13 Ca 1 | Đứng thang máy ca 1 lúc 00:13 | Nút nhấp nháy, không ấn được |
| TC-004 | Nút 13 Ca 2 | Trong khoảng 00:13–01:13 | Nút hiện, ấn được; ngoài khoảng thì ẩn |
| TC-005 | M02 mở nút 13 | Có M02, bất kỳ giờ nào ca 3 | Nút 13 hiện |
| TC-006 | Chỉ vào 13 một lần/ca | Vào lần 2 trong cùng ca | Nút bị vô hiệu hóa |
| TC-007 | Biến thể F13 | Vào lần lượt các ca | Lần 1 = A, 2 = B, 3 = C, ca 5 = D |
| TC-008 | Tỉnh táo = 0 (ca 2–4) | Cố tình để về 0 | Về sảnh, +60 phút, vật phẩm đã nhặt vẫn giữ |
| TC-009 | Tỉnh táo = 0 (F13-D) | Cố tình để về 0 | Cờ `sanityZeroD`, kết thúc E1 |
| TC-010 | Chìa khóa | Dùng I04 mở L08 | Cửa mở; không có I04 thì báo khóa |
| TC-011 | Inventory đầy | Nhặt khi đủ 12 ô | Thông báo; vật cốt truyện vào Hộp di vật |
| TC-012 | Gợi ý | Thất bại P03 4 lần | Hiện G1 → G2 → G3 theo cấp |
| TC-013 | Chất vấn đúng | Dùng C02 phản bác H-L1 | Hạnh bỏ lời nói dối; thiện cảm −2 |
| TC-014 | Chất vấn sai | Dùng manh mối không liên quan | Trust −1, NPC phản ứng "không liên quan" |
| TC-015 | Trust ngưỡng | Đưa Trust Bảo = 4 | Bảo đưa I07 |
| TC-016 | Xác nhận sự thật | Nối C03 và C17 | T2 xác nhận ✓ |
| TC-017 | CH04 đưa M04 | Đưa cho bà Ngô | C17/C19 mở; máy ảnh trả lại ở ca sau |
| TC-018 | Bẫy két | Nhập sai 3 lần P06 | Chuông báo, Hạnh −2, bị đưa ra khỏi văn phòng |
| TC-019 | Ngày lịch | Kiểm tra mọi lịch (L01, L03, L11) | Thiếu trang 13/9, không có lịch lệch ngày |
| TC-020 | Autosave | Hoàn thành puzzle | Autosave được tạo, Load lại giữ trạng thái puzzle |

## 4. Kiểm tra từng câu đố

Mỗi câu đố cần: (1) lời giải đúng hoạt động, (2) lời giải sai không phá trạng thái, (3) Reset hoạt động, (4) gợi ý đủ 3 cấp, (5) thoát giữa chừng không mất vật phẩm, (6) Save/Load trong lúc đang giải.

| Puzzle | Kiểm tra đặc biệt |
|--------|-------------------|
| P01 | Chọn chìa sai nhiều lần chỉ trừ thời gian |
| P03 | Chỉ chấp nhận "1309"; chuỗi khác không đổi trạng thái |
| P04 | Mọi bố cục ngẫu nhiên đều có lời giải; không có thế bí |
| P05 | Ghép đủ 3 mảnh theo mọi thứ tự nhặt |
| P06 | Chỉ chấp nhận "130904" |
| P07 | Chỉ một thứ tự đúng 2→4→1→5→3 |
| P08 | Đảo thứ tự băng không thành công; tốc độ chỉnh được |
| P09 | Mỗi vòng có đúng một chi tiết thay đổi; Tỉnh táo giảm đúng |
| P10 | Giai điệu khớp EV03; nhập sai quá 3 lần gây sự kiện Bóng Cháy |
| P11 | Đồng hồ nào cũng chỉnh được; bóng người di chuyển theo vòng cố định |
| P12 | Bấm SOS đúng (3 ngắn – 3 dài – 3 ngắn) cho phép bà Ngô thấy |
| P13 | Đặt đúng/sai ghi nhận điểm `altar`; ô 13 phản ứng đúng CH08 |

## 5. Kiểm tra softlock (danh sách rủi ro)

| Tình huống | Kỳ vọng |
|------------|---------|
| Bỏ lỡ I04 ở ca 1 | Ca 2 Hạnh cho mượn |
| Từ chối CH01 (không hứa) → thiếu I05 | Lấy ở L08 (đường B) |
| Báo Hạnh ở CH02 → mất I06 từ Tuấn | Vẫn có I06 qua P04 |
| Không ấn nút 13 ở ca 2 | Vẫn vào F13-A ở ca 3; ca 5 vẫn có F13-D |
| Bỏ lỡ M01 trong F13-B | Bảo trả lại nếu Trust ≥ 5, ca 4 |
| Không lấy M02 | Có thể nhận qua Hạnh bị vạch mặt ca 5 |
| Bỏ lỡ F13-C | Vào lại ca 5 bằng M02 (xem tài liệu 03) |
| Không đủ Trust Bảo cho I07 | Nhiệm vụ phụ cho Bảo (+1) |
| Hết giờ trước khi xong nhiệm vụ bắt buộc | Chuyển ca với cờ trễ, không game over |
| Tỉnh táo = 0 khi đang cầm vật phẩm quan trọng | Vật phẩm không mất |
| Thoát đột ngột trong hội thoại | Load lại về đầu hội thoại, không mất cờ đã ghi |

## 6. Kiểm thử các kết thúc

| Kết thúc | Kịch bản test | Xác minh |
|----------|---------------|----------|
| E1 | CH08 = Bước vào ô | Cutscene E1, thống kê cập nhật |
| E1 | Tỉnh táo = 0 ở F13-D | E1 |
| E2 | CH07 = Giao | E2 |
| E2 | CH05 = Nhận, truths < 3 | E2 |
| E3 | 2–3 sự thật, CH08 = Từ chối | E3 |
| E4 | M04 đưa bà Ngô, đủ băng, M03, P12, altar ≥ 10, CH07 = Giữ | E4 |
| E5 | E4 + 12 di vật, T5, Bảo Trust ≥ 7, CH08 = Gọi tên | E5 |
| Ranh giới | altar = 9 (E4 không đạt) → E3; altar = 11 (E5 không đạt) → E4 | Đúng như bảng điều kiện |
| Xung đột | CH07 = Giao nhưng CH08 = Bước vào | E1 (ưu tiên cao nhất) |

Dùng Debug Panel để đặt nhanh các biến `truths`, `altar`, `baoTrust`... rồi gọi `EndingResolver`.

## 7. Thiết bị kiểm thử đề xuất

| Nhóm | Ví dụ | Mục đích |
|------|-------|----------|
| Cấu hình thấp | Android 8, RAM 3GB | FPS, bộ nhớ |
| Tầm trung | Android 11–12, RAM 4–6GB | Mục tiêu chính |
| Cao cấp | Android 13+, 8GB | Tương thích |
| Tỉ lệ màn hình | 16:9, 19.5:9, 20:9, có tai thỏ | Safe area |
| Tablet | 10 inch | Bố cục UI |

## 8. Tiêu chí chất lượng

| Mức độ lỗi | Định nghĩa | Hạn xử lý |
|------------|-----------|-----------|
| Blocker | Crash, softlock, mất save | Sửa trong ngày |
| Major | Sai điều kiện kết thúc, puzzle không hoàn thành được | Trước bản Beta |
| Minor | Sai chính tả, vị trí UI lệch | Trước Release |
| Trivial | Hiệu ứng nhỏ | Nếu còn thời gian |

**Điều kiện phát hành:** 0 Blocker, 0 Major, ≤ 5 Minor, đạt đủ 5 kết thúc.

## 9. Mẫu báo cáo lỗi

```
Tiêu đề: [Mức độ] Mô tả ngắn
Build / Thiết bị:
Ca / Khu vực / Giờ trong game:
Bước tái hiện:
1.
2.
3.
Kết quả thực tế:
Kết quả mong đợi:
Ảnh chụp / video / log:
File save đính kèm:
Tần suất: Luôn luôn / Thỉnh thoảng / Một lần
```

## 10. Khảo sát playtest (rút gọn)

1. Bạn có hiểu mình phải làm gì ở ca 1? (1–5)
2. Có câu đố nào quá khó/quá dễ? Câu nào?
3. Có lúc nào bạn bị kẹt không biết đi đâu?
4. Mức độ sợ/hồi hộp? (1–5)
5. Bạn hiểu cốt truyện đến đâu? Tóm tắt trong 3 câu.
6. Kết thúc bạn nhận được là gì? Bạn có muốn chơi lại không?
7. Góp ý khác.
