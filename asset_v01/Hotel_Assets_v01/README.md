# Khách sạn không có tầng 13 — Bộ asset duyệt v01

Ngày tạo: 06/10/2026. Trạng thái: **bản duyệt đầu, chưa phải bộ asset đầy đủ để phát hành**.

Mở `index.html` bằng trình duyệt để xem ảnh, nghe âm thanh, lọc nhóm, phóng to, ghi góp ý và xem hai cảnh ghép thử. Giữ nguyên cấu trúc thư mục. Góp ý lưu cục bộ trong trình duyệt; nút “Xuất góp ý” tải file JSON, không tự gửi dữ liệu đi.

## Đã có trong gói

| Nhóm | Số file | Nội dung |
|---|---:|---|
| Bối cảnh PNG | 13 | BG02, BG04, BG06, BG09, BG11, BG15, BG16, BG26, BG29, BG31, BG36, BG38, BG45 |
| Nhân vật PNG | 8 | Châu, Hạnh, Bảo, Tuấn, bà Ngô, Thu Hà, bé Châu, người áo mưa |
| Vật phẩm PNG | 13 | M01–M12 đủ 12 di vật và I02 mặt dây chuyền |
| UI SVG | 48 | 3 trạng thái nút, khung thoại, 3 trạng thái ô đồ, 12 icon, 28 nút thang máy (14 nút × 2 trạng thái), logo chữ |
| Trang giấy SVG | 4 | C05 danh sách mất tích, C08 thư Thu Hà, C18 ghi chú Tuấn, giấy Morse đi với M08 |
| Âm thanh WAV | 17 | 5 nốt, mô-típ 3–1–4–2–5, 7 tiếng tương tác/Morse, SOS, chuông thang máy, nhiễu radio, drone 12 giây |
| **Tổng asset** | **103** | Không tính manifest, trang duyệt, prompt và tài liệu |

`manifest.csv` và `manifest.json` liệt kê file thực tế, kích thước, nhóm và ghi chú. Số file không đồng nghĩa số concept độc lập: UI gồm nhiều trạng thái dùng chung. C05/C08/C18 là ba ID manh mối; trang thứ tư là giấy Morse M08, không phải manh mối C mới.

## Các quyết định đã dùng để tạo v01

- Cảnh tĩnh point-and-click, khung ngang; chất liệu vẽ tay tối, xanh rêu, gỗ cũ, ánh vàng. Các background hiện nghiêng về minh họa hiện thực có texture hơn là màu nước loang mạnh; đây là điểm có thể góp ý khi duyệt.
- F13-A dùng tìm chi tiết khác biệt; mới có nền chuẩn, chưa có ba vòng hoàn chỉnh.
- M01 nằm trong tủ; bàn F13-B để trống cho lớp nến.
- F13-D dùng 12 hốc di vật (hai cụm 2 × 3) và lối người đứng ở giữa; chữ khắc và đồ đặt là lớp riêng.
- Giữ đủ 12 di vật và ý định 5 kết thúc. F13-C dự kiến chuyển thành cutscene; phần này chưa được tạo trong gói.
- Không đổi các file thiết kế gốc trên ổ D. Những quyết định trên áp dụng cho bản asset để duyệt, chưa phải bản đồng bộ toàn bộ docs.

## Giới hạn đã biết — không bỏ qua trước khi tích hợp

