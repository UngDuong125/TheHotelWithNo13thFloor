# Rà soát tài liệu trước khi tạo asset

**Dự án:** Khách sạn không có tầng 13  
**Ngày rà soát:** 06/10/2026  
**Phạm vi:** Đọc toàn bộ `docs/00_README.md` đến `docs/11_Danh_Sach_Asset.md` và nội dung 3 trang `23120061.pdf` trong `D:\Dang\Game\DA\TheHotelWithNo13thFloor`. Đây là rà soát tài liệu, chưa có build game để kiểm chứng hành vi. Không sửa tài liệu nguồn.

## 1. Kết luận

Bộ tài liệu đủ để thử phong cách, dựng bản mẫu và lên danh mục sơ bộ, nhưng **chưa đủ ổn định để tạo hàng loạt asset hoàn chỉnh**. Rủi ro lớn nhất là làm đúng một tài liệu nhưng sai tài liệu khác, hoặc vẽ asset liền nền rồi phải tách/vẽ lại khi triển khai tương tác.

PDF gốc là ý tưởng ban đầu với 7 cơ chế; không bắt buộc chính xác 5 ca, 13 câu đố, 12 di vật, 22 manh mối hay số lượng tranh hiện tại. Các con số này do bộ Markdown mở rộng. Vì vậy có thể thu gọn, nhưng phải giữ nhất quán chuỗi điều kiện để chơi được và đạt các kết thúc.

Ba loại nhận xét trong báo cáo:

- **Mâu thuẫn:** hai mô tả hiện có không khớp; cần chọn một bản chuẩn.
- **Thiếu đặc tả:** chưa đủ thông tin để sản xuất hoặc tích hợp; không đồng nghĩa phải thêm một ảnh mới.
- **Đề xuất tiết kiệm:** có thể dùng chung hoặc hoãn; không phải yêu cầu đã được chốt.

Các dẫn nguồn bên dưới dùng tên file và dòng của bản đã đọc. Số dòng có thể thay đổi sau khi sửa.

## 2. Các điểm cần chốt trước khi làm asset hoàn chỉnh

### A01 — Phạm vi MVP và ưu tiên asset không thống nhất

**Loại:** Mâu thuẫn — ảnh hưởng toàn bộ kế hoạch sản xuất.

- `01_GDD.md:137–139`: P01–P08 là Must, P09–P13 và 12 di vật là Should, nhưng 5 kết thúc lại là Must.
- `09_Ke_Hoach_San_Xuat.md:56`: MVP gồm P01–P08 + P12 + P13, F13-A/B/D; không liệt kê P09/P10, dù đây là đường lấy máy ảnh/nhạc hộp và giải biến thể A/B.
- `11_Danh_Sach_Asset.md:205–217`: P09/P10/P12/P13 đều P0.
- I07 và I16 bị xếp P1 (`11:144,153`), trong khi lần lượt mở sân thượng cho Q4-1/P12 và tủ chứa M03/I12 cho P08/E4.
- Nhiều di vật là P1 (`11:162–173`), nhưng E4 cần đặt đúng ít nhất 10, E5 cần đủ 12.

**Ảnh hưởng:** cắt theo P1 hiện tại có thể cắt mất đường tới kết thúc bắt buộc. Sản lượng và thứ tự làm việc vì thế chưa đáng tin.

**Đề xuất:** chọn một cấu hình MVP duy nhất. Nếu giữ đủ 5 kết thúc, phải có đủ 12 di vật và đường nhận chúng; có thể giản lược minh họa, animation, hoặc thay F13-C bằng cutscene, nhưng phải chuyển phần thưởng M12/C16/C21 sang đường thay thế rõ ràng. Tách “bắt buộc có chức năng” khỏi “mức độ trau chuốt hình ảnh”.

### A02 — Quay lại tầng 13 ở ca 5 bị chính quy tắc chặn

**Loại:** Mâu thuẫn — cần chốt trước UI thang máy và cảnh quay lại.

- `01:91`, `03:73–77`, `10:32–33`: tối đa một lần mỗi ca; ca 5 luôn vào D.
- Ngay `03:77`, `05:48`, `10:77` lại cho dùng M02 vào lại A–C ở ca 5 trước D.
- `07:134–137` cũng khóa khi `enteredThisNight` đã bật.

**Ảnh hưởng:** chưa biết có cần giao diện chọn ký ức/biến thể, cảnh quay lại, trạng thái đã hoàn thành, hay một đường dẫn khác. Lời hứa “bỏ ca không mất nội dung” chưa được bảo đảm.

