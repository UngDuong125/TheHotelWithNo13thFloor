# 01 — Game Design Document (GDD)

## 1. Tổng quan

| Mục | Nội dung |
|-----|----------|
| Tên game | **Khách sạn không có tầng 13** |
| Thể loại | Giải đố – Kinh dị – Trinh thám |
| Nền tảng | Android (chính), Windows (test) |
| Góc nhìn | 2D, chuyển cảnh theo phòng, chạm để tương tác |
| Đối tượng | 16+ (kinh dị tâm lý, không máu me quá mức) |
| Số người chơi | 1 |
| Thời lượng | 5 ca trực, khoảng 2–2,5 giờ; chơi lại để thấy các kết thúc khác |

### Pitch một câu
Một cô gái trẻ nhận ca đêm tại khách sạn cổ chỉ có 12 tầng, nơi nút "13" thỉnh thoảng hiện lên trong thang máy. Mỗi người cô gặp đều phản ứng khác nhau về tầng đó, và cô dần nhận ra vụ mất tích 20 năm trước gắn với chính mình.

### Trụ cột thiết kế (Design pillars)
1. **Sợ vì không biết, không vì giật mình.** Bầu không khí, âm thanh và chi tiết bất thường quan trọng hơn jumpscare.
2. **Mọi vật nhỏ đều có thể là mảnh ghép.** Vật phẩm trông vô nghĩa ở ca 1 sẽ có tác dụng ở ca 4–5.
3. **Lời người khác không phải lúc nào cũng đúng.** Người chơi phải đối chiếu lời khai với manh mối.
4. **Lựa chọn của bạn quyết định sự thật bạn thấy.** Thứ tự làm việc và quyết định thay đổi sự kiện và kết thúc.

## 2. Vòng lặp chơi (Core loop)

```
Nhận ca (22:00) -> Chọn thứ tự làm việc -> Di chuyển & khám phá
      ^                                            |
      |                                  Thu thập vật phẩm/manh mối
      |                                            |
 Kết thúc ca (06:00) <- Giải đố / Nói chuyện / Lựa chọn
      |
 Tóm tắt ca: bảng manh mối cập nhật, cờ sự kiện được lưu
```

- **Vòng ngắn (vài phút):** đến khu vực → quan sát → nhặt/dùng đồ → giải đố → mở lối đi mới.
- **Vòng trung (một ca):** hoàn thành nhiệm vụ bắt buộc, chọn nhiệm vụ phụ, đối mặt tầng 13 trong khung giờ cho phép.
- **Vòng dài (cả game):** gom 5 sự thật (T1–T5), 12 di vật, tạo niềm tin với nhân vật → quyết định kết thúc.

## 3. Hệ thống thời gian

- Một ca trực chạy từ **22:00 đến 06:00** (480 phút trong game), khoảng 20–25 phút thực.
- Đồng hồ tăng theo hành động: chuyển phòng +2 phút, quan sát/tìm kiếm +5, mỗi bước nhiệm vụ +10, giải đố +10 đến +20. Đồng hồ **dừng** khi hội thoại, mở túi đồ hoặc menu.
- Nhiệm vụ bắt buộc phải xong trước 06:00. Nếu trễ, Hạnh nhắc nhở (giảm thiện cảm của NPC01) nhưng không game over.
- **Cửa sổ tầng 13:** nút 13 hiện từ **00:13 đến 01:13** từ ca 2 trở đi (xem mục 4.6).

## 4. Bảy cơ chế cốt lõi

### 4.1 Khám phá khách sạn
- Di chuyển giữa các khu vực: sảnh chính, hành lang các tầng, phòng khách, kho đồ, phòng bảo vệ, bếp, sân thượng, tầng hầm, thang máy và tầng 13 (chi tiết ở tài liệu 03).
- Mỗi khu vực là một hoặc nhiều "cảnh" với các điểm tương tác (hotspot). Chạm vào hotspot để quan sát, nhặt, mở hoặc đọc.
- **Khóa/mở khu vực** theo ba loại điều kiện: (a) vật phẩm (chìa khóa), (b) mốc thời gian/ca, (c) sự kiện hoặc độ tin tưởng của NPC.
- Hotspot có ba trạng thái: chưa phát hiện → đã phát hiện (nhấp nháy nhẹ) → đã khai thác (mờ đi).
- Nút "Quan sát" hiển thị các điểm bất thường trong phòng (có thời gian hồi, tốn 5 phút game) để người chơi không phải mò từng pixel.

