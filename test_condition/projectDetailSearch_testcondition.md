| Chức năng test | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất |
|---|---|---|---|---|---|---|
| projectDetailSearch | Bình thường | URL phải đúng | URL | - | - | GET /v1/project |
| projectDetailSearch | Bất thường | Check chứng thực | Tổng thể | - | - | Status: 401 Unauthorized <br> `{ "errors": [ "認証エラー" ] }` |
| projectDetailSearch | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag của login user NOT IN LIST (1,2,11,12) | Status: 403 Forbidden <br> `{ "errors": [ "権限がないURLです" ] }` |
| projectDetailSearch | Bất thường | Check required | deliveryDate | Không gửi | - | Status: 400 Bad Request <br> `{ "errors": [ "deliveryDateは必須です。" ] }` |
| projectDetailSearch | Bất thường | Check required | deliveryDate | Không nhập | - | Status: 400 Bad Request <br> `{ "errors": [ "deliveryDateは必須です。" ] }` |
| projectDetailSearch | Bất thường | Check format | deliveryDate | Khác format date | - | Status: 400 Bad Request <br> `{ "errors": [ "deliveryDateは日付を正しく入力してください。" ] }` |
| projectDetailSearch | Bình thường | Xác nhận kết quả search có đúng không khi không nhập gì | Response | - | Chỉ truyền required: deliveryDate | Trả về tất cả record projectDetail có project.deliveryDate = [Params].deliveryDate |
| projectDetailSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | - | Không xảy ra lỗi | Trả về theo thứ tự: <br> 1. [project].[customerId].[kanaAcronym] (あいうえお) <br> 2. [customerItem].[itemId].[itemClass1Id].[sort] ASC <br> 3. [customerItem].[itemId].[kana] (あいうえお) <br> 4. [id] ASC |
| projectDetailSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | [project].[customerId].[kanaAcronym] trùng nhau | Không xảy ra lỗi | Trả về tiếp theo theo thứ tự [customerItem].[itemId].[itemClass1Id].[sort] ASC |
| projectDetailSearch | Bình thường | Kết quả search là 0 record phải xử lý đúng | Response | Điều kiện không có kết quả search | Số record tương ứng = 0 | Status: 200 OK <br> `[]` |
| projectDetailSearch | Bình thường | Response phải đúng | Response | Điều kiện có kết quả search | Số record tương ứng > 0 | Status: 200 OK <br> `[ { ※Chi tiết tham chiếu test case bên dưới } ]` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | id | - | - | projectDetail.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.id | - | - | project.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.orderDate | - | - | project.orderDate |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.deliveryDate | - | - | project.deliveryDate |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer | - | Record customer có id = project.customerId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.id | - | - | customer.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.name | - | - | customer.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.kana | - | - | customer.kana |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.nameAcronym | - | - | customer.nameAcronym |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customer.kanaAcronym | - | - | customer.kanaAcronym |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff | - | [project].customerStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff.id | - | - | customerStaff.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaff.name | - | - | customerStaff.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff | - | [project].salesStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff.id | - | - | staff.id (salesStaffId) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.salesStaff.name | - | - | staff.name (salesStaffId) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerSectionName | - | - | project.customerSectionName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerTitle | - | - | project.customerTitle |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerStaffName | - | - | project.customerStaffName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDeliveryType | - | - | project.customerDeliveryType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery | - | [project].customerDeliveryId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery.id | - | - | customerDelivery.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.customerDelivery.name | - | - | customerDelivery.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.type | - | - | project.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.deliveryStaffType | - | - | project.deliveryStaffType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff | - | [project].staffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff.id | - | - | staff.id (staffId) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.staff.name | - | - | staff.name (staffId) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency | - | [project].agencyId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency.id | - | - | agency.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agency.name | - | - | agency.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff | - | [project].agencyStaffId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff.id | - | - | agencyStaff.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.agencyStaff.name | - | - | agencyStaff.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier | - | [project].supplierId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier.id | - | - | supplier.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.supplier.name | - | - | supplier.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.companyComment | - | - | project.companyComment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.comment | - | - | project.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.amount | - | - | project.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.regularDeliveryId | - | - | project.regularDeliveryId |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdAt | - | - | project.createdAt |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdBy | - | - | project.createdBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.createdUserName | - | - | project.createdUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedAt | - | - | project.updatedAt |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedBy | - | - | project.updatedBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | project.updatedUserName | - | - | project.updatedUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.id | - | - | customerItem.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.type | - | - | customerItem.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.id | - | - | item.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.name | - | - | item.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.kana | - | - | item.kana |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.item.itemClass1Id.sort | - | - | item.itemClass1Id.sort |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.unitType | - | - | customerItem.unitType |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem | - | [customerItem].collectCustomerItemId != NULL | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.id | - | - | collectCustomerItem.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.type | - | - | collectCustomerItem.type |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item | - | - | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.id | - | - | item.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.name | - | - | item.name |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.kana | - | - | item.kana |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | customerItem.collectCustomerItem.item.unit | - | - | item.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | quantity | - | - | projectDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | unit | - | - | projectDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | unitPrice | - | - | projectDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | amount | - | - | projectDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | comment | - | - | projectDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | sort | - | - | projectDetail.sort |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdAt | - | - | projectDetail.createdAt |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdBy | - | - | projectDetail.createdBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | createdUserName | - | - | projectDetail.createdUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedAt | - | - | projectDetail.updatedAt |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedBy | - | - | projectDetail.updatedBy |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | updatedUserName | - | - | projectDetail.updatedUserName |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail | - | Tồn tại salesDetail có projectDetailId = projectDetail.id AND projectDetailCreatedType = 1:納品 | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.id | - | - | salesDetail.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.quantity | - | - | salesDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.unit | - | - | salesDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.unitPrice | - | - | salesDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.amount | - | - | salesDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.comment | - | - | salesDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | deliverySalesDetail.salesId | - | - | salesDetail.salesId |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail | - | Tồn tại salesDetail có projectDetailId = projectDetail.id AND projectDetailCreatedType = 2:紛失 | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.id | - | - | salesDetail.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.quantity | - | - | salesDetail.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.unit | - | - | salesDetail.unit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.unitPrice | - | - | salesDetail.unitPrice |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.amount | - | - | salesDetail.amount |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | lostSalesDetail.comment | - | - | salesDetail.comment |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect | - | Tồn tại collect có projectDetailId = projectDetail.id | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.id | - | - | collect.id |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.quantity | - | - | collect.quantity |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.collectUnit | - | - | collect.collectUnit |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | collect.comment | - | - | collect.comment |
| projectDetailSearch | Bình thường | Check rentalCheck parameter | rentalCheck | Giá trị 1 | Optional parameters khác để trống | Chỉ trả về record có customerItem.type = 2:レンタル AND deliverySalesDetail.quantity != collect.quantity (NULL = 0) |
| projectDetailSearch | Bình thường | Chi tiết response là chính xác | agency | - | login user.userFlag = 11 OR 12 | Trả về record project có project.agencyId = login user.agencyId |