**Đề xuất:** định nghĩa riêng chế độ quay lại ký ức trước điểm không thể quay đầu vào D; ghi rõ giới hạn lượt, thời gian, mức Tỉnh táo, cách chọn A/B/C và trạng thái sau khi lấy đồ. Hoặc bỏ cơ chế quay lại và chuyển vật phẩm bỏ lỡ sang đường khác; không giữ đồng thời hai luật hiện tại.

### A03 — Góc nhìn và cách điều khiển chưa đủ rõ để vẽ cảnh/nhân vật

**Loại:** Thiếu đặc tả.

`01:10,51` mô tả point-and-click theo phòng; `08:5` ghi side-view; `08:53` và SP01 (`11:122`) xem sprite đi bộ là tùy chọn. Nhưng P11 (`04:98`) yêu cầu tránh các bóng người di chuyển và “chạm vào bóng”; P09 (`04:88`) phạt khi nhìn thẳng thực thể.

**Cần chốt:** Châu có hiện diện trong cảnh và được điều khiển di chuyển không? Hay người chơi chỉ click hotspot và chuyển góc nhìn? “Nhìn thẳng” nghĩa là giữ con trỏ, giữ vùng nhìn, chạm vào bóng, hay đứng trong vùng nguy hiểm?

**Ảnh hưởng asset:** nếu là cảnh tĩnh, có thể dùng ảnh nền + sprite NPC đứng; nếu di chuyển thực, cần kích thước nhân vật trong cảnh, hướng nhìn, animation, đường đi và vật che phía trước. Không nên tạo sprite sheet đi bộ hoặc toàn bộ nền trước khi chốt.

### A04 — P09 là tìm cửa sai số hay tìm mọi chi tiết khác biệt?

**Loại:** Mâu thuẫn trực tiếp.

`04:84–86` yêu cầu mỗi vòng có một cánh cửa đổi số, chọn cánh cửa; nhưng ví dụ vòng 2 là biển thoát hiểm đảo ngược, vòng 3 là tranh đổi thành ảnh. `10:61` và BG36 (`11:85`) dùng quy tắc một “chi tiết” thay đổi.

**Đề xuất:** thống nhất thành tìm một chi tiết bất thường và click trực tiếp chi tiết đó, phù hợp các ví dụ hiện có. Chốt ảnh chuẩn để so sánh, vị trí từng sai khác và điều kiện qua vòng. Không vẽ ba nền độc lập; dùng một nền chuẩn cùng các lớp biển số/biển thoát hiểm/tranh thay thế để tránh vô tình tạo thêm khác biệt.

### A05 — Nhạc hộp M01 vừa nằm trên bàn vừa bị khóa trong tủ

**Loại:** Mâu thuẫn trực tiếp.

`03:82`, `04:91`, `05:34` đặt M01 trong tủ, nhận sau P10; BG38 (`11:87`) lại có nhạc hộp trên bàn. I10 nằm dưới nhạc hộp (`05:16`). Story Bible (`02:78`) nói nghe giai điệu lần đầu ở ca 3, trong khi EV03 đã phát từ ca 2 (`03:97`, `04:91–94`).

**Đề xuất:** để hộp trong tủ khóa, âm thanh vọng ra; trên bàn chỉ có 5 nến. Khi P10 hoàn tất, mở tủ và lộ M01 + I10. Chốt lại “lần đầu nghe từ xa” và “lần đầu nghe rõ”. Asset cần nền tủ sạch, cửa mở/đóng, hộp có/không, ngăn thư C08 mở/đóng; không bake hộp vào nền bàn.

### A06 — Bàn thờ P13 vừa là bàn đặt đồ vừa là nơi Châu bước vào

**Loại:** Thiếu đặc tả không gian quan trọng.

`04:109–112` mô tả 13 ô đặt di vật nhưng lựa chọn E1 là Châu “bước vào ô”; BG45 và `pz_P13_altar` (`11:94,217`) chưa quy định kích thước thực.

**Đề xuất:** vẽ sơ đồ bàn thờ trước. Một phương án là 12 hốc đặt di vật và một ô/ngưỡng cửa kích thước người ở giữa dành cho Châu. Đánh số vị trí, camera, vùng kéo thả, vị trí đứng và nơi đặt I02. Đây phải là cùng một thiết kế trong gameplay, E1 và E5.

### A07 — Ngày ca trực, ngày cháy và lịch chưa thống nhất

**Loại:** Mâu thuẫn và thiếu quy ước thời gian.

