# Capas geoespaciales
Este repositorio contiene las capas del [Portal Geoespacial de BIODATACR]() y los procedimientos empleados para obtenerlas.

## Lista de capas
Las capas se dividen en contextuales y ambientales, de acuerdo con la clasificación empleada en el portal.

### Contextuales (vectoriales)
Todas las capas provienen de archivos Shapefile (.shp) comprimidos (en .zip) con los mismos nombres de las capas.

<table>
  <tr>
    <th>Nombre</th>
    <th>Id</th>      
    <th>Clasificación 1</th>
    <th>Clasificación 2</th>
    <th>Nombre Campo</th>
    <th>Id Campo</th>
    <th>Campo Id en fuente</th>
    <th>Campo descripción en fuente</th>
  </tr>
  <tr>
    <td>provincias</td>
    <td>10020</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>provincias</td>
    <td>cl10020</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>cantones</td>    
    <td>10021</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>cantones</td>
    <td>cl10021</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>distritos</td>
    <td>10022</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>distritos</td>
    <td>cl10022</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>areas_conservacion</td>
    <td>10023</td>      
    <td>territorial</td>
    <td>conservacion</td>
    <td>areas_conservacion</td>
    <td>cl10023</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
   <tr>
    <td>areas_silvestres_protegidas</td>     
    <td>10024</td>
    <td>territorial</td>
    <td>conservacion</td>
    <td>areas_silvestres_protegidas</td>
    <td>cl10024</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>corredores_biologicos</td>    
    <td>10025</td>
    <td>territorial</td>
    <td>conservacion</td>
    <td>corredores_biologicos</td>
    <td>cl10025</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>cuencas_hidrograficas</td>
    <td>10026</td>
    <td>territorial</td>
    <td>hidrografica</td>
    <td>cuencas_hidrograficas</td>
    <td>cl10026</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>zonas_vida_holdridge</td>    
    <td>10027</td>
    <td>bioclimatica</td>
    <td>vegetacion</td>
    <td>zonas_vida_holdridge</td>
    <td>cl10027</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>regiones_climaticas</td>    
    <td>10028</td>
    <td>territorial</td>
    <td>bioclimatica</td>
    <td>regiones_climaticas</td>
    <td>cl10028</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>temperatura_media_1960_2013</td>    
    <td>10029</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>temperatura_media_1960_2013</td>
    <td>cl10029</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>temperatura_maxima_1960_2013</td>
    <td>10030</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>temperatura_maxima_1960_2013</td>
    <td>cl10030</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>temperatura_minima_1960_2013</td>
    <td>10031</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>temperatura_minima_1960_2013</td>
    <td>cl10031</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>precipitacion_anual_1960_2013</td>    
    <td>10032</td>
    <td>bioclimatica</td>
    <td>precipitacion</td>
    <td>precipitacion_anual_1960_2013</td>
    <td>cl10032</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>evapotranspiracion_media_2004</td>    
    <td>10033</td>
    <td>bioclimatica</td>
    <td>evapotranspiracion</td>
    <td>evapotranspiracion_media_2004</td>
    <td>cl10033</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>brillo_solar_2004</td>
    <td>10034</td>
    <td>bioclimatica</td>
    <td>brillo_solar</td>
    <td>brillo_solar_2004</td>
    <td>cl10034</td>
    <td>valor</td>
    <td>valor</td>
  </tr>    
<table>

### Ambientales (raster)
Todas las capas provienen de archivos GeoTIFF (.tif) comprimidos (en .zip) con los mismos nombres de las capas.

<table>
  <tr>
    <th>Nombre</th>
    <th>Id</th>      
    <th>Clasificación 1</th>
    <th>Clasificación 2</th>
    <th>Id Campo</th>
  </tr>
  <tr>
    <td>bio01_temperatura_media_anual_1970_2000</td>
    <td>10035</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>el10035</td>
  </tr>
  <tr>
    <td>bio02_rango_medio_diurno_temperatura_1970_2000</td>
    <td>10036</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>el10036</td>
  </tr>
<table>

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
  
### Contextuales (vectoriales)

