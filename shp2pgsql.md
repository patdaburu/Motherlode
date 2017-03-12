#Import a TIGER Roads File Into PostGIS Using `shp2pgsql` Using Command Line Tools



## Use `wget` to Download Tiger Files

```sh
wget http://www2.census.gov/geo/tiger/TIGER2012/ROADS/tl_2012_72001_roads.zip --no-parent --relative --recursive --level=2 --accept=zip --mirror
```

## Import the Shapefile into PostGIS
```sh
shp2pgsql -I -W "latin1" -s 4269 tl_2012_72001_roads.shp staging.tiger_roads | psql -U postgres -h localhost -d postgis_in_action
```