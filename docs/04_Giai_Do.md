# 04 — Thiết kế câu đố (P01–P13)

Quy ước gợi ý: **G1** nhắc nơi cần tìm, **G2** nhắc loại manh mối, **G3** nói cách làm. Độ khó: ★ dễ, ★★ vừa, ★★★ khó.

## Tổng quan

| ID | Tên | Ca | Khu vực | Loại | Độ khó | Phần thưởng |
|----|-----|----|---------|------|--------|-------------|
| P01 | Bảng chìa khóa lễ tân | 1 | L02 | Ghép/nối | ★ | I04 Chìa kho đồ |
| P02 | Hộp cầu chì tầng 5 | 1 | L10 | Nối dây | ★ | Sửa đèn phòng 502, I08 dùng xong |
| P03 | Tủ khóa phòng bảo vệ | 2 | L03 | Mật mã | ★★ | M08 Còi bảo vệ, C06 |
| P04 | Xếp thùng kho lạnh | 2 | L06 | Sắp xếp (đẩy thùng) | ★★ | Mở lối xuống hầm, I06 |
| P05 | Ghép ảnh xé | 3 | L11 / L08 / L02 | Ghép + thu thập | ★★ | C12, C13 |
| P06 | Két sắt văn phòng | 3 | L13 | Mật mã 6 số | ★★ | M02, C14, C15 |
| P07 | Van nồi hơi | 3 | L15 | Trình tự | ★★ | I17 Xà beng, M09 |
| P08 | Ghép băng cassette | 4 | L03 | Ghép + âm thanh | ★★★ | C09–C11 đầy đủ |
| P09 | Hành lang vô tận | 2 | F13-A | Quan sát | ★★ | Lối thoát, M04 |
| P10 | Giai điệu nhạc hộp | 3 | F13-B | Nhịp / ghi nhớ | ★★★ | M01, thoát |
| P11 | Đồng hồ năm 2004 | 4 | F13-C | Thời gian + stealth nhẹ | ★★★ | M12, C06, C21 |
| P12 | Đèn hiệu sân thượng | 5 | L14 | Mật mã Morse | ★★ | Gọi bà Ngô / cứu viện |
| P13 | Bàn thờ 13 ô | 5 | F13-D | Sắp xếp (đặt di vật) | ★★★ | Quyết định E1/E3/E4/E5 |

---

## P01 — Bảng chìa khóa lễ tân (Ca 1, hướng dẫn)
- **Mục tiêu:** Khách làm mất chìa, Châu phải tìm đúng chìa trên bảng 12 móc.
- **Cách chơi:** Mỗi chìa có hình đầu chìa và thẻ số cũ mờ. Tờ giấy ghi chú của khách mô tả: "chìa đầu tam giác, thẻ có số bắt đầu bằng 5".
- **Lời giải:** Chìa đầu tam giác, thẻ 502.
- **Gợi ý:** G1 "Đọc kỹ ghi chú của khách" · G2 "Hình đầu chìa quan trọng" · G3 "Móc thứ 5 từ trái".
- **Thất bại:** chọn sai chỉ mất 2 phút game, Hạnh liếc nhìn.
- **Thưởng:** sau khi trả chìa cho khách, Châu thấy ngăn kéo có I04 (Chìa kho đồ).

## P02 — Hộp cầu chì tầng 5 (Ca 1, hướng dẫn)
- **Mục tiêu:** Khôi phục điện phòng 502.
- **Cách chơi:** 3 dây (đỏ, xanh, vàng) cần nối từ 3 cầu chì đến 3 cổng; sơ đồ dán ở mặt trong nắp hộp. Cần I08 (cầu chì dự phòng) lấy ở quầy.
- **Lời giải:** Đỏ → cổng 1, Xanh → cổng 3, Vàng → cổng 2 (sơ đồ ghi hình dạng ổ cắm).
- **Gợi ý:** G1 "Xem mặt trong nắp" · G2 "Màu tương ứng cổng" · G3 hiện đường nối.
- **Sự kiện:** khi điện nháy, EV05 (bóng ở cuối hành lang) lần đầu.

## P03 — Tủ khóa phòng bảo vệ (Ca 2)
- **Mục tiêu:** Mở tủ khóa của Bảo (chứa M08 và C06).
- **Cơ chế:** khóa 4 số.
- **Lời giải:** **1309**.
- **Cách suy ra:** tờ lịch trong phòng chỉ còn ngày 13 và 14 của tháng 9, bị xé quanh ngày 13 (C01); hồ sơ trực có ghi "ngày hôm đó, 13/9" bị bôi đen; khi có cả hai người chơi thử "1309".
- **Gợi ý:** G1 "Có một ngày bị xé khỏi mọi cuốn lịch" · G2 "Ngày và tháng" · G3 "Nhập 1309".
- **Thưởng:** M08 (Còi), C06 (Nhật ký Khoa). Lưu ý: mở tủ trước khi có Tin tưởng Bảo ≥ 3 sẽ trừ 1 Tin tưởng.

