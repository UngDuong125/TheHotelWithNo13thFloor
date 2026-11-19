# Khách sạn không có tầng 13

**The Hotel With No 13th Floor** là game giải đố, kinh dị tâm lý, trinh thám cho một người chơi. Đây là đồ án môn CSC13009 Game Development của nhóm BB (Group ID 3).

Người chơi vào vai Minh Châu, lễ tân ca đêm của một khách sạn cổ chỉ có 12 tầng. Thỉnh thoảng nút "13" sáng lên trong thang máy. Mỗi người trong khách sạn kể một phiên bản khác nhau về tầng đó, và vụ "13 người mất tích" trong đêm cháy 20 năm trước dần chỉ về chính Châu.

| Mục | Nội dung |
|---|---|
| Thể loại | Adventure 2D point-and-click theo từng phòng |
| Nền tảng | Android (chính), Windows (chơi thử trong nhóm) |
| Công cụ dự kiến | Unity 2022.3 LTS (C#), ink cho hội thoại |
| Thời lượng | 5 ca trực, khoảng 2 đến 2,5 giờ cho một lượt chơi |
| Đối tượng | 16+ (kinh dị tâm lý, hỏa hoạn; không máu me) |

## Trạng thái hiện tại

Dự án đang ở giai đoạn tiền sản xuất:

- Đã có bộ tài liệu thiết kế đầy đủ trong `docs/`.
- Đã có bộ asset duyệt v01 trong `asset_v01/`, chỉ dùng để duyệt phong cách, chưa tích hợp vào engine.
- Chưa có project Unity.

## Cấu trúc thư mục

```
.
├── docs/                    Tài liệu thiết kế (GDD, cốt truyện, giải đố, kỹ thuật, kế hoạch...)
├── asset_v01/               Bộ asset duyệt v01 và báo cáo rà soát trước khi tạo asset
│   └── Hotel_Assets_v01/    Ảnh, UI, âm thanh, manifest và trang duyệt index.html
├── 23120061.pdf             Ý tưởng ban đầu của dự án
├── CONTRIBUTING.md          Quy định commit và làm việc với Git
└── README.md
```

## Tài liệu thiết kế

Bắt đầu đọc từ [docs/00_README.md](docs/00_README.md). File này liệt kê toàn bộ tài liệu, các giả định và quy ước ID dùng xuyên suốt dự án (NPC, L, I, M, C, T, P, Q, CH, E, F).

| File | Nội dung |
|---|---|
| [01_GDD.md](docs/01_GDD.md) | Game Design Document: vòng lặp, 7 cơ chế, hệ thống, UI |
| [02_Cot_Truyen_Nhan_Vat.md](docs/02_Cot_Truyen_Nhan_Vat.md) | Cốt truyện, dòng thời gian, nhân vật, 5 ca trực |
| [03_Ban_Do_Khu_Vuc.md](docs/03_Ban_Do_Khu_Vuc.md) | Bản đồ, điều kiện mở khu vực, 4 biến thể tầng 13 |
| [04_Giai_Do.md](docs/04_Giai_Do.md) | 13 câu đố, lời giải, gợi ý 3 cấp |
| [05_Vat_Pham_Manh_Moi.md](docs/05_Vat_Pham_Manh_Moi.md) | Vật phẩm, 12 di vật, 22 manh mối, 5 sự thật |
| [06_Hoi_Thoai_Lua_Chon_Ket_Thuc.md](docs/06_Hoi_Thoai_Lua_Chon_Ket_Thuc.md) | Tin tưởng, nói dối, lựa chọn, 5 kết thúc |
| [07_Thiet_Ke_Ky_Thuat.md](docs/07_Thiet_Ke_Ky_Thuat.md) | Kiến trúc, schema dữ liệu, lưu game |
| [08_Art_Audio_UI.md](docs/08_Art_Audio_UI.md) | Phong cách hình ảnh, âm thanh, UI |
| [09_Ke_Hoach_San_Xuat.md](docs/09_Ke_Hoach_San_Xuat.md) | Vai trò, mốc tiến độ, backlog, rủi ro |
| [10_Kiem_Thu_QA.md](docs/10_Kiem_Thu_QA.md) | Kế hoạch kiểm thử, test case |
| [11_Danh_Sach_Asset.md](docs/11_Danh_Sach_Asset.md) | Danh sách và mô tả toàn bộ asset |

## Đóng góp

Đọc [CONTRIBUTING.md](CONTRIBUTING.md) trước khi commit. Tóm tắt: commit theo chuẩn Conventional Commits, mô tả bằng tiếng Việt, ví dụ `feat(assets): thêm bộ asset duyệt v01`.

## Thành viên

| MSSV | Họ và tên |
|---|---|
| 23120034 | Ứng Thị Thùy Dương |
| 23120061 | Nguyễn Thị Ánh Ngọc |
