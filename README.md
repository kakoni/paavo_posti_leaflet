# Paavo postinumerot and leaflet

Finnish postal number boundaries.

This example app uses stat.fi paavo-postalnumber data, http://www.stat.fi/tup/rajapintapalvelut/paavo.html.
Data has been converted into topojson form and can be found in data/posti.topo.json

Oh do notice, it does take time to initialize.

# Demo
1. http://rawgit.com/kakoni/paavo_posti_leaflet/master/index.html Demonstrates leaflet + l.proj + topojson
2. http://rawgit.com/kakoni/paavo_posti_leaflet/master/d3_test.html d3 + topojson
3. http://rawgit.com/kakoni/paavo_posti_leaflet/master/index_4326.html leaflet + l.omnivore + topojson(4326 formatted)
4. http://rawgit.com/kakoni/paavo_posti_leaflet/master/d3_leaflet.html leaflet + d3 + topojson



# About data conversions
Paavo data was also converted into EPSG:4326 coordinate system using ogr2ogr.
```
ogr2ogr -f GeoJSON -lco ENCODING=UTF-8 -s_srs http://spatialreference.org/ref/epsg/3067/ -t_srs EPSG:4326 posti.geo_4326.json posti.geo.json
```

Topojson was typically run with
```
topojson --id-property posti_alue -p nimi -o posti.topo.json -- posti.geo.json
```
except for simplication case ( `--simplify-proportion 0.1` was used )
