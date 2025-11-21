

## customerUpdate [/v1/customer/:id]

### customerUpdate [PUT]

#### Khái quát xử lý

* UPDATE thông tin [id] được chỉ định 
* Trường hợp không tồn tại record tương ứng trong bảng customer hoặc record customer đã bị xóa (deleted_date is NOT NULL), trả lỗi 404 
* Trường hợp position_id của login user != 0 AND customer.id của login user != Parameters.id, trả lỗi 404 
* Trường hợp không gửi Parameters.password, không update customer.password 
* Trường hợp gửi Parameters.password AND giá trị gửi = NULL, trả lỗi requiredError 
* Trường hợp gửi Parameters.password AND giá trị gửi != NULL, update customer.password 

+ Parameters
    + id: (string,required) - id
    + name: `ABC` (string,required) - 顧客名
    + email: `email@example.com` (string,required) - メールアドレス
    + position_id: `1` (string,required) - 役職
    + started_date: `2025/06/30` (string,required) - 会員登録日
    + password: `1` (string,optional) - パスワード

+ Response 200 (application/json)
    + Attributes (object)
        + id: `1` (string, required) - ID
