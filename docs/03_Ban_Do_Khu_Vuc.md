# 03 — Bản đồ và thiết kế khu vực (Level Design)

## 1. Sơ đồ tổng thể

```
         [R] Sân thượng (L14)  <- thang thoát hiểm ngoài trời từ tầng 12
              |
      F13  (L16, ẩn: F13-A/B/C/D)
              |
 F12  Văn phòng quản lý (L13)
 F11  Hành lang + P1104 (L12)
 F10, F9  Hành lang chung (cảnh dùng chung)
 F8   Hành lang + P807, P808 (L11)
 F7, F6   Hành lang chung
 F5   Hành lang + P502, P505 (L10)
 F4   Hành lang chung
 F3   Kho đồ thất lạc + vật tư (L08)
 F2   Nhà hàng (L07), Bếp (L05), Kho lạnh (L06)
 F1   Sảnh chính (L01), Quầy lễ tân (L02), Phòng bảo vệ (L03)
 B1   Tầng hầm (L15): Phòng nồi hơi, hành lang cũ, cầu thang thoát hiểm bị hàn
 Thang máy (L04) nối B1–F12 (và 13 khi đủ điều kiện)
```

> Tầng 4, 6, 7, 9, 10 chỉ là cảnh hành lang dùng chung: cửa có biển "Đừng làm phiền", dùng cho nhiệm vụ giao đồ, có vài sự kiện nhỏ.

## 2. Danh sách khu vực

| ID | Khu vực | Tầng | Điều kiện mở | Nội dung chính | Tính năng cơ chế |
|----|---------|------|--------------|----------------|------------------|
| L01 | Sảnh chính | F1 | Mở từ đầu | Bảng tin, đồng hồ dừng lúc 00:13, lịch thiếu trang 13/9 | Điểm bắt đầu, hub |
| L02 | Quầy lễ tân | F1 | Mở từ đầu | Bảng chìa khóa (P01), ngăn kéo (I04), sổ khách | Nhiệm vụ, vật phẩm |
| L03 | Phòng bảo vệ | F1 | Mở từ đầu (ca 1), tủ khóa cần P03 (ca 2+) | Màn hình CCTV, máy cassette (I09), tủ khóa (M08), lịch rách | NPC02, P03, P08 |
| L04 | Thang máy | F1 → tất cả | Mở từ đầu | Bảng nút B1, 1–12; nút 13 theo điều kiện | Cổng vào tầng 13, sự kiện |
| L05 | Bếp | F2 | Mở từ đầu | Tuấn, hộp diêm (I18), kệ sau (M07) | NPC03, nhiệm vụ |
| L06 | Kho lạnh | F2 | Q2-2 + Tin tưởng Tuấn ≥ 2 | Thùng hàng (P04), cửa ngầm xuống hầm | P04 → mở L15 |
| L07 | Nhà hàng | F2 | Mở từ đầu | Khu bàn ăn, máy hát (flavor), vài khách | Nhiệm vụ phụ |
| L08 | Kho đồ | F3 | Chìa I04 (xong P01, ca 1) | Đồ thất lạc, mảnh ảnh B (I14), đĩa than (M05), chìa vạn năng dự phòng (I05, đường B) | Manh mối, vật phẩm |
| L10 | Hành lang F5 + P502, P505 | F5 | Mở từ đầu (P502 ca 1; P505 từ ca 3) | Hộp cầu chì (P02), nhẫn cưới (M11 ở P505) | Nhiệm vụ |
| L11 | Hành lang F8 + P807, P808 | F8 | Từ ca 2 (nhiệm vụ); P807 mở khi đến giao đồ | Bà Ngô, mảnh ảnh A (I13), lịch rách | NPC04, P05 |
| L12 | Hành lang F11 + P1104 | F11 | Chìa vạn năng I05 (ca 4) | Phòng bỏ trống phát nhạc, bật lửa vàng (M06) | Sự kiện nhạc hộp |
| L13 | Văn phòng quản lý | F12 | Hạnh có mặt đến 02:00; sau đó cần I05 (ca 3+) | Két sắt (P06), két (P06 → M02, I16, C14, C15), tủ hồ sơ (I16 → M03/C07, I12, C22) | P06, rủi ro bị bắt gặp |
| L14 | Sân thượng | R | Chìa I07 (Bảo tin tưởng ≥ 4, ca 4+) | Kèn harmonica (M10), đèn hiệu (P12) | P12, M10 |
| L15 | Tầng hầm | B1 | Chìa I06 (Tuấn hoặc xong P04, ca 2+) | Phòng nồi hơi (P07), hành lang cũ (I11 băng đoạn 2), bảng thông báo mất tích (C05), cầu thang hàn (cần I17) | P07, M09 |
| L16 | Tầng 13 | 13 | Xem mục 4 | 4 biến thể F13-A/B/C/D | P09–P11, P13 |

