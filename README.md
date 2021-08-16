# Capas geoespaciales
Capas geoespaciales utilizadas en el portal de datos.

```shell
# Provincias
ogr2ogr -t_srs EPSG:4326 -makevalid provincias.shp WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k" -lco ENCODING=ISO-8859-1
```
