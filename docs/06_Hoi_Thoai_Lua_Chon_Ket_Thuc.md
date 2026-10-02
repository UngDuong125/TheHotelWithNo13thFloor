# 06 — Hội thoại, lựa chọn và kết thúc

## 1. Mô hình hội thoại

Mỗi NPC có:
- **Tin tưởng (Trust) 0–10** (với Hạnh gọi là *Thiện cảm*: càng cao càng dễ bị lợi dụng, nhưng cũng dễ để lộ sơ hở).
- **Hồ sơ trung thực:** Nói thật / Che giấu / Nói dối.
- **Danh sách "thông tin"** gắn với ngưỡng Tin tưởng hoặc điều kiện manh mối.

Hành động hội thoại:
| Hành động | Mô tả |
|-----------|-------|
| Hỏi | Chọn chủ đề; NPC trả lời tùy Trust và hồ sơ |
| Đưa vật phẩm | Có thể làm NPC phản ứng (tăng Trust, mở thông tin, hoặc nghi ngờ) |
| Chất vấn | Dùng manh mối để phản bác lời nói dối; chọn sai manh mối → Trust −1 |
| Thân mật / Cứng rắn | Giọng điệu: thân thiện tăng Trust, cứng rắn làm NPC lộ thông tin nhưng giảm Trust |
| Rời đi | Kết thúc hội thoại |

### Quy tắc nói dối và chất vấn
- Câu nói dối được đánh dấu trong dữ liệu (`lie: true`, `refutedBy: [Cxx, ...]`).
- Người chơi chỉ thấy nút "Chất vấn" khi đang có ít nhất một manh mối liên quan trong Bảng manh mối.
- Chất vấn đúng: NPC lộ thêm thông tin hoặc bỏ lời nói dối; Trust của Bảo/Tuấn/bà Ngô +1 (họ thấy Châu nghiêm túc); Hạnh −2 (thiện cảm).

## 2. Cấu hình từng NPC

### NPC01 — Hạnh (Nói dối)
| Lời nói dối | Nội dung | Bị bác bởi | Hậu quả khi bác bỏ thành công |
|-------------|----------|-----------|--------------------------------|
| H-L1 | "Khách sạn chỉ có 12 tầng, chưa từng có tầng 13." | C02, C21 | Hạnh đổi chủ đề, tăng áp lực công việc |
| H-L2 | "Năm 2004 chỉ cháy nhỏ ở kho, không ai bị thương." | C03 + C05 | Hạnh thừa nhận "có người mất tích nhưng đã bỏ đi" |
| H-L3 | "Thu Hà bỏ trốn cùng tiền, bỏ cả con." | C08, C14 | Hạnh cứng người, nói "Cô là con bé đó sao?" (xác nhận gián tiếp T5) |
| H-L4 | "Tôi không có mặt đêm đó." | C09 | Hạnh im lặng, ca 5 mở thoại đối đầu |
| H-L5 | "Cửa thoát hiểm vẫn mở, thang vẫn chạy." | C15, C16 | Lộ T3 trực tiếp, mở khả năng M02 qua thương lượng |

Ca 5: nếu bác được ≥ 3 lời nói dối, Hạnh thừa nhận một phần và giao M02 nếu chưa có (đường dự phòng).

### NPC02 — Bảo (Che giấu → thật khi tin tưởng)
| Trust | Mở ra |
|-------|-------|
| 0–2 | Câu cảnh báo ngắn: "Đừng ấn nút đó." |
| ≥ 3 | Cho mượn I09; mở tủ khóa không bị trừ Trust; kể về Khoa (bảo vệ trẻ) |
| ≥ 4 | Đưa I07 (sân thượng) |
| ≥ 5 | Trả M01 nếu người chơi chưa có; kể về cầu thang hầm |
| ≥ 7 | **C20 Lời thú nhận**: ông cứu Châu năm 2004 |
| ≥ 9 | Đưa Châu đến bàn thờ ở P13 (cảnh phụ, không bắt buộc) |

Thay đổi Tin tưởng: +1 hỏi nhẹ nhàng (CH06), +1 trả M08, +2 đưa C06 (nhật ký Khoa) kèm lời xin lỗi, +1 làm nhiệm vụ phụ, −1 chất vấn khi chưa có M08, −2 báo cho Hạnh việc ông bí mật giúp.

### NPC03 — Tuấn (Nói thật, thiếu thông tin)
| Trust | Mở ra |
|-------|-------|
| ≥ 2 | Dẫn vào kho lạnh (Q2-2) |
| ≥ 4 | C18 (thang máy chạy 00:13) |
| ≥ 6 | Kể thấy Hạnh đốt hồ sơ trong lò hơi sau ca (bổ sung T3) |

