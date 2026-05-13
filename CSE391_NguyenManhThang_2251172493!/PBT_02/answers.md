## Phần A - Kiểm tra đọc hiểu
### Câu A1 - Input Types
1. type="email"
- Ô nhập text có dạng email
- Tự kiểm tra có ký tự @ và domain
- Dùng cho form đăng ký tài khoản
2. type="password"
- Ô nhập bị ẩn ký tự bằng dấu chấm hoặc *
- Có thể kết hợp minlength, required
- Dùng cho đăng nhập tài khoản
3. type="number"
- Ô nhập số có nút tăng giảm
- Kiểm tra chỉ nhập số, min/max
- Dùng nhập số lượng sản phẩm
4. type="tel"
- Ô nhập số điện thoại
- Không validate mạnh mặc định
- Dùng nhập số điện thoại giao hàng
5. type="url"
- Ô nhập địa chỉ website
- Kiểm tra đúng định dạng URL
- Dùng nhập link website shop
6. type="date"
- Giao diện chọn ngày
- Kiểm tra dữ liệu ngày hợp lệ
- Dùng chọn ngày sinh hoặc ngày giao hàng
7. type="time"
- Giao diện chọn giờ
- Kiểm tra định dạng thời gian
- Dùng chọn giờ nhận hàng
8. type="file"
- Nút upload file
- Có thể giới hạn accept
- Dùng upload ảnh đánh giá sản phẩm
9. type="checkbox"
- Ô vuông tick chọn nhiều mục
- Không có validation đặc biệt
- Dùng chọn đồng ý điều khoản
10. type="radio"
- Nút chọn duy nhất trong nhóm
- Chỉ chọn được 1 option
- Dùng chọn phương thức thanh toán

### Câu A2 - Validation Attributes
<!-- Trường hợp 1 -->
<input type="text" required value="">
- Kết quả: Form không submit được
- Lý do: + required bắt buộc nhập dữ liệu
         + Giá trị đang rỗng ("")

<!-- Trường hợp 2 -->
<input type="email" value="abc">
- Kết quả: Form không submit được
- Lý do: + type="email" yêu cầu định dạng email hợp lệ
         + "abc" không có @domain

<!-- Trường hợp 3 -->
<input type="number" min="1" max="10" value="15">
- Kết quả: Form không submit được
- Lý do: Giá trị 15 lớn hơn max="10"

<!-- Trường hợp 4 -->
<input type="text" pattern="[0-9]{10}" value="abc123">
- Kết quả: Form không submit được
- Lý do: + Pattern yêu cầu đúng 10 chữ số
         + "abc123" chứa chữ và không đủ 10 số

<!-- Trường hợp 5 -->
<input type="password" minlength="8" value="123">
- Kết quả: Form không submit được
- Lý do: + Mật khẩu chỉ có 3 ký tự
         + minlength="8" yêu cầu tối thiểu 8 ký tự

### Câu A3 - Accessibility
1. Screen reader sẽ đọc label để người khiếm thị biết ô input dùng để nhập gì.
- Ví dụ: 
```html
 <label for="email">Email</label>
 <input type="email" id="email">
```
- Khi focus vào input screen reader đọc: “Email, edit text”.
- Click vào label cũng focus được input, tăng usability trên mobile.
2. Dùng khi nhóm nhiều input liên quan
- Ví dụ: + Chọn phương thức thanh toán
         + Thông tin giới tính
```html
<fieldset>
    <legend>Phương thức thanh toán</legend>

    <input type="radio" name="pay"> Tiền mặt
    <input type="radio" name="pay"> Thẻ ngân hàng
</fieldset>
```
legend giúp screen reader hiểu nhóm input này thuộc cùng một chủ đề.
3. Dùng khi không có text label hiển thị.
- Không dùng khi:
+ Semantic HTML tự nhiên luôn tốt hơn
+ <label> hỗ trợ accessibility + usability tốt hơn
+ aria-label chỉ nên là giải pháp bổ sung
