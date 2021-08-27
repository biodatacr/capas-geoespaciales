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
    temperatura_media_anual.bil
$ zip -m temperatura_media_anual.zip temperatura_media_anual.*

# Precipitación anual
$ gdalwarp \
    -dstnodata -9999 \
    -tr 0.008333333333333 0.008333333333333 \
    -q \
    -cutline provincias.shp \
    -crop_to_cutline wc2.1_30s_bio_12.tif \
    precipitacion_anual.bil
$ zip -m precipitacion_anual.zip precipitacion_anual.*

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
<table>