```shell
# Se utiliza el ambiente conda.
$ conda activate biodatacr


#
# División territorial administrativa
#

# Provincias
$ rm provincias.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(provincia,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"IGN_5:limiteprovincial_5k\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    provincias.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k"
$ zip -m provincias.zip provincias.*

# Cantones
$ rm cantones.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(canton,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"IGN_5:limitecantonal_5k\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    cantones.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitecantonal_5k"
$ zip -m cantones.zip cantones.*
# Cantones 2 (se usó este método porque estaba fallando la capa en el SNIT. El archivo cantones.geojson se obtuvo a partir de una versión descargada previamente)
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(canton,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geometry FROM cantones" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    cantones.shp \
    cantones.geojson
$ rm cantones.geojson
$ zip -m cantones.zip cantones.*

# Distritos
$ rm distritos.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(distrito,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"IGN_5:limitedistrital_5k\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    distritos.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limitedistrital_5k"
$ zip -m distritos.zip distritos.*


#
# División territorial de conservación
#

# Áreas de conservación
$ rm areas_conservacion.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(nombre_ac,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"PNE:areas_conservacion\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    areas_conservacion.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:areas_conservacion"
$ zip -m areas_conservacion.zip areas_conservacion.*

# Áreas silvestres protegidas
$ rm areas_silvestres_protegidas.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(nombre_asp,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"PNE:areas_silvestres_protegidas\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    areas_silvestres_protegidas.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:areas_silvestres_protegidas"
$ zip -m areas_silvestres_protegidas.zip areas_silvestres_protegidas.*

# Corredores biológicos
$ rm corredores_biologicos.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(nombre_cb,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, SHAPE FROM \"PNE:corredoresbiologicos\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    corredores_biologicos.shp \
    WFS:"http://geos1pne.sirefor.go.cr/wfs" "PNE:corredoresbiologicos"
$ zip -m corredores_biologicos.zip corredores_biologicos.*


#
# División territorial hidrográfica
#

# Cuencas hidrográficas
$ rm cuencas_hidrograficas.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(nombre,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, the_geom FROM \"CENIGA:cuencas_hidrograficas_50k\"" \
    -lco ENCODING=ISO-8859-1 \
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
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(nombre,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"CENIGA:zonas_de_vida_08\"" \
    -lco ENCODING=ISO-8859-1 \
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
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(REGION,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:reg_climaticas_imn\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    regiones_climaticas.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:reg_climaticas_imn"
$ zip -m regiones_climaticas.zip regiones_climaticas.*

# Temperatura media 1960-2013
$ rm temperatura_media_1960_2013.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(RANGO_TEMP,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:Tem_media_CR_60_13\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    temperatura_media_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Tem_media_CR_60_13"
$ zip -m temperatura_media_1960_2013.zip temperatura_media_1960_2013.*

# Temperatura mínima 1960-2013
$ rm temperatura_minima_1960_2013.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(RANGO_TEMP,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:Tem_min_CR_60_13\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    temperatura_minima_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Tem_min_CR_60_13"
$ zip -m temperatura_minima_1960_2013.zip temperatura_minima_1960_2013.*

# Temperatura máxima 1960-2013
$ rm temperatura_maxima_1960_2013.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(RANGO_TEMP,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:Tem_max_CR_60_13\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    temperatura_maxima_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Tem_max_CR_60_13"
$ zip -m temperatura_maxima_1960_2013.zip temperatura_maxima_1960_2013.*

# Precipitación anual 1960-2013
$ rm precipitacion_anual_1960_2013.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(RANGO_PREC,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:anual_pre_60_13\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    precipitacion_anual_1960_2013.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:anual_pre_60_13"
$ zip -m precipitacion_anual_1960_2013.zip precipitacion_anual_1960_2013.*

# Evapotranspiración media 2004
$ rm evapotranspiracion_media_2004.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(POLIGONO,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:Evapotranspiración_Media_Anual_Costa_Rica_2004\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    evapotranspiracion_media_2004.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:Evapotranspiración_Media_Anual_Costa_Rica_2004"
$ zip -m evapotranspiracion_media_2004.zip evapotranspiracion_media_2004.*

# Brillo solar 2004
$ rm brillo_solar_2004.*
$ ogr2ogr \
    -dialect sqlite -sql "SELECT replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(replace(VALOR_1,'Ñ','N'),'Ú','U'),'Ó','O'),'Í','I'),'É','E'),'Á','A'),'ñ','n'),'ú','u'),'ó','o'),'í','i'),'é','e'),'á','a') AS valor, geom FROM \"IMN:brillo_solar_anual_2004\"" \
    -lco ENCODING=ISO-8859-1 \
    -t_srs EPSG:4326 \
    -makevalid \
    brillo_solar_2004.shp \
    WFS:"http://18.218.14.134:8080/geoserver/IMN/wfs" "IMN:brillo_solar_anual_2004"
$ zip -m brillo_solar_2004.zip brillo_solar_2004.*


# Desactivación del ambiente conda
$ conda deactivate
```  
  
### Ambientales (raster)

```shell
# Se utiliza el ambiente conda.
$ conda activate biodatacr
  

#
# WorldClim
#

# Descarga y descompresión del archivo con las 19 variables de Bioclim (https://www.worldclim.org/data/bioclim.html)
$ wget https://biogeo.ucdavis.edu/data/worldclim/v2.1/base/wc2.1_30s_bio.zip
$ unzip wc2.1_30s_bio.zip
  
  
# Para los siguientes comandos, el archivo provincias.shp puede tomarse de las capas contextuales de la sección anterior.
  
# BIO01 Temperatura media anual
$ gdalwarp \
    -dstnodata -9999 \
    -tr 0.008333333333333 0.008333333333333 \
    -q \
    -cutline provincias.shp \
    -crop_to_cutline wc2.1_30s_bio_1.tif \
    bio01_temperatura_media_anual_1970_2000.bil
$ zip -m bio01_temperatura_media_anual_1970_2000.zip bio01_temperatura_media_anual_1970_2000.*
  
# BIO02 Rango medio diurno de temperatura
$ gdalwarp \
    -dstnodata -9999 \
    -tr 0.008333333333333 0.008333333333333 \
    -q \
    -cutline provincias.shp \
    -crop_to_cutline wc2.1_30s_bio_2.tif \
    bio02_rango_medio_diurno_temperatura_1970_2000.bil
$ zip -m bio02_rango_medio_diurno_temperatura_1970_2000.zip bio02_rango_medio_diurno_temperatura_1970_2000.*

  
# Desactivación del ambiente conda
$ conda deactivate
```