- Ca chạy 22:00–06:00 (`01:42`); ca 5 ghi 13/09 (`02:70`). Nếu đó là ngày bắt đầu, 00:13 trong ca 5 đã là 14/09, trong khi vụ cháy được ghi 00:13 ngày 13/09/2004 (`02:29`).
- `02:9` và QA `10:45` nói mọi lịch đều thiếu trang 13/9. P03 (`04:44`) lại mô tả lịch còn ngày 13 và 14, bị xé quanh ngày 13.
- C01 trong asset list (`11:178`) là lịch tháng 9/2004 ở nhiều phòng, dù hiện tại là 2024. Có thể là chủ ý siêu nhiên, nhưng chưa có mô tả phân biệt lịch hiện tại và lịch bằng chứng cũ.

**Đề xuất:** chốt ngày bắt đầu/kết thúc từng ca bằng timestamp đầy đủ; xác định vụ cháy là rạng sáng 13 hay 14/09. Khóa một đáp án lịch/mật mã, rồi đồng bộ C01, C03, C05, C06, C14, P03, P06, thẻ ca và tranh kết thúc. Tách lịch đang dùng năm 2024 khỏi lịch cũ năm 2004 nếu cả hai cùng xuất hiện.

### A08 — Tranh kết thúc và điều kiện kết thúc chưa khớp

**Loại:** Mâu thuẫn — cần sửa trước storyboard CS03–CS07.

1. **E3:** `06:111` nói Châu “chưa biết tên thật của mình”, dù đầu game đã tên Minh Châu. Hơn nữa nhánh E3 vẫn có thể xảy ra khi đã biết T5 nhưng thiếu di vật/trợ giúp. Nên đổi sang câu kết trung tính về điều chưa giải quyết, hoặc phân nhánh lời dẫn theo T5.
2. **E1:** C05 đã có “Minh Châu, 6 tuổi” (`05:58`), nhưng `06:109` và CS03 (`11:274`) nói danh sách thêm một tên. Cần chỉ rõ đây là danh sách năm 2024, một hồ sơ mất tích mới, hay dòng cũ biến đổi; tránh tự động vẽ tên thứ 14 trên bảng 13 người.
3. **E1 do cạn Tỉnh táo:** điều kiện cho phép Châu gục ngã, nhưng CS03 chỉ mô tả bước vào ô. Cần một mở đầu thay thế, hoặc một shot chung phù hợp cả hai nguyên nhân.
4. **E5:** thang máy “chỉ còn 12 nút” (`06:113`, `11:278`) không khớp bảng B1 + 1–12 (13 nút thường). Nên ghi “nút 13 biến mất; giữ B1 và 1–12”.
5. **E5 và P08:** bảng điều kiện `06:101` và thuật toán `07:166–167` không yêu cầu `tapeFull`/`ledger` như E4, nhưng hướng dẫn `06:123` và QA `10:93` nói “như E4 +…”. `altar == 12` gián tiếp bao gồm M03, nhưng 5 sự thật có thể xác nhận không qua P08. Cần quyết định băng đầy đủ có bắt buộc cho E5 không.
6. **CH07:** `06:76` nói giao bằng chứng là E2 ngay, nhưng QA `10:95` lại mong có CH08 sau đó để E1 được ưu tiên. Cần chốt thời điểm kết thúc; đừng dựng cảnh bàn thờ sau nhánh đã kết thúc nếu không có chủ ý.

### A09 — Nguồn gợi ý P13 chưa đủ để ghép đúng 12 người

**Loại:** Thiếu đặc tả và xung đột nội dung gợi ý.

P13 dùng thứ tự trong “ảnh nhân viên” C12 (`04:110,113`), nhưng 12 nạn nhân gồm chủ khách sạn, khách VIP, khách lưu trú, phóng viên và nhân viên (`05:34–45`). Không thể mặc định tất cả cùng có trong ảnh nhân viên. Quy định chung `11:158` nói di vật có khắc tên, nhưng từng dòng chỉ có tên viết tắt, ngày cưới, hoặc ảnh 3 người; chưa đủ nhận diện nhất quán.

**Đề xuất:** dùng C05 làm danh sách chuẩn; tạo bảng 12 dòng gồm tên đầy đủ, nghề, di vật, dấu nhận diện đọc được, vị trí ô. C12 chỉ phục vụ nhận diện Châu–Thu Hà, hoặc đổi thành ảnh buổi tiệc có lý do để đủ người xuất hiện. Chốt ngày cưới trên M11, người trong M12 và nội dung nhãn từng vật trước khi tạo ảnh chi tiết.