1. **Nền trong suốt:** các PNG nhân vật/vật phẩm có alpha, nhưng một số vẫn còn quầng nền mờ. Các ID cần làm sạch đã được đánh dấu trong trang duyệt: NPC01, NPC02, NPC00B, SP03, I02, M01, M04, M05, M07, M08, M10, M11. Đã thử sửa bằng ImageGen với NPC01/NPC02/M01/I02 nhưng kết quả chưa tốt hơn; gói giữ bản đầu. Không đánh dấu những ảnh này là cutout sạch.
2. **Kích thước:** ảnh giữ độ phân giải gốc từ công cụ, được ghi trong manifest; chưa đồng loạt xuất background 1920×1080, portrait 768×1024 hay icon 128×128. Không có PSD tách layer tự động. SVG là nguồn chỉnh sửa được, chưa xuất PNG và chưa nhập engine.
3. **Vật phẩm:** mỗi di vật mới có một hình xem trước. Chưa có mặt sau, chữ khắc/nhãn cuối cùng, icon riêng hoặc các trạng thái mở/đóng. M02 cần kiểm tra/chỉnh mặt đồng hồ đúng 00:13 trước khi dùng như bằng chứng chính xác. I02 cần đồng bộ kích thước/hoa văn giữa ảnh item và dây chuyền trên nhân vật.
4. **Tương tác cảnh:** nền hiện còn bake cửa/tủ/két vào cảnh. Chưa có đầy đủ lớp cửa mở, ngăn kéo, đồ nhặt, mask che khuất, hotspot, hoặc cận cảnh puzzle. Đây là background plates để duyệt, không phải scene Unity hoàn chỉnh.
5. **Nội dung:** thư C08 và ghi chú C18/M08 là bản soạn mới để duyệt. C05 dùng 13 tên theo tài liệu. Chưa khóa toàn bộ ngày giờ và chữ trên 22 manh mối.
6. **Nhân vật:** một hình cho mỗi nhân vật/biến thể, chưa đủ 35 biểu cảm. Thu Hà là mẫu gương mặt; hiệu ứng hồn mờ cần thêm khi tích hợp. Chưa có animation Bóng Cháy/đi bộ hay đầy đủ nhân vật năm 2004.
7. **Âm thanh:** nguyên gốc tổng hợp bằng mã, PCM16 mono 44.1 kHz, đã kiểm tra không clipping số. Chưa được đánh giá nghe trong engine, chưa phải toàn bộ SFX/ambience, nhạc nền hoặc giọng diễn. Mô-típ dùng C5, D5, E5, G5, A5, thứ tự 3–1–4–2–5; Morse 1 đơn vị = 0,15 giây. Drone được tạo theo chu kỳ 12 giây để lặp.
8. **Font:** SVG dùng font hệ thống Arial/Georgia. Không kèm file font hay giấy phép phân phối font. Trước release phải chọn và đóng gói font được phép sử dụng.

## Còn phải sản xuất để đủ game theo tài liệu

- Các background còn lại, đặc biệt ngoại cảnh, kho lạnh, phòng 502/505/807/1104, hành lang hầm, cầu thang, F13-C và các cận cảnh.
- I01 và I03–I18; đạo cụ nhiệm vụ; ảnh ghép C12/I13–I15 và các bằng chứng hình ảnh.
- C01–C22 ngoài ba bản đã có; các đoạn băng và transcript C09–C11.
- Trạng thái và thành phần puzzle P01–P13; các vòng P09; nến và tủ P10; lớp P13.
- Biểu cảm nhân vật, animation, các NPC phụ và mẫu quá khứ cần cho cutscene.
- Storyboard/tranh của 5 kết thúc và F13-C; chưa có file trong `endings/`.
- VFX, các màn UI hoàn chỉnh, save/load, bảng manh mối, tóm tắt ca và thư viện ending.
- Nhạc đầy đủ, SFX hiện thực, ambience theo phòng và phương án giọng nói.
- Xuất đúng kích thước, làm sạch alpha, atlas, tối ưu và thử trên engine/điện thoại.

## Kiểm tra đã thực hiện

- Mở và xem trực tiếp các ảnh do ImageGen trả về; kiểm tra số hốc bàn thờ và thành phần chính.
- Đọc metadata file; xác nhận file tồn tại; phân tích SVG và thông số WAV; kiểm tra không clipping số.
- Chạy trang duyệt trong trình duyệt: 103 thẻ, lọc nhóm, phóng to, lưu góp ý sau tải lại, 17 audio controls, bố cục mobile không tràn ngang.
- Xem ảnh chụp trang duyệt, hai cảnh ghép thử và các trang giấy. Chưa có kiểm thử game vì chưa có dự án engine.

## Nguồn và khả năng chỉnh sửa

- 34 ảnh PNG tạo bằng **ImageGen tích hợp**, không dùng CLI/API fallback. Prompt và lịch sử thử sửa nằm trong `prompts.json`; bản thử sửa bị loại không tính vào 103 file.
- UI và trang giấy tạo từ SVG; âm thanh tạo bằng tổng hợp tín hiệu. Không dùng thư viện ảnh/âm thanh tải ngoài.
- Chỉnh sửa sau duyệt nên tạo v02, giữ bản v01 để so sánh.
