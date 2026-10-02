# 11 — Danh sách và mô tả tất cả asset

Tài liệu này liệt kê toàn bộ asset cần cho game *Khách sạn không có tầng 13*, bám theo các tài liệu 01–10 (ID khu vực L##, vật phẩm I##, di vật M##, manh mối C##, câu đố P##, nhạc MU##).

**Cột Ưu tiên:** `P0` = bắt buộc cho MVP · `P1` = nên có · `P2` = có thì tốt, cắt đầu tiên khi thiếu thời gian.
**Cột Tái dùng:** cho biết có thể dùng lại ảnh khác (đổi ánh sáng/màu) để tiết kiệm công.
Quy ước tên file theo tài liệu 08 (mục 6).

---

## 0. Thông số kỹ thuật chung

| Loại | Kích thước / định dạng | Ghi chú |
|------|------------------------|---------|
| Background | 1920×1080 PNG (hoặc 2560×1080 cho cảnh rộng, có cuộn ngang) | Nén ASTC 6x6 khi import |
| Close-up câu đố | 1920×1080 PNG | Có thể là ảnh phóng to của background |
| Chân dung hội thoại | 768×1024 PNG nền trong suốt | Căn chân dung nửa người |
| Icon vật phẩm | 128×128 PNG | Hiển thị trong túi đồ |
| Ảnh xem chi tiết vật phẩm/manh mối | 1024×1024 PNG | Có mặt sau nếu cần (ghi chú, ảnh) |
| Sprite UI | PNG, 9-slice cho khung | Dùng Sprite Atlas |
| Sprite hiệu ứng | Sprite sheet 8–16 khung | 12 fps |
| Nhạc | OGG, 44,1 kHz, loop | Stereo, ~128–160 kbps |
| SFX | WAV 44,1 kHz mono (nén Vorbis khi build) | Ngắn, chuẩn hóa -3 dB |
| Ambience | OGG loop 30–90 giây | |
| Font | TTF/OTF hỗ trợ tiếng Việt đầy đủ dấu | Kiểm tra dấu "ẫ ệ ữ ự" |

---

## 1. Background / cảnh (BG)

### 1.1 Tầng 1 — Sảnh (L01–L04)
| ID | File | Mô tả | Khu vực | Ưu tiên | Tái dùng |
|----|------|-------|---------|---------|----------|
| BG01 | `bg_L00_exterior_night.png` | Mặt tiền khách sạn Liên Hoa về đêm, 12 tầng, biển hiệu cũ, tầng 13 chỉ lộ ra trong cutscene | Menu, kết thúc | P0 | Dùng làm nền menu |
| BG02 | `bg_L01_lobby_normal.png` | Sảnh chính: sàn đá hoa, ghế sofa cũ, đèn chùm vàng, bảng tin, **đồng hồ dừng lúc 00:13**, lịch thiếu trang 13/9 | L01 | P0 | Biến thể BG03 |
| BG03 | `bg_L01_lobby_event.png` | Sảnh khi sự kiện (đèn tắt, ánh đỏ, thang máy sáng) | L01 | P1 | Từ BG02 |
| BG04 | `bg_L02_reception.png` | Quầy lễ tân gỗ, sổ khách, bảng chìa khóa 12 móc, ngăn kéo | L02 | P0 | |
| BG05 | `bg_L02_keyboard_closeup.png` | Cận cảnh bảng chìa khóa (P01) | L02 | P0 | |
| BG06 | `bg_L03_security.png` | Phòng bảo vệ nhỏ: màn hình CCTV, bàn, tủ khóa, lịch rách, radio, máy cassette | L03 | P0 | |
| BG07 | `bg_L03_locker_closeup.png` | Cận cảnh tủ khóa 4 số (P03) | L03 | P0 | |
| BG08 | `bg_L03_cctv_closeup.png` | Màn hình CCTV 4 ô, có một ô hiện hành lang không tồn tại (EV06) | L03 | P1 | |
| BG09 | `bg_L04_elevator_cabin.png` | Bên trong cabin thang máy, gương mờ, bảng nút | L04 | P0 | |
| BG10 | `bg_L04_panel_closeup.png` | Cận cảnh bảng nút B1, 1–12, vị trí trống cho nút 13 | L04 | P0 | Nút 13 là sprite riêng (mục 5) |

### 1.2 Tầng 2–3 (L05–L08)
| ID | File | Mô tả | Khu vực | Ưu tiên | Tái dùng |
|----|------|-------|---------|---------|----------|
| BG11 | `bg_L05_kitchen.png` | Bếp công nghiệp, bàn inox, kệ gia vị, lò hơi, hộp diêm | L05 | P0 | |
| BG12 | `bg_L06_coldroom.png` | Kho lạnh, thùng hàng xếp lộn xộn, hơi lạnh | L06 | P0 | |
| BG13 | `bg_L06_coldroom_open.png` | Kho lạnh sau khi đẩy thùng, lộ cửa ngầm xuống hầm | L06 | P0 | Từ BG12 |
| BG14 | `bg_L07_restaurant.png` | Nhà hàng vắng, bàn phủ khăn trắng, máy hát | L07 | P2 | |
| BG15 | `bg_L08_storage.png` | Kho đồ thất lạc: kệ chất đầy vali, ô, hộp giấy, đĩa than | L08 | P0 | |

### 1.3 Hành lang và phòng khách
| ID | File | Mô tả | Khu vực | Ưu tiên | Tái dùng |
|----|------|-------|---------|---------|----------|
| BG16 | `bg_corridor_generic_a/b/c.png` | Hành lang chung (tầng 4,6,7,9,10), 3 biến thể màu/đèn, cửa có biển "Đừng làm phiền" | Chung | P0 | Cũng dùng làm nền F13-A |
| BG17 | `bg_L10_corridor_f5.png` | Hành lang tầng 5, hộp cầu chì trên tường | L10 | P0 | |
| BG18 | `bg_L10_room502.png` | Phòng 502: giường, đèn tắt | L10 | P0 | |
| BG19 | `bg_L10_fusebox_closeup.png` | Hộp cầu chì mở nắp, 3 dây + sơ đồ (P02) | L10 | P0 | |
| BG20 | `bg_L10_room505.png` | Phòng 505: nước tràn từ phòng tắm, ván sàn hở | L10 | P0 | |
| BG21 | `bg_L11_corridor_f8.png` | Hành lang tầng 8, lịch rách ở cuối | L11 | P0 | |
| BG22 | `bg_L11_room807.png` | Phòng bà Ngô: giường, tủ gỗ, ảnh con trai, ngăn kéo | L11 | P0 | |
| BG23 | `bg_L11_room808.png` | Phòng 808 (khách phụ) | L11 | P2 | Từ BG18 |
| BG24 | `bg_L12_corridor_f11.png` | Hành lang tầng 11, điện thoại phòng trống | L12 | P1 | |
| BG25 | `bg_L12_room1104.png` | Phòng bỏ trống phát nhạc, bụi và đồ cũ | L12 | P1 | |

### 1.4 Tầng 12, sân thượng, tầng hầm
| ID | File | Mô tả | Khu vực | Ưu tiên | Tái dùng |
|----|------|-------|---------|---------|----------|
| BG26 | `bg_L13_office.png` | Văn phòng quản lý: bàn gỗ, tủ hồ sơ, tranh, bình hoa giả | L13 | P0 | |
| BG27 | `bg_L13_safe_closeup.png` | Két sắt 6 số (P06) | L13 | P0 | |
| BG28 | `bg_L13_cabinet_closeup.png` | Tủ hồ sơ mở | L13 | P1 | |
| BG29 | `bg_L14_rooftop.png` | Sân thượng: bể nước, ăng-ten, ánh trăng, đèn hiệu | L14 | P0 | |
| BG30 | `bg_L14_signal_closeup.png` | Đèn hiệu lớn với công tắc (P12) | L14 | P0 | |
| BG31 | `bg_L15_boiler.png` | Phòng nồi hơi, ống nước, van | L15 | P0 | |
| BG32 | `bg_L15_valves_closeup.png` | 5 van + sơ đồ ố vàng (P07) | L15 | P0 | |
| BG33 | `bg_L15_oldcorridor.png` | Hành lang cũ tầng hầm, tường ẩm, băng cassette | L15 | P0 | |
| BG34 | `bg_L15_missingboard_closeup.png` | Bảng thông báo 13 người mất tích (C05) | L15 | P0 | |
| BG35 | `bg_L15_sealedstairs.png` | Cầu thang thoát hiểm bị hàn kín | L15 | P1 | |

### 1.5 Tầng 13 (L16)
| ID | File | Mô tả | Biến thể | Ưu tiên | Tái dùng |
|----|------|-------|----------|---------|----------|
| BG36 | `bg_F13A_loop_1/2/3.png` | Hành lang giống tầng 12, cửa số sai, 3 vòng với 3 chi tiết thay đổi khác nhau (P09) | F13-A | P0 | Từ BG16 + chỉnh |
| BG37 | `bg_F13A_end.png` | Cuối hành lang, bàn nhỏ để máy ảnh Tùng (M04) | F13-A | P0 | |
| BG38 | `bg_F13B_ballroom.png` | Phòng tiệc cháy dở: bàn ghế đổ, nến, nhạc hộp trên bàn | F13-B | P0 | |
| BG39 | `bg_F13B_closet.png` | Tủ trốn "Bóng Cháy" (2 trạng thái: sạch/cháy xém) | F13-B | P0 | |
| BG40 | `bg_F13B_candles_closeup.png` | Bàn 5 nến cho P10 | F13-B | P0 | |
| BG41 | `bg_F13C_lobby2004.png` | Sảnh năm 2004: tươi mới, đèn sáng, bóng người mờ | F13-C | P1 | Từ BG02 (đổi màu) |
| BG42 | `bg_F13C_kitchen2004.png` | Bếp năm 2004 | F13-C | P1 | Từ BG11 |
| BG43 | `bg_F13C_corridor2004.png` | Hành lang năm 2004 + đồng hồ | F13-C | P1 | Từ BG16 |
| BG44 | `bg_F13C_firedoor.png` | Cửa thoát hiểm bị khóa, khói (C16) | F13-C | P1 | |
| BG45 | `bg_F13D_altar.png` | Bàn thờ 13 ô, tường cháy, ánh lạnh và đỏ | F13-D | P0 | |
| BG46 | `bg_F13D_lounge_approach.png` | Phòng trà bị cháy sau tường dẫn vào bàn thờ | F13-D | P0 | |

**Tổng: 46 background** (kể cả cận cảnh câu đố; 28 cảnh chính + 18 cận cảnh/biến thể).

---

## 2. Nhân vật

### 2.1 Chân dung hội thoại
Mỗi chân dung 768×1024, tên file: `ch_{NPC}_{tên}_{biểu cảm}.png`.

| NPC | Nhân vật | Biểu cảm cần vẽ | Số | Ưu tiên |
|-----|----------|-----------------|----|---------|
| NPC00 | **Minh Châu** (26 tuổi) | bình thường, lo lắng, sợ hãi, quyết tâm, ngạc nhiên, buồn | 6 | P0 |
| NPC00b | Bé Châu (6 tuổi, cảnh hồi ức) | ngơ ngác, khóc | 2 | P1 |
| NPC01 | **Hạnh** (quản lý) | cười lịch sự, lạnh, tức giận, hoảng hốt, bình tĩnh giả tạo | 5 | P0 |
| NPC02 | **Bảo** (bảo vệ) | mệt mỏi, cảnh giác, day dứt, rơm rớm, hiền | 5 | P0 |
| NPC03 | **Tuấn** (phụ bếp) | lo âu, bình thường, sợ, nhẹ nhõm, quyết tâm | 5 | P0 |
| NPC04 | **Bà Ngô** | lạnh nhạt, dò xét, xúc động, cảm ơn, quyết đoán | 5 | P0 |
| NPC05 | Người áo mưa | chỉ bóng (silhouette), 1 tư thế | 1 | P0 |
| NPC06 | Thu Hà (hồn mẹ) | mờ nhạt, mỉm cười, buồn | 3 | P0 |
| NPC07 | Khách ngẫu nhiên (3 người: nam trung niên, nữ trẻ, ông già) | 1 biểu cảm mỗi người | 3 | P2 |
| | **Tổng chân dung** | | **35** | |

### 2.2 Sprite và hoạt họa nhỏ
| ID | Asset | Mô tả | Frame | Ưu tiên |
|----|-------|-------|-------|---------|
| SP01 | `sp_chau_silhouette_walk` | Bóng Châu đi trong hành lang khi chuyển cảnh (nhỏ) | 8 | P2 |
| SP02 | `sp_shadow_burned_idle/move` | **Bóng Cháy**: dáng người cháy xém, idle và giật chuyển động (F13-B) | 4 + 6 | P0 |
| SP03 | `sp_raincoat_figure` | Bóng áo mưa đứng cuối hành lang (EV05, F13-A) | 2 | P0 |
| SP04 | `sp_ghost_2004_a/b/c` | 3 bóng người mờ trong khách sạn 2004 (P11) | 3 × 4 | P1 |
| SP05 | `sp_thuha_light` | Quầng sáng ấm hình người Thu Hà | 4 | P1 |
| SP06 | `sp_child_chau_2004` | Bé Châu 6 tuổi (cảnh F13-C) | 2 | P1 |

---

## 3. Vật phẩm, di vật và manh mối

### 3.1 Vật phẩm thường (I01–I18)
Mỗi vật phẩm có **icon 128×128**; vật có chữ "chi tiết" có thêm ảnh xem 1024×1024.

| ID | File icon | Mô tả hình ảnh | Chi tiết | Ưu tiên |
|----|-----------|----------------|----------|---------|
| I01 | `it_I01_staffcard` | Thẻ nhân viên nhựa có ảnh, logo Liên Hoa | Có (mặt trước/sau) | P0 |
| I02 | `it_I02_locket` | Mặt dây chuyền bạc cũ hình trái tim, khắc nhỏ | Có (mở ra, ảnh nhỏ bên trong) | P0 |
| I03 | `it_I03_flashlight` | Đèn pin kim loại cũ | Không | P0 |
| I04 | `it_I04_key_storage` | Chìa gỉ, thẻ tên "K3" | Không | P0 |
| I05 | `it_I05_masterkey` | Chìa vạn năng sáng, móc tròn | Không | P0 |
| I06 | `it_I06_key_basement` | Chìa to, thẻ ghi "B1" | Không | P0 |
| I07 | `it_I07_key_rooftop` | Chìa mạ đồng, tay nắm hình mái | Không | P1 |
| I08 | `it_I08_fuse` | Cầu chì sứ nhỏ | Không | P0 |
| I09 | `it_I09_cassette_player` | Máy cassette cầm tay (Walkman cũ) | Có (nút bấm để dùng P08) | P0 |
| I10 | `it_I10_tape_1` | Băng cassette nhãn số "1 · 00:00" | Có (nhãn viết tay) | P0 |
| I11 | `it_I11_tape_2` | Băng nhãn "2 · 01:10" | Có | P0 |
| I12 | `it_I12_tape_3` | Băng nhãn "3 · 02:05" | Có | P0 |
| I13 | `it_I13_photo_a` | Mảnh ảnh xé (góc trên trái) | Có (mảnh ghép P05) | P0 |
| I14 | `it_I14_photo_b` | Mảnh ảnh xé (giữa) | Có | P0 |
| I15 | `it_I15_photo_c` | Mảnh ảnh xé (góc dưới phải) | Có | P0 |
| I16 | `it_I16_key_cabinet` | Chìa nhỏ tủ hồ sơ | Không | P1 |
| I17 | `it_I17_crowbar` | Xà beng gỉ | Không | P0 |
| I18 | `it_I18_matchbox` | Hộp diêm có logo nhà hàng | Không | P0 |

### 3.2 Di vật của 12 nạn nhân (M01–M12)
Mỗi di vật: icon 128 + ảnh chi tiết 1024 (có khắc tên nạn nhân ở mặt sau) + **hình minh họa hồi ức** (tuỳ chọn, 1 khung ngắn khi nhặt).

| ID | File | Mô tả hình ảnh | Chi tiết khắc / nhãn | Hồi ức (P2) | Ưu tiên |
|----|------|----------------|----------------------|-------------|---------|
| M01 | `it_M01_musicbox` | Hộp nhạc gỗ nhỏ, nắp hơi cháy, lên dây | Ngăn bí mật chứa thư C08 | Thu Hà ru con | P0 |
| M02 | `it_M02_pocketwatch` | Đồng hồ bỏ túi mạ vàng, kim dừng ở 00:13 | Khắc "T.Q.H" | Hưng đứng trước cửa khóa | P0 |
| M03 | `it_M03_ledger` | Sổ sách bìa da, cột số tiền | Trang mở: danh sách "Phòng trà Mười Ba" | Đức kê khai | P0 |
| M04 | `it_M04_camera` | Máy ảnh phim cũ | Cuộn phim bên trong (C19) | Tùng chụp lén | P0 |
| M05 | `it_M05_vinyl` | Đĩa than đen, nhãn "Mỹ Dung" | Khắc tên ca sĩ | Dung hát | P1 |
| M06 | `it_M06_lighter` | Bật lửa vàng chạm hoa | Khắc "Đ.H.T" | Tài đánh bài | P1 |
| M07 | `it_M07_bowtie` | Nơ bướm đen của pha chế | Nhãn "H.T.L" | Lan pha rượu | P1 |
| M08 | `it_M08_whistle` | Còi bảo vệ nhỏ, kèm mẩu giấy gập mã Morse SOS (P12) | Mẩu giấy | Khoa phá cửa | P0 |
| M09 | `it_M09_scarf` | Khăn len cũ, cháy xém góc | Nhãn "B.T.S" | Sen quét dọn | P1 |
| M10 | `it_M10_harmonica` | Kèn harmonica | Khắc "N.Q.B" | Bình thổi kèn | P1 |
| M11 | `it_M11_ring` | Nhẫn cưới trơn | Khắc ngày cưới | Huy cầu hôn | P1 |
| M12 | `it_M12_familyphoto` | Ảnh gia đình khung kim loại | Ảnh 3 người | Mai chụp ảnh | P1 |

### 3.3 Manh mối (C01–C22) — ảnh xem chi tiết 1024×1024
| ID | File | Mô tả nội dung hình | Ưu tiên |
|----|------|---------------------|---------|
| C01 | `cl_C01_calendar_torn` | Tờ lịch tháng 9/2004 bị xé ngày 13; một vài bản (sảnh, phòng bảo vệ, 807) | P0 |
| C02 | `cl_C02_blueprint` | Bản vẽ kiến trúc 13 tầng, tầng 13 viết tay chữ đỏ | P0 |
| C03 | `cl_C03_newspaper` | Bài báo ố vàng "Cháy nhỏ tại Khách sạn Liên Hoa" kèm ảnh cũ | P0 |
| C04 | `cl_C04_invoice` | Hóa đơn tiệc "Phòng trà Mười Ba" có dấu đỏ | P1 |
| C05 | `cl_C05_missinglist` | Danh sách 13 tên (gồm "Minh Châu, 6 tuổi"), ghim bằng đinh rỉ | P0 |
| C06 | `cl_C06_khoa_diary` | Cuốn nhật ký của Khoa, trang cuối "Bà Hạnh bảo khóa cửa..." | P0 |
| C07 | `cl_C07_ledger_page` | Trang sổ thu chi sòng bạc | P0 |
| C08 | `cl_C08_letter_thuha` | Lá thư tay nét chữ mẹ, gấp tư | P0 |
| C09–C11 | `cl_C09/10/11_tape_transcript` | Giao diện phát băng + bản ghi chữ tương ứng | P0 |
| C12 | `cl_C12_staffphoto` | Ảnh nhân viên 2004 hoàn chỉnh (ghép từ 3 mảnh) | P0 |
| C13 | `cl_C13_locket_match` | Cận cảnh mặt dây chuyền trong ảnh khớp I02 | P0 |
| C14 | `cl_C14_hr_file` | Hồ sơ nhân sự Lê Thu Hà, ảnh thẻ, ghi "con: Minh Châu" | P0 |
| C15 | `cl_C15_fire_report` | Báo cáo PCCC giả, dấu mộc mờ | P1 |
| C16 | `cl_C16_firedoor_scene` | Hình cảnh khóa cửa thoát hiểm (tĩnh) | P1 |
| C17 | `cl_C17_ngo_story` | Ảnh bà Ngô với con trai Tùng (trong hội thoại) | P1 |
| C18 | `cl_C18_tuan_note` | Mẩu giấy tay của Tuấn | P1 |
| C19 | `cl_C19_film_photos` | 3 bức ảnh rửa từ phim: sòng bạc, bàn cờ, Hưng | P1 |
| C20 | `cl_C20_bao_confession` | Hình Bảo bế bé Châu (minh họa lời thú nhận) | P1 |
| C21 | `cl_C21_elevator_diagram` | Sơ đồ thang máy 2004 có nút 13 quẹt thẻ | P1 |
| C22 | `cl_C22_transfer_contract` | Thỏa thuận chuyển nhượng khách sạn cho Hạnh | P1 |

---

## 4. Asset riêng cho câu đố (P01–P13)

| Puzzle | Asset cần | Chi tiết | Ưu tiên |
|--------|-----------|----------|---------|
| P01 | `pz_P01_keys` | 12 móc chìa, 12 sprite chìa khác hình đầu (tam giác, tròn, vuông…), thẻ số mờ, tờ ghi chú khách | P0 |
| P02 | `pz_P02_wires` | 3 dây (đỏ, xanh, vàng), 3 cổng, sơ đồ nắp hộp, tia lửa khi nối sai | P0 |
| P03 | `pz_P03_lock` | Khóa 4 bánh số xoay, âm thanh kẹt | P0 |
| P04 | `pz_P04_grid` | Lưới 5×4, 3 sprite thùng, 3 ô đánh dấu, tường, nhân vật Châu (icon nhỏ) | P0 |
| P05 | `pz_P05_photo` | 3 mảnh ảnh có viền xé, khung ghép, hiệu ứng "khóa" khi đúng | P0 |
| P06 | `pz_P06_safe` | Bàn phím số 0–9 + màn hình LED, hiệu ứng báo động | P0 |
| P07 | `pz_P07_valves` | 5 van, mũi tên chỉ dòng chảy, ống nước, hiệu ứng hơi nước | P0 |
| P08 | `pz_P08_tape` | Ngăn máy cassette, 3 khe băng, thanh trượt tốc độ, sóng âm | P0 |
| P09 | `pz_P09_diff` | Hiệu ứng viền sáng nhẹ lên chi tiết thay đổi (gợi ý G3) | P0 |
| P10 | `pz_P10_candles` | 5 nến, 5 trạng thái cháy/tắt, đèn nhịp tương ứng nốt | P0 |
| P11 | `pz_P11_clocks` | 3 đồng hồ treo tường (sảnh, bếp, hành lang), kim chỉnh được, vòng sáng gợi ý | P1 |
| P12 | `pz_P12_signal` | Công tắc đèn hiệu, tia sáng, minh họa mã Morse (chấm/gạch) | P0 |
| P13 | `pz_P13_altar` | 13 ô khắc tên, khung đặt di vật, ô thứ 13 trống, hiệu ứng ánh sáng | P0 |

---

## 5. Giao diện (UI)

| Nhóm | Asset | Mô tả | Ưu tiên |
|------|-------|-------|---------|
| Logo | `ui_logo_title` | Logo "Khách sạn không có tầng 13", chữ 12 + số 13 mờ | P0 |
| Menu | `ui_menu_btn_{play,continue,endings,settings,quit}` | Nút menu 5 trạng thái (normal/pressed/disabled) | P0 |
| HUD | `ui_hud_clock`, `ui_hud_btn_inventory/shiftlog/clueboard/observe/menu` | Đồng hồ ca kiểu LED vàng và 5 nút | P0 |
| Túi đồ | `ui_inv_slot`, `ui_inv_frame`, `ui_inv_relicbox` | Ô vật phẩm, khung, hộp di vật (12 ô có hình bóng) | P0 |
| Sổ ca | `ui_shiftlog_paper`, `ui_task_check` | Sổ giấy kẻ dòng, dấu tích hoàn thành, sao ★ bắt buộc | P0 |
| Bảng manh mối | `ui_board_cork`, `ui_board_pin`, `ui_board_string`, `ui_truth_slot_T1..T5`, `ui_truth_check` | Bảng ghim, đinh, dây đỏ (có thể vẽ bằng line renderer), 5 ô sự thật + dấu ✓ | P0 |
| Hội thoại | `ui_dlg_box`, `ui_dlg_name`, `ui_dlg_choice_btn`, `ui_dlg_accuse_btn`, `ui_trust_icon_up/down` | Khung chữ, thanh tên, nút lựa chọn, nút Chất vấn, icon thay đổi tin tưởng | P0 |
| Thang máy | `ui_elev_btn_B1,1..12`, `ui_elev_btn_13_{off,flicker,on}`, `ui_elev_indicator` | Nút tròn kim loại; nút 13 có 3 trạng thái và hiệu ứng phát sáng đỏ | P0 |
| Tầng 13 | `ui_sanity_bar`, `ui_sanity_vignette` | Thanh Tỉnh táo (tim/nốt nhạc), overlay viền tối | P0 |
| Hotspot | `ui_hotspot_glow`, `ui_cursor_{look,take,use,talk,door}` | Viền sáng, 5 icon hành động | P0 |
| Gợi ý | `ui_hint_btn`, `ui_hint_level_1/2/3` | Nút bóng đèn + 3 cấp | P0 |
| Thông báo | `ui_toast_item`, `ui_toast_clue`, `ui_toast_truth` | Banner nhỏ "Nhận vật phẩm/Manh mối mới/Sự thật" | P0 |
| Cài đặt | `ui_set_slider`, `ui_set_toggle`, `ui_set_tab` | Thanh trượt, công tắc, tab | P0 |
| Lưu/Tải | `ui_save_slot`, `ui_save_thumb_frame` | 3 slot + autosave | P0 |
| Cảnh báo | `ui_content_warning` | Màn hình cảnh báo nội dung | P0 |
| Thống kê kết | `ui_end_stats`, `ui_end_badges_E1..E5` | Bảng thống kê sự thật /5, di vật /12, kết thúc /5 | P1 |
| Tiêu đề ca | `ui_night_card_1..5` | 5 thẻ tiêu đề "Ca 1 · Nhận ca" ... "Ca 5 · Đêm 13" | P0 |
| Loading | `ui_loading_icon` | Biểu tượng thang máy quay | P2 |

---

## 6. Hiệu ứng hình ảnh (VFX / Shader)

| ID | Tên | Mô tả | Dùng ở | Ưu tiên |
|----|-----|-------|--------|---------|
| FX01 | Đèn nhấp nháy | Flicker độ sáng, 3 cường độ | Hành lang, EV | P0 |
| FX02 | Vignette | Viền tối động theo Tỉnh táo | Tầng 13 | P0 |
| FX03 | Nhiễu hạt / glitch | Nhiễu màn hình nhẹ | Tầng 13, CCTV | P0 |
| FX04 | Méo màu (chromatic) | Tách màu khi Tỉnh táo thấp | Tầng 13 | P1 |
| FX05 | Khói | Particle khói mỏng | F13-B, F13-C | P1 |
| FX06 | Lửa | Sprite sheet lửa (nhỏ, vừa) | F13-C, F13-D, cutscene | P1 |
| FX07 | Bụi bay | Particle bụi trong tia sáng | Sảnh, phòng bỏ trống | P2 |
| FX08 | Nước chảy | Dòng nước ra gầm cửa | P505 (EV04) | P1 |
| FX09 | Hơi lạnh | Sương lạnh | Kho lạnh | P2 |
| FX10 | Tia điện | Spark nhỏ | P02 | P1 |
| FX11 | Ánh sáng ấm Thu Hà | Quầng sáng + hạt sáng | Nhạc hộp, F13-D | P1 |
| FX12 | Sóng âm | Hiển thị âm thanh nhạc hộp/cassette | P08, P10 | P1 |
| FX13 | Bóng đổ chuyển động | Bóng người lướt qua tường | EV05 | P1 |
| FX14 | Lật trang/zoom giấy | Chuyển động xem vật phẩm | UI | P1 |
| FX15 | Hiệu ứng "xóa" | Chữ 13 mờ dần khi E5 | Kết thúc | P1 |

---

## 7. Cutscene và minh họa

| ID | Asset | Mô tả | Ưu tiên |
|----|-------|-------|---------|
| CS01 | `cs_intro_1..3` | Mở đầu: thư tuyển dụng, Châu đứng trước khách sạn, nút 13 trong giấc mơ | P1 |
| CS02 | `cs_night_transition` | Chuyển ca: đồng hồ chạy tới 06:00, đèn sáng dần | P0 |
| CS03 | `cs_E1_1..2` | E1: Châu bước vào ô 13; bảng thang máy chỉ còn 12 nút, danh sách mất tích thêm một tên | P0 |
| CS04 | `cs_E2_1..2` | E2: nhân viên mới nhìn nút 13 nhấp nháy | P0 |
| CS05 | `cs_E3_1..2` | E3: Châu trước khách sạn lúc bình minh, cầm mặt dây chuyền | P0 |
| CS06 | `cs_E4_1..3` | E4: cảnh sát bóc tường, Hạnh bị đưa đi, lễ tưởng niệm | P0 |
| CS07 | `cs_E5_1..3` | E5: Thu Hà mỉm cười, thang máy chỉ còn 12 nút, Châu cầm nhạc hộp | P0 |
| CS08 | `cs_flashback_2004_1..4` | Hồi tưởng đêm 13/09/2004: cháy, Bảo bế bé Châu qua cầu thang hầm | P1 |
| CS09 | `cs_credits_bg` | Nền phần credits | P2 |

---

## 8. Âm thanh

### 8.1 Nhạc (MU)
| ID | File | Mô tả | Dùng ở | Ưu tiên |
|----|------|-------|--------|---------|
| MU01 | `mu_MU01_menu.ogg` | Piano một nốt, drone thấp | Menu | P0 |
| MU02 | `mu_MU02_lobby.ogg` | Ambient, chuông xa | Sảnh và khu vực thường | P0 |
| MU03 | `mu_MU03_musicbox.ogg` | **Mô-típ chính 5 nốt** của nhạc hộp (3-1-4-2-5), kèm các biến thể: bản đầy đủ, bản méo, bản đảo | Xuyên suốt, P10 | P0 |
| MU04 | `mu_MU04_floor13_ab.ogg` | Drone, kim loại, thở | F13-A/B | P0 |
| MU05 | `mu_MU05_floor13_memory.ogg` | Nhạc phòng trà năm 2004 bị méo | F13-C | P1 |
| MU06 | `mu_MU06_confrontation.ogg` | Căng thẳng, nhịp tim | Ca 5 | P1 |
| MU07 | `mu_MU07_ending_E1..E5.ogg` | 5 biến thể của MU03 cho từng kết thúc | Kết thúc | P0 |
| MU08 | `mu_MU08_stinger_*.ogg` | Các nhạc ngắn (stinger): nhận manh mối, xác nhận sự thật, bước vào tầng 13 | HUD, sự kiện | P1 |
| MU09 | `mu_MU09_credits.ogg` | Credits | Credits | P2 |

### 8.2 Hiệu ứng âm thanh (SFX)
| Nhóm | Tên file / số lượng | Mô tả | Ưu tiên |
|------|---------------------|-------|---------|
| Thang máy | `sfx_elevator_{chime,open,close,move,stop,buzz}` (6) | Chuông "ting", cửa mở/đóng, chạy, dừng, tiếng buzz khi nút 13 không bấm được | P0 |
| Bước chân | `sfx_step_{tile,wood,metal,carpet,wet}` (5) | Theo chất liệu sàn | P0 |
| Cửa | `sfx_door_{open,close,locked,creak,slam}` (5) | | P0 |
| Khóa/chìa | `sfx_key_{insert,turn}`, `sfx_lock_{click,fail,unlock}` (5) | | P0 |
| Giấy/vật | `sfx_paper_{flip,tear}`, `sfx_item_{pickup,drop}` (4) | | P0 |
| Túi đồ/UI | `sfx_ui_{tap,open,close,error,confirm}` (5) | | P0 |
| Điện thoại | `sfx_phone_{ring,pickup}` (2) | Điện thoại phòng trống | P1 |
| Điện/đèn | `sfx_light_flicker`, `sfx_spark`, `sfx_fusebox` (3) | | P0 |
| Nước/hơi | `sfx_water_drip`, `sfx_water_flow`, `sfx_steam`, `sfx_valve` (4) | | P1 |
| Máy cassette | `sfx_cassette_{insert,play,rewind,stop,static}` (5) | | P0 |
| Nhạc hộp | `sfx_musicbox_{wind,note1..5}` (6) | 5 nốt dùng trong P10 | P0 |
| Còi/Morse | `sfx_whistle`, `sfx_morse_{short,long}` (3) | | P1 |
| Lửa | `sfx_fire_{small,large}`, `sfx_alarm_fire_short` (3) | Chuông cháy ngắn, không quá to | P1 |
| Tầng 13 | `sfx_f13_{knock,breath,whisper,heartbeat,drone_hit}` (5) | | P0 |
| Bóng Cháy | `sfx_burnt_{step,crackle}` (2) | | P1 |
| Thang bấm nút | `sfx_button_press` (1) | | P0 |
| Radio | `sfx_radio_static`, `sfx_radio_voice_thuha` (2) | EV09 | P1 |
| Két/van | `sfx_safe_{beep,open,alarm}`, `sfx_crate_push` (4) | | P0 |
| Kết thúc | `sfx_end_{chime,bell}` (2) | | P1 |
| **Tổng SFX** | **~70** | | |

### 8.3 Ambience (nền, loop)
| ID | Tên | Dùng ở | Ưu tiên |
|----|-----|--------|---------|
| AM01 | `am_lobby_night` | Sảnh | P0 |
| AM02 | `am_corridor_hum` | Hành lang | P0 |
| AM03 | `am_kitchen_fridge` | Bếp, kho lạnh | P0 |
| AM04 | `am_boiler_pipes` | Hầm | P0 |
| AM05 | `am_rooftop_wind` | Sân thượng | P1 |
| AM06 | `am_office_clock` | Văn phòng | P1 |
| AM07 | `am_f13_void` | Tầng 13 A/B/D | P0 |
| AM08 | `am_f13_memory` | F13-C | P1 |
| AM09 | `am_elevator_hum` | Cabin | P0 |
| AM10 | `am_room_silence` | Phòng khách (rất nhẹ) | P1 |

### 8.4 Thoại / giọng
| ID | Asset | Mô tả | Ưu tiên |
|----|-------|-------|---------|
| VO01 | `vo_tape_C09/10/11.ogg` | Giọng Thu Hà, Hưng, Hạnh trong băng (cần diễn viên giọng) | P1 |
| VO02 | `vo_thuha_whisper_*.ogg` | Giọng thì thầm trong tầng 13 | P1 |
| VO03 | `vo_child_chau_*.ogg` | Giọng bé Châu (hồi ức) | P2 |
| VO04 | `vo_bao_*`, `vo_hanh_*` | Câu thoại quan trọng (nếu lồng tiếng) | P2 |

---

## 9. Font, văn bản và dữ liệu hỗ trợ

| Asset | Mô tả | Ưu tiên |
|-------|-------|---------|
| Font chính (đọc thoại) | Sans-serif dễ đọc, hỗ trợ tiếng Việt, 3 cỡ | P0 |
| Font tiêu đề | Serif cổ điển/typewriter cho logo, thẻ ca | P0 |
| Font viết tay | Dùng cho thư, nhật ký, ghi chú (C06, C08, C18) | P1 |
| Font LED | Cho đồng hồ ca | P0 |
| Bảng chuỗi | `strings_vi.csv` (và `strings_en.csv` nếu làm) | P0 |
| Kịch bản Ink | `.ink` cho từng NPC/ca | P0 |
| Dữ liệu JSON | `items.json`, `clues.json`, `truths.json`, `quests/*.json`, `locations/*.json` | P0 |
| Icon ứng dụng | 512×512 và adaptive icon Android (foreground + background) | P0 |

---

## 10. Asset phục vụ phát hành

| Asset | Quy cách | Ưu tiên |
|-------|----------|---------|
| Icon Google Play | 512×512 PNG | P0 |
| Feature graphic | 1024×500 | P0 |
| Ảnh chụp màn hình | 5–8 ảnh (9:16 và 16:9) | P0 |
| Trailer | 30–60 giây, 1080p | P1 |
| Poster/Key art | 1920×1080 | P1 |
| Ảnh bìa fanpage/TikTok | Theo kích thước từng nền tảng | P2 |

---

## 11. Thống kê tổng hợp

| Nhóm | Số lượng (ước tính) | P0 | P1 | P2 |
|------|---------------------|----|----|----|
| Background | 46 (cộng biến thể ~55 file) | 31 | 12 | 3 |
| Chân dung | 35 | 31 | 1 | 3 |
| Sprite nhân vật/hoạt họa | 6 nhóm (~11 file) | 2 | 3 | 1 |
| Icon vật phẩm thường | 18 | 17 | 1 | 0 |
| Di vật | 12 (icon + chi tiết) | 4 | 8 | 0 |
| Manh mối | 22 | 11 | 11 | 0 |
| Asset câu đố | 13 nhóm | 12 | 1 | 0 |
| UI | ~19 nhóm (~90 sprite) | ~17 | 1 | 1 |
| VFX | 15 | 3 | 11 | 1 |
| Cutscene | 9 nhóm (~20 ảnh) | 4 | 2 | 1 |
| Nhạc | 9 nhóm (~19 track) | 6 | 3 | 1 |
| SFX | ~70 | ~46 | ~24 | 0 |
| Ambience | 10 | 6 | 4 | 0 |
| Thoại | 4 nhóm | 0 | 2 | 2 |

> Các con số là ước tính để lập kế hoạch và có thể lệch vài mục. Ưu tiên tạo **placeholder** (hộp màu, tiếng bíp) cho tất cả mục P0 trước tuần 3 để lập trình viên không bị chặn, sau đó thay dần bằng asset thật.

## 12. Gợi ý nguồn và cách tiết kiệm

| Loại | Gợi ý |
|------|-------|
| Hình ảnh | Tự vẽ; dùng tái sử dụng background + đổi bảng màu; cận cảnh có thể cắt từ background độ phân giải cao |
| Nhạc/SFX | Tự làm bằng DAW (LMMS, Reaper), hoặc nguồn CC0/CC-BY (freesound.org, opengameart.org, incompetech) và **ghi nguồn trong credits** |
| Font | Google Fonts (kiểm tra hỗ trợ tiếng Việt) |
| Giọng nói | Thành viên nhóm hoặc bạn bè thu, chỉnh bằng Audacity |
| Quản lý | Mỗi asset có dòng trong bảng theo dõi (Trello/Notion) với trạng thái: Chưa làm · Placeholder · Hoàn thành · Đã tích hợp |
