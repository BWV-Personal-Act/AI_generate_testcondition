# 📋 Test Cases API Chi Tiết - projectDetailSearch

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
|:---|:---|:---|:---|:---|:---|:---|
| projectDetailSearch | Bình thường | URL phải đúng | URL | -- | -- | `GET /v1/project` |
| projectDetailSearch | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| projectDetailSearch | Bất thường | Check quyền hạn | Quyền hạn | -- | user.userFlag NOT IN (1, 2) | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| projectDetailSearch | Bất thường | Check required | deliveryDate | Gửi rỗng | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| projectDetailSearch | Bất thường | Check required | deliveryDate | Không gửi | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は必須です。" ] }` |
| projectDetailSearch | Bất thường | Check format | deliveryDate | Khác format YYYY-MM-DD | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "納品日は日付のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | deliveryStaffType | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "配送区分は数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | staffId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "担当者IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | agencyId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "代理店IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | agencyStaffId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "代理店担当者IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | supplierId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "外注先IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | customerId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "顧客IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | itemId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "商品IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | projectId | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "案件IDは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | rentalCheck | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "貸出増減チェックは数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | limit | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "取得件数は数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bất thường | Check format | offset | Nhập khác số | -- | **Status: 400 Bad Request**<br>`{ "errors": [ "ページ数は数値のみ入力可能です。" ] }` |
| projectDetailSearch | Bình thường | Response phải đúng | Response | [Params].deliveryDate tồn tại record | Số record tương ứng > 0 | **Status: 200 OK**<br>Header: X-Total-Count: {Số record}<br>`[ { ※Chi tiết tham chiếu test case bên dưới } ]` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | id | -- | -- | projectDetail.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.id | -- | -- | project.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.orderDate | -- | -- | project.orderDate (format: YYYY-MM-DD) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.deliveryDate | -- | -- | project.deliveryDate (format: YYYY-MM-DD) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.id | -- | -- | customer.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.name | -- | -- | customer.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.kana | -- | -- | customer.kana |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.nameAcronym | -- | -- | customer.nameAcronym |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.kanaAcronym | -- | -- | customer.kanaAcronym |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff.id | -- | -- | customerStaff.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff.name | -- | -- | customerStaff.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff.id | -- | -- | staff.id (sales staff) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff.name | -- | -- | staff.name (sales staff) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerSectionName | -- | -- | project.customerSectionName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerTitle | -- | -- | project.customerTitle |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaffName | -- | -- | project.customerStaffName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDeliveryType | -- | -- | project.customerDeliveryType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery.id | -- | -- | customerDelivery.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery.name | -- | -- | customerDelivery.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.type | -- | -- | project.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.deliveryStaffType | -- | -- | project.deliveryStaffType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff.id | -- | -- | staff.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff.name | -- | -- | staff.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency.id | -- | -- | agency.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency.name | -- | -- | agency.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff.id | -- | -- | agencyStaff.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff.name | -- | -- | agencyStaff.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier.id | -- | -- | supplier.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier.name | -- | -- | supplier.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.companyComment | -- | -- | project.companyComment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.comment | -- | -- | project.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.amount | -- | -- | project.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.regularDeliveryId | -- | -- | project.regularDeliveryId |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdAt | -- | -- | project.createdAt (format: YYYY-MM-DD HH:MM:SS) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdBy | -- | -- | project.createdBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdUserName | -- | -- | project.createdUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedAt | -- | -- | project.updatedAt (format: YYYY-MM-DD HH:MM:SS) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedBy | -- | -- | project.updatedBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedUserName | -- | -- | project.updatedUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.id | -- | -- | customerItem.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.type | -- | -- | customerItem.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.id | -- | -- | item.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.name | -- | -- | item.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.unitType | -- | -- | customerItem.unitType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem | -- | customerItem.type = 2:レンタル OR 4:紛失 | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.id | -- | -- | collectCustomerItem.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.type | -- | -- | collectCustomerItem.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item | -- | -- | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.id | -- | -- | item.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.name | -- | -- | item.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.unit | -- | -- | item.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | quantity | -- | -- | projectDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | unit | -- | -- | projectDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | unitPrice | -- | -- | projectDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | amount | -- | -- | projectDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | comment | -- | -- | projectDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | sort | -- | -- | projectDetail.sort |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdAt | -- | -- | projectDetail.createdAt (format: YYYY-MM-DD HH:MM:SS) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdBy | -- | -- | projectDetail.createdBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdUserName | -- | -- | projectDetail.createdUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedAt | -- | -- | projectDetail.updatedAt (format: YYYY-MM-DD HH:MM:SS) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedBy | -- | -- | projectDetail.updatedBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedUserName | -- | -- | projectDetail.updatedUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail | -- | Tồn tại record sales với projectDetailId = projectDetail.id AND projectDetailCreatedType = 1:納品 | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.id | -- | -- | salesDetail.id (record có id nhỏ nhất nếu có nhiều) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.quantity | -- | -- | salesDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.unit | -- | -- | salesDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.unitPrice | -- | -- | salesDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.amount | -- | -- | salesDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.comment | -- | -- | salesDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.salesId | -- | -- | sales.id (của deliverySalesDetail) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail | -- | Tồn tại record sales với projectDetailId = projectDetail.id AND projectDetailCreatedType = 2:紛失 | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.id | -- | -- | salesDetail.id (record có id nhỏ nhất nếu có nhiều) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.quantity | -- | -- | salesDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.unit | -- | -- | salesDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.unitPrice | -- | -- | salesDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.amount | -- | -- | salesDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.comment | -- | -- | salesDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect | -- | Tồn tại record collect với projectDetailId = projectDetail.id | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.id | -- | -- | collect.id (record có id nhỏ nhất nếu có nhiều) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.quantity | -- | -- | collect.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.collectUnit | -- | -- | collect.collectUnit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.comment | -- | -- | collect.comment |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | deliveryStaffType | [Params].deliveryStaffType tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.deliveryStaffType = [Params].deliveryStaffType |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | staffId | [Params].staffId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.staffId = [Params].staffId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | agencyId | [Params].agencyId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.agencyId = [Params].agencyId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | agencyStaffId | [Params].agencyStaffId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.agencyStaffId = [Params].agencyStaffId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | supplierId | [Params].supplierId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.supplierId = [Params].supplierId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | customerId | [Params].customerId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.customerId = [Params].customerId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | itemId | [Params].itemId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có customerItem.itemId = [Params].itemId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | projectId | [Params].projectId tồn tại | Optional parameters khác để trống | Trả về các record projectDetail có project.id = [Params].projectId |
| projectDetailSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng | rentalCheck | [Params].rentalCheck = 1 | Optional parameters khác để trống | Trả về các record projectDetail có customerItem.type = 2:レンタル AND deliverySalesDetail.quantity != collect.quantity (NULL = 0) |
| projectDetailSearch | Bình thường | Xử lý search "and" phải được thực hiện đúng | Giữa parameter với parameter | -- | Nhập nhiều parameters | Kết quả search áp dụng điều kiện AND cho các parameters |
| projectDetailSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | -- | [Params].deliveryDate tồn tại | Trả về theo thứ tự: project.customerId.kanaAcronym ASC, customerItem.itemId.itemClass1Id.sort ASC, customerItem.itemId.kana ASC, projectDetail.id ASC |
| projectDetailSearch | Bình thường | Xử lý phân trang phải được thực hiện đúng | limit | [Params].limit tồn tại | -- | Trả về tối đa [Params].limit record |
| projectDetailSearch | Bình thường | Xử lý phân trang phải được thực hiện đúng | offset | [Params].offset tồn tại | -- | Trả về từ record thứ (([Params].offset-1)*[Params].limit + 1) |
| projectDetailSearch | Bình thường | Xác nhận quyền hạn | Response | [login user].userFlag = 11:代理店管理者 OR 12:代理店一般ユーザ | -- | Trả về các record projectDetail có project.agencyId = [login user].agencyId |
| projectDetailSearch | Bình thường | Xác nhận kết quả search có đúng không khi không nhập params optional | Response | Không nhập params optional | [Params].deliveryDate tồn tại | Trả về tất cả record projectDetail có project.deliveryDate = [Params].deliveryDate |
| projectDetailSearch | Bình thường | Kết quả search là 0 record phải xử lý đúng | Response | Điều kiện không có kết quả search | Không tồn tại record nào thỏa mãn điều kiện | **Status: 200 OK**<br>Header: X-Total-Count: 0<br>`[]` |
