# 📋 Test Cases API Chi Tiết - salesUpdate

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
|:-----------------|:---|:---|:---|:---|:---|:---|
| salesUpdate | Bình thường | URL phải đúng | URL | -- | -- | `PUT /v1/sales/:id` |
| salesUpdate | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| salesUpdate | Bất thường | Check quyền hạn | Quyền hạn | -- | user.userFlag NOT IN (1, 2) | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Tổng thể | Có truyền parameter.id | Không tồn tại record nào thỏa sales.id = parameter.id | **Status: 404 Not Found**<br>`{ "errors": [ "Not Found URL" ] }` |
| salesUpdate | Bất thường | Check required | id | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "idは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | id | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "idは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDate | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "売上日は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDate | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "売上日は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | paymentDueDate | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "入金期限日は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | paymentDueDate | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "入金期限日は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | invoiceType | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "請求書区分は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | invoiceType | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "請求書区分は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "売上明細は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "売上明細は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].customerItemId | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客商品IDは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].customerItemId | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客商品IDは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].quantity | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "数量は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].quantity | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "数量は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].unitPrice | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "単価は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].unitPrice | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "単価は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].amount | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "金額は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].amount | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "金額は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].sort | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "並び順は必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].sort | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "並び順は必須です。" ] }` |
| salesUpdate | Bất thường | Check format | id | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "idは数値のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | invoiceType | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "請求書区分は数値のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDate | Khác format YYYY-MM-DD | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "売上日は日付のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | paymentDueDate | Khác format YYYY-MM-DD | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "入金期限日は日付のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].customerItemId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客商品IDは数値のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].quantity | Nhập khác decimal(10,2) | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "数量は小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].unitPrice | Nhập khác decimal(10,2) | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "単価は小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].amount | Nhập khác số nguyên | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "金額は数値と\"-\"のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].taxRateId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "消費税率IDは数値のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].sort | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "並び順は数値のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].transactionDate | Khác format YYYY-MM-DD | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "取引日は日付のみ入力可能です。" ] }` |
| salesUpdate | Bất thường | Check size | comment | > 3000 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "備考は3000文字以内で入力してください。" ] }` |
| salesUpdate | Bất thường | Check size | salesDetail[i].comment | > 300 ký tự | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "備考は300文字以内で入力してください。" ] }` |
| salesUpdate | Bất thường | Check giá trị | invoiceType | Khác 1, 2 | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "有効な請求書区分を入力してください。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | lockFlag | -- | [Parameters].[id].[lockFlag] = 1 | **Status: 400 Bad Request**<br>`{ "errors": [ "売上ロック中のため更新できません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | type | -- | [Parameters].[salesDetail].[customerItemId].[type] = 5 (tồn tại dù 1 record) | **Status: 400 Bad Request**<br>`{ "errors": [ "回収のみは更新できません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | customerItemId | -- | [Parameters].[salesDetail].[id] != NULL AND [customerItemId trước cập nhật] != [Parameters].[salesDetail].[customerItemId] | **Status: 400 Bad Request**<br>`{ "errors": [ "商品を変更することはできません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | salesDate | -- | [Parameters].[salesDate] là tháng quá khứ so với [closingMonth].[date] OR [salesDate trước cập nhật] đã là tháng quá khứ | **Status: 400 Bad Request**<br>`{ "errors": [ "売上日が締め後のため更新できません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | customerId | -- | [Parameters].[id].[projectId].[customerId] != [Parameters].[salesDetail].[customerItemId].[customerId] | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客が一致しません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | -- | Trường hợp [Parameters].[salesDetail].[customerItemId].[type] = 4 AND không có record [customerItem] thỏa điều kiện | **Status: 400 Bad Request**<br>`{ "errors": [ "紛失の商品と同一のレンタル商品が登録されていません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | -- | Trường hợp [Parameters].[salesDetail].[customerItemId].[type] = 4 AND tồn tại nhiều record [customerItem] | **Status: 500 Internal Server Error**<br>`{ "errors": [ "ERROR" ] }` |
| salesUpdate | Bình thường | Response phải đúng | Response | -- | Không xảy ra lỗi bên trên | **Status: 204 No Content** |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | -- | Xử lý cập nhật phải được tiến hành đúng vào table sales<br>※Chi tiết tham chiếu test case bên dưới |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | id | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | projectId | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | salesDate | -- | [Params].salesDate | [Params].salesDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | paymentDueDate | -- | [Params].paymentDueDate | [Params].paymentDueDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | invoiceType | -- | [Params].invoiceType | [Params].invoiceType |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | comment | -- | [Params].comment | [Params].comment |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | amount | -- | -- | SUM([salesDetail].[amount]) |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | totalAmount | -- | -- | [amount] + SUM([salesTaxRate].[tax]) |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | lockFlag | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdAt | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdBy | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdUserName | -- | -- | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedAt | -- | -- | System datetime (JST) |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedBy | -- | -- | user.id của login user |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | -- | -- | user.userName của login user |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý salesDetail | -- | -- | Xử lý cập nhật/đăng ký/xóa phải được tiến hành đúng vào table salesDetail |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | Xử lý INSERT | Trường hợp [Parameters].[salesDetail].[id] = NULL | -- | Xử lý INSERT phải được tiến hành đúng vào table salesDetail |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | id | -- | INSERT case | auto increment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | salesId | -- | INSERT case | sales.id |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | -- | [Params].salesDetail[i].transactionDate | [Params].salesDetail[i].transactionDate |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | -- | [Params].salesDetail[i].customerItemId | [Params].salesDetail[i].customerItemId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | -- | [Params].salesDetail[i].quantity | [Params].salesDetail[i].quantity |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unit | -- | -- | [itemId].[unit] |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | -- | [Params].salesDetail[i].unitPrice | [Params].salesDetail[i].unitPrice |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | amount | -- | [Params].salesDetail[i].amount | [Params].salesDetail[i].amount |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | -- | [Params].salesDetail[i].taxRateId | [Params].salesDetail[i].taxRateId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | comment | -- | [Params].salesDetail[i].comment | [Params].salesDetail[i].comment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | sort | -- | [Params].salesDetail[i].sort | [Params].salesDetail[i].sort |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdAt | -- | INSERT case | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdBy | -- | INSERT case | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdUserName | -- | INSERT case | user.userName của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedAt | -- | INSERT case | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedBy | -- | INSERT case | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | -- | INSERT case | user.userName của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | Xử lý UPDATE | Trường hợp [Parameters].[salesDetail].[id] != NULL AND tồn tại trong [Parameters].[id] | -- | Xử lý UPDATE phải được tiến hành đúng vào table salesDetail |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | id | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | salesId | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | -- | [Params].salesDetail[i].transactionDate | [Params].salesDetail[i].transactionDate |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | -- | [Params].salesDetail[i].quantity | [Params].salesDetail[i].quantity |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unit | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | -- | [Params].salesDetail[i].unitPrice | [Params].salesDetail[i].unitPrice |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | amount | -- | [Params].salesDetail[i].amount | [Params].salesDetail[i].amount |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | -- | [Params].salesDetail[i].taxRateId | [Params].salesDetail[i].taxRateId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | comment | -- | [Params].salesDetail[i].comment | [Params].salesDetail[i].comment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | sort | -- | [Params].salesDetail[i].sort | [Params].salesDetail[i].sort |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdAt | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdBy | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdUserName | -- | UPDATE case | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedAt | -- | UPDATE case | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedBy | -- | UPDATE case | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | -- | UPDATE case | user.userName của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | Xử lý DELETE | Trường hợp [salesDetail].[id] không tồn tại trong [Parameters].[id] | -- | Xử lý DELETE phải được tiến hành đúng vào table salesDetail |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | deleted_date | -- | DELETE case | System datetime (JST) hoặc xóa vật lý record |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý customerItem | -- | Trường hợp [salesDetail].[customerItemId].[type] = 2:レンタル hoặc 4:紛失 | Xử lý cập nhật phải được tiến hành đúng vào table customerItem |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - INSERT | -- | [Parameters].[salesDetail].[customerItemId].[type] = 2:レンタル và INSERT | [lendingTotalNumber] + [quantity] |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - UPDATE | -- | [Parameters].[salesDetail].[customerItemId].[type] = 2:レンタル và UPDATE | [lendingTotalNumber] - [salesDetail.quantity trước] + [Parameters].[salesDetail].[quantity] |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - DELETE | -- | [salesDetail].[customerItemId].[type] = 2:レンタル và DELETE | [lendingTotalNumber] - [salesDetail.quantity đối tượng xóa] |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - INSERT LOSS | -- | [Parameters].[salesDetail].[customerItemId].[type] = 4:紛失 và INSERT | [lendingTotalNumber] - [quantity] |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - UPDATE LOSS | -- | [Parameters].[salesDetail].[customerItemId].[type] = 4:紛失 và UPDATE | [lendingTotalNumber] + [salesDetail.quantity trước] - [Parameters].[salesDetail].[quantity] |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber - DELETE LOSS | -- | [salesDetail].[customerItemId].[type] = 4:紛失 và DELETE | [lendingTotalNumber] + [salesDetail.quantity đối tượng xóa] |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý salesTaxRate DELETE | -- | -- | Xóa hết các record [salesTaxRate] ràng buộc với [Parameters].[id] |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý salesTaxRate INSERT | -- | -- | Xử lý INSERT phải được tiến hành đúng vào table salesTaxRate |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | tax | -- | Trường hợp nhiều salesDetail có cùng taxRateId, taxType = 1:切り上げ (từ customer.invoiceCustomerId.taxType) | ceil(SUM([salesDetail.amount theo taxRateId]) * [taxRate]%) |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | tax | -- | Trường hợp nhiều salesDetail có cùng taxRateId, taxType = 2:四捨五入 (từ customer.invoiceCustomerId.taxType) | round(SUM([salesDetail.amount theo taxRateId]) * [taxRate]%) |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | tax | -- | Trường hợp nhiều salesDetail có cùng taxRateId, taxType = 3:切り捨て (từ customer.invoiceCustomerId.taxType) | floor(SUM([salesDetail.amount theo taxRateId]) * [taxRate]%) |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | id | -- | INSERT case | auto increment |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | salesId | -- | INSERT case | sales.id |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | taxRateId | -- | INSERT case | taxRateId từ salesDetail |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | createdAt | -- | INSERT case | System datetime (JST) |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | createdBy | -- | INSERT case | user.id của login user |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | createdUserName | -- | INSERT case | user.userName của login user |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | updatedAt | -- | INSERT case | System datetime (JST) |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | updatedBy | -- | INSERT case | user.id của login user |
| Bảng salesTaxRate | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | -- | INSERT case | user.userName của login user |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý salesVersion | -- | -- | Xử lý INSERT thông tin trước khi cập nhật vào các bảng [salesVersion], [salesVersionDetail], [salesVersionTaxRate] |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | versionNo | -- | -- | [versionNo] + 1 từ [salesVersion] cũ (bao gồm cả salesDetail và salesTaxRate cũ) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | salesId | -- | -- | sales.id |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | salesDate | -- | -- | sales.salesDate (trước cập nhật) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | paymentDueDate | -- | -- | sales.paymentDueDate (trước cập nhật) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | invoiceType | -- | -- | sales.invoiceType (trước cập nhật) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | comment | -- | -- | sales.comment (trước cập nhật) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | amount | -- | -- | sales.amount (trước cập nhật) |
| Bảng salesVersion | Bình thường | Giá trị lưu DB phải đúng | totalAmount | -- | -- | sales.totalAmount (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | versionNo | -- | -- | [versionNo] + 1 từ [salesVersion] cũ |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | salesDetailId | -- | -- | salesDetail.id (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | -- | -- | salesDetail.transactionDate (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | -- | -- | salesDetail.customerItemId (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | -- | -- | salesDetail.quantity (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | unit | -- | -- | salesDetail.unit (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | -- | -- | salesDetail.unitPrice (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | amount | -- | -- | salesDetail.amount (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | -- | -- | salesDetail.taxRateId (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | comment | -- | -- | salesDetail.comment (trước cập nhật) |
| Bảng salesVersionDetail | Bình thường | Giá trị lưu DB phải đúng | sort | -- | -- | salesDetail.sort (trước cập nhật) |
| Bảng salesVersionTaxRate | Bình thường | Giá trị lưu DB phải đúng | versionNo | -- | -- | [versionNo] + 1 từ [salesVersion] cũ |
| Bảng salesVersionTaxRate | Bình thường | Giá trị lưu DB phải đúng | salesTaxRateId | -- | -- | salesTaxRate.id (trước cập nhật) |
| Bảng salesVersionTaxRate | Bình thường | Giá trị lưu DB phải đúng | taxRateId | -- | -- | salesTaxRate.taxRateId (trước cập nhật) |
| Bảng salesVersionTaxRate | Bình thường | Giá trị lưu DB phải đúng | tax | -- | -- | salesTaxRate.tax (trước cập nhật) |
