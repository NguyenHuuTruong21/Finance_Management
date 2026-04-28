# Finance_Management

## 1. Mô tả bài toán

`Finance_Management` là ứng dụng web quản lý tài chính cá nhân, hỗ trợ người dùng theo dõi thu nhập, chi tiêu, tài khoản, ngân sách và các khoản nhắc nhở thanh toán.

Bài toán mà hệ thống giải quyết gồm:

- Ghi nhận giao dịch thu và chi theo danh mục.
- Quản lý tài khoản và số dư hiện có.
- Lập ngân sách cho từng nhóm chi tiêu.
- Theo dõi các khoản cần thanh toán hoặc mục tiêu tích lũy.
- Tổng hợp báo cáo theo tháng, năm và theo danh mục.

Ứng dụng phù hợp cho đồ án môn học, bài tập lớn hoặc làm nền tảng để phát triển thêm các chức năng về quản lý tài chính cá nhân.

## 2. Chức năng chính

- Đăng ký, đăng nhập, đăng xuất người dùng.
- Quản lý giao dịch:
  - Thêm giao dịch.
  - Sửa giao dịch.
  - Xóa giao dịch.
  - Kiểm tra khả năng chi tiêu theo số dư tài khoản.
- Quản lý danh mục thu/chi.
- Quản lý tài khoản tài chính.
- Quản lý ngân sách.
- Quản lý nhắc nhở thanh toán và mục tiêu tích lũy.
- Xem dashboard tổng quan:
  - Tổng thu nhập.
  - Tổng chi tiêu.
  - Số dư còn lại.
  - Danh sách giao dịch gần đây.
- Báo cáo:
  - Báo cáo theo tháng.
  - Báo cáo theo năm.
  - Biểu đồ chi tiêu theo danh mục.
  - Biểu đồ thu nhập theo danh mục.

## 3. Công nghệ sử dụng

### Backend

- Java 21
- Spring MVC
- Spring Core / Spring JDBC
- Spring Security Crypto (dùng `BCrypt` để mã hóa mật khẩu)
- JDBC kết nối trực tiếp MySQL

### Frontend

- JSP / JSTL
- Bootstrap 5
- Font Awesome

### Database

- MySQL

### Môi trường phát triển

- Eclipse Dynamic Web Project
- Servlet/JSP web application
- Thư viện được quản lý trực tiếp trong `src/main/webapp/WEB-INF/lib`

## 4. Cấu trúc dự án

```text
src/main/java/com/finance
|-- config/         Cấu hình Spring MVC, Dispatcher Servlet, kết nối DB
|-- controllers/    Xử lý request và điều hướng giao diện
|-- dao/            Truy vấn dữ liệu bằng JDBC
|-- entities/       Các đối tượng dữ liệu
`-- service/        Xử lý nghiệp vụ

src/main/webapp/WEB-INF/views
`-- *.jsp           Giao diện người dùng

finance_management.sql
`-- Script tạo CSDL và dữ liệu mẫu
```

## 5. Cơ sở dữ liệu

File `finance_management.sql` tạo các bảng chính:

- `user`
- `category`
- `account`
- `transaction`
- `budget`
- `reminder`
- ....

## 6. Cách chạy dự án

### Bước 1: Tạo database

Chạy file:

```sql
finance_management.sql
```

Script sẽ tạo database `finance_db` và nạp dữ liệu mẫu.

### Bước 2: Cấu hình kết nối MySQL

Cập nhật thông tin trong file:

Giá trị hiện tại:

- URL: ``
- User: ``
- Password: ``

Bạn nên đổi lại cho phù hợp với máy của mình.

### Bước 3: Import vào Eclipse

- Mở Eclipse.
- Chọn `Import > Existing Projects into Workspace`.
- Import project `Finance_Management`.
- Đảm bảo server Tomcat đã được cấu hình trong Eclipse.

### Bước 4: Deploy và chạy

- Add project vào Apache Tomcat.
- Run server.
- Truy cập ứng dụng qua đường dẫn dạng:

```text
http://localhost:8080/Finance_Management/
```

## 7. Điểm nổi bật trong xử lý nghiệp vụ

- Mật khẩu người dùng được mã hóa bằng `BCrypt`.
- Mọi dữ liệu được tách theo `user_id`.
- Khi thêm giao dịch chi, hệ thống có kiểm tra số dư khả dụng.
- Dashboard hỗ trợ lọc giao dịch theo tháng và năm.
- Nhắc nhở có thể được đánh dấu đã thanh toán.

## 8. Hạn chế hiện tại

- Dự án chưa sử dụng Maven/Gradle, phụ thuộc đang được đưa trực tiếp vào `WEB-INF/lib`.
- Thông tin kết nối database đang hard-code trong source.
- File `finance_management.sql` hiện đang còn conflict marker Git ở cuối file và cần được làm sạch trước khi dùng trong môi trường thật.
- Trong repo có một số dấu hiệu lỗi mã hóa tiếng Việt trên source/JSP.
- `AuthController.java` đang được comment out, luồng đăng nhập hiện tại nằm trong `HomeController`.

## 9. Hướng phát triển

- Chuyển sang Maven hoặc Gradle để quản lý dependency.
- Đưa cấu hình DB vào file properties hoặc biến môi trường.
- Bổ sung phân quyền rõ ràng cho admin/user.
- Thêm validation form và thông báo lỗi thân thiện hơn.
- Bổ sung unit test, integration test.
- Cải thiện dashboard và biểu đồ thống kê.

## 11. Tác giả

- Nguyễn Hữu Trường.
- Cách tách `Controller - Service - DAO - Entity`.
- Tích hợp JSP, JDBC, MySQL và Spring MVC trong một ứng dụng quản lý thực tế.
