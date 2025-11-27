## product
### 案件

|No|Tên logic|Tên vật lý|Kiểu data|length|lov|NotNull|auto|relation|ref_table|comment|productCreateBatch|
|----|-----------|---------------------|---------|--------|-----|----------|----------------|----------|-----------|--------------------------------------------------------------------|-------------|
|1|id|id|bigint|||TRUE|auto_increment||||auto_increment|
|2|受注日|orderDate|date|||TRUE|||||ngày hôm nay|
|3|納品日|deliveryDate|date|||TRUE|||||ngày đối tượng tạo|
|3|顧客id|customerId|bigint|||TRUE||1:N|customer||regularDelivery.customerId|
|4|顧客担当者id|customerStaffId|bigint|||||1:N|customerStaff||regularDelivery.customerStaffId|
|5|営業担当者id|salesStaffId|bigint|||TRUE||1:N|staff||regularDelivery.customerId.salesStaffId|
|6|顧客担当部署|customerSectionName|varchar|100|||||||regularDelivery.customerStaffId.sectionName|
|7|顧客担当者肩書|customerTitle|varchar|100|||||||regularDelivery.customerStaffId.title|
|8|顧客担当者名|customerStaffName|varchar|100|||||||regularDelivery.customerStaffId.name|
|9|納品先区分|customerDeliveryType|tinyint|||TRUE||||0*:顧客<br/>1:顧客納品先|regularDelivery.customerDeliveryType|
|10|顧客納品先id|customerDeliveryId|bigint|||||1:N|customerDelivery||regularDelivery.customerDeliveryId|
|11|顧客種別|type|tinyint|||TRUE||||1*:顧客<br>2:顧客(代行先)|regularDelivery.customerId.type|
|12|配送区分|deliveryStaffType|tinyint|||TRUE||||1*:自社<br/>2:代理店<br>3:外注先|regularDelivery.deliveryStaffType|
|13|担当者id|staffId|bigint|||||1:N|staff||regularDelivery.staffId|
|14|代理店id|agencyId|bigint|||||1:N|agency||regularDelivery.agencyId|
|15|代理店担当者id|agencyStaffId|bigint|||||1:N|agencyStaff||regularDelivery.agencyStaffId|
|16|外注先id|supplierId|bigint|||||1:N|supplier||regularDelivery.supplierId|
|17|社内備考|companyComment|varchar|1000|||||||regularDelivery.comment|
|18|伝票表記備考|comment|varchar|1000|||||||NULL|
|19|税抜金額|amount|bigint|||TRUE||||cho phép âm <br> default:0|giá trị tổng của productDetail.amount|
|21|定期配送id|regularDeliveryId|bigint|||||1:N|regularDelivery||regularDelivery.id|
|22|起点週|startingPointWeek|date||||||||ngày đối tượng tạo|