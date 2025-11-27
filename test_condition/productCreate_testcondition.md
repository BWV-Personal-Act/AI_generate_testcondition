# 📋 Test Cases API Chi Tiết - productCreate

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| productCreate | Bình thường | URL phải đúng | URL | -- | -- | `POST /v1/product/create` |
| productCreate | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| productCreate | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag != 0,1,2 | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| productCreate | Bất thường | Check required | orderDate | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "受注日は必須です。" ] }` |
| productCreate | Bất thường | Check required | orderDate | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "受注日は必須です。" ] }` |
| productCreate | Bất thường | Check required | deliveryDate | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| productCreate | Bất thường | Check required | deliveryDate | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| productCreate | Bất thường | Check required | customerId | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客idは必須です。" ] }` |
| productCreate | Bất thường | Check required | customerId | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客idは必須です。" ] }` |
| productCreate | Bất thường | Check required | deliveryStaffType | Gửi rỗng | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "配送区分は必須です。" ] }` |
| productCreate | Bất thường | Check required | deliveryStaffType | Không gửi | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "配送区分は必須です。" ] }` |
| productCreate | Bất thường | Check required | staffId | Gửi rỗng | deliveryStaffType = 1:自社 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | staffId | Không gửi | deliveryStaffType = 1:自社 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | agencyId | Gửi rỗng | deliveryStaffType = 2:代理店 AND userFlag != 11,12 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | agencyId | Không gửi | deliveryStaffType = 2:代理店 AND userFlag != 11,12 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | agencyStaffId | Gửi rỗng | deliveryStaffType = 2:代理店 AND userFlag != 11,12 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店担当者IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | agencyStaffId | Không gửi | deliveryStaffType = 2:代理店 AND userFlag != 11,12 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店担当者IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | supplierId | Gửi rỗng | deliveryStaffType = 3:外注先 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "外注先IDは必須です。" ] }` |
| productCreate | Bất thường | Check required | supplierId | Không gửi | deliveryStaffType = 3:外注先 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "外注先IDは必須です。" ] }` |
| productCreate | Bất thường | Check format | orderDate | Khác format yyyy-mm-dd | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "受注日は日付を正しく入力してください。" ] }` |
| productCreate | Bất thường | Check format | deliveryDate | Khác format yyyy-mm-dd | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "納品日は日付を正しく入力してください。" ] }` |
| productCreate | Bất thường | Check format | customerId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客idは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | customerStaffId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客担当者idは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | deliveryStaffType | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "配送区分は数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | staffId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "担当者IDは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | agencyId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店IDは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | agencyStaffId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "代理店担当者IDは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | supplierId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "外注先IDは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check format | customerDeliveryId | Khác số | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客納品先idは数値のみ入力可能です。" ] }` |
| productCreate | Bất thường | Check size | customerSectionName | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客担当部署は100文字以内で入力してください。" ] }` |
| productCreate | Bất thường | Check size | customerTitle | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客担当肩書は100文字以内で入力してください。" ] }` |
| productCreate | Bất thường | Check size | customerStaffName | > 100 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "顧客担当者名は100文字以内で入力してください。" ] }` |
| productCreate | Bất thường | Check size | companyComment | > 1000 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "社内備考は1000文字以内で入力してください。" ] }` |
| productCreate | Bất thường | Check size | comment | > 1000 ký tự | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "伝票表記備考は1000文字以内で入力してください。" ] }` |
| productCreate | Bất thường | Check giá trị | deliveryStaffType | Khác 1:自社 2:代理店 3:外注先 | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "有効な配送区分を入力してください。" ] }` |
| productCreate | Bất thường | Check tồn tại | customerId | customerId không tồn tại trong DB | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する顧客がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | customerStaffId | customerStaffId không tồn tại trong DB | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する顧客担当者がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | customerDeliveryId | customerDeliveryId không tồn tại trong DB | - | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する顧客納品先がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | staffId | staffId không tồn tại trong DB | deliveryStaffType = 1:自社 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する担当者がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | agencyId | agencyId không tồn tại trong DB | deliveryStaffType = 2:代理店 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する代理店がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | agencyStaffId | agencyStaffId không tồn tại trong DB | deliveryStaffType = 2:代理店 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する代理店担当者がありません。" ] }` |
| productCreate | Bất thường | Check tồn tại | supplierId | supplierId không tồn tại trong DB | deliveryStaffType = 3:外注先 | **Status: 422 Unprocessable Entity**<br>`{ "errors": [ "該当する外注先がありません。" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId != [Params].customerDeliveryId.customerId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "システムエラーが発生しました" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId != [Params].customerStaffId.customerId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "システムエラーが発生しました" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId != [Params].productDetail.customerItemId.customerId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "システムエラーが発生しました" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].agencyId != [Params].agencyStaffId.agencyId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "システムエラーが発生しました" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.type = 1:顧客 AND [Params].deliveryStaffType = 2:代理店 | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productDeliveryStaffTypeError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.type = 2:顧客(代行先) AND [Params].deliveryStaffType = 1:自社 | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productDeliveryStaffTypeError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.type = 2:顧客(代行先) AND [Params].deliveryStaffType = 3:外注先 | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productDeliveryStaffTypeError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.type = 2:顧客(代行先) AND userFlag != 11,12 AND [Params].agencyId != [Params].customerId.agencyId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productDeliveryStaffTypeError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.type = 2:顧客(代行先) AND (userFlag = 11 OR 12) AND login user.agencyId != [Params].customerId.agencyId | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productDeliveryStaffTypeError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].customerId.approvalFlag = 0:未承認 | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "noApprovalError" ] }` |
| productCreate | Bất thường | Response phải đúng | Response | [Params].productDetail.customerItemId.type = 4:紛失 | Điều kiện tiên quyết sai | **Status: 400 Bad Request**<br>`{ "errors": [ "productItemTypeError" ] }` |
| productCreate | Bình thường | Response phải đúng | Response | Không xảy ra lỗi bên trên | Tất cả điều kiện tiền đề hợp lệ | **Status: 201 Created**<br>`{ "id": "product.id vừa tạo" }` |
| productCreate | Bình thường | Chi tiết response là chính xác | id | - | - | product.id được tạo mới |
| Bảng product | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | -- | Xử lý đăng ký phải được tiến hành đúng vào table product<br>※Chi tiết tham chiếu test case bên dưới |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | id | -- | -- | auto_increment |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | orderDate | -- | parameter.orderDate | parameter.orderDate |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | deliveryDate | -- | parameter.deliveryDate | parameter.deliveryDate |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerId | -- | parameter.customerId | parameter.customerId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerStaffId | -- | parameter.customerStaffId | parameter.customerStaffId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerSectionName | -- | parameter.customerSectionName | parameter.customerSectionName |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerTitle | -- | parameter.customerTitle | parameter.customerTitle |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerStaffName | -- | parameter.customerStaffName | parameter.customerStaffName |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerDeliveryType | -- | parameter.customerDeliveryId = NULL | 0:顧客 |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerDeliveryType | -- | parameter.customerDeliveryId != NULL | 1:顧客納品先 |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | customerDeliveryId | -- | parameter.customerDeliveryId | parameter.customerDeliveryId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | type | -- | parameter.customerId.type | parameter.customerId.type |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | deliveryStaffType | -- | parameter.deliveryStaffType | parameter.deliveryStaffType |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | staffId | -- | parameter.staffId | parameter.staffId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | agencyId | -- | parameter.customerId.type = 2:顧客(代行先) AND userFlag = 11 OR 12 | login user.agencyId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | agencyId | -- | điều kiện khác | parameter.agencyId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | agencyStaffId | -- | parameter.agencyStaffId | parameter.agencyStaffId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | supplierId | -- | parameter.supplierId | parameter.supplierId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | companyComment | -- | parameter.companyComment | parameter.companyComment |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | comment | -- | parameter.comment | parameter.comment |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | salesStaffId | -- | [customerId].salesStaffId | [customerId].salesStaffId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | amount | -- | Tổng số tiền của parameter.productDetail.amount | Tổng số tiền của parameter.productDetail.amount |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | regularDeliveryId | -- | parameter.regularDeliveryId | parameter.regularDeliveryId |
| Bảng product | Bình thường | Giá trị lưu DB phải đúng | startingPointWeek | -- | -- | ngày đối tượng tạo |
| Bảng productDetail | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | -- | Xử lý đăng ký phải được tiến hành đúng vào table productDetail<br>※Chi tiết tham chiếu test case bên dưới |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | productId | -- | -- | product.id vừa tạo |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | customerItemId | -- | Có truyền parameter.productDetail[n].customerItemId | parameter.productDetail[n].customerItemId |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | quantity | -- | Có truyền parameter.productDetail[n].quantity | parameter.productDetail[n].quantity |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | unitPrice | -- | Có truyền parameter.productDetail[n].unitPrice | parameter.productDetail[n].unitPrice |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | amount | -- | Có truyền parameter.productDetail[n].amount | parameter.productDetail[n].amount |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | comment | -- | Có truyền parameter.productDetail[n].comment | parameter.productDetail[n].comment |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | sort | -- | Có truyền parameter.productDetail[n].sort | parameter.productDetail[n].sort |
| Bảng productDetail | Bình thường | Giá trị lưu DB phải đúng | unit | -- | - | parameter.productDetail[n].customerItemId.itemId.unit |
| Bảng productDetailAddChangeHistory | Bình thường | Xử lý đăng ký phải được tiến hành đúng trong table và field | Xử lý lưu DB | -- | parameter.deliveryStaffType = 1:自社 | Xử lý đăng ký phải được tiến hành đúng vào table productDetailAddChangeHistory<br>※Chi tiết tham chiếu test case bên dưới |
| Bảng productDetailAddChangeHistory | Bình thường | Giá trị lưu DB phải đúng | quantity | -- | [loadingStartRecord] được tìm thấy | parameter.productDetail[n].quantity |
| Bảng productDetailAddChangeHistory | Bình thường | Giá trị lưu DB phải đúng | addFlag | -- | [loadingStartRecord] được tìm thấy dựa trên parameter.deliveryDate AND staffId | 1:Yes |
