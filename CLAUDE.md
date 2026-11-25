# One2free — giao diện xác thực

## Mục đích

Tài liệu này tóm tắt yêu cầu, chức năng và kết quả của hai trang xác thực hiện có, đồng thời quy định chuẩn thiết kế cho các trang cơ bản được bổ sung trong tương lai.

## Các trang hiện có

### `login.html` — Đăng nhập

- Cho phép người dùng nhập email và mật khẩu; cả hai trường đều bắt buộc.
- Có tùy chọn ghi nhớ đăng nhập, liên kết quên mật khẩu và nút đăng nhập.
- Cung cấp nút đăng nhập qua Google, GitHub và Facebook.
- Có điều khiển hiện/ẩn mật khẩu.
- Có liên kết “Please sign up” chuyển đến `register.html`.

### `register.html` — Đăng ký

- Thu thập họ tên, email, mật khẩu và mật khẩu xác nhận; các trường này bắt buộc.
- Mật khẩu xác nhận phải trùng mật khẩu. Hiển thị lỗi bằng kiểm tra hợp lệ của trình duyệt.
- Giới tính, địa chỉ và số điện thoại là tùy chọn. Nếu nhập số điện thoại, yêu cầu đúng 10 chữ số.
- Yêu cầu người dùng đồng ý Terms of Service và Privacy Policy trước khi gửi biểu mẫu.
- Có điều khiển hiện/ẩn cho cả hai trường mật khẩu và liên kết “Sign in” quay lại `login.html`.

### Giới hạn hiện tại

Hai trang là giao diện phía trình duyệt. Biểu mẫu, OAuth, quên mật khẩu, điều khoản và chính sách chưa được kết nối với backend hoặc URL dịch vụ thực tế. Khi triển khai xác thực, cần nối các hành động này với endpoint và luồng phù hợp; không coi kiểm tra phía trình duyệt là biện pháp xác thực hoặc bảo mật phía máy chủ.

## Quy chuẩn thiết kế cho trang mới

### Thương hiệu và ngôn ngữ

- Dùng wordmark **One2free** nhất quán; không thay bằng tên thương hiệu khác.
- Nội dung hiển thị trong giao diện phải viết hoàn toàn bằng tiếng Anh.
- Dùng câu chữ ngắn, dễ hiểu và nhất quán giữa các trang liên quan.

### Màu sắc và kiểu chữ

- Dùng dark theme toàn trang: nền chính `#090A14`, bề mặt thẻ tối hơn hoặc sáng hơn nhẹ để tạo phân cấp.
- Dùng màu chính/CTA `#DF6B33`; màu này dành cho hành động chính, điểm nhấn và trạng thái focus phù hợp.
- Tiêu đề dùng **Poppins**, đậm (700–800); nội dung và biểu mẫu dùng **Inter**, thường (400), có thể dùng các độ đậm cần thiết cho nhãn/nút.
- Giữ độ tương phản dễ đọc; trạng thái hover, focus, disabled và lỗi phải nhận biết được trên nền tối.

### Bố cục và biểu tượng

- Mọi trang phải responsive từ điện thoại đến tablet và desktop; không tạo tràn ngang ở viewport hẹp.
- Ưu tiên bố cục một cột trên màn hình nhỏ; chỉ dùng nhiều cột khi đủ không gian.
- Dùng Tailwind CSS và giữ nhất quán với các token/màu/font đang có trong `login.html` và `register.html`.
- Dùng Lucide Icons để hỗ trợ nhận biết trường hoặc hành động. Icon trang trí cần được ẩn khỏi công nghệ hỗ trợ; icon không thay thế nhãn văn bản.
- Giữ nhãn liên kết với input, vùng bấm đủ dùng trên thiết bị cảm ứng và trạng thái bàn phím nhìn thấy được.

### Biểu mẫu và kiểm tra dữ liệu

- Đánh dấu rõ trường bắt buộc và tùy chọn; dùng `required` cho dữ liệu cần thiết.
- Chọn `type`, `autocomplete`, `inputmode`, `pattern` và độ dài phù hợp với từng dữ liệu.
- Ràng buộc các trường quan trọng theo yêu cầu nghiệp vụ, bao gồm quan hệ giữa các trường (ví dụ: mật khẩu xác nhận phải trùng).
- Trường tùy chọn chỉ bị kiểm tra định dạng khi người dùng có nhập giá trị.
- Hiển thị lỗi hữu ích và giữ dữ liệu người dùng đã nhập khi có thể.
- Kiểm tra dữ liệu ở server khi tích hợp backend; không dựa riêng vào HTML/JavaScript phía client.

### Điều hướng giữa các trang

- Cung cấp liên kết đến các trang liên quan ở vị trí dễ tìm (ví dụ: đăng nhập ↔ đăng ký).
- Dùng đường dẫn tương đối thực sự trỏ đến trang đích, không để `#` làm URL tạm cho hành động cần hoạt động.
- Giữ tên trang, tiêu đề trình duyệt và wordmark nhất quán với One2free.

## Xác minh khi bổ sung trang

- Kiểm tra bố cục ở kích thước điện thoại, tablet và desktop; đảm bảo không có tràn ngang.
- Kiểm tra trường bắt buộc, định dạng, ràng buộc giữa các trường và checkbox bắt buộc.
- Kiểm tra liên kết điều hướng, thao tác bàn phím, nhãn biểu mẫu và trạng thái focus.