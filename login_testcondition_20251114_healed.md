| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| login | Bình thường | URL phải đúng | URL | -- | -- | `POST /v1/login` |
| login | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| login | Bất thường | Check quyền hạn | Quyền hạn | - | User không có quyền login | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| login | Bất thường | Check truy cập URL không tồn tại | URL | -- | Truy cập vào URL không tồn tại (vd: /v1/loginn) | **Status: 404 Not Found**<br>`{ "errors": [ "Not Found URL" ] }` |
| login | Bất thường | Check lỗi server | Tổng thể | -- | Giả lập lỗi server | **Status: 500 ERROR**<br>`{ "errors": [ "ERROR" ] }` |
| login | Bất thường | Check required | email | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "emailは必須です。" ] }` |
| login | Bất thường | Check required | email | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "emailは必須です。" ] }` |
| login | Bất thường | Check required | password | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "passwordは必須です。" ] }` |
| login | Bất thường | Check required | password | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "passwordは必須です。" ] }` |
| login | Bất thường | Check size | email | > 255 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "emailは255文字以内で入力してください。" ] }` |
| login | Bất thường | Check size | password | > 255 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "passwordは255文字以内で入力してください。" ] }` |
| login | Bất thường | Check format | email | khác format email | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効なEメールアドレスを入力してください。" ] }` |
| login | Bất thường | Check logic | email, password | - | Nhập email không tồn tại trong DB | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "loginFailure" ] }` |
| login | Bất thường | Check logic | email, password | - | Nhập email đúng, password sai | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "loginFailure" ] }` |
| login | Bất thường | Check logic | email, password | - | User tồn tại nhưng `deleted_date` != NULL | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "loginFailure" ] }` |
| login | Bình thường | Response phải đúng | Response | - | Nhập email và password chính xác, user active | **Status: 200 OK**<br> `{ "id": "customer.id", "email": "customer.email", "name": "customer.name", "started_date": "customer.started_date", "position_id": "customer.position_id", "created_date": "customer.created_date", "updated_date": "customer.updated_date", "token": { "accessToken": "..." } }` |
| login | Bình thường | Chi tiết response phải đúng | id | - | Login thành công | `customer.id` |
| login | Bình thường | Chi tiết response phải đúng | email | - | Login thành công | `customer.email` |
| login | Bình thường | Chi tiết response phải đúng | name | - | Login thành công | `customer.name` |
| login | Bình thường | Chi tiết response phải đúng | started_date | - | Login thành công | `customer.started_date` |
| login | Bình thường | Chi tiết response phải đúng | position_id | - | Login thành công | `customer.position_id` |
| login | Bình thường | Chi tiết response phải đúng | created_date | - | Login thành công | `customer.created_date` |
| login | Bình thường | Chi tiết response phải đúng | updated_date | - | Login thành công | `customer.updated_date` |
| login | Bình thường | Chi tiết response phải đúng | token.accessToken | - | Login thành công | token được trả về |
