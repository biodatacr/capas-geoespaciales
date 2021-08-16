# Capas geoespaciales

```shell
# Provincias
ogr2ogr -t_srs EPSG:4326 -makevalid provincias.shp WFS:"http://geos.snitcr.go.cr/be/IGN_5/wfs" "IGN_5:limiteprovincial_5k" -lco ENCODING=ISO-8859-1
```


## Creación de un ambiente Conda
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
