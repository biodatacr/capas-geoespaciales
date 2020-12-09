# Capas geoespaciales
Capas geoespaciales utilizadas en el portal de datos.

## División territorial administrativa
```shell
# Provincias
ogr2ogr -t_srs EPSG:4326 -makevalid /vsizip/cr-provincias.zip WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k"

# Cantones
ogr2ogr -t_srs EPSG:4326 -makevalid /vsizip/cr-cantones.zip WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitecantonal_5k"

# Distritos
ogr2ogr -t_srs EPSG:4326 -makevalid /vsizip/cr-distritos.zip WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitedistrital_5k"
```