### NPC04 — Bà Ngô (Che giấu, thử Châu)
| Trust | Mở ra |
|-------|-------|
| ≥ 2 | Cho Châu lấy I13 trong ngăn kéo |
| CH04 = đưa M04 | Kể về Tùng (C17), rửa phim (C19), **trả lại máy ảnh** vào ca kế tiếp |
| ≥ 6 | Nhận tín hiệu SOS (P12) và gọi cảnh sát — điều kiện của E4/E5 |

### NPC05, NPC06 — Thực thể tầng 13
Không có hội thoại, chỉ cảnh ngắn: NPC05 (bóng áo mưa) đứng yên rồi di chuyển; NPC06 (Thu Hà) chỉ thể hiện bằng ánh sáng ấm, giọng thì thầm và giai điệu nhạc hộp.

## 3. Lựa chọn quan trọng (CH01–CH08)

| ID | Ca | Tình huống | Lựa chọn | Hệ quả |
|----|----|-----------|----------|--------|
| CH01 | 1 | Hạnh bắt Châu hứa không nhắc đến tầng 13 | **Hứa** / **Không hứa** | Hứa: Hạnh +2, nhận I05 sớm (ca 2). Không hứa: Hạnh −1, phải lấy I05 từ L08 |
| CH02 | 2 | Tuấn muốn đưa Châu xuống hầm | **Đi cùng bí mật** / **Báo Hạnh** / **Từ chối** | Đi: Tuấn +2, nhận I06. Báo Hạnh: Tuấn −3, Hạnh +2, đóng đường I06 (vẫn có qua P04). Từ chối: không đổi |
| CH03 | 2 | Nút 13 xuất hiện | **Ấn** / **Không** | Không: không vào F13-A ca này (vào ca sau); không mất Tỉnh táo |
| CH04 | 3 | Bà Ngô xin lại máy ảnh/cuộn phim của con | **Đưa** / **Giữ lại** | Đưa: bà +3, mở C17/C19, điều kiện cần cho E4/E5. Giữ: bà −2, mất C17/C19, E4/E5 không mở |
| CH05 | 3 | Hạnh đề nghị chuyển ca ngày, tăng lương, "đừng tò mò" | **Nhận** / **Từ chối** | Nhận: cờ `bribed`, Q3-4 bị khóa, Hạnh +3, kết thúc nghiêng về E2. Từ chối: Hạnh −2, tiếp tục điều tra |
| CH06 | 4 | Thái độ với ông Bảo khi ông né câu hỏi | **Nhẹ nhàng** / **Gây áp lực bằng bằng chứng** | Nhẹ nhàng: Bảo +1. Áp lực: Bảo −1 nhưng lộ C06 sớm nếu có |
| CH07 | 5 | Hạnh đề nghị: "Đưa tôi sổ sách và băng, tôi sẽ lo cho cô" | **Giao** / **Giữ** | Giao: **E2** (bằng chứng bị hủy). Giữ: tiếp tục |
| CH08 | 5 | Bàn thờ 13 ô, ô thứ 13 mang tên "Minh Châu, 6 tuổi" | **Bước vào ô** / **Từ chối, rời đi** / **Gọi tên mình** (chỉ khi đã biết T5) | Bước vào: **E1**. Từ chối: E3/E4 tùy điều kiện. Gọi tên: mở E5 nếu đủ điều kiện |

## 4. Các kết thúc

### Biến số quyết định
| Biến | Ý nghĩa |
|------|---------|
| `truths` | số T1–T5 đã xác nhận (0–5) |
| `ledger` | có M03/C07 |
| `tapeFull` | hoàn thành P08 |
| `altar` | số di vật đặt đúng ở P13 (0–12) |
| `baoTrust` | Tin tưởng ông Bảo |
| `ngoHelped` | đã đưa M04 (CH04) và hoàn thành P12, bà Ngô Trust ≥ 6 |
| `bribed` | CH05 = Nhận |
| `giveEvidence` | CH07 = Giao |
| `ch08` | enter / refuse / name |
| `sanityZeroD` | Tỉnh táo về 0 ở F13-D |

### Thứ tự đánh giá (ưu tiên từ trên xuống)

| Thứ tự | Kết thúc | Điều kiện |
|--------|----------|-----------|
| 1 | **E1 — Người thứ mười ba** (Xấu) | `ch08 == enter` **hoặc** `sanityZeroD` |
| 2 | **E2 — Vết nứt được trát lại** (Xấu) | `giveEvidence` **hoặc** (`bribed` và `truths < 3`) **hoặc** `truths < 2` |
| 3 | **E5 — Được tìm thấy** (Bí mật) | `truths == 5` và `altar == 12` và `ch08 == name` và `baoTrust >= 7` và `ngoHelped` |
| 4 | **E4 — Ánh sáng sau bức tường** (Tốt) | `truths >= 4` và `ledger` và `tapeFull` và `altar >= 10` và `ngoHelped` |
| 5 | **E3 — Đêm cuối cùng** (Trung tính) | Còn lại |

