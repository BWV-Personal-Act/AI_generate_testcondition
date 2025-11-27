# Group productDetail

## productDetailSearch [/v1/product]

### productDetailSearch [GET]

#### Khái quát xử lý


* Trả về N record kết quả của điều kiện search đã nhận <br>
* Trả về [product].[customerId].[kanaAcronym] theo thứ tự bảng chữ cái tiếng nhật (あいうえお), [customerItem].[itemId].[itemClass1Id].[sort] ASC, [customerItem].[itemId].[kana] theo thứ tự bảng chữ cái tiếng nhật (あいうえお), [id] ASC <br>
<br>
* Trường hợp [userFlag] (của login user) = 11:代理店管理者 OR 12:代理店一般ユーザ, đối tượng trả về chỉ [agencyId] (của login user) = [product].[agencyId] <br>
<br>
* [Parameters].[rentalCheck] <br>
 Chỉ data có [productDetail].[customerItemId].[type] = 2:レンタル AND <br>
 [Response].[deliverySalesDetail].[quantity] != [Response].[collect].[quantity] là đối tượng trả về <br>
 Trường hợp NULL OR không tồn tại data thì tiến hành xử lý coi như là 0 <br>
<br>
* [Response].[deliverySalesDetail]
 Trả về data có [Response].[id] = [salesDetail].[productDetailId] AND [salesDetail].[productDetailCreatedType] = 1:納品 <br>
 ※Tiền đề chỉ tồn tại 1 record, trường hợp tồn tại nhiều thì trả về data có [id] nhỏ nhất <br>
 Lưu [Response].[deliverySalesDetail].[salesId] = [id] của đối tượng trả về <br>
<br>
* [Response].[lostSalesDetail]
 Trả về data có [Response].[id] = [salesDetail].[productDetailId] AND [salesDetail].[productDetailCreatedType] = 2:紛失 <br>
 ※Tiền đề chỉ tồn tại 1 record, trường hợp tồn tại nhiều thì trả về data có [id] nhỏ nhất <br>
<br>
* [Response].[collect]
 Trả về data có[Response].[id] = [collect].[productDetailId] <br>
 ※Tiền đề chỉ tồn tại 1 record, trường hợp tồn tại nhiều thì trả về data có [id] nhỏ nhất <br>

+ Parameters
    + deliveryDate: `2020-04-01` (string,required) - 納品日( [product].[deliveryDate] )
    + deliveryStaffType: `1` (string,optional) - 配送区分( [product].[deliveryStaffType] )
    + staffId: `1` (string,optional) - 担当者id( [product].[staffId] )
    + agencyId: `1` (string,optional) - 代理店id( [product].[agencyId] )
    + agencyStaffId: `1` (string,optional) - 代理店担当者id
    + supplierId: `1` (string,optional) - 外注先id( [product].[supplierId] )
    + customerId: `1` (string,optional) - 顧客id( [product].[customerId] )
    + itemId: `1` (string,optional) - 商品id
    + productId: `1` (string,optional) - 案件id
    + rentalCheck: `1` (string,optional) - 貸出増減チェック
    + limit: `20` (string,optional) - 取得件数
    + offset: `2` (string,optional) - page数
    
