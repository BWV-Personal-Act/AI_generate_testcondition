# Group auth

## login [/v1/login]

### login [POST]

#### Khái quát

Login bằng email,password đã nhận, phát hành token

#### Xử lý

* Nếu thông tin customer đã nhận trùng khớp thì phát hành TOKEN.
* Trả lỗi message [loginFailure] trong trường hợp dưới đây : 
　　　Trường hợp [customer].[deleted_date] != NULL
　　　Trường hợp không khớp password
　　　Trường hợp không tồn tại hoặc tồn tại nhiều [customer] thỏa điều kiện

+ Parameters
    + email: `example@mail.com` (string, optional) - メールアドレス
    + password: `passwordAbc` (string, required) - パスワード

+ Response 200 (application/json)
    + Attributes (object)
        + id: `1` (string, required) - 顧客ID
        + email: `example@email.com` (string, required) - メールアドレス
        + name: `ABC` (string, required) - 顧客名
        + started_date: `2025/06/30` (string, required) - 会員登録日		
        + position_id: `0` (string, required) - 役職
        + created_date: `2025/06/30` (string, required) - 登録日
        + updated_date: `2025/06/30` (string, required) - 更新日
        + token: (object) - トークン
            + accessToken: `abcd...` (string, required) - アクセストークン