# 09 — Kế hoạch sản xuất và phát hành

## 1. Vai trò trong dự án (đối chiếu mục I của đề)

File gốc liệt kê các vai trò trong ngành. Bảng dưới ánh xạ vai trò đó vào nhóm làm game (giả định 5–6 người; một người có thể kiêm nhiều vai).

| Nhóm ngành (theo đề) | Vai trò | Trách nhiệm trong dự án | Gợi ý người đảm nhận |
|----------------------|---------|-------------------------|----------------------|
| Developer | **Production** (Producer / PM) | Lập kế hoạch, theo dõi tiến độ, họp, quản lý rủi ro | Thành viên A |
| Developer | **Design** (Game/Narrative/Level/Puzzle) | GDD, cốt truyện, câu đố, cân bằng | Thành viên B (+ A) |
| Developer | **Art & Animation** | Background, chân dung, UI, hiệu ứng | Thành viên C (+ D nếu có) |
| Developer | **Programming / Engineering** | Hệ thống lõi, puzzle, UI, build | Thành viên D, E |
| Developer | **Audio** | Nhạc, SFX, mix | Thành viên F hoặc dùng thư viện miễn phí |
| Developer | **QA** | Kiểm thử, ghi bug, xác minh kết thúc | Cả nhóm luân phiên, 1 người chính |
| Publisher | **Marketing & PR** | Trailer, ảnh chụp màn hình, fanpage, mô tả cửa hàng | Thành viên A + C |
| Publisher | **Business Development / Product Management** | Mô hình thu phí, giá, lộ trình cập nhật | A |
| Publisher | **Translator / Localization** | Bản tiếng Anh | B hoặc người ngoài |
| Platform holders | **Developer Relations / Certification** | Quy trình đăng ký Google Play, tuân thủ chính sách | D |
| Platform holders | **Store Curator** | Chuẩn bị tài liệu quảng bá để xin được feature | A |
| Middleware/Service | **Engine / Cloud / Anti-cheat / Support** | Dùng Unity, GitHub; hỗ trợ người chơi qua email/form | D |
| Press & Academia | **Reviewer / Creator / Lecturer / Market Researcher** | Gửi bản demo cho giảng viên, bạn bè, nhà sáng tạo nội dung; thu feedback | Cả nhóm |

> Nhóm điền tên thật vào cột cuối trước khi bắt đầu.

## 2. Mốc tiến độ (đề xuất 10 tuần — điều chỉnh theo lịch môn học)

| Tuần | Mốc | Sản phẩm bàn giao |
|------|-----|-------------------|
| 1 | **Pre-production** | Chốt ý tưởng, nền tảng, công cụ, phân vai; hoàn thiện GDD v1 |
| 2 | **Prototype (Vertical Slice 1)** | Di chuyển giữa 3 cảnh, Interactable, Inventory, hội thoại đơn giản |
| 3 | **Ca 1 chơi được** | L01–L05, L10; P01, P02; Quest, Clue board cơ bản |
| 4 | **Ca 2 + tầng 13 lần 1** | L06, L11, L15; P03, P04, P09; F13-A; Save/Load |
| 5 | **Ca 3** | L08, L13, P05–P07, P10; F13-B; Trust system đầy đủ |
| 6 | **Ca 4** | L12, L14, P08, P11; F13-C; hệ thống kết thúc |
| 7 | **Ca 5 + 5 kết thúc** | P12, P13; F13-D; EndingResolver; cutscene |
| 8 | **Alpha — Feature complete** | Toàn bộ nội dung có thể chơi từ đầu đến cuối |
| 9 | **Beta — Polish & QA** | Sửa bug, cân bằng Tỉnh táo/gợi ý, tối ưu hiệu năng, âm thanh |
| 10 | **Release Candidate + Báo cáo** | Build Android, video demo, tài liệu nộp, trình bày |

### Điều kiện hoàn thành (Definition of Done)
- Tính năng chạy được trên điện thoại thật, không crash trong 30 phút.
- Có dữ liệu trong file JSON chuẩn, không hard-code ID.
- Đã review code/PR bởi ít nhất 1 người.
- Có test case tương ứng trong tài liệu 10.

## 3. Phạm vi cắt giảm (nếu thiếu thời gian)

| Mức ưu tiên cắt | Nội dung có thể cắt |
|-----------------|---------------------|
| 1 | Lồng tiếng, tiếng Anh, thành tựu |
| 2 | Nhà hàng (L07), sân thượng chi tiết, EV bổ sung |
| 3 | Kéo nối manh mối (chuyển sang tự động xác nhận khi đủ manh mối) |
| 4 | F13-C chuyển thành đoạn cutscene thay vì puzzle P11 |
| 5 | Rút gọn còn 4 ca: gộp ca 3 và 4 (**không** cắt F13-D hay các kết thúc) |

**MVP tối thiểu:** 5 ca, ~18 cảnh, P01–P08 + P12 + P13, F13-A/B/D, 5 kết thúc.

