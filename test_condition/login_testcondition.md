# 📋 Test Cases - Login API

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| login | Bình thường | URL phải đúng | URL | -- | -- | `POST /v1/login` |
| login | Bất thường | Check required | password | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| login | Bất thường | Check required | password | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "パスワードは必須です。" ] }` |
| login | Bất thường | Check format | email | Khác format email | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスを正しく入力してください。" ] }` |
| login | Bất thường | Check size | email | > 255 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスは「255」文字以下で入力してください。（現在256文字）" ] }` |
| login | Bất thường | Response phải đúng (loginFailure) | Tổng thể | email + password | [customer].[deleted_date] != NULL | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| login | Bất thường | Response phải đúng (loginFailure) | Tổng thể | email + password sai | password không khớp | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| login | Bất thường | Response phải đúng (loginFailure) | Tổng thể | email không tồn tại | không tồn tại customer thỏa điều kiện | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| login | Bất thường | Response phải đúng (loginFailure) | Tổng thể | email | tồn tại nhiều customer thỏa điều kiện | **Status: 400 Bad Request**<br>`{ "errors": [ "メールアドレスまたは会員IDが間違っています。" ] }` |
| login | Bình thường | Response phải đúng (thành công) | Tổng thể | email + password | customer tồn tại, deleted_date = NULL, password khớp | **Status: 200 OK**<br>`{ "id": "1", "email": "example@email.com", "name": "ABC", "started_date": "2025/06/30", "position_id": "0", "created_date": "2025/06/30", "updated_date": "2025/06/30", "token": { "accessToken": "abcd..." } }` |
| login | Bình thường | Chi tiết response là chính xác | id | -- | Response 200 OK | customer.id |
| login | Bình thường | Chi tiết response là chính xác | email | -- | Response 200 OK | customer.email |
| login | Bình thường | Chi tiết response là chính xác | name | -- | Response 200 OK | customer.name |
| login | Bình thường | Chi tiết response là chính xác | started_date | -- | Response 200 OK | customer.started_date (định dạng yyyy/mm/dd) |
| login | Bình thường | Chi tiết response là chính xác | position_id | -- | Response 200 OK | customer.position_id |
| login | Bình thường | Chi tiết response là chính xác | created_date | -- | Response 200 OK | customer.created_date (định dạng yyyy/mm/dd) |
| login | Bình thường | Chi tiết response là chính xác | updated_date | -- | Response 200 OK | customer.updated_date (định dạng yyyy/mm/dd) |
| login | Bình thường | Chi tiết response là chính xác | token | -- | Response 200 OK | object chứa accessToken |
| login | Bình thường | Chi tiết response là chính xác | token.accessToken | -- | Response 200 OK | accessToken value |
