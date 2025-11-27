

# Group product

## productCreate [/v1/product/create]

### productCreate [POST]

#### Khái quát xử lý

* Insert record mới bằng thông tin đã nhận <br>
<br>
* Trường hợp [Parameters].[customerId] != [Parameters].[customerDeliveryId].[customerId] OR <br>
 Trường hợp [Parameters].[customerId] != [Parameters].[customerStaffId].[customerId] OR <br>
 Trường hợp [Parameters].[customerId] != [Parameters].[productDetail].[customerItemId].[customerId] OR <br>
 Trường hợp [Parameters].[agencyId] != [Parameters].[agencyStaffId].[agencyId]  <br>
 thì trả lỗi hệ thống <br>
<br>
* Trường hợp [Parameters].[customerId].[type] = 1:顧客 AND [Parameters].[deliveryStaffType] = 2:代理店 OR <br>
 [Parameters].[customerId].[type] = 2:顧客(代行先) AND [Parameters].[deliveryStaffType] = 1:自社 OR <br>
 [Parameters].[customerId].[type] = 2:顧客(代行先) AND [Parameters].[deliveryStaffType] = 3:外注先 <br>
 thì trả lỗi <br>
 Message [productDeliveryStaffTypeError] <br>
<br>
* Trường hợp [Parameters].[customerId].[type] = 2:顧客(代行先) AND <br>
    Trường hợp [userFlag] (của login user) != 11:代理店管理者 OR 12:代理店一般ユーザ <br>
　　　　　Trường hợp [Parameters].[agencyId] != [Parameters].[customerId].[agencyId] thì trả lỗi  <br>
　　　　　Message [productDeliveryStaffTypeError] <br>
    Trường hợp [userFlag] (của login user) = 11:代理店管理者 OR 12:代理店一般ユーザ <br>	  
　　　　　Không cần quan tâm [Parameters].[deliveryStaffType] , [agencyId] <br> 
　　　　　Trường hợp [agencyId] của login user != [Parameters].[customerId].[agencyId] thì trả lỗi  <br>
　　　　　Message [productDeliveryStaffTypeError] <br>
　　　　　[deliveryStaffType] = 2:代理店 <br>
　　　　　Lưu [agencyId] = [agencyId] của login user  <br>
<br>
* Trường hợp [Parameters].[customerId].[approvalFlag] = 0:未承認 thì trả lỗi <br>
 Message [noApprovalError] <br>
<br>
* Trường hợp tồn tại 1 record data có [Parameters].[productDetail].[customerItemId].[type] = 4:紛失 thì trả lỗi <br>
 Message [productItemTypeError] <br>
<br>
* Trường hợp [Parameters].[deliveryStaffType] = 1:自社, [staffId] sẽ require <br>
 Trường hợp [Parameters].[deliveryStaffType] = 2:代理店, [agencyId] , [agencyStaffId] sẽ require, ngoại trừ trường hợp [userFlag](của login user) = 11:代理店管理者 OR 12:代理店一般ユーザ  <br>
 Trường hợp [Parameters].[deliveryStaffType] = 3:外注先, [supplierId] sẽ require <br>
<br>
* [salesStaffId] = [Parameters].[customerId].[salesStaffId] <br>
<br>
* Lưu [amount] = Tổng số tiền của [Parameters].[productDetail].[amount] <br>
<br>
* Trường hợp [Parameters].[customerDeliveryId] = NULL, lưu [customerDeliveryType] = 0:顧客 <br>
 Ngược lại, lưu 1:顧客納品先 <br>
<br>
* Lưu [type] = [Parameters].[customerId].[type]<br>
<br>
* Lưu [productDetail].[unit] = [Parameters].[productDetail].[customerItemId].[itemId].[unit]<br>
 <br>
* Chỉ trường hợp [Parameters].[deliveryStaffType] = 1:自社 thì chạy xử lý dưới đây<br>
 INSERT record [productDetailAddChangeHistory] theo đơn vị 1 dòng [productDetail] <br>
 Search [loadingStartRecord] dựa trên [Parameters].[deliveryDate] AND [staffId]<br>
 Trường hợp search được dù 1 record thì sẽ INSERT record với [addFlag] = 1:Yes <br>
 [quantity] = [Parameters].[productDetail].[quantity] <br>

+ Parameters
    + orderDate: `2020-04-01` (string,required) - 受注日
    + deliveryDate: `2020-04-01` (string,required) - 納品日
    + customerId: `1` (string,required) - 顧客id
    + customerStaffId:  `1` (string,optional) - 顧客担当者id
    + customerSectionName: `田中 太郎` (string,optional) - 顧客担当部署名
    + customerTitle: `田中 太郎` (string,optional) - 顧客担当肩書
    + customerStaffName: `田中 太郎` (string,optional) - 顧客担当者名
    + customerDeliveryId: `1` (string,optional) - 顧客納品先id
    + deliveryStaffType: `1` (string,optional) - 配送区分
    + staffId: `1` (string,optional) - 担当者id
    + agencyId: `1` (string,optional) - 代理店id
    + agencyStaffId: `1` (string,optional) - 代理店担当者id
    + supplierId: `1` (string,optional) - 外注先id
    + companyComment: `備考` (string,optional) - 社内備考
    + comment: `備考` (string,optional) - 伝票表記備考
    + productDetail: (array,optional) - 案件明細
        + (object)
            + customerItemId: `1` (string,required) - 顧客商品id
            + quantity: `10` (string,required) - 数量
            + unitPrice: `1000` (string,required) - 単価
            + amount: `10000` (string,required) - 金額
            + comment: `備考` (string,optional) - 備考
            + sort: `1` (string,required) - 並び順

+ Response 201 (application/json)
    + Attributes (object)
        + id: 1 (string,required) - id