## 4. Backlog theo epic

| Epic | Công việc chính | Phụ trách |
|------|-----------------|-----------|
| E-01 Core | GameState, EventBus, Save/Load, Time | Programmer |
| E-02 Khám phá | Scene loader, Interactable, khóa/mở, Elevator | Programmer + Level designer |
| E-03 Nhiệm vụ | Quest system, Shift log | Programmer + Designer |
| E-04 Vật phẩm/Manh mối | Inventory, Clue board, Truth | Programmer + UI |
| E-05 Hội thoại | Ink integration, Trust, Chất vấn | Programmer + Writer |
| E-06 Giải đố | PuzzleBase, P01–P13, Hint | Programmer + Designer |
| E-07 Tầng 13 | Sanity, 4 biến thể, sự kiện | Cả nhóm |
| E-08 Kết thúc | EndingResolver, cutscene, thống kê | Programmer + Artist |
| E-09 Nội dung | Viết thoại, ghi chú, tài liệu trong game | Writer |
| E-10 Nghệ thuật | Background, chân dung, UI, hiệu ứng | Artist |
| E-11 Âm thanh | Nhạc, SFX, mix | Audio |
| E-12 QA & Phát hành | Test, build, cửa hàng | QA + Producer |

## 5. Quy trình làm việc

- **Họp:** daily 15 phút (chat), weekly 45 phút (review demo).
- **Công cụ:** Git (nhánh `main`, `dev`, `feature/*`), Trello hoặc Notion để quản lý task, Discord/Zalo để liên lạc, Google Drive cho asset gốc.
- **Quy tắc nhánh:** không đẩy trực tiếp lên `main`; PR cần 1 review.
- **Naming:** theo ID trong tài liệu (P06, C09...).
- **Phân bổ ID dữ liệu:** thay đổi ID phải thông báo cả nhóm và cập nhật tài liệu.

## 6. Quản lý rủi ro

| Rủi ro | Xác suất | Ảnh hưởng | Giảm thiểu |
|--------|----------|-----------|-----------|
| Thiếu artist / chậm asset | Cao | Cao | Dùng placeholder sớm, phong cách đơn giản, tái dùng background |
| Phạm vi quá lớn | Cao | Cao | Ưu tiên MoSCoW, cắt theo mục 3 |
| Bug kẹt tiến trình (softlock) | Trung bình | Cao | Đường dự phòng (tài liệu 03, 05), QA softlock (tài liệu 10), debug panel |
| Lỗi build Android | Trung bình | Cao | Build thử mỗi tuần từ tuần 2 |
| Cốt truyện rời rạc, người chơi bối rối | Trung bình | Trung bình | Sổ ca + gợi ý, playtest với người ngoài nhóm |
| Mâu thuẫn dữ liệu (ID, điều kiện) | Trung bình | Trung bình | Data validator, tài liệu là nguồn chuẩn |
| Một thành viên rút / bận | Thấp | Cao | Tài liệu đầy đủ, có người dự phòng cho từng vai |
| Bản quyền nhạc/ảnh | Thấp | Cao | Chỉ dùng tài nguyên tự làm hoặc có giấy phép (CC0/CC-BY, ghi nguồn) |

## 7. Phát hành (Publisher / Platform)

| Hạng mục | Nội dung |
|----------|----------|
| Kênh | Google Play (nội bộ/closed testing → public), có thể itch.io cho bản Windows |
| Hồ sơ cửa hàng | Tên, mô tả ngắn/dài, 5–8 ảnh chụp màn hình, icon 512×512, feature graphic 1024×500, trailer 30–60 giây |
| Xếp hạng nội dung | Khai báo kinh dị, bạo lực nhẹ, nội dung gây sợ; đề xuất 16+ |
| Chính sách | Chính sách quyền riêng tư (dù không thu thập dữ liệu), khai báo Data safety |
| Mô hình | Miễn phí (demo 2 ca) + mở khóa đầy đủ, hoặc trả phí một lần; quyết định theo giảng viên |
| Marketing | Trailer teaser "nút 13", poster, bài đăng fanpage/TikTok, gửi bản demo cho reviewer/streamer |
| Hỗ trợ | Email/biểu mẫu báo lỗi, FAQ gợi ý, cập nhật bản vá |
| Phân phối | Chỉ phân phối số (không cần logistics vật lý) |
| Dữ liệu thị trường | Khảo sát 20–30 người chơi để rút kinh nghiệm cho phiên bản sau |

## 8. Chỉ số thành công (KPI) cho dự án môn học

- Hoàn thành 5 ca, 5 kết thúc, không có lỗi chặn tiến trình.
- ≥ 80% người thử hoàn thành ca 1 mà không cần giúp đỡ.
- ≥ 70% người thử đánh giá không khí "hấp dẫn / đáng sợ" từ 4/5.
- Điểm gợi ý: dưới 20% câu đố cần gợi ý cấp 3.
