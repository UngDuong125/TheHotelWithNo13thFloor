# 07 — Thiết kế kỹ thuật (Technical Design Document)

## 1. Lựa chọn công nghệ

| Thành phần | Lựa chọn | Lý do / Phương án thay thế |
|------------|----------|----------------------------|
| Engine | **Unity 2022.3 LTS**, 2D URP | Build Android ổn định, nhiều tài liệu. Thay thế: Godot 4 (nhẹ hơn, GDScript) |
| Ngôn ngữ | C# | |
| Hội thoại | **Ink** (inkle) + plugin Ink-Unity-Integration | Hỗ trợ biến, nhánh, tag; viết kịch bản bằng text, writer không cần code |
| Dữ liệu | ScriptableObject + JSON (Newtonsoft) | Designer chỉnh trong editor, build đọc JSON |
| Lưu game | JSON mã hóa nhẹ (Base64) tại `Application.persistentDataPath` | Đơn giản, đủ cho phạm vi môn học |
| Âm thanh | Unity Audio Mixer (nhạc / SFX / thoại) | Có thể cân bằng riêng |
| Input | Unity Input System (Touch + chuột) | Chạm / click như nhau |
| Localization | Unity Localization hoặc bảng CSV tự làm | Tách chuỗi từ đầu để thêm tiếng Anh |
| Version control | Git + Git LFS (ảnh, âm thanh), `.gitignore` chuẩn Unity | |
| Build | Android API 24+ (ARM64), IL2CPP; Windows x64 để test | |

## 2. Kiến trúc tổng thể

```
GameBootstrap
 └─ Managers (singleton / ServiceLocator, DontDestroyOnLoad)
     ├─ GameStateManager     (trạng thái: Menu, Playing, Dialogue, Puzzle, Cutscene, Paused)
     ├─ TimeSystem           (đồng hồ ca, sự kiện theo giờ)
     ├─ SaveSystem           (lưu/đọc GameData)
     ├─ InventorySystem      (vật phẩm, di vật)
     ├─ ClueSystem           (manh mối, nối, xác nhận sự thật)
     ├─ QuestSystem          (nhiệm vụ ca, bước, hoàn thành)
     ├─ DialogueSystem       (Ink runner, trust, chất vấn)
     ├─ FlagSystem           (cờ boolean/int)
     ├─ LocationSystem       (cảnh, khóa/mở, chuyển cảnh)
     ├─ ElevatorSystem       (bảng nút, điều kiện 13)
     ├─ SanitySystem         (chỉ trong tầng 13)
     ├─ EventSystem          (sự kiện bất thường EV##)
     ├─ PuzzleManager        (đăng ký, trạng thái, gợi ý)
     ├─ EndingResolver       (tính E1–E5)
     ├─ AudioManager
     └─ UIManager            (HUD, túi đồ, bảng manh mối, hội thoại, menu)
```

- **Giao tiếp:** event bus đơn giản (`EventBus.Publish<ItemAcquired>(...)`) để các hệ thống không phụ thuộc trực tiếp.
- **Một cảnh Unity cho mỗi khu vực** (additive load cho UI). Dữ liệu cảnh nằm trong `LocationData` (ScriptableObject).
- **Hotspot:** component `Interactable` chung với danh sách `Condition` (cờ, vật phẩm, ca, giờ) và `Action` (nhặt, đọc, mở puzzle, bắt đầu thoại, chuyển cảnh).

## 3. Schema dữ liệu

### 3.1 Item (`items.json`)
```json
{
  "id": "I04",
  "name": { "vi": "Chìa khóa kho đồ", "en": "Storage room key" },
  "type": "key",
  "icon": "icons/key_storage",
  "description": { "vi": "Chìa gỉ, khắc chữ K3." },
  "unlocks": ["door_L08"],
  "stackable": false
}
```

### 3.2 Clue (`clues.json`)
```json
{
  "id": "C03",
  "title": { "vi": "Bài báo: Cháy nhỏ tại Khách sạn Liên Hoa" },
  "supports": ["T2"],
  "linkableWith": ["C01", "C17", "C05"]
}
```

