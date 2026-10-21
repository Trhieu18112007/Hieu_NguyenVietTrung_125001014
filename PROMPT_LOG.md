# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

**Họ và tên:** Nguyễn Viết Trung Hiếu
**MSSV:** 125001014
**Tên đề tài Website:** Portfolio giới thiệu bản thân (Dark/Cyber Theme)
**Công cụ AI đã sử dụng:** Gemini

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)
> Đóng vai một chuyên gia Frontend (Senior Developer). Hãy viết cho tôi một trang Landing Page chủ đề "Portfolio giới thiệu bản thân" chuyên nghiệp, hiện đại.
> Yêu cầu kỹ thuật bắt buộc: 
> 1. Chỉ dùng HTML5 Semantic (tuyệt đối không dùng div bọc ngoài nếu có thể dùng main/section).
> 2. Khai báo CSS Variables cho hệ màu ở :root.
> 3. Dùng CSS Grid/Flexbox để responsive. 
> 4. Tích hợp sẵn CDN của Animate.css và AOS vào file HTML.

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iterations)

### Lần 1: Dựng khung chi tiết và Tách cấu trúc file
- **Prompt đã dùng:** Yêu cầu AI tách rõ 5 sections: Header, Hero, About, Skills, Projects, Footer. Bắt buộc có hiệu ứng hover custom tự viết bằng CSS transition và xuất ra 2 file `index.html` và `style.css` riêng biệt.
- **Kết quả AI tạo ra:** AI xuất ra bộ code đầy đủ, UI/UX ở mức cơ bản, hiệu ứng cuộn trang hoạt động ổn định.
- **Nhận xét & Tinh chỉnh của SV:** AI đã tuân thủ đúng chuẩn Semantic HTML5 (`<main>`, `<section>`, `<article>`). Tuy nhiên, ban đầu AI gộp chung mã CSS vào file HTML. Tôi đã can thiệp bằng tay (hoặc yêu cầu AI tách ra) thành file `style.css` riêng biệt và tạo thêm thư mục `assets/` để chứa hình ảnh thật thay thế cho placeholder, đảm bảo đúng chuẩn cấu trúc dự án.

### Lần 2: Nâng cấp UI/UX - Đổi Theme IT và Code chức năng Modal
- **Prompt đã dùng:** Yêu cầu đổi theme sang "Dark/Cyber Mode" (Màu nền xanh đen `#0a192f`, màu nhấn xanh Cyan `#64ffda`). Yêu cầu dùng Vanilla JavaScript viết chức năng Popup Modal cho nút "Xem chi tiết" ở các thẻ dự án.
- **Lý do tinh chỉnh:** Theme mặc định khá nhàm chán, chưa mang bản sắc của sinh viên IT. Nút "Xem chi tiết" chỉ là UI giả (dummy), làm giảm trải nghiệm người dùng.
- **Cách sửa prompt (Debug prompt):** Yêu cầu cụ thể AI xử lý sự kiện click, tạo màn hình Overlay mờ và Modal nằm giữa màn hình chứa thông tin mở rộng của dự án, đồng thời xử lý logic đóng Modal khi click ra ngoài.
- **Kết quả:** Giao diện tối hiện đại, đậm chất lập trình viên. Modal JavaScript hoạt động mượt mà, đúng logic.

### Lần 3: Cross-Check AI - Debug chuyên sâu lỗi Semantic và Xung đột Animation
- **Thách thức & Lỗi phát hiện:** Bằng việc rà soát kỹ lưỡng, tôi phát hiện AI tạo ra 3 lỗi kỹ thuật ẩn:
  1. **Xung đột Animation:** Thư viện AOS ghi đè thuộc tính `transform`, làm mất tác dụng của hiệu ứng `:hover` tự viết ở thẻ bài viết. Lỗi `overflow-x` gây cuộn ngang màn hình trên Mobile.
  2. **Lỗi HTML5 Semantic:** Lạm dụng `<div>` cho Logo và Social links, sai thứ tự Heading (`<h2>` trước `<h1>`).
  3. **Lỗi CSS:** Còn sót màu HEX hard-code chưa khai báo vào biến `:root`.
