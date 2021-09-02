## Creación de ambiente Conda

```shell
# Actualización de Conda
$ conda update -n base -c defaults conda

# Creación del ambiente
$ conda create -n biodatacr

# Activación del ambiente
$ conda activate biodatacr

# Configuración
$ conda config --env --add channels conda-forge
$ conda config --env --set channel_priority strict

# Instalación de módulos
$ conda install gdal

# Desactivación del ambiente
$ conda deactivate
```

## Descarga de capas geoespaciales

```shell
# Se utiliza el ambiente conda creado como se muestra en la siguiente sección
$ conda activate biodatacr


#
# División territorial administrativa
#

# Provincias
$ rm provincias.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln provincias \
    -t_srs EPSG:4326 \
    -makevalid \
    provincias.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k"
$ zip -m provincias.zip provincias.*

# Cantones
$ rm cantones.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln cantones \
    -t_srs EPSG:4326 \
    -makevalid \
    cantones.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitecantonal_5k"
$ zip -m cantones.zip cantones.*

# Distritos
$ rm distritos.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln distritos \
    -t_srs EPSG:4326 \
    -makevalid \
    distritos.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitedistrital_5k"
$ zip -m distritos.zip distritos.*


#
# División territorial de conservación
#

# Áreas silvestres protegidas
$ rm areas_silvestres_protegidas.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln areas_silvestres_protegidas \
    -t_srs EPSG:4326 \
    -makevalid \
    areas_silvestres_protegidas.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:areas_silvestres_protegidas"
$ zip -m areas_silvestres_protegidas.zip areas_silvestres_protegidas.*

# Áreas de conservación
$ rm areas_conservacion.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln areas_conservacion \
    -t_srs EPSG:4326 \
    -makevalid \
    areas_conservacion.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:areas_conservacion"
$ zip -m areas_conservacion.zip areas_conservacion.*

# Corredores biológicos
$ rm corredores_biologicos.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln corredores_biologicos \
    -t_srs EPSG:4326 \
    -makevalid \
    corredores_biologicos.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:corredoresbiologicos"
$ zip -m corredores_biologicos.zip corredores_biologicos.*

#
# Cuencas hidrográficas
#

# Cuencas hidrográficas
$ rm cuencas_hidrograficas.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln cuencas_hidrograficas \
    -t_srs EPSG:4326 \
    -makevalid \
    cuencas_hidrograficas.shp \
    WFS:"http://18.218.14.134:8080/geoserver/CENIGA/wfs" "CENIGA:cuencas_hidrograficas_50k"
$ zip -m cuencas_hidrograficas.zip cuencas_hidrograficas.*


#
# Zonas de vida de Holdridge
#

# Zonas de vida de Holdridge
$ rm zonas_vida_holdridge.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln zonas_vida_holdridge \
    -t_srs EPSG:4326 \
    -makevalid \
    zonas_vida_holdridge.shp \
    WFS:"http://18.218.14.134:8080/geoserver/CENIGA/wfs" "CENIGA:zonas_de_vida_08"
$ zip -m zonas_vida_holdridge.zip zonas_vida_holdridge.*


#
# Clima
#

# Regiones climáticas
$ rm regiones_climaticas.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln regiones_climaticas \
    -t_srs EPSG:4326 \
    -makevalid \
    regiones_climaticas.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:reg_climaticas_imn"
$ zip -m regiones_climaticas.zip regiones_climaticas.*

# Temperatura media 1960-2013
$ rm temperatura_media_1960_2013.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln temperatura_media_1960_2013 \
    -t_srs EPSG:4326 \
    -makevalid \
    temperatura_media_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Tem_media_CR_60_13"
$ zip -m temperatura_media_1960_2013.zip temperatura_media_1960_2013.*

# Temperatura mínima 1960-2013
$ rm temperatura_minima_1960_2013.*
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln temperatura_minima_1960_2013 \
    -t_srs EPSG:4326 \
    -makevalid \
    temperatura_minima_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Tem_min_CR_60_13"
$ zip -m temperatura_minima_1960_2013.zip temperatura_minima_1960_2013.*

#
# WorldClim
#

# Descarga y descompresión
$ wget https://biogeo.ucdavis.edu/data/worldclim/v2.1/base/wc2.1_30s_bio.zip
$ unzip -l wc2.1_30s_bio.zip
$ unzip wc2.1_30s_bio.zip wc2.1_30s_bio_1.tif
$ unzip wc2.1_30s_bio.zip wc2.1_30s_bio_12.tif

# Temperatura media anual
$ gdalwarp \
    -dstnodata -9999 \
    -tr 0.008333333333333 0.008333333333333 \
    -q \
    -cutline provincias.shp \
    -crop_to_cutline wc2.1_30s_bio_1.tif \
    temperatura_media_anual_1970_2000.bil
$ zip -m temperatura_media_anual_1970_2000.zip temperatura_media_anual_1970_2000.*

# Precipitación anual
$ gdalwarp \
    -dstnodata -9999 \
    -tr 0.008333333333333 0.008333333333333 \
    -q \
    -cutline provincias.shp \
    -crop_to_cutline wc2.1_30s_bio_12.tif \
    precipitacion_anual_1970_2000.bil
$ zip -m precipitacion_anual_1970_2000.zip precipitacion_anual_1970_2000.*

# Desactivación del ambiente conda
$ conda deactivate
```  