### 3.3 Truth (`truths.json`)
```json
{
  "id": "T2",
  "requires": { "min": 2, "pool": ["C01", "C03", "C17"], "mustInclude": [] }
}
```

### 3.4 Interactable
```json
{
  "id": "L02_keyboard",
  "scene": "L02",
  "visibleIf": ["night>=1"],
  "actions": [
    { "type": "startPuzzle", "puzzle": "P01" }
  ],
  "once": false
}
```

### 3.5 Quest
```json
{
  "id": "Q2-2",
  "night": 2,
  "required": true,
  "title": { "vi": "Kiểm tra tiếng động ở kho lạnh" },
  "steps": [
    { "id": "s1", "text": "Nói chuyện với Tuấn", "completeWhen": "flag:met_tuan_n2" },
    { "id": "s2", "text": "Vào kho lạnh", "completeWhen": "scene:L06" },
    { "id": "s3", "text": "Giải P04", "completeWhen": "puzzle:P04" }
  ]
}
```

### 3.6 Save (`GameData`)
```json
{
  "version": 1,
  "progress": { "night": 3, "shiftMinutes": 140, "enteredThisNight": false, "location": "L02", "enteredF13": 2 },
  "flags": { "met_tuan": true, "bribed": false },
  "trust": { "NPC01": 3, "NPC02": 5, "NPC03": 4, "NPC04": 2 },
  "inventory": ["I01", "I02", "I03", "I04", "I05"],
  "keepsakes": ["M04", "M07"],
  "clues": { "C01": "found", "C02": "linked" },
  "truths": ["T1"],
  "puzzles": { "P01": "done", "P03": "done", "P08": "locked" },
  "choices": { "CH01": "promise", "CH02": "secret", "CH03": "press" },
  "endingsUnlocked": ["E3"],
  "playTimeSec": 5230
}
```
- **Autosave:** khi kết thúc ca, khi hoàn thành puzzle, khi vào/ra tầng 13.
- **3 slot** + 1 autosave. Phiên bản `version` để migrate khi cập nhật.

## 4. Thuật toán chính

### 4.1 Nút 13 trên thang máy
Đồng hồ ca lưu bằng `shiftMinutes` (0–480, 0 = 22:00, 480 = 06:00), nên cửa sổ 00:13–01:13 tương ứng `shiftMinutes` 133–193. Ca 1 chỉ nhấp nháy, không ấn được.

```csharp
const int WindowStart = 133; // 00:13
const int WindowEnd   = 193; // 01:13
bool Is13Available(GameData d) =>
    d.progress.night >= 2 && !d.progress.enteredThisNight &&
    ((d.progress.shiftMinutes >= WindowStart && d.progress.shiftMinutes <= WindowEnd)
     || d.inventory.Contains("M02"));
```

### 4.2 Xác nhận sự thật
```csharp
bool TryConfirmTruth(Truth t, ClueState clues) {
    var found = t.pool.Where(c => clues.IsFound(c)).ToList();
    bool enough = found.Count >= t.min;
    bool must = t.mustInclude.All(clues.IsFound) || t.mustInclude.Count == 0;
    bool linked = clues.HasLinkAmong(found);
    return enough && must && linked;
}
```
Quy tắc đặc biệt T3 (cần ít nhất 1 trong C09/C10/C15/C16), T5 (cần C12+C13 hoặc C20) được cấu hình bằng `mustInclude` hoặc `anyOf`.

### 4.3 Ending Resolver
```csharp
Ending Resolve(GameData d) {
    int truths = d.truths.Count;
    bool ledger = d.keepsakes.Contains("M03");
    bool tape = d.puzzles["P08"] == "done";
    int altar = d.altarScore;
    bool ngo = d.flags["ngoHelped"];
    bool bribed = d.flags["bribed"];
    bool give = d.flags["giveEvidence"];
    var ch08 = d.choices["CH08"]; // enter/refuse/name

    if (ch08 == "enter" || d.flags["sanityZeroD"]) return E1;
    if (give || (bribed && truths < 3) || truths < 2) return E2;
    if (truths == 5 && altar == 12 && ch08 == "name"
        && d.trust["NPC02"] >= 7 && ngo) return E5;
    if (truths >= 4 && ledger && tape && altar >= 10 && ngo) return E4;
    return E3;
}
```