## P04 — Xếp thùng kho lạnh (Ca 2)
- **Mục tiêu:** Đẩy 3 thùng hàng lên 3 ô đánh dấu để lộ cửa ngầm xuống hầm.
- **Cách chơi:** lưới 5×4 kiểu Sokoban nhẹ; người chơi vuốt để đẩy thùng; Reset không giới hạn.
- **Lời giải (mẫu):** thùng A lên ô ngoài cùng trái, thùng B ô giữa, thùng C ô phải; tổng 14 bước tối thiểu. Có sẵn 3 bố cục để chọn ngẫu nhiên.
- **Gợi ý:** G1 "Các ô vạch trắng" · G2 "Đẩy thùng cạnh tường trước" · G3 chỉ bước đầu.
- **Thưởng:** I06 (Chìa hầm) nếu chưa nhận từ Tuấn; M07 sau kệ.

## P05 — Ghép ảnh xé (Ca 3)
- **Thu thập 3 mảnh:** I13 trong ngăn kéo P807 (cần bà Ngô cho phép hoặc Tin tưởng ≥ 2), I14 ở Kho đồ (L08), I15 trong ngăn kéo quầy lễ tân (xuất hiện sau Q3-1).
- **Cách chơi:** ghép 3 mảnh thành ảnh nhân viên khách sạn 2004. Mảnh nào để đúng chỗ thì "khóa" vào.
- **Kết quả:** thấy Thu Hà bế bé gái đeo mặt dây chuyền giống I02. Mở C12 và khiến Châu so sánh với I02 (C13).
- **Gợi ý:** G1 "Ba mảnh ở ba nơi khác nhau" · G2 "Mép ảnh có hoa văn tường" · G3 tự ghép một mảnh.

## P06 — Két sắt văn phòng quản lý (Ca 3–5)
- **Mục tiêu:** Mở két của Hạnh, lấy M02, I16 (chìa tủ hồ sơ), C14, C15. Tủ hồ sơ (mở bằng I16) chứa M03/C07, I12 và C22.
- **Cơ chế:** 6 số.
- **Lời giải:** **130904** (ngày 13/09/2004).
- **Cách suy ra:** tờ hợp đồng "khai trương 1978, tu sửa 1998" không phải đáp án (đánh lạc hướng); bài báo C03 nêu ngày và năm; lịch thiếu ngày 13/9 là điểm nhắc.
- **Gợi ý:** G1 "Ngày bị xóa ở mọi nơi" · G2 "Cần thêm năm" · G3 "Nhập 130904".
- **Rủi ro:** thử sai 3 lần mở chuông báo → Hạnh xuất hiện nếu đang trong giờ có mặt; Tin tưởng Hạnh −2 và bị đuổi ra (không game over).

## P07 — Van nồi hơi (Ca 3)
- **Mục tiêu:** Khôi phục nước nóng, mở khoang chứa I17 và M09.
- **Cách chơi:** 5 van gắn mũi tên chỉ hướng dòng chảy trên sơ đồ ố vàng; phải mở theo thứ tự nước chảy từ bình vào ống chính.
- **Lời giải:** van 2 → 4 → 1 → 5 → 3.
- **Gợi ý:** G1 "Theo mũi tên trên sơ đồ" · G2 "Bắt đầu từ bình" · G3 "Bắt đầu bằng van 2".
- **Sự kiện:** nếu làm Q3-3 trước Q3-1 → EV08.

## P08 — Ghép băng cassette (Ca 4)
- **Điều kiện:** I09 (máy cassette), I10, I11, I12 (3 đoạn băng; lấy lần lượt ở: F13-B, hành lang cũ tầng hầm, tủ hồ sơ văn phòng).
- **Cách chơi:** đặt 3 đoạn vào đúng thứ tự dựa trên số đếm giây in trên nhãn (00:00–03:12) và nội dung nghe được (câu cuối đoạn trước nối câu đầu đoạn sau). Sau đó chỉnh tốc độ (trượt) để giọng nghe rõ.
- **Lời giải:** đoạn 1 (C09) → đoạn 2 (C10) → đoạn 3 (C11).
- **Thưởng:** nghe đủ giọng Thu Hà; xác nhận T3, T4.
- **Gợi ý:** G1 "Nhãn trên băng có ghi số" · G2 "Câu nối giữa các đoạn" · G3 hiện thứ tự.

