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
<table>
