# 08 — Nghệ thuật, âm thanh và giao diện (Art/Audio/UI Bible)

## 1. Định hướng hình ảnh

- **Phong cách:** 2D vẽ tay kiểu tranh màu nước tối + nét chì, góc nhìn ngang (side-view) cho phòng, hành lang có phối cảnh nhẹ.
- **Cảm giác:** khách sạn cổ Việt Nam thập niên 90: gạch hoa, đèn vàng, cửa gỗ sơn xanh, sàn đá mài, rèm nhung cũ.
- **Hai tông:** *Hiện tại* (ấm vàng, bóng đổ dài, bẩn nhẹ) và *Tầng 13* (lạnh xanh xám, đỏ cam của lửa, nhiễu hạt).
- **Nguyên tắc:** dùng ánh sáng để dẫn mắt; vật tương tác có viền sáng rất nhẹ khi bật "Quan sát"; kinh dị bằng chi tiết sai (số cửa sai, bóng lệch) thay vì quái vật.

### Bảng màu

| Vai trò | Mã màu gợi ý | Dùng cho |
|---------|--------------|----------|
| Nền tối | `#14110F` | Nền UI, bóng đổ |
| Vàng đèn | `#E0B15A` | Đèn hành lang, chữ nhấn |
| Xanh rêu | `#2F4A45` | Tường cũ, cửa |
| Đỏ cháy | `#B3361F` | Tầng 13, cảnh báo, lửa |
| Trắng ngà | `#EDE6D5` | Giấy, chữ chính |
| Xám lạnh | `#6C7A89` | Tầng 13 (A, B, D) |
| Xanh nhạt linh hồn | `#8EC9C0` | Nhạc hộp, Thu Hà |

### Quy tắc ánh sáng theo khu vực
| Khu vực | Ánh sáng |
|---------|----------|
| Sảnh | Vàng ấm, bóng mềm, đồng hồ dừng 00:13 |
| Hành lang | Đèn nhấp nháy, hành lang dài, cuối hành lang tối |
| Bếp / Kho lạnh | Trắng lạnh huỳnh quang |
| Hầm | Đèn pin là nguồn sáng chính |
| Sân thượng | Ánh trăng + đèn cảnh báo máy bay đỏ |
| Tầng 13 | Xanh xám, viền đỏ cam; F13-C ấm hơn như ký ức |

## 2. Nhân vật (concept)

| Nhân vật | Mô tả hình ảnh | Chú ý |
|----------|----------------|-------|
| Châu | 26 tuổi, tóc buộc thấp, đồng phục áo sơ mi trắng + gile xanh đậm, mặt dây chuyền cũ | Thay đổi biểu cảm: bình thản → lo → quyết tâm |
| Hạnh | 54 tuổi, áo dài tối màu, tóc búi, mắt sắc | Luôn nở nụ cười lịch sự |
| Bảo | 62 tuổi, đồng phục bảo vệ cũ, vai hơi chùng, đeo chùm chìa | Bàn tay run |
| Tuấn | 24 tuổi, tạp dề, tay có sẹo bỏng | |
| Bà Ngô | 70 tuổi, áo bà ba, kính dày, khăn len | |
| NPC05 áo mưa | Bóng cao, áo mưa nhựa nhàu, không thấy mặt | Chỉ có silhouette |
| NPC06 Thu Hà | Ánh sáng ấm mờ, mái tóc dài, nụ cười | Luôn mờ, không rõ nét |
| Bóng Cháy | Hình người cháy xém, chuyển động giật | Chỉ ở F13-B |

Mỗi nhân vật có 4–6 biểu cảm chân dung cho hội thoại.

## 3. Danh sách asset (ước tính tối thiểu)

| Nhóm | Số lượng | Ghi chú |
|------|----------|---------|
| Background cảnh | 26–28 | Nhiều cảnh tái dùng với biến thể ánh sáng |
| Chân dung nhân vật | 6 × 5 biểu cảm | |
| Sprite nhân vật nhỏ (nếu có đi bộ trong hành lang) | Châu + 5 | Có thể dùng chỉ khi chuyển cảnh |
| Vật phẩm (icon + ảnh chi tiết) | 18 + 12 + 22 manh mối | Icon 128×128, ảnh xem chi tiết 1024×1024 |
| Câu đố UI | 13 bố cục | Tái dùng thành phần |
| Hiệu ứng | nhiễu, vignette, lửa, khói, mưa, nháy đèn | Shader đơn giản |
| UI | Nút, khung, icon HUD, bảng ghim | Bộ UI kit thống nhất |
| Cutscene | 5 kết thúc × 1–3 minh họa | Dạng tranh tĩnh + chuyển động nhẹ |

