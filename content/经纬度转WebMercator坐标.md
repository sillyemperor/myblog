Title: 经纬度转WebMercator坐标
Date: 2019-06-04
Category: GIS
Tags: GIS,WebMercator,经纬度

输入x_lon,y_lat

输出x_mercator，y_mercator

 num = x_lon * 0.017453292519943295          
 x = 6378137.0 * num          
 a = y_lat * 0.017453292519943295          
 x_mercator = x         
 y_mercator = 3189068.5 * math.log((1.0 + math.sin(a)) / (1.0 - math.sin(a)))