### A10 — Kiến trúc tầng 13 và tín hiệu sân thượng cần một sơ đồ chuẩn

**Loại:** Thiếu đặc tả không gian; chưa đủ cơ sở kết luận bất khả thi.

`02:26` xây tầng 13 từ sân thượng cũ; `03:7–22` đặt sân thượng R phía trên tầng 13, nối thang ngoài trời từ F12; BG01 (`11:34`) yêu cầu mặt tiền 12 tầng và tầng 13 chỉ lộ trong cutscene. Cần thể hiện cách tầng 13 bị giấu về mặt hình học. P12 (`04:104`) yêu cầu bà Ngô từ phòng 807 nhìn thấy đèn trên sân thượng cùng tòa nhà; đường nhìn chưa được xác định.

**Đề xuất:** một mặt cắt và một sơ đồ đường nhìn, quy định tầng lùi vào, khu bị xây bít, thang ngoài, hướng cửa sổ 807 và đèn nhô ra/chiếu đến đâu. Đồng bộ mặt tiền, bản vẽ C02, sơ đồ C21, sân thượng, cửa thoát hiểm và cutscene phá tường.

## 3. Các mâu thuẫn phụ và rủi ro tiến trình liên quan asset

| ID | Bằng chứng | Vấn đề / hướng xử lý |
|---|---|---|
| B01 | `07:137` so với `05:26`, `07:113–114` | M02 là di vật lưu trong `keepsakes`, nhưng thuật toán nút 13 tìm trong `inventory`. Chuẩn hóa hàm kiểm tra sở hữu; không thiết kế UI như thể M02 là vật phẩm thường. |
| B02 | `05:26`; `11:228`; `07:113` | Vật cốt truyện và di vật vào Hộp di vật, nhưng UI chỉ có 12 ô hình bóng cho 12 di vật; I02 còn cần dùng ở ô 13. Chốt khu riêng cho đồ cốt truyện và vị trí I02; quy định đồ đã dùng có giải phóng ô không. |
| B03 | `06:47`; `04:103–105`; `05:41` | Trả M08 cho Bảo tăng Trust, nhưng M08 còn cần P12/P13. Chưa nói trả lại lúc nào hay chỉ cho xem. Chốt trạng thái sở hữu và đường lấy lại; máy ảnh M04 đã có quy tắc trả, còi thì chưa. |
| B04 | `05:37`; `06:60,73`; `03:77` | Nếu lấy M04 muộn qua đường quay lại ca 5, “trả máy ảnh ở ca kế tiếp” không còn phù hợp; CH04 cũng chỉ gắn ca 3. Cần điều kiện cho lựa chọn trễ và trả máy ảnh trước P13 nếu vẫn muốn bảo đảm đường bù. |
| B05 | `04:53`; `05:40`; `03:34` | M07 được mô tả sau kệ ở kho lạnh và kệ sau bếp. Chốt một vị trí, hoặc là phần thưởng hội thoại sau P04. Tránh vẽ vật ở cả hai cảnh. |
| B06 | `04:19,99`; `05:59,69` | Bảng tổng quan P11 ghi thưởng C06, phần chi tiết ghi C16; C06 là nhật ký ở P03. Khả năng cao cần sửa C06 thành C16 trong dòng tổng quan P11. |
| B07 | `02:50`; `03:99`; `04:38` | NPC05 ghi xuất hiện ca 2–4, EV05 ghi ca 1,2,4, P02 đã cho xuất hiện ca 1. Chốt lịch sự kiện để lập bảng trạng thái cảnh. |
| B08 | `01:66`; `03:102`; `07:174` | EV08 ở hầm trừ Tỉnh táo trong khi hệ thống chỉ hoạt động ở L16. Chốt đây là thay đổi Tỉnh táo lưu lại hay chỉ hiệu ứng kinh dị. |
| B09 | `01:97`; `05:83–87` | GDD nói T1/T3/T4/T5 chỉ có ở tầng 13, nhưng các cặp C02+C04, C06+C15, C08+C14 qua M01 dự phòng, C05+C20 có thể xác nhận ngoài tầng 13. Cần sửa lời khẳng định hoặc bổ sung điều kiện, không vô tình tạo thêm cảnh bắt buộc. |
| B10 | `04:56`; `02:68`; `05:21` | Q3-1 gắn P05, nhưng I15 chỉ xuất hiện “sau Q3-1”. Có nguy cơ vòng điều kiện nếu hoàn thành Q3-1 cần P05. Tách bước giao vật thất lạc/mở ngăn kéo khỏi bước ghép ảnh. |
| B11 | `06:71`; `03:61–62`; `07:99–101` | Báo Hạnh làm Tuấn −3, nhưng đường dự phòng P04 cũng nằm trong kho lạnh cần Trust ≥2. Có nhắc nhiệm vụ bù nhưng chưa định danh/nội dung/giới hạn. Chưa thể xác nhận đường dự phòng luôn đạt được. |
| B12 | `06:40–61`; `03:66`; `02:69–70` | Không có bảng Trust ban đầu và đầy đủ hành động tăng điểm. Nhiệm vụ bắt buộc sân thượng/băng có thể lệ thuộc Trust và đồ bỏ lỡ. Cần liệt kê nhiệm vụ bù, NPC, lời thoại và đạo cụ tương ứng. |
| B13 | `05:48`; `06:29–35` | M02 dự phòng cần bác ≥3 lời nói dối; nhiều chứng cứ lại nằm sau P06/F13. Không được mặc định đây là đường cứu cho mọi tình huống bỏ lỡ. Cần kiểm tra theo tổ hợp chứng cứ thực tế. |
| B14 | `01:70`; `11:134–155` | GDD cho kiểm tra chi tiết/xoay/phóng to nhưng nhiều vật ghi “Không” có ảnh chi tiết. Xác định chỉ một số vật được inspect, hay dùng ảnh gốc lớn để sinh icon; tránh phóng icon 128 px lên toàn màn hình. |
| B15 | `11:226` | “5 trạng thái” nhưng chỉ liệt kê normal/pressed/disabled. Có thể là 5 nút, mỗi nút 3 trạng thái. Sửa cách ghi trước khi giao UI. |
| B16 | `04:51,92`; `11:291` | P04 còn “lời giải mẫu” và 3 bố cục ngẫu nhiên chưa có layout; P10 ghi nốt “ví dụ”, asset list lại xem 3-1-4-2-5 là cố định. Khóa dữ liệu câu đố trước khi thu âm/vẽ hướng dẫn. |

