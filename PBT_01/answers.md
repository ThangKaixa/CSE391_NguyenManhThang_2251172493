## Phần A - Kiểm tra và đọc hiểu
### Câu A1 - HTTP and Browser
1. Các bước chính khi nhập https://shopee.vn:
- B1: DNS lookup: trình duyệt hỏi DNS server để lấy IP của shopee.vn
- B2: Thiết lập kết nối: mở kết nối TCP đến IP đó, sau đó thực hiện TLS handshake vì dùng https
- B3: Gửi HTTP request: trình duyệt gửi request GET / tới server.
- B4: Server xử lý và trả về response: server Shopee trả về HTML cùng các header.
- B5: Render trang: trình duyệt phân tích HTML/CSS/JS, tải thêm tài nguyên, xây DOM/CSSOM rồi vẽ giao diện.

2. Tab NetWork của Chrome hiển thị:
- Request list: tất cả request đến server.
- Status code: mã phản hồi HTTP của từng request.
- Tổng thời gian load trang: thời gian từ request đầu đến khi tải xong.
- Resource type: HTML, CSS, JS, image, font...
- Size và timing chi tiết (DNS, TCP, SSL, TTFB, content download).
### Câu A2 - Semantic HTML
- 4 lỗi semantic chính:
+ div class="header" nên dùng <header>.
+ Logo ShopTLU nên là <h1> hoặc ít nhất <a> nằm trong header, không chỉ <div>.
+ Menu điều hướng nên dùng <nav> và danh sách <ul><li>, không dùng <div> cho từng link.
+ Product card nên dùng <article>, tiêu đề dùng <h2>, giá nên dùng <strong> chứ không chỉ <div>.
- Sửa lại: 

<header>
    <a class="logo" href="/">ShopTLU</a>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>
<main>
    <article class="product">
        <h2>iPhone 16 Pro</h2>
        <p class="price"><strong>25.990.000đ</strong></p>
        <figure class="image">
            <img src="iphone.jpg" alt="iPhone 16 Pro">
        </figure>
    </article>
</main>
<footer>
    <p>© 2026 ShopTLU</p>
</footer>

### Câu A3 - Block vs Inline
- Mô tả:
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3
- Giải thích:
<div> là thẻ block, luôn chiếm cả dòng và tạo ngắt dòng trước/sau.
<span> là thẻ inline, không tạo ngắt dòng, nội dung tiếp nối trên cùng dòng.

### Câu A4 - Table
- Khác nhau giữa <thead>, <tbody>, <tfoot>
+ <thead>: chứa phần header của bảng, thường là các tiêu đề cột.
+ <tbody>: chứa phần dữ liệu chính của bảng.
+ <tfoot>: chứa phần footer hoặc tổng kết của bảng, như tổng tiền, ghi chú.
- Tại sao không dùng table để làm layout:
1. Không semantic: layout không phải dữ liệu bảng -> không đúng ý nghĩa HTML.
2. Accessibility kém: screen reader và công cụ trợ năng hiểu nhầm cấu trúc.
3. Responsive khó: bảng cố định cột/dòng, khó tối ưu trên mobile.
