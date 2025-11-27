# Test Cases - Login API [POST /v1/login]

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| /v1/login | Bình thường | URL phải đúng | URL | -- | -- | `POST /v1/login` |
| /v1/login | Bất thường | Check required | email | Gửi rỗng | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは必須です。" ] }` |
| /v1/login | Bất thường | Check required | email | Không gửi | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは必須です。" ] }` |
| /v1/login | Bất thường | Check required | password | Gửi rỗng | - | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| /v1/login | Bất thường | Check required | password | Không gửi | - | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| /v1/login | Bất thường | Check format | email | Khác format email | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスを正しく入力してください。" ] }` |
| /v1/login | Bất thường | Check max-length | email | > 255 ký tự | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは255文字以下で入力してください。" ] }` |
| /v1/login | Bất thường | Check max-length | password | > 255 ký tự | - | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは255文字以下で入力してください。" ] }` |
| /v1/login | Bất thường | Check tồn tại customer | email | Email không tồn tại trong DB | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| /v1/login | Bất thường | Check tồn tại customer | email | Email tồn tại nhiều record | - | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| /v1/login | Bất thường | Check deleted_date | Tổng thể | customer.deleted_date != NULL | Email & password nhập đúng nhưng customer đã xóa | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| /v1/login | Bất thường | Check password | password | Password không khớp | Email tồn tại nhưng password sai | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| /v1/login | Bình thường | Response phải đúng | Response | - | Email & password nhập đúng, customer tồn tại, deleted_date = NULL | **Status: 200 OK**<br>`{ Tham chiếu bên dưới }` |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | email | - | - | customer.email |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | started_date | - | - | customer.started_date (định dạng: yyyy/mm/dd) |
| Bảng customer | Bình thường | Chi tiết response là chính xác | position_id | - | - | customer.position_id (0: Manager, 1: Deputy Manager, 2: Staff) |
| Bảng customer | Bình thường | Chi tiết response là chính xác | created_date | - | - | customer.created_date (định dạng: yyyy/mm/dd) |
| Bảng customer | Bình thường | Chi tiết response là chính xác | updated_date | - | - | customer.updated_date (định dạng: yyyy/mm/dd) |
| Bảng token | Bình thường | Chi tiết response là chính xác | token | - | - | `{ Tham chiếu bên dưới }` |
| Bảng token | Bình thường | Chi tiết response là chính xác | accessToken | - | - | Token string được phát hành bởi hệ thống |