## 3. Luồng mở khóa tổng quát

```
Ca1: L01-L03, L05, L07, L10(P502) -> P01 -> I04 -> L08
Ca2: L11 (807), L06 (P04) -> I06 -> L15 (hầm sơ bộ) ; nút 13 -> F13-A
Ca3: L10(P505), L15 (P07), L13 (sau 02:00 cần I05) ; nút 13 -> F13-B
Ca4: L12 (I05), L14 (I07), cầu thang hàn (I17) ; nút 13 -> F13-C
Ca5: tất cả; bắt buộc F13-D
```

Bảng khóa chi tiết:

| Khu vực bị khóa | Khóa gì | Cách mở | Đường dự phòng (chống kẹt) |
|-----------------|---------|---------|----------------------------|
| L08 Kho đồ | I04 | P01 ở ca 1 | Hạnh cho mượn chìa ca 2 nếu chưa có |
| L06 Kho lạnh | Tin tưởng Tuấn ≥ 2 | Nói chuyện với Tuấn (Q2-2) | Làm nhiệm vụ phụ cho Tuấn (+1) |
| L15 Hầm | I06 | CH02 (Tuấn đưa) hoặc hoàn thành P04 | Cả hai đường đều có |
| P807 | Giao đồ Q2-1 | Gõ cửa | Có thể quay lại bất kỳ lúc nào |
| L12 P1104 | I05 | Hạnh cho vào ca 2 (CH01 = hứa) hoặc lấy ở L08 | Hai đường |
| L13 Văn phòng | Hạnh đi khỏi / I05 | Sau 02:00 | Q3-4 (đi vào chính thức) |
| L14 Sân thượng | I07 | Tin tưởng Bảo ≥ 4 | Nhiệm vụ phụ cho Bảo (+1) |
| Cầu thang hầm bị hàn | I17 | Lấy ở phòng nồi hơi sau P07 | — |

## 4. Tầng 13 — bốn biến thể

### Điều kiện hiện nút 13
```
available = (night >= 2 && 00:13 <= clock <= 01:13) || hasItem(M02)
if night == 1: flicker only
if enteredThisNight: disabled
```
Chọn biến thể: nếu `night == 5` thì luôn là **D**; ngược lại `variant = [A, B, C][min(enterCount, 2)]`. Biến thể A–C chưa xem vẫn còn đó nếu người chơi giữ M02 và vào lại ở ca 5 trước khi vào D (đường quay lại, tránh mất manh mối).

| ID | Tên | Môi trường | Nguy hiểm | Câu đố | Nội dung chính |
|----|-----|------------|-----------|--------|----------------|
| F13-A | **Hành lang vô tận** | Hành lang giống tầng 12 nhưng cửa đánh số sai, lặp vô hạn | NPC05 xuất hiện cuối hành lang; −Tỉnh táo khi nhìn trực diện | **P09** | M04 (máy ảnh Tùng) cuối hành lang; lần đầu nghe "tiếng đàn" |
| F13-B | **Phòng bỏ hoang** | Phòng tiệc cháy dở, bàn ghế đổ, đèn nến | "Bóng Cháy" tuần tra, trốn trong tủ khi có tiếng gõ | **P10** | M01 (nhạc hộp), I10 (băng đoạn 1), C03 |
| F13-C | **Khách sạn năm 2004** | Khách sạn y hệt hiện tại nhưng tươi mới, người qua lại như bóng | Không nguy hiểm trực tiếp; nhưng nếu chạm vào người sẽ bị "kéo" vào đoạn lửa | **P11** | M12, C16, C21, chứng kiến cảnh khóa cửa (T3), thấy bé Châu |
| F13-D | **Tầng 13 thật** | Phòng trà bị cháy sau tường, bàn thờ 13 ô | Cuối game, Tỉnh táo giảm nhanh hơn ×1.5 | **P13** | Kết thúc, CH08 |