## 4. Những đặc tả còn thiếu trước khi giao artist hoặc tạo ảnh

### 4.1 Hợp đồng tách lớp và trạng thái của từng cảnh

Tài liệu đã có độ phân giải, định dạng, bảng màu và naming cơ bản. Phần còn thiếu là **cách asset kết hợp để chơi được**:

- Nền sạch không chứa vật có thể nhặt/di chuyển; lớp tiền cảnh che nhân vật; lớp ánh sáng; lớp tương tác; vị trí hotspot.
- Mỗi đồ tương tác cần trạng thái nào: cửa/tủ/ngăn kéo đóng–mở, có đồ–đã lấy, bật–tắt, khóa–mở, trước–sau câu đố.
- Danh sách cụ thể còn chưa có dòng riêng: phòng 502 sau khi sửa đèn; sàn 505 trước/sau cạy và nhẫn còn/đã lấy; cầu thang hầm sau khi mở; két/tủ hồ sơ đóng–mở–trống; nhạc hộp đóng–mở–ngăn thư; đèn tín hiệu tắt–sáng.
- Không nhất thiết vẽ thêm cả background cho mỗi trạng thái. Ưu tiên lớp vật/ánh sáng tái dùng, nhưng phải có quy định và tên file.

**Đề xuất manifest:** `Asset ID | L/P/Q/EV sử dụng | nguồn hình dùng chung | trạng thái | kích thước | pivot/vị trí | lớp | alpha | chữ động | ưu tiên chức năng | mức hoàn thiện | trạng thái duyệt`.

### 4.2 Bộ mẫu nhân vật và đồ vật nhất quán

Cần model sheet cho Châu/Hạnh/Bảo/Tuấn/bà Ngô/Thu Hà, gồm khuôn mặt, trang phục, tỷ lệ, màu, hướng nhìn và phụ kiện. Chân dung hội thoại không tự thay thế sprite trong cảnh.

Đặc biệt cần bản năm 2004: Bảo khoảng 42 tuổi, Hạnh khoảng 34 tuổi, bé Châu 6 tuổi và Thu Hà lúc còn sống. Những người này xuất hiện trong C12/C14/C20, cảnh ký ức và cutscene. Tùng và Hưng cũng cần mẫu nhận diện cho C17/C19 và các hồi ức dù không nhất thiết có bộ biểu cảm hội thoại.

I02 mới được asset list thêm hình trái tim, ảnh trong nắp và chữ khắc (`11:139`), nhưng chưa chốt ảnh ai, khắc gì, thời điểm được xem. Đây có thể làm lộ bí mật sớm. Chốt một thiết kế dùng chung cho chân dung Châu, ảnh C12, cận cảnh C13, vật phẩm và E3/E5.