## 4. Âm thanh

### Nhạc
| ID | Tên | Dùng ở | Tâm trạng |
|----|-----|--------|-----------|
| MU01 | Menu chính | Menu | Lạnh, một nốt piano |
| MU02 | Sảnh ban đêm | L01 | Ambient thấp, tiếng chuông xa |
| MU03 | Giai điệu nhạc hộp | Mô-típ chính (5 nốt) | Dịu, hơi lệch tông |
| MU04 | Tầng 13 — A/B | F13-A/B | Drone, tiếng kim loại |
| MU05 | Tầng 13 — Ký ức | F13-C | Nhạc phòng trà 2004 méo |
| MU06 | Đối đầu | Ca 5 | Căng thẳng, nhịp tim |
| MU07 | Kết thúc E1–E5 | Cutscene | Mỗi kết thúc một biến thể của MU03 |

### SFX tiêu biểu
Thang máy (mở/đóng/chuông), bước chân (sàn đá/gỗ/kim loại), cửa kẹt, khóa/chìa, giấy lật, điện thoại phòng trống, nước chảy, lò hơi, ngọn lửa, máy cassette, đèn nhấp nháy, tiếng gõ, tiếng thở, nhiễu radio, tiếng chuông cháy (rất ngắn, tránh gây giật mình).

### Thoại
- Phiên bản 1: chỉ chữ + vài tiếng đệm (thở, cười khẽ, giọng Thu Hà trong băng).
- Nếu có lồng tiếng: ưu tiên Thu Hà (băng ghi âm) và Bảo.

### Nguyên tắc âm thanh
- Im lặng cũng là công cụ: giảm nhạc trước sự kiện.
- Không dùng âm thanh quá to bất ngờ; có tùy chọn "giảm cú giật mình".
- Tầng 13: lọc thông thấp + reverb; Tỉnh táo càng thấp, âm thanh càng méo.

## 5. UI/UX chi tiết

| Thành phần | Mô tả |
|------------|-------|
| HUD | Đồng hồ ca (trên-trái), nút Túi đồ (dưới-phải), Sổ ca, Bảng manh mối, Quan sát (mắt) |
| Hotspot | Viền sáng nhẹ khi đã "phát hiện"; chạm → hiện nhãn hành động (Xem / Nhặt / Mở / Nói chuyện) |
| Túi đồ | Lưới 12 ô + Hộp di vật; chạm giữ để kiểm tra, kéo vật vào hotspot để dùng |
| Bảng manh mối | Giấy ghim, dây nối đỏ, 5 ô sự thật ở trên; tự đánh dấu ✓ khi xác nhận |
| Hội thoại | Khung chữ, tên nhân vật, thanh Trust ẩn (hiển thị bằng biểu tượng cảm xúc nhỏ khi thay đổi) |
| Thang máy | Bảng nút thật; nút 13 phát sáng đỏ mờ khi có điều kiện |
| Thanh Tỉnh táo | Chỉ hiện ở tầng 13: viền màn hình tối dần, tim đập |
| Tutorial | Ca 1 hướng dẫn bằng sự kiện (không popup dài) |

### Khả năng tiếp cận (Accessibility)
- Cỡ chữ 3 mức, tương phản cao.
- Giảm nhấp nháy / giảm rung màn hình.
- Phụ đề cho mọi âm thanh quan trọng (ví dụ "[Tiếng nhạc hộp]").
- Tùy chọn cảnh báo nội dung và nút "Bỏ qua tạm" câu đố.
- Vùng chạm tối thiểu 48dp.

## 6. Tên file và quy ước asset

```
bg_L01_lobby_day.png        # bg_{ID}_{tên}_{biến thể}
ch_NPC02_bao_neutral.png    # ch_{NPC}_{tên}_{biểu cảm}
it_I04_key_storage.png      # it_{ID}_{tên}
cl_C03_newspaper.png        # cl_{ID}_{tên}
ui_btn_inventory.png
sfx_elevator_chime.wav
mu_MU03_musicbox.ogg
```
