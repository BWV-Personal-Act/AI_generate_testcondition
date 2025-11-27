# 📋 Test Cases API Chi Tiết

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| customerUpdate | Bình thường | URL phải đúng | URL | -- | -- | `PUT /v1/customer/:id` |
| customerUpdate | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "message": "Unauthorized" }` |
| customerUpdate | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag của login user != 0,1,2 | **Status: 403 Forbidden**<br>`{ "message": "権限がないURLです" }` |
| customerUpdate | Bất thường | Response phải đúng | Tổng thể | có truyền parameter.id | không có record nào thỏa customer.id = parameter.id | **Status: 404 Not Found**<br>`{ "message": "Not Found: customer.id = [parameter.id]." }` |
| customerUpdate | Bất thường | Check required | name | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名は必須です。" ] }` |
| customerUpdate | Bất thường | Check required | name | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名は必須です。" ] }` |
| customerUpdate | Bất thường | Check required | kana | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは必須です。" ] }` |
| customerUpdate | Bất thường | Check required | kana | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは必須です。" ] }` |
| customerUpdate | Bất thường | Check required | title | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "敬称は必須です。" ] }` |
| customerUpdate | Bất thường | Check required | title | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "敬称は必須です。" ] }` |
| customerUpdate | Bất thường | Check required | staffId | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは必須です。" ] }` |
| customerUpdate | Bất thường | Check required | staffId | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは必須です。" ] }` |
| customerUpdate | Bất thường | Check required | billingStaffName | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者名は必須です。" ] }` |
| customerUpdate | Bất thường | Check required | billingStaffName | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者名は必須です。" ] }` |
| customerUpdate | Bất thường | Check format | class | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "分類は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | title | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "敬称は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | staffId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceCustomerId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求グループIDは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | zip | Khác format xxx-xxxx | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な郵便番号を入力してください" ] }` |
| customerUpdate | Bất thường | Check format | vendorTypeId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "業者区分IDは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | collectMethod | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "回収方法は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | collectClosingDate | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "回収締日は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | collectDate1 | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "回収サイトは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | collectDate2 | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "回収日は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | salesFee | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "販売手数料は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | fee | Khác decimal(5,2) | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "手数料は数値と\".\"のみ入力可能です。", "手数料は小数点前5桁、小数点以下2桁で入力してください。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceNotation | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書表記は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | paymentMethod | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "支払方法は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | paymentClosingDate | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "支払締日は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | paymentDate1 | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "支払サイトは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | paymentDate2 | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "支払日は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書発行区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | deliveryType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "納品書発行区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | receiptType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "領収書発行区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | deliveryAmountType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "納品書金額表示区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceFormat | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書フォーマットは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceNotationType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書表記は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | invoiceTitle | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書発行区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | taxType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "税区分は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | fraction | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "端数処理は数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check format | presidentEmail | khác format email | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効なEメールアドレスを入力してください。" ] }` |
| customerUpdate | Bất thường | Check format | billingStaffEmail | khác format email | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効なEメールアドレスを入力してください。" ] }` |
| customerCreate | Bất thường | Check format | kana | Khác format kana | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは全角カタカナのみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check format | tel | khác số và "-" | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは全角カタカナのみ入力可能です。", "電話番号は数値と\"-\"のみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check format | fax | khác số và "-" | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは全角カタカナのみ入力可能です。", "FAXは数値と\"-\"のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check size | code | > 10 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "取引先コードは10文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | name | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名は100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | kana | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名カナは100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | nameAbbreviation | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客名略称は100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | zip | > 8 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "郵便番号は8文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | prefectural | > 50 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "都道府県は50文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | address | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "住所は100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | buildingName | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "建物名は100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | tel | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "電話番号は20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | fax | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "FAXは20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | invoiceRegistrationNumber | > 14 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "T番号は14文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | hpUrl | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "URLは100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | presidentName | > 50 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代表者名は50文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | presidentTel | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代表者電話番号は20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | presidentEmail | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代表者メールアドレスは100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | billingStaffName | > 50 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者名は50文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | billingStaffTel | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者電話番号は20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | billingStaffEmail | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者メールアドレスは100文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | billingSectionName | > 50 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求先担当者部署は50文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | otherCollectMethod | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "その他回収方法は20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | bankAccount | > 50 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "振込名義人は50文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | paymentComment | > 3000 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "支払備考は3000文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | otherPaymentMethod | > 20 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "その他支払方法は20文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check size | comment | > 3000 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "備考は3000文字以内で入力してください。" ] }` |
| customerUpdate | Bất thường | Check giá trị | class | Khác 1:顧客 2:得意先 3:外注先 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な分類を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | title | Khác 1:御中 2:様 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な敬称を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | collectMethod | Khác 1:振込 2:現金 3:その他 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な回収方法を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | collectClosingDate | Khác 1:月末 2:5日 3:10日 4:15日 5:20日 6:25日 7:随時締め | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な回収締日を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | collectDate1 | Khác 1:当月 2:翌月 3:翌々月 4:翌翌々月 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な回収サイトを入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | collectDate2 | Khác 1:月末 2:5日 3:10日 4:15日 5:20日 6:25日 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な回収日を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | salesFee | Khác 1:無 2:有 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な販売手数料を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceNotation | Khác 1:する 2*:しない | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書表記を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | paymentMethod | Khác 1:振込 2:現金 3:相殺 4:その他 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な支払方法を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | paymentClosingDate | Khác 1:月末 2:5日 3:10日 4:15日 5:20日 6:25日 7:随時締め | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な支払締日を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | paymentDate1 | Khác 1:当月 2:翌月 3:翌々月 4:翌翌々月 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な支払サイトを入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | paymentDate2 | Khác 1:月末 2:5日 3:10日 4:15日 5:20日 6:25日 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な支払日を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceType | Khác 1:する 2:しない | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書発行区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | deliveryType | Khác 1:する 2:しない | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な納品書発行区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | receiptType | Khác 1:する 2:しない | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な領収書発行区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | deliveryAmountType | Khác 1:する 2:しない | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な納品書金額表示区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceFormat | Khác 1:顧客 2:得意先 3:顧客・得意先 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書フォーマットを入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceNotationType | Khác 1:顧客 2:届先 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書表記を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceTitle | Khác 1:請求書 2:明細書 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書発行区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | taxType | Khác 1:内税 2:外税 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な税区分を入力してください" ] }` |
| customerUpdate | Bất thường | Check giá trị | fraction | Khác 1:切り捨て 2:四捨五入 3:切り上げ端数処理 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な端数処理を入力してください" ] }` |
| customerUpdate | Bình thường | Response phải đúng | Response | - | Không xảy ra lỗi bên trên | **Status: 204 NO CONTENT**<br>`{ "id": "customer.id vừa tạo" }` |
| customerUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | -- | Xử lý cập nhật phải được tiến hành đúng vào table customer<br>※Chi tiết tham chiếu test case bên dưới<br>(Các gía trị bên dưới lấy từ Request Parameter) |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | id | -- | -- | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | class | -- | parameter.class | parameter.class |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | class | - | parameter.class = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | code | -- | parameter.code | parameter.code |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | code | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | name | -- | parameter.name | parameter.name |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | kana | -- | parameter.kana | parameter.kana |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | title | -- | parameter.title | parameter.title |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | title | - | parameter.title = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | nameAbbreviation | -- | parameter.nameAbbreviation | parameter.nameAbbreviation |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | nameAbbreviation | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | staffId | -- | parameter.staffId | parameter.staffId |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceCustomerId | -- | parameter.invoiceCustomerId | parameter.invoiceCustomerId |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceCustomerId | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | zip | -- | parameter.zip | parameter.zip |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | zip | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | prefectural | -- | parameter.prefectural | parameter.prefectural |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | prefectural | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | address | -- | parameter.address | parameter.address |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | address | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | buildingName | -- | parameter.buildingName | parameter.buildingName |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | buildingName | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | tel | -- | parameter.tel | parameter.tel |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | tel | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fax | -- | parameter.fax | parameter.fax |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fax | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceRegistrationNumber | -- | parameter.invoiceRegistrationNumber | parameter.invoiceRegistrationNumber |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceRegistrationNumber | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | vendorTypeId | -- | parameter.vendorTypeId | parameter.vendorTypeId |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | vendorTypeId | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | hpUrl | -- | parameter.hpUrl | parameter.hpUrl |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | hpUrl | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentName | -- | parameter.presidentName | parameter.presidentName |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentName | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentTel | -- | parameter.presidentTel | parameter.presidentTel |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentTel | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentEmail | -- | parameter.presidentEmail | parameter.presidentEmail |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | presidentEmail | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingStaffName | -- | parameter.billingStaffName | parameter.billingStaffName |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingStaffTel | -- | parameter.billingStaffTel | parameter.billingStaffTel |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingStaffTel | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingStaffEmail | -- | parameter.billingStaffEmail | parameter.billingStaffEmail |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingStaffEmail | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingSectionName | -- | parameter.billingSectionName | parameter.billingSectionName |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | billingSectionName | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectMethod | -- | parameter.collectMethod | parameter.collectMethod |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectMethod | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | otherCollectMethod | -- | parameter.otherCollectMethod | parameter.otherCollectMethod |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | otherCollectMethod | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectClosingDate | -- | parameter.collectClosingDate | parameter.collectClosingDate |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectClosingDate | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectDate1 | -- | parameter.collectDate1 | parameter.collectDate1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectDate1 | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectDate2 | -- | parameter.collectDate2 | parameter.collectDate2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | collectDate2 | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | bankAccount | -- | parameter.bankAccount | parameter.bankAccount |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | bankAccount | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | salesFee | -- | parameter.salesFee | parameter.salesFee |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | salesFee | - | parameter.salesFee = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | salesFee | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fee | - | parameter.fee | parameter.fee |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fee | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceNotation | -- | parameter.invoiceNotation | parameter.invoiceNotation |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceNotation | - | parameter.invoiceNotation = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceNotation | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentComment | -- | parameter.paymentComment | parameter.paymentComment |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentComment | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentMethod | -- | parameter.paymentMethod | parameter.paymentMethod |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentMethod | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | otherPaymentMethod | -- | parameter.otherPaymentMethod | parameter.otherPaymentMethod |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | otherPaymentMethod | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentClosingDate | -- | parameter.paymentClosingDate | parameter.paymentClosingDate |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentClosingDate | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentDate1 | -- | parameter.paymentDate1 | parameter.paymentDate1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentDate1 | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentDate2 | -- | parameter.paymentDate2 | parameter.paymentDate2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | paymentDate2 | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceType | -- | parameter.invoiceType | parameter.invoiceType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceType | - | parameter.invoiceType = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryType | -- | parameter.deliveryType | parameter.deliveryType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryType | - | parameter.deliveryType = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | receiptType | -- | parameter.receiptType | parameter.receiptType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | receiptType | - | parameter.receiptType = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | receiptType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryAmountType | -- | parameter.deliveryAmountType | parameter.deliveryAmountType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryAmountType | - | parameter.deliveryAmountType = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | deliveryAmountType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceFormat | -- | parameter.invoiceFormat | parameter.invoiceFormat |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceFormat | - | parameter.invoiceFormat = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceFormat | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceNotationType | -- | parameter.invoiceNotationType | parameter.invoiceNotationType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceNotationType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceTitle | -- | parameter.invoiceTitle | parameter.invoiceTitle |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceTitle | - | parameter.invoiceTitle = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | invoiceTitle | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | taxType | -- | parameter.taxType | parameter.taxType |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | taxType | - | parameter.taxType = null | 2 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | taxType | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fraction | -- | parameter.fraction | parameter.fraction |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fraction | - | parameter.fraction = null | 1 |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | fraction | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | comment | -- | parameter.comment | parameter.comment |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | comment | không gửi | - | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | disableFlag | -- | -- | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | createdAt | -- | -- | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | createdBy | -- | -- | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | createdUserName | -- | -- | Không đổi |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | updatedAt | -- | -- | system datetime |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | updatedBy | -- | -- | user.id của login user |
| Bảng customer | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | -- | -- | user.name của login user |
| customerUpdate | Bất thường | Check format | invoiceTitle | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "請求書タイトルは数値のみ入力可能です。" ] }` |
| customerUpdate | Bất thường | Check giá trị | invoiceTitle | Khác 1:請求書 2:明細書 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な請求書タイトルを入力してください" ] }` |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | name | -- | -- | 取引先名 |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | kana | -- | -- | 取引先名カナ |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | title | -- | -- | 敬称区分 |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | nameAbbreviation | -- | -- | 取引先略称 |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | invoiceNotationType | -- | -- | 請求書表記区分 |
| customerUpdate | Bình thường | Tên hạng mục phải đúng | comment | -- | -- | 取引先備考 |
| customerCreate | Bất thường | Check format | kana | Khác format katakana 1 byte | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "取引先名カナは半角カタカナのみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check format | invoiceRegistrationNumber | Khác "T"và giá trị số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "T番号は数値と\"T\"のみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check format | presidentTel | Khác số và "-" | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代表者電話番号は数値と\"-\"のみ入力可能です。" ] }` |
| customerCreate | Bất thường | Check format | invoiceNotationType | Khác số | - | Không hiện lỗi (Có thể nhập nhiều option ngăn cách nhau bởi dấu ",") |
| customerUpdate | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag của login user != 0,1 | **Status: 403 Forbidden**<br>`{ "message": "権限がないURLです" }` |
| customerSearch | Bình thường | Response phải đúng | Response | Điều kiện có kết quả search | Số record tương ứng > 0 | Status: 200 OK <br> `[ {Tham chiếu bên dưới} ]` <br> ※Chi tiết tham chiếu test case bên dưới |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | type | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | careType | - | - | customer.kana |
| Bảng customerType | Bình thường | Chi tiết response là chính xác | customerType | - | Record customerType có customerType.id = customer.customerTypeId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerType | Bình thường | Chi tiết response là chính xác | id | - | - | customerType.id |
| Bảng customerType | Bình thường | Chi tiết response là chính xác | name | - | - | customerType.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | etcFlag | - | - | customerType.etcFlag |
| Bảng customer | Bình thường | Chi tiết response là chính xác | customerTypeText | - | - | customer.customerTypeText |
| Bảng customer | Bình thường | Chi tiết response là chính xác | approvalStaff | - | Record staff có staff.id = customer.approvalStaffId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng staff | Bình thường | Chi tiết response là chính xác | id | - | - | staff.id |
| Bảng staff | Bình thường | Chi tiết response là chính xác | name | - | - | staff.name |
| Bảng agency | Bình thường | Chi tiết response là chính xác | agency | - | Record agency có agency.id = customer.agencyId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng agency | Bình thường | Chi tiết response là chính xác | id | - | - | agency.id |
| Bảng agency | Bình thường | Chi tiết response là chính xác | name | - | - | agency.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kana | - | - | customer.kana |
| Bảng customer | Bình thường | Chi tiết response là chính xác | salesStaff | - | Record staff có staff.id = customer.salesStaffId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng staff | Bình thường | Chi tiết response là chính xác | id | - | - | staff.id |
| Bảng staff | Bình thường | Chi tiết response là chính xác | name | - | - | staff.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | nameAcronym | - | - | customer.nameAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kanaAcronym | - | - | customer.kanaAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | zip | - | - | customer.zip |
| Bảng customer | Bình thường | Chi tiết response là chính xác | prefectural | - | - | customer.prefectural |
| Bảng customer | Bình thường | Chi tiết response là chính xác | address | - | - | customer.address |
| Bảng customer | Bình thường | Chi tiết response là chính xác | buildingName | - | - | customer.buildingName |
| Bảng customer | Bình thường | Chi tiết response là chính xác | tel | - | - | customer.tel |
| Bảng customer | Bình thường | Chi tiết response là chính xác | fax | - | - | customer.fax |
| Bảng customer | Bình thường | Chi tiết response là chính xác | email | - | - | customer.email |
| Bảng customer | Bình thường | Chi tiết response là chính xác | startDate | - | - | customer.startDate |
| Bảng customer | Bình thường | Chi tiết response là chính xác | taxType | - | - | customer.taxType |
| Bảng customer | Bình thường | Chi tiết response là chính xác | salesAmountType | - | - | customer.salesAmountType |
| Bảng customer | Bình thường | Chi tiết response là chính xác | closingDate | - | - | customer.closingDate |
| Bảng customer | Bình thường | Chi tiết response là chính xác | paymentDate1 | - | - | customer.paymentDate1 |
| Bảng customer | Bình thường | Chi tiết response là chính xác | paymentDate2 | - | - | customer.paymentDate2 |
| Bảng customer | Bình thường | Chi tiết response là chính xác | fee | - | - | customer.fee |
| Bảng customer | Bình thường | Chi tiết response là chính xác | receiveType | - | - | customer.receiveType |
| Bảng customer | Bình thường | Chi tiết response là chính xác | invoicePrintType | - | - | customer.invoicePrintType |
| Bảng customer | Bình thường | Chi tiết response là chính xác | invoiceType | - | - | customer.invoiceType |
| Bảng customer | Bình thường | Chi tiết response là chính xác | receiveCustomer | - | Record customer có id = customer.receiveCustomerId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kana | - | - | customer.kana |
| Bảng customer | Bình thường | Chi tiết response là chính xác | nameAcronym | - | - | customer.nameAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kanaAcronym | - | - | customer.kanaAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | aggregateCustomer | - | Record customer có id = customer.aggregateCustomerId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kana | - | - | customer.kana |
| Bảng customer | Bình thường | Chi tiết response là chính xác | nameAcronym | - | - | customer.nameAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kanaAcronym | - | - | customer.kanaAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | invoiceCustomer | - | Record customer có id = customer.invoiceCustomerId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kana | - | - | customer.kana |
| Bảng customer | Bình thường | Chi tiết response là chính xác | nameAcronym | - | - | customer.nameAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kanaAcronym | - | - | customer.kanaAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | bankAccount | - | - | customer.bankAccount |
| Bảng customer | Bình thường | Chi tiết response là chính xác | comment | - | - | customer.comment |
| Bảng customer | Bình thường | Chi tiết response là chính xác | rakurakuCode | - | - | customer.rakurakuCode |
| Bảng customer | Bình thường | Chi tiết response là chính xác | disableFlag | - | - | customer.disableFlag |
| Bảng customer | Bình thường | Chi tiết response là chính xác | approvalFlag | - | - | customer.approvalFlag |
| Bảng customer | Bình thường | Chi tiết response là chính xác | createdAt | - | - | customer.createdAt |
| Bảng customer | Bình thường | Chi tiết response là chính xác | createdBy | - | - | customer.createdBy |
| Bảng customer | Bình thường | Chi tiết response là chính xác | createdUserName | - | - | customer.createdUserName |
| Bảng customer | Bình thường | Chi tiết response là chính xác | updatedAt | - | - | customer.updatedAt |
| Bảng customer | Bình thường | Chi tiết response là chính xác | updatedBy | - | - | customer.updatedBy |
| Bảng customer | Bình thường | Chi tiết response là chính xác | updatedUserName | - | - | customer.updatedUserName |
| projectSearch | Bình thường | Xác nhận kết quả search có đúng không khi không nhập gì | Response | - | - | Trả về tất cả record project |
| projectSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | - | - | [Response].[deliveryDate] DESC |
| projectSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | [Response].[deliveryDate] trùng nhau | - | [Response].[id] DESC |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | orderDateFrom | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.orderDate >= Request parameter:orderDateFrom |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | orderDateFrom | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | orderDateTo | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.orderDate <= Request parameter:orderDateTo |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | orderDateTo | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | deliveryDateFrom | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.deliveryDate >= Request parameter:deliveryDateFrom |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | deliveryDateFrom | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | deliveryDateTo | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.deliveryDate <= Request parameter:deliveryDateTo |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | deliveryDateTo | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | projectDetail | =1 | Optional parameters khác để trống | Trả về các record project có projectDetail.length > 0 |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | projectDetail | != 1 OR Ko nhập | Optional parameters khác để trống | Trả về tất cả record project |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | salesStaffId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.salesStaffId = Request parameter: salesStaffId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | salesStaffId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | customerId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.customerId = Request parameter: customerId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | customerId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | deliveryStaffType | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.invoiceprojectId = Request parameter: deliveryStaffType |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | deliveryStaffType | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | staffId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record project có project.staffId = Request parameter: staffId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | staffId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | agencyId | - | - | Trả về các record project có project.agencyId = Request parameter: agencyId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | agencyId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | agencyStaffId | - | - | Trả về các record project có project.agencyStaffId = Request parameter: agencyStaffId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | agencyStaffId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | supplierId | - | - | Trả về các record project có project.supplierId = Request parameter: supplierId |
| projectSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | supplierId | - | - | Search giống toàn bộ |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | limit | >=0 | Optional parameters khác để trống | Trả về Request parameter.limit record đầu tiên |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | offset | >=1 | Optional parameters khác để trống | Trả về từ record có thứ tự từ Request parameter: offset + 1 |
| projectSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | agency | - | login user.userFlag = 11 OR 12 | Trả về record project có project.agencyId = login user.agencyId |
| projectSearch | Bình thường | Xử lý search "and" hoặc "or" phải được thực hiện đúng. | deliveryStaffType | - | Nhập 2 option trở lên | Search "or" |
| projectSearch | Bình thường | Xử lý search "and" hoặc "or" phải được thực hiện đúng. | Giữa parameter với parameter | - | - | Search "and" |
| projectSearch | Bình thường | Kết quả search là 0 record phải xử lý đúng | Response | Điều kiện không có kết quả search | Số record tương ứng = 0 | **Status: 200 OK**<br>`[]` |