### 4.3 Nội dung chữ của tất cả manh mối

Hiện phần lớn chỉ có mô tả tóm tắt. Cần bản chữ cuối cùng của lịch, báo, nhật ký, danh sách 13 người, thư mẹ, hồ sơ nhân sự, hợp đồng, sổ thu chi, nhãn băng và giấy Morse; kiểm tra ngày, tên, chữ ký và mức tiết lộ.

Đề xuất tạo chất liệu giấy/ảnh nền riêng, đặt chữ bằng lớp text có thể sửa và dịch. Với chữ khắc/viết tay tích hợp hình ảnh, vẫn lưu bản text chuẩn và lớp chữ riêng trong nguồn. Nếu dùng AI tạo ảnh, không giao AI tự quyết định tên người, con số và lời giải.

### 4.4 Đạo cụ cho nhiệm vụ hằng đêm

Q1-2 mang khăn, Q2-1 mang đồ ăn, Q2-3/Q3-4 giao hồ sơ, Q3-1 tìm đồ thất lạc (`02:66–69`) nhưng chưa có mapping rõ trong danh sách I01–I18 và asset list. Cần chốt khăn, khay ăn, tập hồ sơ, vật thất lạc có xuất hiện trên màn hình/túi đồ hay chỉ được thể hiện bằng text.

Không nhất thiết thêm inventory ID cho mọi đạo cụ. Tuy nhiên mỗi nhiệm vụ cần ghi rõ asset được tái dùng hoặc quyết định chỉ dùng lời thoại để không phát sinh bất ngờ khi làm quest.

### 4.5 UI còn thiếu bố cục và luồng

Đã có nhiều thành phần UI, nhưng chưa đủ thiết kế hoàn chỉnh cho:

- Màn inspect/phóng to/mặt sau, kết hợp đồ và chọn vật để đưa NPC.
- Tóm tắt ca; thư viện kết thúc đã mở; màn pause; xác nhận ghi đè save/chơi mới.
- Puzzle: Reset, Bỏ qua tạm, Thoát, replay âm thanh, trạng thái sai/đúng và trạng thái vô hiệu hóa.
- Phụ đề âm thanh quan trọng và trạng thái khi âm lượng bằng 0.
- Cách trình bày khi túi đồ đầy, thiếu đồ, vùng khóa, vật phẩm đang được NPC giữ.

Đa số dùng cùng UI kit và text, không cần vẽ bộ nút mới cho từng màn. Cần wireframe để ước lượng thật.

### 4.6 P08/P10: âm thanh là dữ liệu giải đố

VO01 là P1 (`11:340`) nhưng P08 yêu cầu nghe câu nối và chỉnh tốc độ để rõ (`04:78`). Nếu không thu thoại, phải có phiên bản puzzle thay thế bằng transcript/timestamp rõ ràng; không chỉ xóa âm thanh khỏi asset list.

P10 cần chốt 5 cao độ cụ thể, thứ tự nốt, nhịp, độ dài, khoảng nghỉ, ánh sáng đồng bộ và tín hiệu khi bấm sai. Câu phụ đề “[Tiếng nhạc hộp]” chưa truyền được lời giải khi người chơi tắt tiếng. Nên có chuỗi sáng tương đương hoặc chế độ hỗ trợ.

P12 cần quy định thời lượng chấm/gạch/khoảng cách và dung sai, cùng hiển thị SOS. Chốt script C09/C10/C11, người nói, độ dài và mốc 00:00/01:10/02:05/03:12 trước khi thu âm.

### 4.7 Kích thước hiển thị và xuất file

`07:229` hỗ trợ 16:9–20:9; `11:15` dùng 1920×1080 và tùy chọn 2560×1080 cuộn ngang. Cần chọn crop, letterbox hay mở rộng khung nhìn; đánh dấu vùng an toàn cho hotspot và câu đố. Không để đáp án hoặc vật phẩm nằm ngoài màn hình ở tỉ lệ khác.

Cần bổ sung: hướng màn hình cố định hay xoay; kích thước nhân vật trong cảnh; pivot; pixels-per-unit nếu dùng; vùng 9-slice; kích thước sheet/số frame theo animation; nguồn có layer; quy tắc texture atlas; ngân sách ảnh lớn theo cảnh. Quy định sheet 8–16 frame (`11:21`) không nên áp đặt cho SP02/SP03 vốn chỉ có 4+6 và 2 frame; tách quy cách theo loại asset.

