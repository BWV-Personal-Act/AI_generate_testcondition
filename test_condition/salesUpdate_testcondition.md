| Chức năng test | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất |
|---|---|---|---|---|---|---|
| salesUpdate | Bình thường | URL phải đúng | URL | - | - | PUT /v1/sales/:id |
| salesUpdate | Bất thường | Check chứng thực | Tổng thể | - | - | Status: 401 Unauthorized <br> `{ "errors": [ "認証エラー" ] }` |
| salesUpdate | Bất thường | Check required | id | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "idは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDate | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDate | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | paymentDueDate | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | paymentDueDate | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | invoiceType | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | invoiceType | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].customerItemId | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].customerItemId | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].quantity | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].quantity | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].unitPrice | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].unitPrice | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].amount | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].amount | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].sort | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは必須です。" ] }` |
| salesUpdate | Bất thường | Check required | salesDetail[i].sort | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは必須です。" ] }` |
| salesUpdate | Bất thường | Check format | id | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "idは数値で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDate | Khác format date | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは日付を正しく入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | paymentDueDate | Khác format date | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは日付を正しく入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | invoiceType | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは数値で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].customerItemId | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは数値で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].quantity | Khác số hoặc không phải decimal(10,2) | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].unitPrice | Khác số hoặc không phải decimal(10,2) | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].amount | Khác số hoặc > bigint | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは正しい形式で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].taxRateId | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "taxRateIdは数値で入力してください。" ] }` |
| salesUpdate | Bất thường | Check format | salesDetail[i].sort | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは数値で入力してください。" ] }` |
| salesUpdate | Bất thường | Check size | comment | > 3000 ký tự | - | Status: 400 Bad Request <br> `{ "errors": [ "commentは「3000」文字以下で入力してください。（現在{Số ký tự hiện tại}文字）" ] }` |
| salesUpdate | Bất thường | Check size | salesDetail[i].comment | > 300 ký tự | - | Status: 400 Bad Request <br> `{ "errors": [ "commentは「300」文字以下で入力してください。（現在{Số ký tự hiện tại}文字）" ] }` |
| salesUpdate | Bất thường | Check tồn tại | id | Không tồn tại trong DB hoặc deletedAt != NULL | - | Status: 400 Bad Request <br> `{ "errors": [ "該当するidがありません。" ] }` |
| salesUpdate | Bất thường | Check tồn tại | salesDetail[i].customerItemId | Không tồn tại trong DB hoặc deletedAt != NULL | - | Status: 400 Bad Request <br> `{ "errors": [ "該当するcustomerItemIdがありません。" ] }` |
| salesUpdate | Bất thường | Check tồn tại | salesDetail[i].taxRateId | Không tồn tại trong DB hoặc deletedAt != NULL | [Params].salesDetail[i].taxRateId được gửi | Status: 400 Bad Request <br> `{ "errors": [ "該当するtaxRateIdがありません。" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].id.projectId.customerId != [Params].salesDetail[i].customerItemId.customerId | - | Status: 500 Internal Server Error <br> `{ "errors": [ "ERROR" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].id.lockFlag = 1:Yes | - | Status: 400 Bad Request <br> `{ "errors": [ "salesLockError" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | Tồn tại dù chỉ 1 record [Params].salesDetail[i].customerItemId.type = 5:回収のみ | - | Status: 400 Bad Request <br> `{ "errors": [ "salesProjectItemTypeError" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].salesDetail[i].id != NULL <br> AND [Params].salesDetail[i].customerItemId (trước khi thay đổi) != [Params].salesDetail[i].customerItemId | - | Status: 400 Bad Request <br> `{ "errors": [ "salesUpdateCustomerItemError" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].salesDate là tháng quá khứ so với closingMonth.date <br> OR <br> [salesDate] (trước khi cập nhật) đã là tháng quá khứ so với closingMonth.date | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateError" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> Không tồn tại record customerItem có [Params].salesDetail[i].customerItemId.customerId AND [Params].salesDetail[i].customerItemId.itemId AND type = 2:レンタル | - | Status: 400 Bad Request <br> `{ "errors": [ "notRegisteredRentalItemError" ] }` |
| salesUpdate | Bất thường | Response phải đúng | Response | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> Tồn tại nhiều record customerItem có [Params].salesDetail[i].customerItemId.customerId AND [Params].salesDetail[i].customerItemId.itemId AND type = 2:レンタル | - | Status: 500 Internal Server Error <br> `{ "errors": [ "ERROR" ] }` |
| salesUpdate | Bình thường | Response phải đúng | Response | - | Không xảy ra lỗi bên trên | Status: 204 No Content |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý lưu DB | - | - | Xử lý cập nhật phải được tiến hành đúng vào table sales <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | id | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | projectId | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | salesDate | - | - | [Params].salesDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | paymentDueDate | - | - | [Params].paymentDueDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | invoiceType | - | - | [Params].invoiceType |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | comment | - | - | [Params].comment |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | amount | - | - | Tổng số tiền của [Params].salesDetail[i].amount |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | totalAmount | - | - | amount + Tổng số tiền của salesTaxRate.tax được tính từ [Params].salesDetail[i].taxRateId |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | lockFlag | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdAt | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdBy | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdUserName | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedAt | - | - | System datetime (JST) |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedBy | - | - | user.id của login user |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | - | - | user.userName của login user |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý lưu DB | - | - | Xử lý cập nhật/thêm/xóa phải được tiến hành đúng vào table salesDetail <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Xử lý thêm record phải được tiến hành đúng | salesDetail[i].id = NULL | - | Thêm record mới (INSERT) | Bảng salesDetail được thêm record <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | id | - | INSERT mới | auto increment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | salesId | - | INSERT mới | sales.id |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | - | INSERT mới | [Params].salesDetail[i].transactionDate |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | - | INSERT mới | [Params].salesDetail[i].customerItemId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | - | INSERT mới | [Params].salesDetail[i].quantity |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unit | - | INSERT mới | [Params].salesDetail[i].customerItemId.itemId.unit |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | - | INSERT mới | [Params].salesDetail[i].unitPrice |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | amount | - | INSERT mới | [Params].salesDetail[i].amount |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | - | INSERT mới | [Params].salesDetail[i].taxRateId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | comment | - | INSERT mới | [Params].salesDetail[i].comment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | sort | - | INSERT mới | [Params].salesDetail[i].sort |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailId | - | INSERT mới | projectDetail.id có projectDetail.customerItemId = [Params].salesDetail[i].customerItemId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailCreatedType | - | INSERT mới <br> [Params].salesDetail[i].customerItemId.type = 2:レンタル | 1:納品 |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailCreatedType | - | INSERT mới <br> [Params].salesDetail[i].customerItemId.type = 4:紛失 | 2:紛失 |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdAt | - | INSERT mới | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdBy | - | INSERT mới | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdUserName | - | INSERT mới | user.userName của login user |
| Bảng salesDetail | Bình thường | Xử lý cập nhật record phải được tiến hành đúng | salesDetail[i].id != NULL | - | Cập nhật record tồn tại (UPDATE) | Bảng salesDetail được cập nhật <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | id | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | salesId | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | - | UPDATE | [Params].salesDetail[i].transactionDate |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | - | UPDATE | [Params].salesDetail[i].quantity |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unit | - | UPDATE | [Params].salesDetail[i].customerItemId.itemId.unit |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | - | UPDATE | [Params].salesDetail[i].unitPrice |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | amount | - | UPDATE | [Params].salesDetail[i].amount |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | - | UPDATE | [Params].salesDetail[i].taxRateId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | comment | - | UPDATE | [Params].salesDetail[i].comment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | sort | - | UPDATE | [Params].salesDetail[i].sort |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailId | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailCreatedType | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdAt | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdBy | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdUserName | - | UPDATE | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedAt | - | UPDATE | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedBy | - | UPDATE | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | - | UPDATE | user.userName của login user |
| Bảng salesDetail | Bình thường | Xử lý xóa record phải được tiến hành đúng | salesDetail[i].id được get | - | Xóa record tồn tại (DELETE) | Bảng salesDetail được xóa record tương ứng |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý DELETE salesTaxRate | - | - | Xử lý xóa phải được tiến hành đúng trong table salesTaxRate <br> (Xóa tất cả record ràng buộc với salesId) |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý INSERT salesTaxRate | - | - | Xử lý thêm phải được tiến hành đúng trong table salesTaxRate <br> (Thêm các record mới dựa trên grouping [Params].salesDetail[i].taxRateId) |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [Params].salesDetail[i].customerItemId.type = 2:レンタル <br> AND <br> [Params].salesDetail[i].id = NULL (INSERT mới) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 2 <br> [Params].salesDetail[i].id = NULL (INSERT) | [Params].salesDetail[i].customerItemId.lendingTotalNumber + [Params].salesDetail[i].quantity |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> AND <br> [Params].salesDetail[i].id = NULL (INSERT mới) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 4 <br> [Params].salesDetail[i].id = NULL (INSERT) | [customerItemId.lendingTotalNumber được get] - [Params].salesDetail[i].quantity |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [Params].salesDetail[i].customerItemId.type = 2:レンタル <br> AND <br> [Params].salesDetail[i].id != NULL (UPDATE) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 2 <br> [Params].salesDetail[i].id != NULL (UPDATE) | [Params].salesDetail[i].customerItemId.lendingTotalNumber - [salesDetail.quantity (trước UPDATE)] + [Params].salesDetail[i].quantity |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> AND <br> [Params].salesDetail[i].id != NULL (UPDATE) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 4 <br> [Params].salesDetail[i].id != NULL (UPDATE) | [customerItemId.lendingTotalNumber được get] + [salesDetail.quantity (trước UPDATE)] - [Params].salesDetail[i].quantity |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [salesDetail.id được get].[customerItemId].[type] = 2:レンタル <br> AND <br> [salesDetail.id được get] không tồn tại trong [Params].id (DELETE) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | Xóa record có type = 2 | [salesDetail.customerItemId.lendingTotalNumber (đối tượng xóa)] - [salesDetail.quantity (đối tượng xóa)] |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý cập nhật customerItem | - | [salesDetail.id được get].[customerItemId].[type] = 4:紛失 <br> AND <br> [salesDetail.id được get] không tồn tại trong [Params].id (DELETE) | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | Xóa record có type = 4 | [customerItemId.lendingTotalNumber được get] + [salesDetail.quantity (đối tượng xóa)] |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý INSERT salesVersion | - | - | Xử lý thêm phải được tiến hành đúng trong table salesVersion <br> (Lưu thông tin trước khi cập nhật) |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý INSERT salesVersionDetail | - | - | Xử lý thêm phải được tiến hành đúng trong table salesVersionDetail <br> (Lưu thông tin chi tiết trước khi cập nhật) |
| salesUpdate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý INSERT salesVersionTaxRate | - | - | Xử lý thêm phải được tiến hành đúng trong table salesVersionTaxRate <br> (Lưu thông tin thuế trước khi cập nhật) |