## Propiedades de las capas

<table>
  <tr>
    <th>Archivo</th>
    <th>Nombre</th>
    <th>Id</th>      
    <th>Clasificación 1</th>
    <th>Clasificación 2</th>
    <th>Nombre Campo</th>
    <th>Id Campo</th>
    <th>Source Id</th>
    <th>Source description</th>
  </tr>
  <tr>
    <td>provincias.shp</td>
    <td>provincias</td>
    <td>10000</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>provincias</td>
    <td>cl10000</td>
    <td>provincia</td>
    <td>provincia</td>
  </tr>
  <tr>
    <td>cantones.shp</td>
    <td>cantones</td>
    <td>10001</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>cantones</td>
    <td>cl10001</td>
    <td>canton</td>
    <td>canton</td>
  </tr>
  <tr>
    <td>distritos.shp</td>
    <td>distritos</td>
    <td>10002</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>distritos</td>
    <td>cl10002</td>
    <td>distrito</td>
    <td>distrito</td>
  </tr>
  <tr>
    <td>temperatura_media_anual_1970_2000.shp</td>
    <td>temperatura_media_anual_1970_2000</td>
    <td>10003</td>      
    <td>climatica</td>
    <td>temperatura</td>
    <td>temperatura_media_anual_1970_2000</td>
    <td>el10003</td>
    <td>temperatura_media_anual_1970_2000</td>
    <td>temperatura_media_anual_1970_2000</td>
  </tr>
  <tr>
    <td>precipitacion_anual_1970_2000.shp</td>
    <td>precipitacion_anual_1970_2000</td>
    <td>10004</td>      
    <td>climatica</td>
    <td>precipitacion</td>
    <td>precipitacion_anual_1970_2000</td>
    <td>el10004</td>
    <td>precipitacion_anual_1970_2000</td>
    <td>precipitacion_anual_1970_2000</td>
  </tr>
  <tr>
    <td>areas_conservacion.shp</td>
    <td>areas_conservacion</td>
    <td>10005</td>      
    <td>territorial</td>
    <td>conservacion</td>
    <td>areas_conservacion</td>
    <td>cl10005</td>
    <td>nombre_ac</td>
    <td>nombre_ac</td>
  </tr>
  <tr>
    <td>areas_silvestres_protegidas.shp</td>
    <td>areas_silvestres_protegidas</td>
    <td>10006</td>      
    <td>territorial</td>
    <td>conservacion</td>
    <td>areas_silvestres_protegidas</td>
    <td>cl10006</td>
    <td>nombre_asp</td>
    <td>nombre_asp</td>
  </tr>
  <tr>
    <td>cuencas_hidrograficas.shp</td>
    <td>cuencas_hidrograficas</td>
    <td>10007</td>      
    <td>territorial</td>
    <td>hidrografica</td>
    <td>cuencas_hidrograficas</td>
    <td>cl10007</td>
    <td>nombre</td>
    <td>nombre</td>
  </tr>
  <tr>
    <td>zonas_vida_holdridge.shp</td>
    <td>zonas_vida_holdridge</td>
    <td>10008</td>      
    <td>bioclimatica</td>
    <td>vegetacion</td>
    <td>zonas_vida_holdridge</td>
    <td>cl10008</td>
    <td>nombre</td>
    <td>nombre</td>
  </tr>
  <tr>
    <td>corredores_biologicos.shp</td>
    <td>corredores_biologicos</td>
    <td>10009</td>      
    <td>territorial</td>
    <td>conservacion</td>
    <td>corredores_biologicos</td>
    <td>cl10009</td>
    <td>nombre_cb</td>
    <td>nombre_cb</td>
  </tr>
  <tr>
    <td>regiones_climaticas.shp</td>
    <td>regiones_climaticas</td>
    <td>10010</td>      
    <td>territorial</td>
    <td>climatica</td>
    <td>regiones_climaticas</td>
    <td>cl10010</td>
    <td>REGION</td>
    <td>REGION</td>
  </tr>
  <tr>
    <td>temperatura_media_1960_2013.shp</td>
    <td>temperatura_media_1960_2013</td>
    <td>10011</td>      
    <td>climatica</td>
    <td>temperatura</td>
    <td>temperatura_media_1960_2013</td>
    <td>cl10011</td>
    <td>RANGO_TEMP</td>
    <td>RANGO_TEMP</td>
  </tr>
  <tr>
    <td>temperatura_minima_1960_2013.shp</td>
    <td>temperatura_minima_1960_2013</td>
    <td>10012</td>
    <td>climatica</td>
    <td>temperatura</td>
    <td>temperatura_minima_1960_2013</td>
    <td>cl10012</td>
    <td>RANGO_TEMP</td>
    <td>RANGO_TEMP</td>
  </tr>
<table>
