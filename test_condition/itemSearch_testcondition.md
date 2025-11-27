# 📋 Test Cases API Chi Tiết

| Chức năng test (URL) | Bình thường / Bất thường | Chi tiết test | Parameter/Hạng mục | Giá trị nhập | Điều kiện tiền đề | Giá trị xuất (Response) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| itemSearch | Bình thường | URL phải đúng | URL | -- | -- | `GET /v1/item/search` |
| itemSearch | Bất thường | Check chứng thực | Tổng thể | -- | -- | **Status: 401 Unauthorized**<br>`{ "errors": [ "認証エラー" ] }` |
| itemSearch | Bất thường | Check quyền hạn | Quyền hạn | - | user.userFlag không có quyền truy cập | **Status: 403 Forbidden**<br>`{ "errors": [ "権限がないURLです" ] }` |
| itemSearch | Bất thường | Response phải đúng | Tổng thể | Có truyền parameter nhưng không tồn tại record nào thỏa điều kiện search | Điều kiện không có kết quả search | **Status: 200 OK**<br>`[]` |
| itemSearch | Bình thường | Xác nhận kết quả search có đúng không khi không nhập gì | Response | - | - | Trả về tất cả record item có item.disableFlag = 0 |
| itemSearch | Bình thường | Thứ tự sort phải được thực hiện đúng | Response | - | - | Trả về theo thứ tự item.kana ASC, item.id ASC |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | id | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record item có item.id = [Params].id và item.disableFlag = 0 |
| itemSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | id | - | - | Search giống toàn bộ |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | code | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record item có item.code = [Params].code và item.disableFlag = 0 |
| itemSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | code | - | - | Search giống toàn bộ |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | name | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record item có item.name LIKE [Params].name và item.disableFlag = 0 |
| itemSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | name | - | - | Search like |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | productionLocation | Giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record item có item.productionLocation = [Params].productionLocation và item.disableFlag = 0 |
| itemSearch | Bình thường | Xử lý search giống toàn bộ hoặc search like phải được thực hiện đúng | productionLocation | - | - | Search giống toàn bộ |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | aggregateTypeId | Một giá trị tồn tại trong DB | Optional parameters khác để trống | Trả về các record item có item.aggregateTypeId = [Params].aggregateTypeId và item.disableFlag = 0 |
| itemSearch | Bình thường | Xử lý search "or" phải được thực hiện đúng | aggregateTypeId | Nhiều giá trị ngăn cách bởi dấu "," | Optional parameters khác để trống | Trả về các record item có item.aggregateTypeId IN ([Params].aggregateTypeId) và item.disableFlag = 0 |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | disableFlag | 0 | Optional parameters khác để trống | Trả về các record item có item.disableFlag = 0 |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | disableFlag | 1 | Optional parameters khác để trống | Trả về các record item có item.disableFlag = 1 |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | limit | >=0 | Optional parameters khác để trống | Trả về [Params].limit record đầu tiên |
| itemSearch | Bình thường | Search từng hạng mục, kết quả search phải đúng với nội dung trong DB | offset | >=1 | Optional parameters khác để trống | Trả về từ record có thứ tự từ ([Params].offset-1)*[Params].limit+1 |
| itemSearch | Bình thường | Xử lý search "and" phải được thực hiện đúng | Giữa parameter với parameter | - | - | Search "and" |
| itemSearch | Bình thường | Response phải đúng | Response | Điều kiện có kết quả search | Số record tương ứng > 0 | **Status: 200 OK**<br>`X-Total-Count: {tổng số record}`<br>`[ { ※Chi tiết tham chiếu test case bên dưới } ]` |
| itemSearch | Bình thường | Chi tiết response là chính xác | id | - | - | item.id |
| itemSearch | Bình thường | Chi tiết response là chính xác | code | - | - | item.code |
| itemSearch | Bình thường | Chi tiết response là chính xác | janCode | - | - | item.janCode |
| itemSearch | Bình thường | Chi tiết response là chính xác | name | - | - | item.name |
| itemSearch | Bình thường | Chi tiết response là chính xác | kana | - | - | item.kana |
| itemSearch | Bình thường | Chi tiết response là chính xác | unit | - | - | item.unit |
| itemSearch | Bình thường | Chi tiết response là chính xác | instructionsType | - | - | item.instructionsType |
| itemSearch | Bình thường | Chi tiết response là chính xác | aggregateType | - | Record aggregateType có aggregateType.id = item.aggregateTypeId | `{ ※Chi tiết tham chiếu test case bên dưới }` |
| itemSearch | Bình thường | Chi tiết response là chính xác | id | - | - | aggregateType.id |
| itemSearch | Bình thường | Chi tiết response là chính xác | name | - | - | aggregateType.name |
| itemSearch | Bình thường | Chi tiết response là chính xác | productionLocation | - | - | item.productionLocation |
| itemSearch | Bình thường | Chi tiết response là chính xác | taxRateType | - | - | item.taxRateType |
| itemSearch | Bình thường | Chi tiết response là chính xác | feeType | - | - | item.feeType |
| itemSearch | Bình thường | Chi tiết response là chính xác | costUnitPrice | - | - | item.costUnitPrice |
| itemSearch | Bình thường | Chi tiết response là chính xác | salesUnitPrice | - | - | item.salesUnitPrice |
| itemSearch | Bình thường | Chi tiết response là chính xác | changeName | - | - | item.changeName |
| itemSearch | Bình thường | Chi tiết response là chính xác | comment | - | - | item.comment |
| itemSearch | Bình thường | Chi tiết response là chính xác | disableFlag | - | - | item.disableFlag |
| itemSearch | Bình thường | Chi tiết response là chính xác | createdAt | - | - | item.createdAt |
| itemSearch | Bình thường | Chi tiết response là chính xác | createdBy | - | - | item.createdBy |
| itemSearch | Bình thường | Chi tiết response là chính xác | createdUserName | - | - | item.createdUserName |
| itemSearch | Bình thường | Chi tiết response là chính xác | updatedAt | - | - | item.updatedAt |
| itemSearch | Bình thường | Chi tiết response là chính xác | updatedBy | - | - | item.updatedBy |
| itemSearch | Bình thường | Chi tiết response là chính xác | updatedUserName | - | - | item.updatedUserName |
