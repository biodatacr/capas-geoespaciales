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
    <td>10020</td>      
    <td>territorial</td>
    <td>administrativa</td>
    <td>provincias</td>
    <td>cl10020</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
  <tr>
    <td>cantones.shp</td>
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
    <td>distritos.shp</td>
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
    <td>areas_conservacion.shp</td>
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
    <td>areas_silvestres_protegidas.shp</td>
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
    <td>corredores_biologicos.shp</td>
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
    <td>cuencas_hidrograficas.shp</td>
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
    <td>zonas_vida_holdridge.shp</td>
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
    <td>regiones_climaticas.shp</td>
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
    <td>temperatura_media_1960_2013.shp</td>
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
    <td>temperatura_maxima_1960_2013.shp</td>
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
    <td>temperatura_minima_1960_2013.shp</td>
    <td>temperatura_minima_1960_2013</td>
    <td>10031</td>
    <td>bioclimatica</td>
    <td>temperatura</td>
    <td>temperatura_minima_1960_2013</td>
    <td>cl10031</td>
    <td>valor</td>
    <td>valor</td>
  </tr>
<table>
