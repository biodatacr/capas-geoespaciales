## Capas geoespaciales

```shell
# Se utiliza el ambiente conda creado como se muestra en la siguiente sección
$ conda activate biodatacr

# Provincias
$ ogr2ogr \
    -lco ENCODING=ISO-8859-1 \
    -nln provincias \
    -t_srs EPSG:4326 \
    -makevalid \
    provincias.shp \
    WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k"
```  

## Creación del ambiente Conda

```shell
# Actualización de Conda
$ conda update -n base -c defaults conda

# Creación del ambiente
$ conda create -n biodatacr

# Activación del ambiente
$ conda activate biodatacr

# Instalación de módulos
$ conda config --env --add channels conda-forge
$ conda config --env --set channel_priority strict
$ conda install gdal

# Desactivación del ambiente
$ conda deactivate
```