“Cận cảnh cắt từ nền” chỉ dùng khi đủ độ phân giải. Vật rất nhỏ trong nền 1920×1080 không tự trở thành ảnh inspect 1024×1024 sắc nét. Nên tạo vật/cận cảnh gốc lớn, rồi thu nhỏ để ghép vào nền.

### 4.8 Storyboard và asset mới xuất hiện trong ending

Cần storyboard từng shot trước khi vẽ 12 ảnh ending. Ghi nhân vật nào xuất hiện, tuổi/trang phục, vị trí, động tác, điều kiện thay lời dẫn. Nhân viên mới E2 và cảnh sát E4 có thể dùng silhouette hoặc chỉ xuất hiện trong tranh, nhưng phải có quyết định này; không nhất thiết thêm NPC có dialogue.

## 5. Phần có thể dư hoặc nên hoãn

| Hạng mục | Đánh giá | Cách giảm công đề xuất |
|---|---|---|
| I13–I15, P05, C12 và C13 | Nhiều biểu diễn của cùng một ảnh/chứng cứ; không phải nhiều concept độc lập | Vẽ một ảnh C12 chuẩn có lớp nhân vật, cắt 3 mảnh dùng cho item/puzzle; C13 là crop hoặc bố cục đối chiếu với I02. |
| M03 và C07 | Cùng sổ thu chi | Một bộ bìa/trang, sinh icon và trang manh mối. |
| M04 và C19 | Cùng máy ảnh và phim | Chốt asset cha/con; 3 ảnh phim vẫn cần nội dung riêng, không tính như 3 máy ảnh. |
| BG34 và C05; BG44 và C16; I09 và P08 | Có thể dùng chung nguồn hình | Tái dùng với crop/zoom/lớp UI, không vẽ hai phiên bản lệch nhau. |
| BG12/BG13 | Hai trạng thái cùng kho lạnh | Một nền sạch + thùng + cửa ngầm, thay vì hai tranh hoàn chỉnh. |
| BG36 ba vòng | Không nên là ba nền độc lập | Một nền + lớp sai khác; bảo đảm đúng một khác biệt theo luật puzzle. |
| 3 biến thể hành lang chung | Có thể vượt nhu cầu MVP | Làm một nền, thử ánh sáng/số cửa; chỉ thêm biến thể khi có sự kiện cụ thể. |
| Chân dung NPC05, Thu Hà, bé Châu | NPC05/NPC06 không có hội thoại theo `06:63–64` | Chỉ sản xuất dạng thực sự xuất hiện: silhouette, sprite cảnh hoặc tranh; không tự động làm đủ chân dung hội thoại cho mọi nhân vật. |
| 5–6 biểu cảm cho toàn bộ NPC chính ngay từ đầu | Chưa có bảng thoại–biểu cảm đầy đủ | Làm neutral + biểu cảm cần cho ca 1, rồi tăng theo script được duyệt. |
| 12 tranh hồi ức riêng cho di vật | Đã là tùy chọn P2 | Có thể dùng zoom vật + 1–2 câu + âm thanh, phù hợp mô tả `05:30`. |
| 5 bản nhạc ending, các bản méo/đảo | Có thể hoãn hòa âm hoàn chỉnh | Chốt mô-típ puzzle trước; các biến thể cảm xúc làm sau storyboard. Không dùng bản đảo ngẫu nhiên trong đoạn dạy đáp án. |
| Nhà hàng/808, đi bộ chuyển cảnh, bụi, hơi lạnh trang trí | Không phải tất cả đều cần để kiểm chứng core loop | Hoãn nếu nhiệm vụ phụ liên quan cũng được cắt hoặc chuyển địa điểm. |
| Feature graphic, poster, trailer và ảnh cửa hàng | Phục vụ phát hành, không phải điều kiện để tạo bản chơi thử | Tách milestone phát hành khỏi P0 gameplay; không dùng cùng một mức ưu tiên cho cả hai. |

Không nên cắt mù các mục P1: I07, I16, M12 và đường nhận vật phẩm có thể bắt buộc về chức năng dù tranh minh họa đẹp hơn là tùy chọn.

## 6. Đếm lại bảng tổng hợp asset

Đếm theo từng dòng chi tiết trong tài liệu 11, với chân dung tính theo số biểu cảm, C09–C11 tính thành 3 manh mối. Các nhóm BG/CS/MU là **nhóm ID**, không phải số file xuất.