## P09 — Hành lang vô tận (F13-A, Ca 2)
- **Luật:** Hành lang lặp. Mỗi vòng có đúng **một cánh cửa số khác** so với vòng trước (spot-the-difference). Chọn đúng cánh cửa để tiếp tục; chọn sai → Tỉnh táo −10, lặp lại.
- **Điều kiện hoàn thành:** đúng 3 vòng liên tiếp → lối ra và M04.
- **Ví dụ:** vòng 1 cửa 12-3 đổi thành 13-3; vòng 2 tấm bảng lối thoát hiểm đảo ngược; vòng 3 bức tranh trên tường đổi thành tấm ảnh.
- **Gợi ý:** G1 "Nhìn tường, không nhìn cuối hành lang" · G2 "Một chi tiết thay đổi mỗi vòng" · G3 viền sáng nhẹ lên chi tiết thay đổi.
- **Nguy cơ:** nhìn thẳng NPC05 → −5 Tỉnh táo/giây.

## P10 — Giai điệu nhạc hộp (F13-B, Ca 3)
- **Luật:** 5 nến trên bàn tiệc, mỗi nến tương ứng một nốt; nhạc hộp (từ EV03) phát giai điệu 5 nốt. Người chơi bấm lại đúng thứ tự để mở tủ chứa M01 và để đuổi "Bóng Cháy".
- **Lời giải:** giai điệu cố định (ví dụ nốt 3-1-4-2-5, đã nghe ở EV03 trước ca 3).
- **Cần:** I18 (hộp diêm) để thắp nến.
- **Gợi ý:** G1 "Nghe lại giai điệu" · G2 "Giai điệu đã xuất hiện trước đây" · G3 hiện thứ tự nốt 2 giây.
- **Trốn:** khi nghe tiếng gõ, phải ẩn vào tủ (không vào tủ đang có dấu cháy).

## P11 — Đồng hồ năm 2004 (F13-C, Ca 4)
- **Luật:** Châu là người quan sát trong khách sạn 2004; tìm và chỉnh 3 chiếc đồng hồ (sảnh, bếp, hành lang) về 00:13 để mở cửa thoát hiểm trước khi "dòng thời gian" cháy tới. Các bóng người di chuyển theo lịch; chạm vào bóng sẽ bị kéo vào lửa (−20 Tỉnh táo).
- **Ràng buộc:** không thể cứu ai; chỉ thu thập C16 (chứng kiến cảnh khóa cửa thoát hiểm), C21 (sơ đồ thang máy 2004) và M12 trên đường đi.
- **Gợi ý:** G1 "Bóng người đi theo vòng cố định" · G2 "Đồng hồ ở 3 tầng" · G3 hiện đồng hồ gần nhất.

## P12 — Đèn hiệu sân thượng (Ca 5)
- **Luật:** Đèn pin lớn gắn trên sân thượng. Còi (M08) của Khoa có mẩu giấy nhỏ ghi mã Morse mô tả tín hiệu cầu cứu của bảo vệ (3 ngắn – 3 dài – 3 ngắn).
- **Lời giải:** bấm nhấp nháy theo mã SOS; bà Ngô nhìn thấy từ phòng 807 và gọi cảnh sát.
- **Điều kiện:** có M08 (hoặc đoán SOS).
- **Hệ quả:** nếu thành công, mở được nhánh E4/E5 (có người ngoài biết).

## P13 — Bàn thờ 13 ô (F13-D, Ca 5)
- **Luật:** 13 ô trên bàn thờ, mỗi ô khắc tên một nạn nhân/mất tích. Châu đặt đúng di vật vào đúng ô. Ô thứ 13 đề **"Minh Châu, 6 tuổi"** để trống.
- **Cách suy ra ô nào của ai:** danh sách C05 (thứ tự tên), ảnh C12 (vị trí đứng), nhãn khắc nhỏ trên di vật.
- **Điểm số:** đặt đúng mỗi di vật +1. Cần ≥ 10/12 để "lễ" có hiệu lực (E4); 12/12 + CH08 đúng → E5.
- **Ô thứ 13 (CH08):** Châu có thể (a) bước vào ô (dù tên không được gọi): **E1**; (b) từ chối: tầng 13 không đóng (E3/E4 tùy điều kiện); (c) nói tên mình "Minh Châu" khi đã biết T5 và đặt I02 vào: **E5**.
- **Gợi ý:** G1 "Tên khắc trên di vật" · G2 "Thứ tự trong ảnh nhân viên" · G3 đặt thử 2 di vật.
