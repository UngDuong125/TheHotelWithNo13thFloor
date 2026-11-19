# Quy định làm việc với Git

## 1. Định dạng commit message

Repo dùng chuẩn [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), phần mô tả viết bằng tiếng Việt.

```
<type>(<scope>): <mô tả ngắn>

<thân: giải thích vì sao thay đổi, không bắt buộc>

<chân: tham chiếu issue hoặc BREAKING CHANGE, không bắt buộc>
```

### Dòng tiêu đề

- Tối đa khoảng 72 ký tự.
- Mô tả bắt đầu bằng động từ, viết thường chữ đầu, không có dấu chấm cuối câu. Ví dụ: `thêm`, `sửa`, `bỏ`, `cập nhật`, `đổi tên`.
- Mỗi commit chỉ làm một việc. Nếu tiêu đề cần chữ "và" cho hai việc không liên quan, hãy tách thành hai commit.
- `(scope)` không bắt buộc, nhưng nên có.

### Thân commit

- Cách dòng tiêu đề một dòng trống.
- Ngắt dòng khoảng 72 ký tự.
- Giải thích **vì sao** thay đổi. Phần thay đổi **cái gì** đã có trong diff.
- Có thể liệt kê bằng gạch đầu dòng `- `.

### Type

| Type | Dùng khi |
|---|---|
| `feat` | Thêm tính năng gameplay, hệ thống mới, hoặc nội dung mới (asset, cảnh, câu đố) |
| `fix` | Sửa lỗi |
| `docs` | Thêm hoặc sửa tài liệu (`docs/`, README, proposal) |
| `refactor` | Sửa cấu trúc code, không đổi hành vi |
| `perf` | Tối ưu hiệu năng |
| `test` | Thêm hoặc sửa test, test case QA |
| `build` | Cấu hình build Android/Windows, package, Unity settings |
| `ci` | Cấu hình CI (GitHub Actions...) |
| `chore` | Việc vặt không thuộc các loại trên (cấu hình Git, `.gitignore`, dọn file) |
| `revert` | Hoàn tác một commit trước |

### Scope gợi ý

| Scope | Phạm vi |
|---|---|
| `docs` | Tài liệu thiết kế trong `docs/` |
| `proposal` | Proposal nộp môn học |
| `assets` | Asset hình ảnh, UI, âm thanh |
| `story` | Cốt truyện, nhân vật, hội thoại (ink) |
| `puzzle` | Câu đố P01 đến P13 |
| `f13` | Tầng 13 và thanh Tỉnh táo |
| `ui` | Giao diện, HUD, menu |
| `audio` | Nhạc, SFX, mix |
| `save` | Lưu và tải game |
| `git` | Cấu hình Git, Git LFS |

Có thể thêm scope mới khi cần, miễn là ngắn và nhất quán.

### Ví dụ

```
feat(assets): thêm bộ asset duyệt v01
```

```
chore(git): cấu hình Git LFS và bỏ qua file nén

Theo dõi PNG, WAV, PSD bằng Git LFS để lịch sử repo không phình to
khi asset được chỉnh sửa qua nhiều phiên bản.
```

```
fix(puzzle): sửa P06 nhận sai mật mã khi nhập số 0 đầu
```

```
docs(proposal): thêm sơ đồ vòng lặp chơi và tiến trình 5 ca
```

## 2. Nhánh

Theo kế hoạch trong [docs/09_Ke_Hoach_San_Xuat.md](docs/09_Ke_Hoach_San_Xuat.md):

- `main`: Bản ổn định. Không push thẳng lên `main`.
- `dev`: Nhánh tích hợp.
- `feature/<mô-tả-ngắn>`: Mỗi tính năng một nhánh, tách từ `dev`. Ví dụ `feature/elevator-system`, `fix/p06-safe-code`, `docs/proposal`.
- Gộp vào `dev` hoặc `main` qua Pull Request, cần ít nhất 1 người review.

## 3. File lớn và Git LFS

- `*.png`, `*.wav`, `*.psd` được Git LFS theo dõi (xem `.gitattributes`). Cài `git lfs install` trước khi clone.
- Khi thêm loại file nhị phân lớn mới (ví dụ `*.ogg`, `*.mp4`), thêm vào Git LFS **trước** khi commit file đó: `git lfs track "*.ogg"`.
- Không commit file `*.zip` trùng nội dung với thư mục asset; chia sẻ qua Release hoặc Drive.
- Không commit file tạm của Office (`~$*.docx`).

## 4. Đặt tên

- Đặt tên file, asset, nhánh theo ID trong tài liệu (P06, C09, BG02...). Xem quy ước ID ở [docs/00_README.md](docs/00_README.md).
- Đổi ID phải báo cả nhóm và cập nhật tài liệu liên quan trong cùng commit.
