# Khách sạn không có tầng 13 — Bộ tài liệu dự án

Nguồn: `23120061.pdf` (MSSV 23120061 – Nguyễn Thị Ánh Ngọc, môn Phát triển game CQ2023/3).
Bộ tài liệu này mở rộng phần "ý tưởng ban đầu" thành tài liệu đủ để cả nhóm bắt tay vào làm game.

## Danh mục tài liệu

| # | File | Nội dung | Người dùng chính |
|---|------|----------|------------------|
| 01 | [01_GDD.md](01_GDD.md) | Game Design Document: tầm nhìn, vòng lặp, 7 cơ chế chi tiết, hệ thống, UI | Cả nhóm |
| 02 | [02_Cot_Truyen_Nhan_Vat.md](02_Cot_Truyen_Nhan_Vat.md) | Cốt truyện đầy đủ, dòng thời gian, nhân vật, 5 ca trực | Writer, Designer |
| 03 | [03_Ban_Do_Khu_Vuc.md](03_Ban_Do_Khu_Vuc.md) | Bản đồ, điều kiện mở khóa khu vực, 4 biến thể tầng 13, sự kiện bất thường | Level designer, Artist |
| 04 | [04_Giai_Do.md](04_Giai_Do.md) | 13 câu đố: vị trí, lời giải, gợi ý 3 cấp | Designer, Programmer |
| 05 | [05_Vat_Pham_Manh_Moi.md](05_Vat_Pham_Manh_Moi.md) | Danh sách vật phẩm, 12 di vật, 22 manh mối, 5 sự thật | Designer, Programmer |
| 06 | [06_Hoi_Thoai_Lua_Chon_Ket_Thuc.md](06_Hoi_Thoai_Lua_Chon_Ket_Thuc.md) | Hệ thống tin tưởng/nói dối, lựa chọn, điều kiện 5 kết thúc, đường đi mẫu | Writer, Programmer |
| 07 | [07_Thiet_Ke_Ky_Thuat.md](07_Thiet_Ke_Ky_Thuat.md) | Công nghệ, kiến trúc, schema dữ liệu, lưu game, thuật toán chọn kết thúc | Programmer |
| 08 | [08_Art_Audio_UI.md](08_Art_Audio_UI.md) | Phong cách hình ảnh, bảng màu, danh sách asset, âm thanh, UI | Artist, Audio |
| 09 | [09_Ke_Hoach_San_Xuat.md](09_Ke_Hoach_San_Xuat.md) | Vai trò (theo mục I của đề), mốc tiến độ, backlog, rủi ro, phát hành | Producer |
| 10 | [10_Kiem_Thu_QA.md](10_Kiem_Thu_QA.md) | Kế hoạch kiểm thử, test case, kiểm tra softlock và các đường kết thúc | QA |
| 11 | [11_Danh_Sach_Asset.md](11_Danh_Sach_Asset.md) | Danh sách và mô tả toàn bộ asset (hình, UI, VFX, nhạc, SFX, font, phát hành) | Artist, Audio, Programmer |

## Các giả định (file gốc chưa nêu — nhóm hãy xác nhận hoặc sửa)

| Hạng mục | Giả định trong tài liệu | Lý do |
|----------|-------------------------|-------|
| Nền tảng | Android là chính, có bản build Windows để test | Môn học nằm trong chuỗi môn Mobile |
| Thể loại điều khiển | 2D point-and-click / adventure theo từng phòng, chạm để tương tác | Nhóm sinh viên, ít asset, phù hợp giải đố + trinh thám |
| Engine | Unity 2022.3 LTS (C#) + Ink cho hội thoại (phương án thay thế: Godot 4) | Phổ biến, build Android ổn định |
| Độ dài | 5 ca trực, khoảng 2–2,5 giờ cho một lượt chơi | Đủ cho 5 kết thúc, vừa phạm vi môn học |
| Ngôn ngữ | Tiếng Việt chính, có chuẩn bị bảng chuỗi để thêm tiếng Anh | Dễ localize sau |
| Bối cảnh | Việt Nam, tháng 9/2024, sự cố xảy ra đêm 13/09/2004 | Đủ cách 20 năm để có "vụ mất tích trong quá khứ" |
| Số thành viên | 5–6 người | Xem bảng vai trò ở tài liệu 09 |

Các tên nhân vật, tên khách sạn, địa danh và sự kiện trong cốt truyện là **đề xuất của tài liệu này** để hoàn thiện ý tưởng. Bạn có thể đổi tên mà không ảnh hưởng cấu trúc, vì mọi thứ được tham chiếu bằng ID.

## Quy ước ID dùng xuyên suốt

| Tiền tố | Ý nghĩa | Ví dụ |
|---------|---------|-------|
| `NPC` | Nhân vật | NPC02 = Ông Bảo |
| `L` | Khu vực | L13 = Văn phòng quản lý |
| `I` | Vật phẩm thường | I05 = Chìa vạn năng |
| `M` | Di vật của 12 nạn nhân | M01 = Nhạc hộp |
| `C` | Manh mối | C09 = Băng ghi âm đoạn 1 |
| `T` | Sự thật cốt lõi (T1–T5) | T5 = Châu là đứa trẻ mất tích |
| `P` | Câu đố | P06 = Két sắt |
| `Q` | Nhiệm vụ ca đêm | Q3-2 = nhiệm vụ 2 của ca 3 |
| `CH` | Lựa chọn quan trọng | CH04 |
| `E` | Kết thúc | E5 = Kết thúc bí mật |
| `F` | Biến thể tầng 13 | F13-A |
