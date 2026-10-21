# Portfolio — Nguyễn Viết Trung Hiếu

Trang portfolio cá nhân một trang (single-page) phong cách dark / cyber neon, xây dựng hoàn toàn bằng HTML, CSS và JavaScript thuần. Không framework, không cần bước build: mở `index.html` là chạy.

<!-- Thêm ảnh chụp màn hình khi có: ![Preview](assets/preview.png) -->

## Tính năng

- **Giao diện dark / neon**: màu sắc, khoảng cách và font được quản lý bằng CSS variables trong `:root`.
- **Responsive**: viết theo hướng mobile-first, đổi bố cục ở breakpoint `768px`.
- **Các phần của trang**: Home, About, Skills, Projects, Contact và Footer.
- **Modal chi tiết dự án**: đóng bằng nút ×, phím `Esc` hoặc click ra vùng tối bên ngoài. Focus được giữ trong modal (Tab / Shift + Tab đi vòng tròn) và trả về nút đã mở khi đóng.
- **Không giật trang khi mở modal**: JS đo độ rộng thanh cuộn rồi bù vào `padding-right` của `body` và header cố định.
- **Scroll progress bar**: thanh neon mỏng 3px cố định ở mép trên, chiều rộng thể hiện phần trăm trang đã cuộn.
- **Form liên hệ (mô phỏng)**: kiểm tra hợp lệ bằng HTML5, tự xóa form sau khi gửi và hiện toast "Hệ thống đã ghi nhận tin nhắn!" trượt vào từ góc dưới bên phải, tự ẩn sau 3 giây.
- **Hiệu ứng khi cuộn**: AOS và Animate.css, tự tắt khi người dùng bật chế độ giảm chuyển động (`prefers-reduced-motion`).
- **Hiệu năng và SEO**: `loading="lazy"` cho ảnh dự án, `preconnect` tới Google Fonts, thẻ meta description và Open Graph.
- **Trợ năng (a11y)**: HTML ngữ nghĩa, `aria-*` cho modal và toast, viền focus rõ khi dùng bàn phím, thông báo `<noscript>` khi tắt JavaScript.

## Công nghệ

| Thành phần | Chi tiết |
| --- | --- |
| Nền tảng | HTML5, CSS3 (Grid, Flexbox, CSS variables), JavaScript ES6+ |
| Hiệu ứng | [AOS 2.3.1](https://github.com/michalsnik/aos), [Animate.css 4.1.1](https://animate.style/) (tải qua CDN) |
| Font | [Inter](https://fonts.google.com/specimen/Inter), [Fira Code](https://fonts.google.com/specimen/Fira+Code) (Google Fonts) |

## Cấu trúc thư mục

```
.
├── index.html        # Cấu trúc trang và JavaScript (modal, progress bar, form, toast)
├── style.css         # Toàn bộ giao diện, chia thành các phần có đánh số
├── README.md
└── assets/
    ├── avatar.jpg
    ├── project1.png
    ├── project2.png
    └── project3.png
```

## Chạy trên máy

Không cần cài đặt gì. Mở trực tiếp `index.html` bằng trình duyệt, hoặc chạy một server tĩnh trong thư mục dự án:

```bash
python3 -m http.server 8000
```

Sau đó truy cập `http://localhost:8000`. Bạn cũng có thể dùng extension Live Server của VS Code.

> AOS, Animate.css và Google Fonts được tải qua CDN nên cần có Internet để hiển thị đầy đủ.

## Tùy chỉnh

**Đổi màu, bố cục chung**: sửa các biến trong `:root` ở đầu `style.css` (ví dụ `--primary`, `--bg-main`, `--container-width`).

**Thêm kỹ năng**: thêm một `<li>` vào `.skills-grid`.

```html
<li data-aos="zoom-in" data-aos-delay="450"><div class="skill-card">Tên kỹ năng</div></li>
```

**Thêm dự án**: sao chép một `<li>` trong `.projects-grid` rồi sửa nội dung. Dữ liệu của modal được lấy từ các thuộc tính `data-*` trên nút "Xem chi tiết":

| Thuộc tính | Ý nghĩa |
| --- | --- |
| `data-title` | Tiêu đề hiển thị trong modal |
| `data-desc` | Mô tả chi tiết |
| `data-tech` | Danh sách công nghệ, ngăn cách bằng dấu phẩy |
| `data-img` | Đường dẫn ảnh lớn trong modal |

**Ảnh**: đặt ảnh thật vào thư mục `assets/`. Nếu ảnh chưa có, trang tự dùng ảnh placeholder từ placehold.co.

## Form liên hệ

Form hiện chỉ **mô phỏng**: dữ liệu không được gửi đi đâu cả. Để nhận tin nhắn thật, hãy thay phần xử lý sự kiện `submit` ở cuối `index.html` bằng lời gọi `fetch` tới backend hoặc dịch vụ nhận form (ví dụ Formspree, EmailJS).

## Checklist trước khi đưa lên mạng

- [ ] Thay email và số điện thoại thật trong phần Contact và Footer.
- [ ] Thay link GitHub, LinkedIn, Facebook trong Footer.
- [ ] Thay `example.com` trong các thẻ `og:url` và `og:image`, và thêm ảnh `assets/og-image.jpg` (1200×630 px).
- [ ] Đặt ảnh avatar và ảnh dự án thật vào `assets/`.
- [ ] Kết nối form liên hệ với dịch vụ thật (nếu cần nhận tin nhắn).

## Triển khai

Đây là site tĩnh nên có thể đưa lên GitHub Pages, Netlify hoặc Vercel mà không cần cấu hình build. Ví dụ với GitHub Pages: đẩy mã lên repository, vào **Settings → Pages**, chọn **Deploy from a branch**, rồi chọn nhánh `main` và thư mục `/ (root)`.

## Trình duyệt hỗ trợ

Các trình duyệt hiện đại, bản gần đây (Chrome, Edge, Firefox, Safari).

## Tác giả

Thiết kế và xây dựng bởi **Nguyễn Viết Trung Hiếu**.
