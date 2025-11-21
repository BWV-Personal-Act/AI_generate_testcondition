

# Group customer

## customerCreate [/v1/customer]

### customerCreate [POST]

#### Khái quát xử lý 

* INSERT record mới theo thông tin đã nhận 
* Trường hợp position_id của login user != 0, trả lỗi 403

+ Parameters
    + name: `ABC` (string,required) - 顧客名
    + email: `email@example.com` (string,required) - メールアドレス
    + position_id: `1` (string,optional) - 役職
    + started_date: `2025/06/30` (string,required) - 会員登録日
    + password: `1` (string,required) - パスワード

+ Response 201 (application/json)
    + Attributes (object)
        + id: 1 (string,required) - id
