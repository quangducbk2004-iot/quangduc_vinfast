# Thư Hồng 20.10

Trang chúc mừng Ngày Phụ nữ Việt Nam 20/10. Người xem nhập tên, mở hộp quà 3D, ngắm một đóa hồng pha lê (kéo để xoay, chạm để hoa tỏa sáng), rồi đọc một lá thư tay được chọn ngẫu nhiên, có nhạc nền.

Xem trang đang chạy: https://nguyenthevietk76-hub.github.io/Th--H-ng/

Toàn bộ trang nằm trong **một file `index.html`**, không cần cài đặt hay build gì. Sửa file, mở lại trình duyệt là thấy thay đổi.

## Lấy code về

Chọn một trong ba cách:

- **Fork (nên dùng nếu có tài khoản GitHub):** bấm **Fork** ở góc trên bên phải trang kho. Bạn sẽ có một bản riêng để sửa và tự đăng trang của mình.
- **Tải về:** bấm **Code → Download ZIP**, giải nén ra là dùng được.
- **Clone:**

  ```bash
  git clone https://github.com/nguyenthevietk76-hub/Th--H-ng.git
  ```

## Chạy thử trên máy

Mở terminal trong thư mục code rồi chạy:

```bash
python -m http.server 8765
```

Sau đó mở `http://localhost:8765`. Nên chạy qua máy chủ như trên thay vì bấm đúp `index.html`, để file nhạc tải đúng.

## Các file

| File | Nội dung |
| --- | --- |
| `index.html` | Toàn bộ giao diện, hiệu ứng, cảnh 3D và nội dung thư |
| `nhac.mp3` | Nhạc nền |
| `README.md` | Hướng dẫn này |

## Tùy chỉnh: muốn đổi gì thì sửa ở đâu

Mở `index.html` bằng trình soạn thảo bất kỳ (khuyên dùng VS Code), dùng **Ctrl+F** tìm đoạn chữ ở cột giữa.

| Muốn đổi | Tìm trong `index.html` | Ghi chú |
| --- | --- | --- |
| Tên người gửi (ký cuối thư) | `sender: "Đào Quang Đức"` | Trong khối `const CONFIG` |
| Ngày ghi trên thư | `date: "Ngày 20 tháng 10 năm 2026"` | Trong `const CONFIG` |
| Nội dung các lá thư | `letters: [` | Xem mục "Viết thư" bên dưới |
| Nhạc nền | `musicUrl: "nhac.mp3"` | Thay file `nhac.mp3`, hoặc đổi tên file ở đây. Để `""` thì trang dùng nhạc hộp nhạc tự tạo |
| Âm lượng nhạc | `const FILE_VOL = 0.5` | Từ 0 đến 1 |
| Tiêu đề lớn | `Happy Women's Day</h1>` và `Happy Women's Day</h2>` | Có ở màn đầu và màn cuối |
| Dòng ngày tháng trang trí | `20 · 10 · 2026` | Có ở màn đầu và màn cuối |
| Câu chào ở màn đầu | `đang chờ cậu mở` | |
| Chữ nhỏ góc trên bên trái | `class="brand"` | |
| Tên trang trên tab trình duyệt | `<title>` | Đổi cả `og:title` ở đầu file để link chia sẻ hiện đúng |
| Chữ trong màn chờ | `const subs = [` | |
| Màu chủ đạo của giao diện | `:root{` | Các biến `--rose`, `--rose-deep`, `--sky`, `--blush`… |
| Màu đóa hồng pha lê | `const roseMats = [` | 4 màu từ tâm ra cánh ngoài, dạng `0xRRGGBB` |
| Màu lá và thân hoa | `const leafMat = crystal(` | |
| Màu trái tim ở màn đầu | `crystal(0xf0307a` | |
| Màu hộp quà | `color: 0xffa9c8` | |
| Số cánh hoa rơi | `const PET_N =` | Ít hơn thì chạy nhẹ hơn trên máy yếu |

### Viết thư

Mỗi lá thư trong `letters` có dạng:

```js
{
  paragraphs: [
    "Đoạn thứ nhất, có thể nhắc tên {ten}.",
    "Đoạn thứ hai.",
    "Đoạn thứ ba."
  ],
  closing: "Câu kết, ví dụ: Chúc mừng ngày của cậu nhé, {ten}!",
  ps: "Nội dung dòng Tái bút."
},
```

- `{ten}` được thay bằng **tên gọi**, tức chữ cuối của tên người xem nhập ("Nguyễn Thị Mai" → "Mai").
- `{name}` được thay bằng **họ tên đầy đủ**.
- Mỗi lần mở thư, trang chọn ngẫu nhiên một lá và không lặp lại lá vừa đọc. Thêm bao nhiêu lá cũng được, chỉ cần giữ đúng dấu phẩy giữa các lá.
- Lời chào "Thân gửi …" và chữ ký cuối thư được tạo tự động, không cần viết trong `paragraphs`.

## Gửi link có sẵn tên

Thêm `?ten=` vào cuối link, ví dụ:

```
https://nguyenthevietk76-hub.github.io/Th--H-ng/?ten=Mai
```

Mở ra là ô tên đã được điền "Mai".

## Đăng trang của bạn lên mạng (GitHub Pages)

1. Fork kho này về tài khoản của bạn.
2. Vào **Settings → Pages**, phần **Source** chọn **Deploy from a branch**, chọn nhánh **main**, thư mục **/ (root)**, bấm **Save**.
3. Đợi 1–2 phút, trang sẽ có địa chỉ dạng `https://<tên-tài-khoản>.github.io/<tên-kho>/`.
4. Mỗi lần sửa và đẩy code lên nhánh `main`, trang tự cập nhật sau vài phút.

## Lưu ý

- **Nhạc nền:** `nhac.mp3` là bài nhạc người tạo trang tự chọn. Nếu dùng cho trang của bạn, hãy thay bằng bài nhạc bạn có quyền sử dụng.
- **Thư viện 3D:** trang dùng Three.js **r128** tải từ cdnjs. Không đổi sang bản mới hơn nếu không sửa lại code 3D, vì các bản sau đổi nhiều hàm.
- **Trình duyệt chặn tự phát nhạc:** nếu bị chặn, trang hiện nút "Chạm để mở quà" sau màn chờ để bật nhạc. Đây là quy định của trình duyệt, không phải lỗi.
- Khi sửa code JavaScript, giữ đúng dấu ngoặc và dấu phẩy. Nếu trang trắng hoặc đứng ở màn chờ, nhấn **F12** và xem tab **Console** để biết lỗi ở dòng nào.
