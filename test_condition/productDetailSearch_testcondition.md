# 📋 Test Cases productDetailSearch API

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| productDetailSearch | Bình thường | URL phải đúng | URL | -- | -- | `GET /v1/product` |
| productDetailSearch | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| productDetailSearch | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag của login user = 11 (代理店管理者) hoặc 12 (代理店一般ユーザ) | Chỉ trả về record có product.agencyId = login user.agencyId |
| productDetailSearch | Bất thường | Check required | deliveryDate | Gửi rỗng | - | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| productDetailSearch | Bất thường | Check required | deliveryDate | Không gửi | - | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| productDetailSearch | Bất thường | Check format | deliveryDate | Khác format yyyy-MM-dd | - | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は日付を正しく入力してください。" ] }` |
| productDetailSearch | Bất thường | Check format | deliveryStaffType | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "配送区分は数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check giá trị | deliveryStaffType | Khác 1:自社 2:代理店 3:外注先 | - | **Status: 400 Bad Request**<br>`{ "errors": [ "有効なリスト値を入力してください。" ] }` |
| productDetailSearch | Bất thường | Check format | staffId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "担当者idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | staffId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する担当者がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | agencyId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "代理店idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | agencyId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する代理店がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | agencyStaffId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "代理店担当者idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | agencyStaffId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する代理店担当者がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | supplierId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "外注先idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | supplierId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する外注先がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | customerId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | customerId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する顧客がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | itemId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "商品idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | itemId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する商品がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | productId | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "案件idは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check tồn tại | productId | Không tồn tại trong DB hoặc deleted_date != NULL | - | **Status: 400 Bad Request**<br>`{ "errors": [ "該当する案件がありません。" ] }` |
| productDetailSearch | Bất thường | Check format | rentalCheck | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "貸出増減チェックは数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check format | limit | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "取得件数は数値で入力してください。" ] }` |
| productDetailSearch | Bất thường | Check format | offset | Khác số | - | **Status: 400 Bad Request**<br>`{ "errors": [ "page数は数値で入力してください。" ] }` |
| productDetailSearch | Bình thường | Response phải đúng | Response | Điều kiện có kết quả search | Số record tương ứng > 0 | **Status: 200 OK**<br>`{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | id | - | - | productDetail.id |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | product | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng product | Bình thường | Chi tiết response là chính xác | id | - | - | product.id |
| Bảng product | Bình thường | Chi tiết response là chính xác | orderDate | - | - | product.orderDate |
| Bảng product | Bình thường | Chi tiết response là chính xác | deliveryDate | - | - | product.deliveryDate |
| Bảng product | Bình thường | Chi tiết response là chính xác | customer | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customer | Bình thường | Chi tiết response là chính xác | id | - | - | customer.id |
| Bảng customer | Bình thường | Chi tiết response là chính xác | name | - | - | customer.name |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kana | - | - | customer.kana |
| Bảng customer | Bình thường | Chi tiết response là chính xác | nameAcronym | - | - | customer.nameAcronym |
| Bảng customer | Bình thường | Chi tiết response là chính xác | kanaAcronym | - | - | customer.kanaAcronym |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerStaff | - | product.customerStaffId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerStaff | - | product.customerStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerStaff | Bình thường | Chi tiết response là chính xác | id | - | - | customerStaff.id |
| Bảng customerStaff | Bình thường | Chi tiết response là chính xác | name | - | - | customerStaff.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | salesStaff | - | product.salesStaffId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | salesStaff | - | product.salesStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng staff | Bình thường | Chi tiết response là chính xác | id | - | - | staff.id |
| Bảng staff | Bình thường | Chi tiết response là chính xác | name | - | - | staff.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerSectionName | - | - | product.customerSectionName |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerTitle | - | - | product.customerTitle |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerStaffName | - | - | product.customerStaffName |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerDeliveryType | - | - | product.customerDeliveryType |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerDelivery | - | product.customerDeliveryType = 0 (顧客) hoặc product.customerDeliveryId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | customerDelivery | - | product.customerDeliveryType = 1 (顧客納品先) AND product.customerDeliveryId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerDelivery | Bình thường | Chi tiết response là chính xác | id | - | - | customerDelivery.id |
| Bảng customerDelivery | Bình thường | Chi tiết response là chính xác | name | - | - | customerDelivery.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | type | - | - | product.type |
| Bảng product | Bình thường | Chi tiết response là chính xác | deliveryStaffType | - | - | product.deliveryStaffType |
| Bảng product | Bình thường | Chi tiết response là chính xác | staff | - | product.staffId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | staff | - | product.staffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng staff | Bình thường | Chi tiết response là chính xác | id | - | - | staff.id |
| Bảng staff | Bình thường | Chi tiết response là chính xác | name | - | - | staff.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | agency | - | product.agencyId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | agency | - | product.agencyId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng agency | Bình thường | Chi tiết response là chính xác | id | - | - | agency.id |
| Bảng agency | Bình thường | Chi tiết response là chính xác | name | - | - | agency.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | agencyStaff | - | product.agencyStaffId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | agencyStaff | - | product.agencyStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng agencyStaff | Bình thường | Chi tiết response là chính xác | id | - | - | agencyStaff.id |
| Bảng agencyStaff | Bình thường | Chi tiết response là chính xác | name | - | - | agencyStaff.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | supplier | - | product.supplierId = NULL | NULL |
| Bảng product | Bình thường | Chi tiết response là chính xác | supplier | - | product.supplierId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng supplier | Bình thường | Chi tiết response là chính xác | id | - | - | supplier.id |
| Bảng supplier | Bình thường | Chi tiết response là chính xác | name | - | - | supplier.name |
| Bảng product | Bình thường | Chi tiết response là chính xác | companyComment | - | - | product.companyComment |
| Bảng product | Bình thường | Chi tiết response là chính xác | comment | - | - | product.comment |
| Bảng product | Bình thường | Chi tiết response là chính xác | amount | - | - | product.amount |
| Bảng product | Bình thường | Chi tiết response là chính xác | regularDeliveryId | - | - | product.regularDeliveryId |
| Bảng product | Bình thường | Chi tiết response là chính xác | createdAt | - | - | product.createdAt |
| Bảng product | Bình thường | Chi tiết response là chính xác | createdBy | - | - | product.createdBy |
| Bảng product | Bình thường | Chi tiết response là chính xác | createdUserName | - | - | product.createdUserName |
| Bảng product | Bình thường | Chi tiết response là chính xác | updatedAt | - | - | product.updatedAt |
| Bảng product | Bình thường | Chi tiết response là chính xác | updatedBy | - | - | product.updatedBy |
| Bảng product | Bình thường | Chi tiết response là chính xác | updatedUserName | - | - | product.updatedUserName |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | customerItem | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | id | - | - | customerItem.id |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | type | - | - | customerItem.type |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | item | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng item | Bình thường | Chi tiết response là chính xác | id | - | - | item.id |
| Bảng item | Bình thường | Chi tiết response là chính xác | name | - | - | item.name |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | unitType | - | - | customerItem.unitType |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | collectCustomerItem | - | customerItem.collectCustomerItemId = NULL | NULL |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | collectCustomerItem | - | customerItem.collectCustomerItemId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | id | - | - | customerItem.id |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | type | - | - | customerItem.type |
| Bảng customerItem | Bình thường | Chi tiết response là chính xác | item | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng item | Bình thường | Chi tiết response là chính xác | id | - | - | item.id |
| Bảng item | Bình thường | Chi tiết response là chính xác | name | - | - | item.name |
| Bảng item | Bình thường | Chi tiết response là chính xác | unit | - | - | item.unit |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | quantity | - | - | productDetail.quantity |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | unit | - | - | productDetail.unit |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | unitPrice | - | - | productDetail.unitPrice |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | amount | - | - | productDetail.amount |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | comment | - | - | productDetail.comment |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | sort | - | - | productDetail.sort |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | createdAt | - | - | productDetail.createdAt |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | createdBy | - | - | productDetail.createdBy |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | createdUserName | - | - | productDetail.createdUserName |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | updatedAt | - | - | productDetail.updatedAt |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | updatedBy | - | - | productDetail.updatedBy |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | updatedUserName | - | - | productDetail.updatedUserName |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | deliverySalesDetail | - | productDetail.deliverySalesDetailId = NULL | NULL |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | deliverySalesDetail | - | productDetail.deliverySalesDetailId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | id | - | - | salesDetail.id |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | quantity | - | - | salesDetail.quantity |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | unit | - | - | salesDetail.unit |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | unitPrice | - | - | salesDetail.unitPrice |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | amount | - | - | salesDetail.amount |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | comment | - | - | salesDetail.comment |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | salesId | - | - | salesDetail.id (từ sales table) |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | lostSalesDetail | - | productDetail.lostSalesDetailId = NULL | NULL |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | lostSalesDetail | - | productDetail.lostSalesDetailId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | id | - | - | salesDetail.id |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | quantity | - | - | salesDetail.quantity |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | unit | - | - | salesDetail.unit |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | unitPrice | - | - | salesDetail.unitPrice |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | amount | - | - | salesDetail.amount |
| Bảng salesDetail | Bình thường | Chi tiết response là chính xác | comment | - | - | salesDetail.comment |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | collect | - | productDetail.collectId = NULL | NULL |
| Bảng productDetail | Bình thường | Chi tiết response là chính xác | collect | - | productDetail.collectId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| Bảng collect | Bình thường | Chi tiết response là chính xác | id | - | - | collect.id |
| Bảng collect | Bình thường | Chi tiết response là chính xác | quantity | - | - | collect.quantity |
| Bảng collect | Bình thường | Chi tiết response là chính xác | collectUnit | - | - | collect.collectUnit |
| Bảng collect | Bình thường | Chi tiết response là chính xác | comment | - | - | collect.comment |
| productDetailSearch | Bình thường | Thứ tự sort của data trả về phải đúng | Response | - | - | [product].[customerId].[kanaAcronym] theo thứ tự bảng chữ cái tiếng nhật (あいうえお), [customerItem].[itemId].[itemClass1Id].[sort] ASC, [customerItem].[itemId].[kana] theo thứ tự bảng chữ cái tiếng nhật (あいうえお), [id] ASC |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | deliveryDate | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.deliveryDate = parameter:deliveryDate |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | deliveryStaffType | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.deliveryStaffType = parameter:deliveryStaffType |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | staffId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.staffId = parameter:staffId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | agencyId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.agencyId = parameter:agencyId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | agencyStaffId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.agencyStaffId = parameter:agencyStaffId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | supplierId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.supplierId = parameter:supplierId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | customerId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.customerId = parameter:customerId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | itemId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có customerItem.itemId = parameter:itemId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | productId | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record productDetail có product.id = parameter:productId |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | rentalCheck | Giá trị = 1 | customerItem.type = 2 (レンタル) AND deliverySalesDetail.quantity != collect.quantity | Trả về các record productDetail thỏa điều kiện |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | rentalCheck | Giá trị != 1 hoặc không gửi | - | Trả về tất cả record productDetail |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | limit | >=0 | Optional parameters khác để trống | Trả về parameter:limit record đầu tiên |
| productDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | offset | >=1 | Optional parameters khác để trống | Trả về từ record thứ ((offset-1)*limit+1) |
| productDetailSearch | Bình thường | Xác nhận kết quả search có đúng không khi không nhập gì | Response | - | - | Trả về tất cả record productDetail có product.deliveryDate không rỗng |
| productDetailSearch | Bình thường | Kết quả search là 0 record phải xử lý đúng | Response | Điều kiện không có kết quả search | Số record tương ứng = 0 | **Status: 200 OK**<br>`[]` |
| productDetailSearch | Bất thường | Response phải đúng | Response | Không có login user hoặc token sai | - | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| productDetailSearch | Bất thường | Response phải đúng | Response | Server lỗi nội bộ | - | **Status: 500 Internal Server Error**<br>`{ "errors": [ "ERROR" ] }` |