### Mô tả từng kết thúc

| ID | Tên | Tóm tắt | Cảnh cuối |
|----|-----|---------|-----------|
| E1 | **Người thứ mười ba** | Châu bước vào ô thứ 13 hoặc gục ngã. Tầng 13 "đủ số". Nút 13 biến mất khỏi bảng thang máy | Sáng hôm sau, Hạnh thông báo Châu "nghỉ việc, không rõ tung tích". Ngày 14/9 thêm một tên vào danh sách mất tích |
| E2 | **Vết nứt được trát lại** | Bằng chứng bị hủy hoặc Châu không biết đủ sự thật; rời đi trong im lặng | Một nhân viên mới nhận ca đêm, nút 13 nhấp nháy. Tiếng nhạc hộp xa xăm |
| E3 | **Đêm cuối cùng** | Châu thoát ra, biết một phần sự thật nhưng thiếu bằng chứng; Hạnh không bị truy cứu | Châu đứng trước khách sạn lúc bình minh, cầm mặt dây chuyền, chưa biết tên thật của mình |
| E4 | **Ánh sáng sau bức tường** | Cảnh sát bóc tường tầng 13, tìm thấy hài cốt; Hạnh bị bắt; Châu biết mẹ là Thu Hà | Lễ tưởng niệm, bà Ngô và Bảo đứng cạnh Châu |
| E5 | **Được tìm thấy** | Châu gọi tên mình ở bàn thờ, nhạc hộp phát trọn; tầng 13 khép lại; 12 linh hồn được yên nghỉ | Cảnh Thu Hà mỉm cười, thang máy chỉ còn 12 nút. Châu cầm lại nhạc hộp. Epilogue mở: "Có những tầng chỉ biến mất khi có người dám nhìn" |

### Đường đi mẫu để đạt từng kết thúc

| Kết thúc | Hướng dẫn tóm tắt |
|----------|-------------------|
| E1 | Chơi bình thường nhưng ở ca 5 chọn "Bước vào ô" (CH08), hoặc để Tỉnh táo về 0 trong F13-D |
| E2 | CH05 = Nhận ở ca 3, hoặc CH07 = Giao ở ca 5 |
| E3 | Làm vừa đủ (2–3 sự thật), CH08 = Từ chối |
| E4 | Đưa M04 cho bà Ngô, tìm M03 + băng đủ 3 đoạn (P08), P12, CH07 = Giữ, đặt ≥ 10 di vật |
| E5 | Như E4 + thu đủ 12 di vật, T5 xác nhận, Bảo Trust ≥ 7, CH08 = Gọi tên mình |

## 5. Mẫu kịch bản hội thoại (rút gọn)

**Ca 1 — Hạnh nhận ca (CH01)**
```
HẠNH: Cô Châu phải không? Ca đêm ở đây yên tĩnh lắm. Chỉ có một điều... đừng bao giờ nhắc đến "tầng 13" với khách.
CHÂU: (1) "Tầng 13 là sao ạ?"   (2) "Dạ, em hứa."   (3) "Em chưa thấy tầng nào như thế."
  (1) HẠNH: Không có tầng nào cả. Đó là điều tôi muốn cô nhớ.        [Hạnh -0, flag asked13]
  (2) HẠNH: Tốt. Cô sẽ làm được.                                      [CH01=hứa, Hạnh +2]
  (3) HẠNH: ...Vậy thì càng tốt.                                      [CH01=không hứa, Hạnh -1]
```

**Ca 4 — Chất vấn Hạnh (H-L4)**
```
HẠNH: Đêm đó tôi ở nhà, không có mặt ở khách sạn.
[Chất vấn] -> chọn C09 (Băng ghi âm đoạn 1)
CHÂU: Vậy giọng này là của ai? "Khóa cửa lại. Không ai được ra khỏi tầng này."
HẠNH: (im lặng) ...Cô lấy cái đó ở đâu?   [H-L4 bị bác; Hạnh -2; flag hanh_confronted_1]
```

## 6. Phản ứng thế giới theo lựa chọn

| Điều kiện | Thay đổi |
|-----------|----------|
| `bribed` | Hạnh thân thiện giả tạo, các cửa văn phòng bị khóa, nhưng Tuấn/Bảo giảm tin tưởng khi thấy Châu "đổi phe" |
| Bà Ngô Trust ≥ 6 | Đứng ở cửa 807 vào đêm 5, có thể thấy tín hiệu |
| Bảo Trust ≥ 7 | Chờ ở thang máy ca 5, đưa đèn pin tốt hơn (giảm mất Tỉnh táo) |
| `thrown_out_N` | Hạnh nhận xét "Cô trông tệ lắm" và đề nghị nghỉ |
