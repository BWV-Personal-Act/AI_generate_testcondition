| Chức năng test | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất |
|---|---|---|---|---|---|---|
| salesCreate | Bình thường | URL phải đúng | URL | - | - | POST /v1/sales |
| salesCreate | Bất thường | Check chứng thực | Tổng thể | - | - | Status: 401 Unauthorized <br> `{ "errors": [ "認証エラー" ] }` |
| salesCreate | Bất thường | Check required | projectId | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "projectIdは必須です。" ] }` |
| salesCreate | Bất thường | Check required | projectId | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "projectIdは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDate | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDate | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは必須です。" ] }` |
| salesCreate | Bất thường | Check required | paymentDueDate | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは必須です。" ] }` |
| salesCreate | Bất thường | Check required | paymentDueDate | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは必須です。" ] }` |
| salesCreate | Bất thường | Check required | invoiceType | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは必須です。" ] }` |
| salesCreate | Bất thường | Check required | invoiceType | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].customerItemId | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].customerItemId | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].quantity | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].quantity | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].unitPrice | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].unitPrice | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].amount | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].amount | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].sort | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは必須です。" ] }` |
| salesCreate | Bất thường | Check required | salesDetail[i].sort | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは必須です。" ] }` |
| salesCreate | Bất thường | Check format | projectId | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "projectIdは数値で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDate | Khác format date | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateは日付を正しく入力してください。" ] }` |
| salesCreate | Bất thường | Check format | paymentDueDate | Khác format date | - | Status: 400 Bad Request <br> `{ "errors": [ "paymentDueDateは日付を正しく入力してください。" ] }` |
| salesCreate | Bất thường | Check format | invoiceType | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "invoiceTypeは数値で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].customerItemId | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "customerItemIdは数値で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].quantity | Khác số hoặc không phải decimal(10,2) | - | Status: 400 Bad Request <br> `{ "errors": [ "quantityは小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].unitPrice | Khác số hoặc không phải decimal(10,2) | - | Status: 400 Bad Request <br> `{ "errors": [ "unitPriceは小数点前8桁、小数点以下2桁で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].amount | Khác số hoặc > bigint | - | Status: 400 Bad Request <br> `{ "errors": [ "amountは正しい形式で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].taxRateId | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "taxRateIdは数値で入力してください。" ] }` |
| salesCreate | Bất thường | Check format | salesDetail[i].sort | Khác số | - | Status: 400 Bad Request <br> `{ "errors": [ "sortは数値で入力してください。" ] }` |
| salesCreate | Bất thường | Check size | comment | > 3000 ký tự | - | Status: 400 Bad Request <br> `{ "errors": [ "commentは「3000」文字以下で入力してください。（現在{Số ký tự hiện tại}文字）" ] }` |
| salesCreate | Bất thường | Check size | salesDetail[i].comment | > 300 ký tự | - | Status: 400 Bad Request <br> `{ "errors": [ "commentは「300」文字以下で入力してください。（現在{Số ký tự hiện tại}文字）" ] }` |
| salesCreate | Bất thường | Check tồn tại | projectId | Không tồn tại trong DB hoặc deletedAt != NULL | - | Status: 400 Bad Request <br> `{ "errors": [ "該当するprojectIdがありません。" ] }` |
| salesCreate | Bất thường | Check tồn tại | salesDetail[i].customerItemId | Không tồn tại trong DB hoặc deletedAt != NULL | - | Status: 400 Bad Request <br> `{ "errors": [ "該当するcustomerItemIdがありません。" ] }` |
| salesCreate | Bất thường | Check tồn tại | salesDetail[i].taxRateId | Không tồn tại trong DB hoặc deletedAt != NULL | [Params].taxRateId được gửi | Status: 400 Bad Request <br> `{ "errors": [ "該当するtaxRateIdがありません。" ] }` |
| salesCreate | Bất thường | Response phải đúng | Response | [Params].projectId.customerId != [Params].salesDetail[i].customerItemId.customerId | - | Status: 500 Internal Server Error <br> `{ "errors": [ "ERROR" ] }` |
| salesCreate | Bất thường | Response phải đúng | Response | [Params].salesDate là tháng quá khứ so với closingMonth.date | - | Status: 400 Bad Request <br> `{ "errors": [ "salesDateError" ] }` |
| salesCreate | Bất thường | Response phải đúng | Response | Tồn tại dù chỉ 1 record [Params].salesDetail[i].customerItemId.type = 5:回収のみ | - | Status: 400 Bad Request <br> `{ "errors": [ "salesProjectItemTypeError" ] }` |
| salesCreate | Bất thường | Response phải đúng | Response | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> Không tồn tại record customerItem có [Params].salesDetail[i].customerItemId.customerId AND [Params].salesDetail[i].customerItemId.itemId AND type = 2:レンタル | - | Status: 400 Bad Request <br> `{ "errors": [ "notRegisteredRentalItemError" ] }` |
| salesCreate | Bất thường | Response phải đúng | Response | [Params].salesDetail[i].customerItemId.type = 4:紛失 <br> Tồn tại nhiều record customerItem có [Params].salesDetail[i].customerItemId.customerId AND [Params].salesDetail[i].customerItemId.itemId AND type = 2:レンタル | - | Status: 500 Internal Server Error <br> `{ "errors": [ "ERROR" ] }` |
| salesCreate | Bình thường | Response phải đúng | Response | - | Không xảy ra lỗi bên trên | Status: 201 Created <br> `{ "id": sales.id vừa tạo }` |
| salesCreate | Bình thường | Chi tiết response là chính xác | id | - | - | sales.id |
| salesCreate | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | - | - | Xử lý đăng ký phải được tiến hành đúng vào table sales <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | id | - | - | auto increment |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | projectId | - | - | [Params].projectId |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | salesDate | - | - | [Params].salesDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | paymentDueDate | - | - | [Params].paymentDueDate |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | invoiceType | - | - | [Params].invoiceType |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | comment | - | - | [Params].comment |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | amount | - | - | Tổng số tiền của [Params].salesDetail[i].amount |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | totalAmount | - | - | amount + Tổng số tiền của salesTaxRate.tax được tính từ [Params].salesDetail[i].taxRateId |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | lockFlag | - | - | NULL |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdAt | - | - | System datetime (JST) |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdBy | - | - | user.id của login user |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | createdUserName | - | - | user.userName của login user |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedAt | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedBy | - | - | Không thay đổi |
| Bảng sales | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | - | - | Không thay đổi |
| salesCreate | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | - | - | Xử lý đăng ký phải được tiến hành đúng vào table salesDetail <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | id | - | - | auto increment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | salesId | - | - | sales.id vừa được tạo |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | transactionDate | - | - | [Params].salesDetail[i].transactionDate |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | - | - | [Params].salesDetail[i].customerItemId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | - | - | [Params].salesDetail[i].quantity |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unit | - | - | [Params].salesDetail[i].customerItemId.itemId.unit |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | - | - | [Params].salesDetail[i].unitPrice |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | amount | - | - | [Params].salesDetail[i].amount |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | taxRateId | - | - | [Params].salesDetail[i].taxRateId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | comment | - | - | [Params].salesDetail[i].comment |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | sort | - | - | [Params].salesDetail[i].sort |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailId | - | - | projectDetail.id có projectDetail.customerItemId = [Params].salesDetail[i].customerItemId |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailCreatedType | - | [Params].salesDetail[i].customerItemId.type = 2:レンタル | 1:納品 |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | projectDetailCreatedType | - | [Params].salesDetail[i].customerItemId.type = 4:紛失 | 2:紛失 |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdAt | - | - | System datetime (JST) |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdBy | - | - | user.id của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | createdUserName | - | - | user.userName của login user |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedAt | - | - | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedBy | - | - | Không thay đổi |
| Bảng salesDetail | Bình thường | Giá trị lưu DB phải đúng | updatedUserName | - | - | Không thay đổi |
| salesCreate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý UPDATE customerItem | - | [Params].salesDetail[i].customerItemId.type = 2:レンタル | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 2:レンタル | [Params].salesDetail[i].customerItemId.lendingTotalNumber + [Params].salesDetail[i].quantity |
| salesCreate | Bình thường | Xử lý cập nhật phải được tiến hành đúng trong table và field | Xử lý UPDATE customerItem | - | [Params].salesDetail[i].customerItemId.type = 4:紛失 | Xử lý cập nhật phải được tiến hành đúng vào table customerItem <br> `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Giá trị lưu DB phải đúng | lendingTotalNumber | - | [Params].salesDetail[i].customerItemId.type = 4:紛失 | [customerItemId.lendingTotalNumber được get] - [Params].salesDetail[i].quantity |
