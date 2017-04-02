# Using `ogr2ogr` to Import and Export File Geodatabases

Install GDAL on Windows
http://www.gisinternals.com/query.html?content=filelist&file=release-1800-x64-gdal-2-1-3-mapserver-7-0-4.zip
gdal-201-1800-x64-core.msi (core)
gdal-201-1800-x64-filegdb.msi (filegdb)

GDAL-2.1.3.win-amd64-py3.3.msi

## Import
"C:\Program Files\QGIS 2.18\bin\ogr2ogr.exe" -f PostgreSQL PG:"host='localhost' port='5432' dbname='mother' user='mother' password='mother'" "C:\Users\pblair\Documents\MotherGeo\File Geodatabases\Stearns County MN\Stearns County MN.gdb" -lco SCHEMA=staging -overwrite -progress --config PG_USE_COPY YES

## Export
"C:\Program Files\GDAL\ogr2ogr.exe" --config FGDB_BULK_LOAD YES -progress -append -f "FileGDB" -gt 65535 -sql "SELECT * FROM staging.roads" "C:\Users\pblair\Documents\MotherGeo\Output\Output.gdb" PG:"host='localhost' port='5432' dbname='mother' user='mother' password='mother'" -nln Line -nlt LINESTRING -a_srs "EPSG:4326"



