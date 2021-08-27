## Capas geoespaciales

```shell
# Se utiliza el ambiente conda creado como se muestra en la siguiente sección
$ conda activate biodatacr

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
    
# Desactivación del ambiente conda
$ conda deactivate
```  

## Creación del ambiente Conda

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
