# 轉換經緯度

## 台灣
- 常見座標：TWD67、TWD97、WGS84，其中 TWD67、TWD97 分別是 1967 年與 1997 年的 Taiwan Datum，台灣才有的地圖座標；WGS84 是國際通用的經緯度座標
- 格式：經緯度、二分帶，其中經緯度係以地球的角度來計算，單位：度(D)、分(M)、秒(S)(1度=60分，1分=60秒)；二分帶座標以公尺為單位，格字都是 1000 公尺為單位(1000M=1KM)
<br>

## 類型簡介
- TWD67(部分地籍圖圖解數化成果)：用傳統天文觀測及三角測量的方式測定經緯度，因為受到地球重力分布不均等因素影響，測出來的經緯度只適合用在台灣附近的局部區域 ＝> EPSG:3821
- TWD97(國土測繪中心發佈全國性資料)：利用衛星打點定位測量的。衛星定位發明後，不僅精度更高，所測得的值更是全球統一的座標系統 ＝> EPSG:3824
- WGS84(全球性資料)：為 GPS 全球定位系统使用所建立的座標系統。通過遍佈世界的衛星觀測站所觀測到的座標建立 ＝> EPSG:4326
- 類型：TWD67 二分帶(如等高線圖)、TWD67 經緯度、TWD97 二分帶(少用)、TWD97 經緯度、WGS84 經緯度(如一般非登山GPS、智慧手機、Google Map)
- 註：TWD97、WGS84 極為相近(誤差很小)

<table border="1" width="15%">
    <tr>
        <th width="5%">類型</a>
        <th width="5%">坐標系統</a>
        <th width="5%">說明</a>
        <th width="5%">代碼</a>
    </tr>
    <tr>
        <td rowspan="5"> 橫麥卡托 (Transverse Mercator) 系 </td>
        <td> TM2 (TWD97，中央經線121度) </td>
        <td> 適用臺灣本島，民國87年之後施行迄今 </td>
        <td> EPSG:3826 </td>
    </tr>
    <tr>
        <td> TM2 (TWD97，中央經線119度) </td>
        <td> 適用澎湖金門馬祖，民國87年之後施行迄今 </td>
        <td>EPSG:3825 </td>
    </tr>
    <tr>
        <td> TM2 (TWD67，中央經線121度) </td>
        <td> 適用臺灣本島，民國69年之後施行 </td>
        <td> EPSG:3828 <a href="http://gis.rchss.sinica.edu.tw/qgis/?p=3542">(內建參數有誤，需自行修正)</a> </td>
    </tr>
    <tr>
        <td> TM3 (TWD67，中央經線121度) </td>
        <td> 適用澎湖金門馬祖，民國69年之後施行 </td>
        <td> EPSG:3827 </td>
    </tr>
    <tr>
        <td> TM2 (TWD97，中央經線119度) </td>
        <td> 適用臺灣本島及澎湖，民國58年之後短暫使用 </td>
        <td> 無EPSG代號 <a href="http://gis.rchss.sinica.edu.tw/qgis/?p=3542">(需自行定義)</a> </td>
    </tr>
    <tr>
        <td rowspan="4"> 經緯度 (Latitude-Longitud) 系 </td>
        <td> WGS84經緯度 </td>
        <td> 全球性資料，如：GPS、kml、geojson</td>
        <td> EPSG:4326 </td>
    </tr>
    <tr>
        <td> TWD97經緯度 </td>
        <td> 國土測繪中心發佈全國性資料 </td>
        <td> EPSG:3824 </td>
    </tr>
    <tr>
        <td> TWD67經緯度 </td>
        <td> 部分地籍圖圖解數化成果 </td>
        <td> EPSG:3821 </td>
    </tr>
    <tr>
        <td> 虎子山經緯度 </td>
        <td> 日治時期陸測地形圖 </td>
        <td> EPSG:4236 </td>
    </tr>
    <tr>
        <td rowspan="2"> 其他 </td>
        <td> Spherical Mercator </td>
        <td> 圖磚、WMS、WMTS等，如：Google Map </td>
        <td> EPSG:3857 </td>
    </tr>
    <tr>
        <td> 虎子山UTM zone 51N </td>
        <td> 中美合作軍用地形圖 </td>
        <td> EPSG:3829 </td>
    </tr>
    <tr>
        <td> 地籍坐標系 </td>
        <td> 地籍坐標 </td>
        <td> 地籍圖、河川地形圖、都市計畫地形圖使用 </td>
        <td> 無EPSG代號，需先轉換成TM2坐標再套圖，單位有分為「間」、「公尺」兩類 </td>
    </tr>
</table>
<br>

## 格式簡介
- 經緯度：由經度、緯度合稱組成一個座標系統，又稱為地理座標系統，它是一種利用三度空間的球面來定義地球上的空間球面座標系統，能夠標示地球上的任何一個位置
- 二分帶：將3D（地球圓球體）投影成平面2D，它將地表隔二度切為一個投影帶，因為切割更細所以其誤差也更小，台灣本島因較狹長所以都在同一投影帶內，不會造成使用上不便，成為國內製作各種圖籍標準

![二分帶](https://github.com/sueshow/Python_Latitude-and-Longitude/blob/master/picture/%E4%BA%8C%E5%88%86%E5%B8%B6_grid_02da.jpg)

![類型分帶](https://github.com/sueshow/Python_Latitude-and-Longitude/blob/master/picture/%E5%88%86%E5%B8%B6%E9%A1%9E%E5%9E%8B.JPG)
<br>

## 地址轉換經緯度
- 方法一：明確名稱，較準確
```
g = geocoder.osm('國立政治大學')
g.json["lat"], g.json["lng"]
g.latlng
```
<br>

- 方法二：完整地址，會有些誤差
```
h = geocoder.arcgis('臺北市中山區集英里權西路35號8樓')
h.json['lat'], h.json['lng']
h.latlng
```
<br>

- 方法三：呼叫 Google API
  - Google API設定：https://tutorials.webduino.io/zh-tw/docs/socket/useful/google-map-1.html
  - 範例：
```
address = '你的地址'
GOOGLE_PLACES_API_KEY = '你的 API KEY'

def get_latitude_longtitude(address, GOOGLE_PLACES_API_KEY):
    # decode url
    # address = urllib.quote(address)
    url = 'https://maps.googleapis.com/maps/api/geocode/json?address=' + address + '&key=' + GOOGLE_PLACES_API_KEY
    
    while True:
        res = requests.get(url)
        js = json.loads(res.text)

        if js['status'] != 'OVER_QUERY_LIMIT':
            time.sleep(1)
            break

    result = js['results'][0]['geometry']['location']
    lat = result['lat'] # 緯度
    lng = result['lng'] # 經度

    return address, lat, lng

get_latitude_longtitude(address, GOOGLE_PLACES_API_KEY)
```

## 參考資料
* https://hiking.biji.co/index.php?q=news&act=info&id=11787
* http://gis.rchss.sinica.edu.tw/qgis/?p=2823
* [座標解讀](https://www.sunriver.com.tw/grid_tm2.htm)