### Cơ chế thoát khỏi tầng 13
- Mỗi biến thể có **"điểm thoát"** (thang máy xuất hiện lại khi giải xong câu đố hoặc khi Tỉnh táo còn > 0 và đến cửa).
- Nếu Tỉnh táo về 0 (ca 2–4): bị đẩy về L01 (sảnh), mất 60 phút game. Các vật phẩm nhặt được trong lần vào **vẫn giữ lại** để tránh người chơi cảm thấy bị phạt quá nặng.
- Có điểm an toàn (ánh đèn ấm, giai điệu nhạc hộp) để hồi Tỉnh táo.

## 5. Sự kiện bất thường

| ID | Sự kiện | Điều kiện kích hoạt | Hiệu ứng |
|----|---------|----------------------|----------|
| EV01 | Thang máy tự chạy lên 12 rồi về B1 | Ca 1, đứng ở sảnh sau 23:00 | Hướng dẫn người chơi nhìn bảng nút |
| EV02 | Điện thoại phòng trống reo | Ca 1+, đi qua P1104 (hoặc cảnh hành lang F11) | Chuỗi nhỏ; giọng thở |
| EV03 | Tiếng nhạc hộp văng vẳng | Ca 2+, gần 00:13 | Gợi ý giai điệu cho P10 |
| EV04 | Nước chảy ra từ gầm cửa 505 | Ca 3 | Dẫn tới Q3-2, nhặt M11 |
| EV05 | Bóng người áo mưa ở cuối hành lang | Ca 1, 2, 4 | −5 Tỉnh táo nếu đang ở tầng 13; ngoài thì chỉ là hiệu ứng |
| EV06 | CCTV hiện tầng không tồn tại | Ca 2+, phòng bảo vệ | Hé lộ T1, mở hội thoại với Bảo |
| EV07 | Đồng hồ sảnh nhích từ 00:13 | Ca 3+ | Báo hiệu cửa sổ tầng 13 |
| EV08 | Tuấn biến mất, bếp có mùi khói | Ca 3, nếu làm Q3-3 trước Q3-1 | Gặp bóng người ở hầm (−10 Tỉnh táo), nhặt M09 sớm |
| EV09 | Radio phòng bảo vệ phát tiếng ồn nhiễu rồi giọng Thu Hà | Ca 4, trước khi phát băng | Mở C11 gợi ý |
| EV10 | Lửa hiện trên bảng thang máy | Ca 5 | Dẫn tới F13-D |

## 6. Phạm vi cảnh (số lượng ước tính)

| Nhóm | Số cảnh | Ghi chú |
|------|---------|---------|
| Sảnh/F1 | 3 | L01, L02, L03 |
| F2 | 3 | Bếp, kho lạnh, nhà hàng |
| F3 | 1 | Kho đồ |
| Hành lang + phòng | 7 | F5, F8, F11 + 807, 505, 502, 1104 |
| Hành lang chung | 1 (tái dùng) | |
| F12 văn phòng | 2 | Phòng chính, két |
| Sân thượng | 1 | |
| Hầm | 3 | Nồi hơi, hành lang cũ, cầu thang |
| Thang máy | 1 | |
| Tầng 13 | 4–6 | 4 biến thể (có tái dùng tile) |
| **Tổng** | **~26–28 cảnh** | Bản MVP có thể cắt tối thiểu ~18 cảnh (xem tài liệu 09) |