### 4.2 Công việc ca đêm
- Mỗi ca có **nhiệm vụ bắt buộc** (Q#-#, đánh dấu ★) và **nhiệm vụ phụ**. Loại việc: mang đồ lên phòng, kiểm tra phòng, tìm đồ thất lạc, sửa thiết bị, hỗ trợ khách.
- Sổ ca (Shift Log) liệt kê nhiệm vụ, người chơi **tự chọn thứ tự**.
- Một số nhiệm vụ bình thường nhưng dẫn tới khu vực lạ hoặc sự kiện bất thường. Ví dụ: "kiểm tra tiếng động ở kho lạnh" dẫn xuống tầng hầm.
- **Thứ tự tạo ra sự kiện khác nhau** (ví dụ bảng bên dưới và bảng ở tài liệu 03).

| Nếu người chơi làm... | Trước... | Thì xảy ra |
|-----------------------|----------|------------|
| Q2-2 (Kho lạnh với Tuấn) | Q2-1 (Phòng 807) | Tuấn tin tưởng sớm (+1), nhưng bà Ngô cảnh giác hơn (khó mở lời) |
| Q2-1 (Phòng 807) | Q2-2 | Bà Ngô kể về con trai sớm, Tuấn thấy Châu "đã biết gì đó" và ít cởi mở |
| Q3-3 (Van nồi hơi) | Q3-1 (Đồ thất lạc) | Gặp bóng người ở tầng hầm; mất 10 Tỉnh táo nhưng nhặt được M09 sớm |
| Q4-3 (Phát băng) | Q4-1 (Sân thượng) | Ông Bảo bị bất ngờ, mất tin tưởng nếu Châu chưa có M08 |

### 4.3 Thu thập vật phẩm và manh mối
- **Túi đồ (Inventory):** tối đa 12 ô vật phẩm; vật phẩm quan trọng không thể bỏ. Có thể kết hợp (ví dụ: băng cassette + máy cassette), kiểm tra chi tiết (xoay, phóng to, đọc mặt sau).
- **Bảng manh mối (Clue Board):** mỗi manh mối (C##) tự thêm khi phát hiện. Có thể kéo nối hai manh mối để "suy luận". Nối đúng sẽ mở ra thông tin mới hoặc mở khóa lựa chọn hội thoại "Chất vấn".
- Có vật phẩm "gây nhiễu" ban đầu vô nghĩa (ví dụ ảnh xé, mảnh giấy ghi số) nhưng cần ở ca sau.
- Danh sách đầy đủ ở tài liệu 05.

### 4.4 Giải đố
- 13 câu đố (P01–P13), phân loại: ghép/nối, mật mã, sắp xếp, nhịp/âm thanh, quan sát, thoát hiểm (xem tài liệu 04).
- Mỗi câu đố có **hệ thống gợi ý 3 cấp**: (1) nhắc nơi cần xem, (2) nhắc loại manh mối, (3) chỉ cách làm. Dùng gợi ý cấp 3 không phạt nhưng đánh dấu để thống kê.
- Câu đố dùng dữ liệu người chơi đã thu thập (mật khẩu, ký hiệu, ảnh), không đòi hỏi kiến thức ngoài.
- Không có câu đố nào chặn hoàn toàn: sau 3 lần thất bại liên tiếp xuất hiện nút "Bỏ qua tạm" (trừ P13 và P09–P11 ở tầng 13).

### 4.5 Tương tác với nhân vật
- Hội thoại dạng cây lựa chọn (Ink). Lựa chọn gồm: **Hỏi**, **Đưa vật phẩm**, **Chất vấn** (dùng manh mối để vạch lời nói dối), **Ra đi**.
- Mỗi NPC có chỉ số **Tin tưởng (0–10)** và hồ sơ **trung thực** (nói thật / che giấu / nói dối). Quy tắc chi tiết ở tài liệu 06.
- Thái độ thể hiện: thân thiện → mở thêm thông tin; cảnh giác → trả lời ngắn; từ chối → khóa nhánh thông tin tạm thời (có thể sửa bằng hành động bù).

### 4.6 Tầng 13
- Nút 13 chỉ xuất hiện khi thỏa **một trong hai**:
  1. Ca 2–5 và đồng hồ trong khoảng **00:13–01:13**; hoặc
  2. Người chơi đang giữ **M02 (Đồng hồ bỏ túi)**: nút hiện bất kỳ lúc nào trong ca.
  - Ca 1: nút nhấp nháy mờ, không ấn được (hướng dẫn / điềm báo).
- Mỗi ca chỉ vào tầng 13 tối đa một lần. Biến thể được chọn theo **số lần đã vào** (lần 1 = A, lần 2 = B, lần 3 = C), nên bỏ qua một ca **không làm mất nội dung**; ca 5 luôn là D:
  - **F13-A** Hành lang vô tận (ca 2) · **F13-B** Phòng bỏ hoang (ca 3) · **F13-C** Khách sạn năm 2004 (ca 4) · **F13-D** Tầng 13 thật / Lễ tưởng niệm (ca 5, bắt buộc).
- **Độ nguy hiểm:** trong tầng 13 có thanh **Tỉnh táo (0–100)**.
  - Giảm khi: ở lâu (−1/10 giây), thấy "Bóng Cháy" (−15), nghe tiếng gọi tên (−10), chọn sai lối (−10).
  - Hồi khi: nghe nhạc hộp M01 (+5/lần, có hồi chiêu), đứng cạnh nguồn sáng an toàn, lấy được di vật (+10).
  - Về 0 trong ca 2–4: bị "cuốn" ra thang máy về sảnh, mất 60 phút game, đánh dấu cờ `thrown_out_N`. Về 0 trong F13-D: dẫn tới **E1**.
- Bí mật quan trọng nhất (T1, T3, T4, T5) chỉ có ở tầng 13.

### 4.7 Lựa chọn và nhiều kết thúc
- 8 lựa chọn quan trọng (CH01–CH08) + hàng chục lựa chọn nhỏ chỉ tăng/giảm tin tưởng.
- Kết thúc: **2 kết thúc xấu (E1, E2), 1 trung tính (E3), 1 tốt (E4), 1 bí mật (E5)** — điều kiện ở tài liệu 06.
- Màn kết có thống kê: sự thật tìm được /5, di vật /12, kết thúc đã mở /5 để khuyến khích chơi lại.

## 5. Hệ thống tiến triển và cờ trạng thái

| Hệ thống | Mô tả | Lưu trong |
|----------|-------|-----------|
| Ca hiện tại | 1–5 | `progress.night` |
| Đồng hồ | phút trong ca (0 = 22:00, 480 = 06:00) | `progress.shiftMinutes` |
| Cờ sự kiện | bool theo tên (ví dụ `met_tuan`) | `flags{}` |
| Tin tưởng NPC | 0–10 mỗi NPC | `trust{}` |
| Túi đồ | danh sách ID vật phẩm | `inventory[]` |
| Manh mối | ID + trạng thái (found/linked) | `clues{}` |
| Sự thật | T1–T5 đã xác nhận | `truths[]` |
| Di vật | M01–M12 đã có | `keepsakes[]` |
| Lựa chọn | CH01–CH08 | `choices{}` |
| Tỉnh táo | 0–100 (chỉ tầng 13) | `runtime.sanity` |

## 6. Giao diện (UI/UX) — tóm tắt

| Màn hình | Thành phần chính |
|----------|------------------|
| Menu chính | Chơi mới, Tiếp tục, Kết thúc đã mở, Cài đặt, Thoát |
| HUD khi chơi | Đồng hồ ca (góc trên), nút Túi đồ, Sổ ca, Bảng manh mối, Quan sát, Menu |
| Thang máy | Bảng nút B1, 1–12 (+ nút 13 khi đủ điều kiện) |
| Hội thoại | Khung chữ dưới màn hình, ảnh chân dung, 2–4 lựa chọn, nút Chất vấn |
| Bảng manh mối | Bảng ghim, dây nối, 5 ô "Sự thật" |
| Tầng 13 | Thanh Tỉnh táo, hiệu ứng nhiễu/méo màn hình tăng dần |
| Cài đặt | Âm lượng (nhạc, SFX, thoại), cỡ chữ, giảm rung/nhấp nháy, ngôn ngữ, cảnh báo nội dung |

Chi tiết phong cách ở tài liệu 08.

## 7. Phạm vi và ưu tiên (MoSCoW)

| Mức | Nội dung |
|-----|----------|
| **Must** | 5 ca, khu vực tối thiểu (xem tài liệu 03), 7 cơ chế, P01–P08, F13-A/B/D, 5 kết thúc, lưu game |
| **Should** | F13-C đầy đủ, P09–P13 đầy đủ, 12 di vật, Clue Board kéo nối |
| **Could** | Lồng tiếng, nhật ký thống kê, thành tựu, tiếng Anh |
| **Won't (phiên bản 1)** | Multiplayer, 3D, thế giới mở |

## 8. Rủi ro thiết kế chính

| Rủi ro | Hướng giảm thiểu |
|--------|------------------|
| Lạc hướng, không biết làm gì | Sổ ca + nút Quan sát + gợi ý 3 cấp |
| Bỏ lỡ manh mối dẫn tới không mở được kết thúc tốt | Có đường dự phòng (ví dụ ông Bảo trả M01 nếu tin tưởng ≥ 5) |
| Quá nhiều nội dung so với nhân lực | Các tầng 4,6,7,9,10 chỉ là hành lang chung; tái sử dụng asset |
| Kinh dị gây khó chịu quá mức | Cài đặt giảm hiệu ứng, cảnh báo nội dung, không có cảnh bạo lực trực diện |
