# GUPriceTracker

## LineBot ID
**@111lduho**

## 使用說明
於Line聊天室輸入
"特價追蹤 (商品序號六位數)"  
例如:
`特價追蹤 349330`

## 使用情境
* 現場逛GU時發現某件衣服很好看，但是太貴了先把商品標籤、商品序號拍起來，等特價再買，但是通常特價的時候都忘記了。
* 在家躺在沙發突然想起來圖庫存著之前想買但是太貴的衣服照片，趕快用LineBot查看看特價沒、還有沒有庫存。

## 目標
**User透過line bot獲得GU的特價資訊**


## 功能
* 爬蟲每日抓取官網資訊
* Mongo資料庫儲存資訊
* Line bot後臺開發，記錄使用者追蹤的商品編號，並回送特價資訊
* Django API傳接後端數據


## 需求
- [X] 資料庫記錄商品資訊
- [X] 使用者追蹤商品編號
- [X] 獲取商品存貨狀態
- [ ] 商品歷史特價紀錄
- [ ] 爬蟲腳本執行時間每次不超過10分鐘(當前為17-20mins，依網路速度)


## 資料庫欄位
> product (商品主檔)
>>productcode (商品編號, Ex:u0000000009343)
>>
>>code (商品序號, Ex:349330)
>>
>>fullname (品名, Ex:女裝 抗UV短版開襟外套(長袖) 349330)
>>
>>url (商品網址, "https://www.gu-global.com/tw/zh_TW/product-detail.html?productCode=u0000000009343")

>price
>>productcode (商品編號)
>>
>>updatetime (腳本更新時間)
>>
>>issale (是否特價中)
>>
>>minprice (最低價格)
>>
>>originprice (原始價格)
>>
>>options (陣列, 存放其它顏色尺寸資訊)

>stock
>>productcode (商品編號)
>>
>>stocks (顏色尺寸存貨資訊)
>>
>>webstock (網路商店庫存)
>>
>>storestock (實體商店庫存)

>usertracks
>>userid (line user token)
>>productcode (商品編號)

### 待新增功能
- [ ] 優化爬蟲腳本
- [ ] 商品歷史價格圖表
- [ ] LineBot user端新增庫存查詢功能(顏色尺寸詳細資料)
- [ ] Server移至雲端


