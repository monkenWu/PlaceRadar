# PlaceRadar
以 CodeIgniter3 與 CHROME 瀏覽器外掛開發之地點評分系統

[立即使用](https://placeradar.monken.tw/)
[Chrome 外掛下載](https://placeradar.monken.tw/chromeExtension.zip)

## 簡介

本團隊將利用台日韓三國之 OpenData 進行分析，搭建 WEB 使用平
台，提供使用者查詢以及比較等服務；開發網頁瀏覽器外掛，幫助使用者
在第三方租屋、購物平台，可以快速的透過本作品之分析結果了解當地狀
況，不需額外開啟搜索改善使用體驗；在資料呈現方面，並非把所有資訊
呈現給使用者，而是使用「人口」與「資源」數量的多寡進行指數設計，
提供使用者一目瞭然的資訊。

## 系統需求

1. PHP 5.6↑
2. Mysql 5.6

## 啟動

1. 於專案根目錄中執行以下指令
```
docker-compose up
```

2. 將專案根目錄中的 ``footprint.sql`` 匯入至資料庫

3. 專案預設連接埠為 `8080` 
    * `localhost:8080`

4. 將 Google Map and Place Token 置入於 

    * `application\views\home\map.php`
        ```javascript=151
		$.fn.tinyMapConfigure({
			'key': '',
			// 載入的函式庫名稱，預設 null
			'libraries': 'places',
			'language':'zh-TW'
		});
        ```
    * `application\controllers\Api.php`
        ```php=135
        $url = 'https://maps.googleapis.com/maps/api/place/textsearch/json?query='.preg_replace('/\s(?=)/', '', $_POST['searchText']).'&key={apiKey}&language='.$_POST['country'];
        ```

### 二、 使用之開放資料概覽
+ 【台】 
  -  鄉鎮戶數及人口數(9701)
	-  犯罪資料
	-  即時交通事故資料
	-  各縣(市)警察局暨所屬分駐(派出)所地址資料
	-  不動產成交案件實際資訊 OpenData
    
+ 【日】 
  -  警視庁の統計（平成 28 年）
	-  区市町村の町丁別、罪種別及び手口別認知数
	-  交通人身事故発生状況(平成 30 年 6 月末)
	-  発生状況・統計
	-  地価公示・地価調査・取引価格情報

+ 【韓】 
  -  National Police _ National Police Officer Address
	-  [Statistics of crime] The crime place of origin (local)
	-  [Statistics of crime] The crime generation site (by place)
	-  성 및 연령별 인구와 인구밀도
	-  교통사고 상세통계
	-  지자체 종합통계

### 資料集(台灣、日本、韓國)

|編號| 主題 | 網址 |原始資料來源|
| --- | --- |--- |--- |
|1| 三國部分資料集 | [三國部分資料集](https://docs.google.com/spreadsheets/d/16t37OKHQAwh8CJ4gBMXeVVhQXtLOO6DFTDxbZbrBCHw/edit#gid=1507801228)|[資料來源](https://www.accupass.com/event/1806221006151202784160)


### 資料集網站(台灣)

|編號| 主題 | 網址 |原始資料來源|
| --- | --- |--- |--- |
|1|鄉鎮戶數及人口數|[鄉鎮戶數及人口數](https://www.ris.gov.tw/346)|[資料來源](https://www.ris.gov.tw/346)
|2|犯罪資料|[犯罪資料](https://data.gov.tw/dataset/14200 )|[資料來源](https://data.gov.tw/)
|3|即時交通事故資料|[即時交通事故資料](https://data.gov.tw/dataset/13139) |[資料來源](https://data.gov.tw/)
|4|各縣(市)警察局暨所屬分駐(派出)所地址資料| [各縣(市)警察局暨所屬分駐(派出)所地址資料](https://data.gov.tw/dataset/5958 )|[資料來源](https://data.gov.tw/)
|5|不動產成交案件實際資訊|[不動產成交案件實際資訊](http://plvr.land.moi.gov.tw/DownloadOpenData)|[資料來源](http://plvr.land.moi.gov.tw/DownloadOpenData)

### 資料集網站(日本)

|編號| 主題 | 網址 |原始資料來源|
| --- | --- |--- |--- |
|1| 警視庁の統計（平成28年） | [警視庁の統計（平成28年）](http://www.keishicho.metro.tokyo.jp/about_mpd/jokyo_tokei/tokei/k_tokei28.html)|[資料來源](http://www.keishicho.metro.tokyo.jp/index.html)
|2| 区市町村の町丁別、罪種別及び手口別認知数 |[区市町村の町丁別、罪種別及び手口別認知数](http://www.keishicho.metro.tokyo.jp/about_mpd/jokyo_tokei/jokyo/ninchikensu.html )|[資料來源](http://www.keishicho.metro.tokyo.jp/index.html)
|3|交通人身事故発生状況(平成30年6月末)|[交通人身事故発生状況(平成30年6月末)](http://www.keishicho.metro.tokyo.jp/about_mpd/jokyo_tokei/tokei_jokyo/traffic_accident.html )|[資料來源](http://www.keishicho.metro.tokyo.jp/index.html)
|4|発生状況・統計|[発生状況・統計](http://www.keishicho.metro.tokyo.jp/about_mpd/jokyo_tokei/index.html) |[資料來源](http://www.keishicho.metro.tokyo.jp/index.html)
|5|地価公示・地価調査・取引価格情報|[地価公示・地価調査・取引価格情報](http://www.land.mlit.go.jp/webland/)|[資料來源](http://www.land.mlit.go.jp/webland/)


### 資料集網站(韓國)

|編號| 主題 | 網址 |原始資料來源|
| --- | --- |--- |---|
|1|開放性資料1|[開放性資料1](https://www.data.go.kr/)|[資料來源](https://www.data.go.kr/)
|2|開放性資料2|[開放性資料2](http://kosis.kr/index/index.do)|[資料來源](http://kosis.kr/index/index.do)
|3|警察局相關資料(2017)|[警察局相關資料(2017)](https://www.data.go.kr/dataset/3075501/fileData.do)|[資料來源](https://www.data.go.kr/)
|4|犯罪統計(2016)|[犯罪統計(2016)](https://www.data.go.kr/dataset/3074462/fileData.do)|[資料來源](https://www.data.go.kr/)
|5|犯罪場所統計(2016)|[犯罪場所統計(2016)](https://www.data.go.kr/dataset/3074463/fileData.do)|[資料來源](https://www.data.go.kr/)
|6|交通事故分類網站|[交通事故分類網站](http://taas.koroad.or.kr/web/shp/sbm/initStatsAnals.do?menuId=WEB_KMP_STA)|[資料來源](http://taas.koroad.or.kr/)
|7|交通事故統計(2017)|[交通事故統計(2017)](https://drive.google.com/file/d/18jxqDc70sKAQxZZJeja1a5AX8IqRzsoS/view?usp=sharing)|[資料來源](http://taas.koroad.or.kr/web/shp/sbm/initStatsAnals.do?menuId=WEB_KMP_STA)
|8|人口密度(2015)|[人口密度(2015)](http://kosis.kr/statHtml/statHtml.do?orgId=110&tblId=DT_11001N_2013_A001&vw_cd=MT_OTITLE&list_id=110_11001_006_01&scrId=&seqNo=&lang_mode=ko&obj_var_id=&itm_id=&conn_path=E1#)|[資料來源](http://taas.koroad.or.kr/web/shp/sbm/initStatsAnals.do?menuId=WEB_KMP_STA)
