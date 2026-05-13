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

## Phần C - Suy luận
### Câu C1 -  Thiết kế cấu trúc
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chi tiết sản phẩm</title>
</head>
<body>

    <!-- header dùng cho phần đầu trang -->
    <header>

        <!-- nav vì đây là khu vực điều hướng chính -->
        <nav>
            <ul>
                <li><a href="#">Trang chủ</a></li>
                <li><a href="#">Danh mục</a></li>
                <li><a href="#">Liên hệ</a></li>
            </ul>
        </nav>

    </header>

    <!-- main chứa nội dung chính của trang -->
    <main>

        <!-- nav dùng cho breadcrumb vì đây là điều hướng -->
        <nav aria-label="breadcrumb">

            <!-- ol vì breadcrumb có thứ tự cấp bậc -->
            <ol>
                <li><a href="#">Trang chủ</a></li>
                <li><a href="#">Điện thoại</a></li>
                <li>iPhone 16</li>
            </ol>

        </nav>

        <!-- section dùng để nhóm nội dung sản phẩm -->
        <section>

            <!-- article vì đây là nội dung độc lập về 1 sản phẩm -->
            <article>

                <!-- section cho khu vực hình ảnh sản phẩm -->
                <section>

                    <h2>Hình ảnh sản phẩm</h2>

                    <!-- figure dùng cho ảnh minh họa -->
                    <figure>
                        <img src="image1.jpg" alt="Ảnh sản phẩm 1">
                        <figcaption>Ảnh mặt trước</figcaption>
                    </figure>

                    <figure>
                        <img src="image2.jpg" alt="Ảnh sản phẩm 2">
                        <figcaption>Ảnh mặt sau</figcaption>
                    </figure>

                    <figure>
                        <img src="image3.jpg" alt="Ảnh sản phẩm 3">
                        <figcaption>Ảnh cạnh bên</figcaption>
                    </figure>

                    <figure>
                        <img src="image4.jpg" alt="Ảnh sản phẩm 4">
                        <figcaption>Ảnh camera</figcaption>
                    </figure>

                    <figure>
                        <img src="image5.jpg" alt="Ảnh sản phẩm 5">
                        <figcaption>Ảnh phụ kiện</figcaption>
                    </figure>

                </section>

                <!-- section cho thông tin sản phẩm -->
                <section>

                    <h1>iPhone 16</h1>

                    <!-- p dùng cho mô tả văn bản -->
                    <p>Giá sản phẩm</p>

                    <!-- strong nhấn mạnh giá -->
                    <strong>29.990.000đ</strong>

                    <!-- p hiển thị đánh giá -->
                    <p>⭐⭐⭐⭐⭐ (120 đánh giá)</p>

                    <!-- article cho mô tả chi tiết -->
                    <article>
                        <h2>Mô tả sản phẩm</h2>
                        <p>Mô tả ngắn về sản phẩm...</p>
                    </article>

                </section>

            </article>

        </section>

        <!-- section chứa bảng thông số kỹ thuật -->
        <section>

            <h2>Thông số kỹ thuật</h2>

            <!-- table dùng để hiển thị dữ liệu dạng bảng -->
            <table border="1">

                <!-- tbody chứa dữ liệu chính -->
                <tbody>
                    <tr>
                        <th>Màn hình</th>
                        <td>6.7 inch</td>
                    </tr>

                    <tr>
                        <th>RAM</th>
                        <td>8GB</td>
                    </tr>

                    <tr>
                        <th>Bộ nhớ</th>
                        <td>256GB</td>
                    </tr>
                </tbody>

            </table>

        </section>

        <!-- section cho đánh giá và bình luận -->
        <section>

            <h2>Đánh giá khách hàng</h2>

            <!-- article vì mỗi bình luận là nội dung độc lập -->
            <article>
                <h3>Nguyễn Văn A</h3>
                <p>Sản phẩm rất tốt.</p>
            </article>

            <article>
                <h3>Trần Văn B</h3>
                <p>Pin dùng ổn, camera đẹp.</p>
            </article>

        </section>

        <!-- aside dùng cho nội dung phụ liên quan -->
        <aside>

            <h2>Sản phẩm tương tự</h2>

            <!-- article cho từng sản phẩm liên quan -->
            <article>
                <h3>Samsung Galaxy S25</h3>
                <a href="#">Xem chi tiết</a>
            </article>

            <article>
                <h3>Xiaomi 15</h3>
                <a href="#">Xem chi tiết</a>
            </article>

        </aside>

    </main>

    <!-- footer cho phần cuối trang -->
    <footer>

        <p>&copy; 2026 Cửa hàng điện thoại</p>

        <!-- nav cho các liên kết cuối trang -->
        <nav>
            <a href="#">Chính sách</a>
            <a href="#">FAQ</a>
            <a href="#">Liên hệ</a>
        </nav>

    </footer>

</body>
</html>

### Câu C2 - So sánh tranh luận
- Việc sử dụng semantic HTML không phải chỉ để “đẹp code” mà còn mang lại nhiều lợi ích kỹ thuật quan trọng. Nếu dùng <div> cho mọi thứ, trình duyệt và các công cụ tìm kiếm sẽ rất khó hiểu cấu trúc thật sự của trang web.
- Lý do đầu tiên là SEO. Các công cụ tìm kiếm như Google ưu tiên những trang có cấu trúc semantic rõ ràng vì chúng giúp bot hiểu đâu là nội dung chính, đâu là menu điều hướng hay footer. Ví dụ, khi sử dụng <article> cho bài viết sản phẩm và <nav> cho menu, Google có thể phân tích nội dung chính xác hơn, từ đó cải thiện khả năng hiển thị trên kết quả tìm kiếm.
- Lý do thứ hai là Accessibility. Người dùng sử dụng screen reader sẽ dựa vào các semantic tags để điều hướng website. Nếu toàn bộ trang chỉ là <div>, screen reader sẽ đọc nội dung rất khó hiểu. Ngược lại, khi dùng <header>, <main>, <section>, hoặc <footer>, người khiếm thị có thể nhanh chóng xác định cấu trúc trang.
- Tuy nhiên, <div> vẫn rất phù hợp trong các trường hợp chỉ dùng để chia layout hoặc grouping phục vụ CSS/JavaScript, đặc biệt với các component giao diện phức tạp như grid, modal hoặc animation container. <div> không sai, nhưng semantic HTML giúp website “có nghĩa” hơn thay vì chỉ là một mê cung hộp chữ nhật.