+ Response 200 (application/json)
    + Headers
        X-Total-Count: 2
    + Attributes (array,required,fixed-type)
        + (object)
            + id: (string,required) - id
            + product: (object,required) - 案件
                + id: (string,required) - id
                + orderDate: `2020-04-01` (string,required) - 受注日
                + deliveryDate: `2020-04-01` (string,required) - 納品日
                + customer: (object,required) - 顧客
                    + id: `1` (string,required) - id
                    + name: `株式会社ブリスウェル` (string,required) - 顧客名
                    + kana: `ブリスウェル` (string,required) - 顧客名かな
                    + nameAcronym: `株式会社ブリスウェル` (string,required) - 顧客名略称
                    + kanaAcronym: `ブリスウェル` (string,required) - 顧客名略称かな
                + customerStaff: (object,optional) - 顧客担当者
                    + id: `1` (string,required) - id
                    + name: `田中` (string,required) - 担当者名
                + salesStaff: (object,optional) - 営業担当者
                    + id: `1` (string,required) - id
                    + name: `田中` (n,required) - 担当者名
                + customerSectionName: `田中 太郎` (string,optional) - 顧客担当部署名
                + customerTitle: `田中 太郎` (string,optional) - 顧客担当肩書
                + customerStaffName: `田中 太郎` (string,optional) - 顧客担当者名
                + customerDeliveryType: `1` (string,required) - 納品先区分
                + customerDelivery: (object,optional) - 顧客納品先
                    + id: `1` (string,required) - id
                    + name: `納品先名` (string,required) - 納品先名
                + type: `1` (string,required) - 顧客種別
                + deliveryStaffType: `1` (string,required) - 配送区分
                + staff: (object,optional) - 担当者
                    + id: `1` (string,required) - id
                    + name: `田中` (n,required) - 担当者名
                + agency: (object,optional) - 代理店
                    + id: `1` (string,required) - id
                    + name: `田中` (string,required) - 代理店名
                + agencyStaff: (object,optional) - 代理店担当者
                    + id: `1` (string,required) - id
                    + name: `田中` (string,required) - 担当者名
                + supplier: (object,optional) - 外注先
                    + id: `1` (string,required) - id
                    + name: `田中` (string,required) - 外注先名
                + companyComment: `備考` (string,optional) - 社内備考
                + comment: `備考` (string,optional) - 伝票表記備考
                + amount: `10000` (string,required) - 税抜金額
                + regularDeliveryId: `1` (string,optional) - 定期配送id
                + createdAt: `2020-01-01 11:11:11` (string,required) - 登録日時
                + createdBy: `1` (string,required) - 登録者
                + createdUserName: `Tanaka` (string,required) - 登録者名
                + updatedAt: `2020-01-01 11:11:11` (string,required) - 更新日時
                + updatedBy: `1` (string,required) - 更新者
                + updatedUserName: `Tanaka` (string,required) - 更新者名
            + customerItem: (object,required) - 顧客商品
                + id: (string,required) - id
                + type: `1` (string,required) - 区分
                + item: (object,required) - 商品
                    + id: (string,required) - id
                    + name: `商品名` (string,required) - 商品名
                + unitType: `1` (string,required) - 単価変更区分
                + collectCustomerItem: (object,optional) - 回収顧客商品
                    + id: (string,required) - id
                    + type: `1` (string,required) - 区分
                    + item: (object,required) - 商品
                        + id: (string,required) - id
                        + name: `商品名` (string,required) - 商品名
                        + unit: `1` (string,required) - 単位
            + quantity: `10` (string,required) - 数量
            + unit: `10` (string,required) - 単位
            + unitPrice: `1000` (string,required) - 単価
            + amount: `10000` (string,required) - 金額
            + comment: `備考` (string,optional) - 備考
            + sort: `1` (string,required) - 並び順
            + createdAt: `2020-01-01 11:11:11` (string,required) - 登録日時
            + createdBy: `1` (string,required) - 登録者
            + createdUserName: `Tanaka` (string,required) - 登録者名
            + updatedAt: `2020-01-01 11:11:11` (string,required) - 更新日時
            + updatedBy: `1` (string,required) - 更新者
            + updatedUserName: `Tanaka` (string,required) - 更新者名
            + deliverySalesDetail: (object,optional) - 納品売上明細
                + id: (string,required) - id
                + quantity: `10` (string,required) - 数量
                + unit: `10` (string,required) - 単位
                + unitPrice: `1000` (string,required) - 単価
                + amount: `10000` (string,required) - 金額
                + comment: `備考` (string,optional) - 備考
                + salesId: `1` (string,required) - 売上id
            + lostSalesDetail: (object,optional) - 紛失売上明細
                + id: (string,required) - id
                + quantity: `10` (string,required) - 数量
                + unit: `10` (string,required) - 単位
                + unitPrice: `1000` (string,required) - 単価
                + amount: `10000` (string,required) - 金額
                + comment: `備考` (string,optional) - 備考
            + collect: (object,optional) - 回収
                + id: (string,required) - id
                + quantity: `1` (string,required) - 数量
                + collectUnit: `部` (string,required) - 回収単位
                + comment: `備考` (string,optional) - 備考