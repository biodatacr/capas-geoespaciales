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

# WorldClim
$ wget https://biogeo.ucdavis.edu/data/worldclim/v2.1/base/wc2.1_30s_bio.zip

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