### 4.4 Sanity
- `Sanity` chỉ cập nhật khi `Location == L16`. Tick mỗi 1 giây thực.
- Tốc độ cơ bản: −1/10 giây; ×1.5 ở F13-D; ×0.7 nếu có I03 và đang ở vùng tối; −10 đến −20 khi sự kiện.
- Hồi: nhạc hộp (cooldown 20s), điểm an toàn.

### 4.5 Gợi ý (Hint)
```
hintLevel = min(failCount / 2, 3)
Nếu người chơi bấm "Gợi ý": hiển thị G[hintLevel] và tăng hintLevel nếu bấm lại sau 30 giây
```

## 5. Cấu trúc thư mục dự án (Unity)

```
Assets/
  _Project/
    Art/ (Sprites, Backgrounds, UI, FX)
    Audio/ (Music, SFX, Voice)
    Data/ (items.json, clues.json, truths.json, quests/, locations/, ink/)
    Scenes/ (Boot, MainMenu, L01..L16, Elevator, F13_A..D)
    Scripts/
      Core/ (EventBus, ServiceLocator, GameData)
      Systems/ (Time, Save, Inventory, Clue, Quest, Dialogue, Sanity, Ending)
      Gameplay/ (Interactable, Hotspot, PuzzleBase, P01..P13)
      UI/ (HUD, Inventory, ClueBoard, Dialogue, Menus)
      Editor/ (công cụ kiểm tra dữ liệu)
    Prefabs/
    Localization/
  Tests/
```

## 6. Lớp Puzzle chung

```csharp
public abstract class PuzzleBase : MonoBehaviour {
    public string Id;
    protected int FailCount;
    public event Action<PuzzleResult> Completed;

    public abstract void Begin(PuzzleContext ctx);
    public abstract void Reset();
    protected void Fail() { FailCount++; HintService.Update(Id, FailCount); }
    protected void Succeed() { Completed?.Invoke(PuzzleResult.Success); }
}
```
Mỗi puzzle P01–P13 kế thừa lớp này; dữ liệu lời giải đặt trong ScriptableObject để dễ chỉnh và test.

## 7. Hiệu năng và thiết bị

| Hạng mục | Mục tiêu |
|----------|---------|
| FPS | 60 trên thiết bị tầm trung, tối thiểu 30 |
| RAM | < 1,5 GB |
| Dung lượng APK/AAB | < 400 MB (đề xuất < 250 MB) |
| Thời gian tải cảnh | < 2 giây |
| Pin | 1 giờ chơi tiêu hao < 20% (ước tính) |
| Độ phân giải | Tham chiếu 1920×1080, hỗ trợ tỉ lệ 16:9 → 20:9, có safe area |

Kỹ thuật: Sprite Atlas, nén ASTC, gom hotspot, không dùng hậu xử lý nặng (chỉ dùng shader nhiễu/vignette nhẹ).

## 8. Công cụ nội bộ và pipeline

- **Data validator (Editor):** kiểm tra ID trùng, tham chiếu thiếu (manh mối, vật phẩm, cảnh).
- **Debug panel:** nhảy tới ca/khu vực, thêm vật phẩm/manh mối, đặt cờ, chỉnh đồng hồ, in ra điều kiện kết thúc (phục vụ QA).
- **CI (tùy chọn):** GitHub Actions + GameCI build Android.
- **Quy ước:** PascalCase cho class, camelCase cho biến, ID dữ liệu giống trong tài liệu (P01, C09...).

## 9. Bảo mật và phát hành

- Không có mạng/online nên không cần backend.
- Android: ký APK/AAB bằng keystore của nhóm (giữ bí mật). Quyền: không cần quyền nhạy cảm.
- Quyền riêng tư: không thu thập dữ liệu cá nhân; nếu dùng analytics phải có chính sách riêng tư.
