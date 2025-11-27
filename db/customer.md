## customer
### 顧客

|No|Tên logic|Tên vật lý|Kiểu data|length|lov|NotNull|auto|relation|ref_table|comment|
|----|---------|-------------------|---------|--------|-----|----------|----------------|----------|-----------|-------------------------------------------------------|
|1|id|id|bigint|||TRUE|auto_increment||||
|2|顧客種別|type|tinyint|||TRUE||||1*:顧客<br>2:顧客(代行先)|
|3|気付区分|careType|tinyint|||||||1:Yes|
|4|顧客区分id|customerTypeId|bigint|||||1:N|customerType||
|5|顧客区分その他テキスト|customerTypeText|varchar|100|||||||
|6|承認担当者id|approvalStaffId|bigint|||TRUE||1:N|staff||
|7|代理店id|agencyId|bigint|||||1:N|agency||
|8|顧客名|name|varchar|100||TRUE|||||
|9|顧客名かな|kana|varchar|100||TRUE||||collate：ja-JP-x-icu|
|10|営業担当者id|salesStaffId|bigint|||TRUE||1:N|staff||
|11|顧客名略称|nameAcronym|varchar|100||TRUE|||||
|12|顧客名略称かな|kanaAcronym|varchar|100||TRUE||||collate：ja-JP-x-icu|
|13|郵便番号|zip|varchar|8||||||xxx-xxxx|
|14|都道府県|prefectural|varchar|50|||||||
|15|住所|address|varchar|100|||||||
|16|建物名|buildingName|varchar|100|||||||
|17|電話番号|tel|varchar|20|||||||
|18|FAX|fax|varchar|20|||||||
|19|メールアドレス|email|varchar|100|||||||
|20|取引開始日|startDate|date||||||||
|21|消費税端数区分|taxType|tinyint|||||||1:切り上げ<br/>2:四捨五入<br/>3:切り捨て|
|22|売価端数区分|salesAmountType|tinyint|||||||1:切り上げ<br/>2:四捨五入<br/>3:切り捨て|
|23|締日|closingDate|tinyint|||||||1:月末<br/>2:5日<br/>3:10日<br/>4:15日<br/>5:20日<br/>6:25日|
|24|支払サイト|paymentDate1|tinyint||||||||
|25|支払日|paymentDate2|tinyint|||||||1:月末<br/>2:5日<br/>3:10日<br/>4:15日<br/>5:20日<br/>6:25日|
|26|振込手数料負担|fee|tinyint|||||||1:当社<br/>2:先方|
|27|入金区分|receiveType|varchar|20||||||1:現金小切手<br/>2:三菱UFJ<br>3:十六銀行<br>4:手形<br>5:電債<br>6:郵便局|
|28|請求書印刷区分|invoicePrintType|tinyint|||||||1:発行する<br/>2:発行しない|
|29|請求書区分|invoiceType|tinyint|||||||1*:楽楽明細から請求書出力<br/>2:即時手書き請求書|
|30|債権管理先顧客id|receiveCustomerId|bigint|||TRUE||1:N|customer||
|31|集計先顧客id|aggregateCustomerId|bigint|||TRUE||1:N|customer||
|32|請求先顧客id|invoiceCustomerId|bigint|||TRUE||1:N|customer||
|33|振込名義人|bankAccount|varchar|30|||||||
|34|備考|comment|varchar|3000|||||||
|35|無効フラグ|disableFlag|tinyint|||TRUE||||0*:有効<br/>1:無効|
|36|承認フラグ|approvalFlag|tinyint|||TRUE||||0*:未承認<br/>1:承認済|
|37|楽楽明細コード|rakurakuCode|varchar|30|||||||