# VR360 · Đồng Khởi Bến Tre

GitHub Pages viewer cho dự án **Di tích Quốc gia Đặc biệt Đồng Khởi Bến Tre**.

## Trải nghiệm

Sau khi bật GitHub Pages cho nhánh `main` / thư mục `/ (root)`, trang sẽ có địa chỉ:

`https://base27-cvnss.github.io/vr360/`

## Bản chất kiến trúc

```text
GitHub Pages (UI shell)
        │
        ├── index.html          → giao diện + iframe + điều khiển
        ├── manifest.webmanifest
        ├── assets/icon.svg
        └── sw.js               → chỉ cache tài nguyên cùng origin
                 │
                 └── KHÔNG cache toàn bộ VR cross-origin

iframe
  └── https://vr360.com.vn/projects/di-tich-quoc-gia-dac-biet-dong-khoi-ben-tre/
```

Trang GitHub Pages là **lớp trình xem/wrapper**, không phải bản sao dữ liệu panorama của máy chủ VR360. Vì vậy:

- UI có thể được cache để mở lại khi mất mạng.
- Nội dung panorama, audio, hotspot và tài nguyên động từ `vr360.com.vn` vẫn phụ thuộc máy chủ nguồn.
- Muốn chạy **VR360 offline thực sự**, cần thu thập/xuất hợp pháp toàn bộ scene, tile panorama, cấu hình hotspot, media và JavaScript engine về cùng origin rồi thay iframe bằng viewer local.

## Điều khiển

| Phím | Chức năng |
|---|---|
| `F` | Toàn màn hình |
| `R` | Tải lại VR |
| `I` | Mở/đóng bảng thông tin |
| `H` | Ẩn/hiện thanh giao diện |
| `Esc` | Đóng bảng thông tin |

## GitHub Pages

Vào **Settings → Pages → Build and deployment**:

1. Chọn **Deploy from a branch**.
2. Branch: `main`.
3. Folder: `/ (root)`.
4. Bấm **Save**.

Nếu Pages đã được bật trước đó, commit mới trên `main` sẽ tự động được xuất bản.

## Nguồn VR

- https://vr360.com.vn/projects/di-tich-quoc-gia-dac-biet-dong-khoi-ben-tre/
