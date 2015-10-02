title: iOS Andriod百度地图仿百度外卖 饿了么 选择我的地址 POI检索
date: 2015-09-19 21:06:26
tags:ios
---
### iOS Andriod百度地图仿百度外卖 饿了么 选择我的地址 POI检索

`百度外卖选择送货地址:`<wid><img src="http://ww1.sinaimg.cn/large/773d7193gw1ew82l06s8aj20jz0zkmze.jpg" width=100 height=200><wid><img src="http://ww1.sinaimg.cn/large/773d7193gw1ew82mf2ldqj20jz0zktat.jpg" width=100 height=200>
`饿了么选择送货地址:`<img src="http://ww1.sinaimg.cn/large/773d7193gw1ew82n6snd1j20jz0zkju8.jpg" width=100 height=200><img src="http://ww1.sinaimg.cn/large/773d7193gw1ew82ng28orj20jz0zkjsx.jpg" width=100 height=200>


[百度地图api官网](http://developer.baidu.com/map/index.php?title=iossdk)

**第一个图**,就是放一个`UIImageView`在`MapView`的中间,然后我们拖动的时候下面地图在跑.
<br><pre>-(void)addMiddleImage{
    UIImageView *imaV=[UIImageView new];
    imaV.center=_mapView.center;
    imaV.bounds=CGRectMake(0, 0, 24, 36);
    imaV.image=[UIImage imageNamed:@"poi_icon"];
    [self.view addSubview:imaV];
}</pre>

### 取屏幕中心点,也就是`UIImageView`的坐标:
`geo.reverseGeoPoint=mapStatus.targetGeoPt;`

geo是`BMKReverseGeoCodeOption *geo;`
移动完成会调用:
<pre>
-(void)mapStatusDidChanged:(BMKMapView *)mapView{
    BMKMapStatus *mapStatus=[mapView getMapStatus];
    geo.reverseGeoPoint=mapStatus.targetGeoPt;
    [_geoSearcher reverseGeoCode:geo];
    NSLog(@"mapStatusDidChanged");
}</pre>

### 回调函数获得反编译结果和周边result.poiList:

<pre>-(void)onGetReverseGeoCodeResult:(BMKGeoCodeSearch *)searcher result:(BMKReverseGeoCodeResult *)result errorCode:(BMKSearchErrorCode)error{
    
    [geoArr removeAllObjects];
    [geoArr addObjectsFromArray:result.poiList];
    if (result.poiList.count) {
        BMKPoiInfo *info=result.poiList[0];
        _city=info.city;
    }
    [_bottomTable reloadData];
}</pre>

### **第二个图**,我开始使用`在线建议查询`,后面发现这个`POI搜索`更好用点,它有三种,我使用的是`POI城市内搜索`:
<br>开始检索:
<br><pre>_bMKPoiSearch =[[BMKPoiSearch alloc]init];
    _bMKPoiSearch.delegate = self;
    BMKCitySearchOption *option=[BMKCitySearchOption new];
//    城市内搜索
    option.city =_city;
    option.keyword  = searchText;
    [_bMKPoiSearch poiSearchInCity:option];</pre>

### 回调返回:
<pre>-(void)onGetPoiResult:(BMKPoiSearch *)searcher result:(BMKPoiResult *)poiResult errorCode:(BMKSearchErrorCode)errorCode{[_suggestionSearchArr removeAllObjects];
    [_suggestionSearchArr addObjectsFromArray:poiResult.poiInfoList];
    [_suggestionTable reloadData];}`</pre>

在`poiResult`里面有`poiInfoList`,成员是`BMKPoiInfo`,跟第一个图一样.

Andriod和这差不多,函数有所区别.有需要demo的朋友可以留邮箱.


