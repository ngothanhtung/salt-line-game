# Saltline

> 🇬🇧 English · 🇻🇳 Tiếng Việt: each section gives English first, then Vietnamese. / Mỗi phần có tiếng Anh trước, tiếng Việt sau.

**EN:** **Saltline** is a first-person 3D shooter that runs in the browser. The whole game is in one file, [index.html](index.html): HTML, CSS, JavaScript, shaders and a 3D engine.

You play the *Breacher*, sent into a rainy, wet port at night. The *Harbormaster* is a machine that has taken over the berth. Your job is to cut its three uplink relays (in the **yard**, the **shed** and the **quay**) while fighting off its machines: **Gulls** fly and **Hounds** walk. When all three relays are dark, run to the boat waiting at the ladder at the south end of the quay.

**VI:** **Saltline** là game bắn súng góc nhìn thứ nhất (FPS) 3D chạy ngay trên trình duyệt. Toàn bộ game nằm trong một file duy nhất, [index.html](index.html): HTML, CSS, JavaScript, shader và engine 3D.

Bạn vào vai *Breacher*, đột nhập một bến cảng ẩm ướt trong đêm mưa. *Harbormaster* là một cỗ máy đã chiếm quyền kiểm soát bến. Nhiệm vụ của bạn là cắt ba trạm relay của nó (ở **bãi container**, **nhà kho** và **cầu cảng**), đồng thời chống lại lũ máy của nó: **Gull** bay trên không, **Hound** đi dưới đất. Khi cả ba relay đã tắt, hãy chạy tới chiếc thuyền đang chờ ở thang cầu cảng, đầu phía nam.

---

## Running it / Cách chạy

**EN:** No install or build step is needed.

- **Quickest:** open `index.html` in a recent Chrome, Edge, Firefox or Safari.
- **With a local server** (recommended while editing): use the VS Code *Live Server* extension, or run the command below, then open `http://localhost:<port>/`.

**VI:** Không cần cài đặt hay build gì cả.

- **Nhanh nhất:** mở `index.html` bằng Chrome, Edge, Firefox hoặc Safari bản mới.
- **Dùng server cục bộ** (nên dùng khi đang sửa code): dùng extension *Live Server* của VS Code, hoặc chạy lệnh dưới đây rồi mở `http://localhost:<port>/`.

```bash
npx serve .        # or / hoặc: python3 -m http.server
```

> **EN:** Keep the `</body>` tag at the end of the file. Without it, Live Server inserts its reload script before the first `</svg>` it finds, which sits inside the JavaScript code, and the page fails with `SyntaxError: Invalid or unexpected token`.
>
> **VI:** Hãy giữ thẻ `</body>` ở cuối file. Nếu thiếu thẻ này, Live Server sẽ chèn script reload vào trước thẻ `</svg>` đầu tiên nó tìm thấy, mà thẻ đó lại nằm trong code JavaScript, khiến trang bị lỗi `SyntaxError: Invalid or unexpected token`.

**EN:** You need a browser and GPU with **WebGL** support. An internet connection is only used to load the Google Fonts; the game still runs without it.

**VI:** Cần trình duyệt và GPU hỗ trợ **WebGL**. Mạng chỉ dùng để tải font từ Google Fonts; không có mạng thì game vẫn chạy.

---

## Controls / Điều khiển

| Action / Hành động | Keyboard & mouse / Bàn phím & chuột | Touch / Cảm ứng |
|---|---|---|
| Move / Di chuyển | `W` `A` `S` `D` | Left thumb, anywhere / Ngón cái trái, chạm ở đâu cũng được |
| Look / Nhìn | Mouse / Chuột | Drag on the right side / Kéo ở nửa phải màn hình |
| Fire / Bắn | Left mouse button / Chuột trái | Hold **FIRE**, drag to track / Giữ **FIRE**, kéo để bám mục tiêu |
| Aim / Ngắm | Right mouse button / Chuột phải | **AIM** toggles / Bấm **AIM** để bật/tắt |
| Reload / Nạp đạn | `R` | **RLD** |
| Cut relay / Cắt relay | Hold `E` / Giữ `E` | Hold **USE** at a relay / Giữ **USE** khi đứng ở relay |
| Jump / Nhảy | `Space` | **JUMP** |
| Sprint / Chạy nhanh | `Shift` | Push the stick fully forward / Đẩy cần hết cỡ về phía trước |
| Crouch / Ngồi | `C` or / hoặc `Ctrl` | — |
| Melee / Cận chiến | `F` | — |
| Pause / Tạm dừng | `Esc` or / hoặc `P` | — |