- **Cách sửa prompt:** Tôi ra lệnh cho AI bọc Card dự án vào thẻ `<li>`, gán `data-aos` ở thẻ cha (`<li>`) và xử lý hiệu ứng `:hover` ở thẻ con (`.project-card`). Yêu cầu AI đổi `<div>` thành `<a>`, `<ul>` và gom 100% màu sắc vào CSS Variables. Thêm `scroll-padding-top` để fix lỗi header che khuất nội dung.
- **Kết quả:** Xử lý triệt để xung đột giữa các thư viện và code custom, chuẩn hóa Clean Code.

### Lần 4: Tối ưu hoá vi mô (Micro-Optimization) và Bổ sung tính năng nâng cao (Scale-up)
- **Phát hiện sự cố:** Mở Modal bằng JS làm ẩn scrollbar, gây lỗi Cumulative Layout Shift (CLS - giật khung hình ngang). Script xử lý Modal bị lỗi Accessibility (bắt cóc phím Tab). Các Card dự án không đều chiều cao.
- **Cách khắc phục:** Yêu cầu AI bỏ logic chặn phím Tab. Viết hàm JS đo chiều rộng scrollbar để bù `padding-right` vào thẻ `body` khi bật Modal. Flex lại `.project-card` thành `height: 100%`. Thêm `loading="lazy"` cho ảnh.
- **Mở rộng tính năng:** Để tăng khối lượng và chất lượng mã nguồn, tôi yêu cầu AI code thêm 2 tính năng:
  1. **Scroll Progress Bar:** Lắng nghe event cuộn để chạy thanh tiến trình Neon trên đỉnh trang.
  2. **Contact Form & Toast Notification:** Bổ sung Section Liên hệ. Khi Submit form, tự động PreventDefault và bật thông báo "Gửi thành công" (Toast) ở góc dưới màn hình.
- **Kết quả:** Trang web mở rộng thêm hơn 100 dòng code chất lượng. Hoạt động như một ứng dụng thực tế với độ hoàn thiện cực kỳ cao.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

**1. AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?**
AI thực sự tỏa sáng trong việc tạo ra bộ khung ban đầu (Boilerplate). Nó giúp tôi nhanh chóng thiết lập hệ thống biến CSS Variables, dàn layout Grid/Flexbox và gắn các CDN thư viện animation chuẩn xác chỉ trong vài giây. Các thao tác viết lại CSS cho Responsive và khởi tạo cú pháp Modal thuần (Vanilla JS) cũng được rút ngắn tối đa thời gian gõ phím.

**2. Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?**
- **Sự cụ thể là chìa khóa:** Không nên chỉ ra lệnh "Hãy làm cho đẹp". Cần đóng vai chuyên gia, mô tả rõ ràng theme màu, các thẻ cần dùng (bắt buộc Semantic), và cấm điều gì (không dùng Bootstrap).
- **Chia nhỏ vấn đề:** Việc yêu cầu AI sửa một lúc quá nhiều lỗi có thể làm hỏng logic cũ. Cần "tinh chỉnh" từng bước (từ Layout -> Theme -> JS Modal -> Fix Animation).
- **Làm chủ công nghệ (Không phụ thuộc hoàn toàn):** Code do AI sinh ra (dù là AI xịn nhất) vẫn luôn tiềm ẩn lỗi xung đột thư viện hoặc vi phạm các chuẩn Trợ năng (Accessibility/CLS). Người lập trình (Prompter) phải có kiến thức nền tảng vững chắc để kiểm tra (Review code), phát hiện lỗi ẩn và viết lệnh bắt AI phải sửa đúng ngay chỗ đó.