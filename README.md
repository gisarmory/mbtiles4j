mbtiles4j
=========

一个用 java 语言写的  [MBTiles](https://github.com/mapbox/mbtiles-spec) 瓦片发布程序

本代码库基于 [mbtiles4j](https://github.com/jtreml/mbtiles4j) 库修改而来。原代码库是针对 png 图片的访问，本代码库改为了针对 pbf 文件的访问。感谢原作者！



配置
-------------

编辑 `src/main/resources` 路径下的 `mbtiles4j.properties` ，配置你要发布的 `.mbtiles` 文件

```properties
tile-dbs = db1,db2,db3

db1.path = D:/files/map1.mbtiles
db2.path = D:/files/map2.mbtiles
db3.path = D:/files/map3.mbtiles
```

**别名配置：**tile-dbs = <数据别名>,<数据别名>

`tile-dbs` 配置数据别名，这个别名用于数据的识别，包括配置  `.mbtiles` 文件的路径，和文件发布后浏览器的访问路径。别名支持配置多个，中间用英文逗号分隔。

**文件配置格式：**<数据别名>.path=mbtiles 文件绝对路径

例如：`db1.path` 中的 `db1` 是 `tile-dbs` 中配置的别名，`D:/files/map1.mbtiles` 是文件的绝对路径。

上述配置中，`db1` 内的矢量瓦片在浏览器中的访问地址为：`htp://<address>:<port>/mbtiles4j/db1/z/x/y.pbf`



数据格式
-----------------------

mbtiles4j 发布的 MBTiles 瓦片，遵循 [TMS](http://en.wikipedia.org/wiki/Tile_Map_Service)  瓦片格式规范。



调用示例 (mapboxGL)
-----------------------

这是 [mapboxGL](https://github.com/mapbox/mapbox-gl-js) 调用 mbtiles4j 发布瓦片的示例，关于数据源配置的部分

```json
{
    "sources": {
        "openmaptiles": {
          "type": "vector",
          "scheme": "tms",
          "tiles": ["http://127.0.0.1:7200/mbtiles4j/db1/{z}/{x}/{y}.pbf"],
          "minzoom": 0,
          "maxzoom": 14
        }
	}
}
```



更多背景
-----------------------

[http://gisarmory.xyz/blog/index.html?blog=OSMMbtiles](http://gisarmory.xyz/blog/index.html?blog=OSMMbtiles)



关于
-----------------------

欢迎关注微信公众号《GIS兵器库》