**EN:** Gamepads are supported too. The full bindings are listed on the Controls screen in the game.

**VI:** Game cũng hỗ trợ tay cầm (gamepad). Danh sách phím đầy đủ có trong màn hình Controls của game.

---

## Settings / Cài đặt

**EN:** The settings panel has: graphics quality, mouse sensitivity, invert Y, master volume, field of view and display options. Settings are saved in `localStorage`.

**VI:** Bảng cài đặt gồm: chất lượng đồ họa, độ nhạy chuột, đảo trục Y, âm lượng tổng, góc nhìn (FOV) và tùy chọn hiển thị. Cài đặt được lưu trong `localStorage`.

---

## Technology / Công nghệ

| Area / Hạng mục | Technology / Công nghệ |
|---|---|
| 3D rendering / Dựng hình 3D | **Three.js r180**, bundled and minified inside the file, no CDN / nhúng và minify sẵn trong file, không tải từ CDN. Runs on / Chạy trên **WebGL / WebGL2** |
| Shaders | Custom GLSL via / GLSL tự viết qua `ShaderMaterial`: clouds and sky / mây và bầu trời; PCSS-style soft shadows with penumbra / bóng đổ mềm có penumbra; wet ground with puddles, cracks, worn road markings and wetness-based roughness / mặt đường ướt với vũng nước, vết nứt, vạch sơn bị mòn và độ nhám thay đổi theo độ ướt; paint damage model / mô hình sơn bị hư hại |
| Post-processing / Hậu kỳ | Bloom, **AgX** tone mapping (Filament/Blender fit), colour grading / chỉnh màu, fog / sương mù |
| Performance / Hiệu năng | `InstancedMesh` for repeated objects / cho các vật thể lặp lại; adjustable quality presets / mức chất lượng tùy chỉnh được |
| Audio / Âm thanh | **Web Audio API** (`AudioContext`, `ConvolverNode` for reverb / tạo vang, `BiquadFilterNode`). Sound is generated in code / Âm thanh được tạo bằng code, no audio files / không có file âm thanh |
| Input / Điều khiển | Pointer Lock API (mouse / chuột), Touch events (on-screen controls / nút trên màn hình), Gamepad API |
| UI / Giao diện | Plain HTML + CSS with custom properties / HTML + CSS thuần, dùng CSS custom properties. Fonts: *Big Shoulders Display*, *IBM Plex Mono*, *Barlow Condensed* (Google Fonts) |
| Accessibility / Trợ năng | Respects `prefers-reduced-motion` / tôn trọng `prefers-reduced-motion`; layout adapts to phones in portrait / bố cục tự thích ứng với điện thoại dọc |
| Storage / Lưu trữ | `localStorage` for settings / cho cài đặt |

**EN:** **No external assets:** all geometry, textures, effects and sound are generated procedurally in code. The file is about 1.4 MB.

**VI:** **Không có asset bên ngoài:** mọi hình khối, texture, hiệu ứng và âm thanh đều được sinh bằng code. File nặng khoảng 1,4 MB.

---

## File layout / Cấu trúc file

**EN:** `index.html` is organized as follows:

1. `<head>`: meta tags, Google Fonts, and the `<style>` block for the UI (boot screen, HUD, radio, touch controls, menus, settings panel, narrow screens, motion preferences).
2. HTML skeleton: boot screen, title screen, pause / death / debrief cards, settings and controls panel.
3. `<script>`: the bundled Three.js engine, followed by the game code (level, enemies, weapons, mission logic, audio, input, shaders).

Most of the JavaScript is minified bundle output. When you need to change behaviour, it is easier to edit the readable parts (CSS, HTML, GLSL comments and strings).

**VI:** `index.html` được chia như sau:

1. `<head>`: thẻ meta, Google Fonts và khối `<style>` cho giao diện (màn hình khởi động, HUD, radio, nút cảm ứng, menu, bảng cài đặt, màn hình hẹp, tùy chọn chuyển động).
2. Khung HTML: màn hình khởi động, màn hình tiêu đề, các thẻ tạm dừng / thua / tổng kết, bảng cài đặt và điều khiển.
3. `<script>`: engine Three.js đã bundle, tiếp theo là code game (màn chơi, kẻ địch, vũ khí, logic nhiệm vụ, âm thanh, điều khiển, shader).

Phần lớn JavaScript là code bundle đã minify. Khi cần thay đổi hành vi, sửa các phần dễ đọc (CSS, HTML, chú thích GLSL và chuỗi văn bản) sẽ dễ hơn.