| Nhóm | Tổng hợp đang ghi P0/P1/P2 | Đếm từ bảng chi tiết P0/P1/P2 | Ghi chú |
|---|---|---|---|
| Background | 31 / 12 / 3 | **34 / 10 / 2** | 46 ID, nhưng BG16/BG36/BG39 chứa nhiều biến thể. |
| Chân dung | 31 / 1 / 3 | **30 / 2 / 3** | Tổng 35 biểu cảm/hình. |
| Icon I01–I18 | 17 / 1 / 0 | **16 / 2 / 0** | I07 và I16 đều P1. |
| Di vật | 4 / 8 / 0 | **5 / 7 / 0** | P0 là M01–M04 và M08. |
| Manh mối | 11 / 11 / 0 | **13 / 9 / 0** | C09–C11 là 3, không phải một manh mối. |
| VFX | 3 / 11 / 1 | **3 / 10 / 2** | Bụi và hơi lạnh là P2. |
| Cutscene | 4 / 2 / 1 | **6 / 2 / 1** | Bảng cũ cộng lại chỉ 7 dù có 9 nhóm. |
| Nhạc | 6 / 3 / 1 | **5 / 3 / 1** | Bảng cũ cộng lại 10 dù có 9 nhóm. |

46 background so với 26–28 cảnh **không tự nó là mâu thuẫn**, vì bảng 11 tính cả cận cảnh/biến thể. Tuy nhiên câu “28 cảnh chính + 18 cận cảnh/biến thể” chưa có mapping rõ để kiểm chứng, và số file còn tùy cách tách lớp. Không dùng số 46 hay ~55 làm định mức sản xuất cuối cùng.

Tương tự, `18 + 12 + 22` là số ID nội dung, không phải số hình mới: một số trùng nguồn hình, một số lại cần icon, front/back, trạng thái và nhiều trang. Cần manifest một dòng cho mỗi deliverable thực tế, có liên kết asset nguồn.

## 7. Trình tự triển khai đề xuất

1. **Khóa thiết kế gây làm lại:** MVP; góc nhìn/điều khiển; quy tắc quay lại tầng 13; ngày giờ; P09/P10/P13; điều kiện và hình ảnh ending.
2. **Lập bảng nguồn chuẩn:** 13 người, di vật, ô bàn thờ; ngày trong bằng chứng; bản chữ manh mối; ngoại hình hiện tại/2004; trạng thái item và trả đồ.
3. **Lập manifest có phụ thuộc:** scene → hotspot → puzzle/quest → item/clue → ending; tách mức bắt buộc về chức năng và mức hoàn thiện hình ảnh; đếm file từ manifest.
4. **Làm một bộ mẫu nhỏ:** L01/L02/L04; Châu/Hạnh/Bảo; UI cơ bản; I02; P01/P02 và vài âm thanh. Dùng asset tạm để kiểm tra thao tác, text và tỉ lệ màn hình trước khi trau chuốt.
5. **Duyệt hai cảnh đối lập:** một phòng thường và F13-A để khóa chất liệu, phối cảnh, ánh sáng, lớp tương tác và độ rõ của manh mối.
6. **Sản xuất theo ca và chuỗi mở khóa:** hoàn thiện ca 1, rồi A/B, sau đó phần còn lại. Chỉ tạo tranh ending sau khi storyboard và luật kết thúc thống nhất.

## 8. Điều kiện để bắt đầu tạo hàng loạt

- [ ] Chỉ còn một bảng phạm vi MVP và một nguồn ưu tiên asset.
- [ ] Quy tắc vào/quay lại tầng 13 không còn tự chặn nhau.
- [ ] Có camera/điều khiển chuẩn, sơ đồ phòng và vùng an toàn UI.
- [ ] P09/P10/P13 có luật, layout và trạng thái rõ ràng.
- [ ] Ngày giờ, lịch, 13 tên và lời giải được khóa.
- [ ] Mỗi di vật có nguồn nhận, trạng thái sở hữu, dấu nhận diện và ô đặt đúng.
- [ ] Nội dung manh mối cùng model sheet năm 2004 đã duyệt.
- [ ] Mỗi asset có quyết định tạo mới/tái dùng và tách lớp.
- [ ] Audio giải đố có dữ liệu chuẩn và cách chơi khi tắt tiếng.
- [ ] Tổng số asset được sinh lại từ manifest thay vì cộng tay.

**Ưu tiên thực tế:** sửa các quyết định nền tảng và làm bộ mẫu nhỏ trước. Chưa cần bổ sung thêm phòng, NPC hay câu đố; vấn đề hiện tại chủ yếu là tính nhất quán, khả năng triển khai và tránh làm trùng.
