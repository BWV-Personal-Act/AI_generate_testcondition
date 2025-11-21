# 📋 Test Cases API customerCreate Chi Tiết

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| customerCreate | Bình thường | URL phải đúng | URL | -- | -- | `POST /v1/customer` |
| customerCreate | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| customerCreate | Bất thường | Check quyền hạn | Quyền hạn | -- | position_id của login user != 0 | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| customerCreate | Bất thường | Check required | name | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客名は必須です。" ] }` |
| customerCreate | Bất thường | Check required | name | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客名は必須です。" ] }` |
| customerCreate | Bất thường | Check required | email | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは必須です。" ] }` |
| customerCreate | Bất thường | Check required | email | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは必須です。" ] }` |
| customerCreate | Bất thường | Check required | started_date | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "会員登録日は必須です。" ] }` |
| customerCreate | Bất thường | Check required | started_date | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "会員登録日は必須です。" ] }` |
| customerCreate | Bất thường | Check required | password | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| customerCreate | Bất thường | Check required | password | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| customerCreate | Bất thường | Check format | email | khác format email | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスを正しく入力してください。" ] }` |
| customerCreate | Bất thường | Check format | started_date | Khác format yyyy/MM/dd | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "会員登録日は日付を正しく入力してください。" ] }` |
| customerCreate | Bất thường | Check format | position_id | Khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "役職は数値のみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check size | name | > 100 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客名は100文字以内で入力してください。" ] }` |
| customerCreate | Bất thường | Check size | email | > 255 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは255文字以内で入力してください。" ] }` |
| customerCreate | Bất thường | Check size | password | > 255 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは255文字以内で入力してください。" ] }` |
| customerCreate | Bất thường | Check giá trị | position_id | Khác 0 hoặc 1 hoặc 2 | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "有効な役職を入力してください。" ] }` |
| customerCreate | Bất thường | Check email trùng | email | Email đã tồn tại trong DB | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "すでにメールアドレスは登録されています。" ] }` |
| customerCreate | Bất thường | Lỗi 500 | Tổng thể | -- | Server error | **Status: 500 Internal Server Error**<br>`{ "errors": [ "ERROR" ] }` |
| customerCreate | Bình thường | Response phải đúng | Response | -- | Không xảy ra lỗi bên trên | **Status: 201 Created**<br>`{ "id": "new customer.id" }` |
| customerCreate | Bình thường | Giá trị trả về phải đúng | id | -- | create success | Trả về `customer.id` được tạo mới (auto-increment) |
| customerCreate | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | -- | Xử lý đăng ký phải được tiến hành đúng vào table customer<br>※Chi tiết tham chiếu test case bên dưới<br>(Các giá trị bên dưới lấy từ Request Parameter) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | id | -- | -- | Auto-increment (new record) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | name | -- | parameter.name | parameter.name |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | email | -- | parameter.email | parameter.email |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | password | -- | parameter.password | Mã hóa của parameter.password |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | started_date | -- | parameter.started_date | parameter.started_date (format: yyyy-MM-dd) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | position_id | -- | parameter.position_id | parameter.position_id |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | position_id | -- | position_id không gửi | 0 (default) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | created_date | -- | -- | Ngày hiện tại (created_date được ghi nhận) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | updated_date | -- | -- | Ngày hiện tại (updated_date được ghi nhận) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deleted_date | -- | -- | NULL |
