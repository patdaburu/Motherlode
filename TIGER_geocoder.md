# Install and Configure the PostGIS TIGER Geocoder

Much of what is written here is excerpted from
*PostGIS in Action, 2nd Edition
Chapter 8*

Go buy a copy right now.

##Create the Extensions

```sh
CREATE EXTENSION fuzzystrmatch;
CREATE EXTENSION postgis_tiger_geocoder;
```

## Grant Permissions to TIGER
PostGIS 2.11 and later create the `tiger` and `tiger_data` schemas in the database where the extension is installed.

### Grant Existing Permissions
Grant permissions on existing objects to the PUBLIC role.
```sh
GRANT USAGE ON SCHEMA tiger to PUBLIC;
GRANT USAGE ON SCHEMA tiger_data to PUBLIC;
```

### Grant Future Permissions
Assign default privileges for future tables created in the `tiger_data` schema.
```sh
GRANT SELECT, REFERENCES, TRIGGER ON ALL TABLES IN SCHEMA tiger to PUBLIC;
GRANT SELECT, REFERENCES, TRIGGER ON ALL TABLES IN SCHEMA tiger_data to PUBLIC;
GRANT EXECUTE ON ALL FUNCTIONS IN SCHEMA tiger TO PUBLIC;
ALTER DEFAULT PRIVILEGES IN SCHEMA tiger_data 
    GRANT SELECT, REFERENCES
        ON TABLES TO PUBLIC;
```


### Load Tiger Data

[See Chapter 8]

### Geocode an Address

```sh
SELECT
	g.rating AS r,
    ST_X(geomout) AS lon,
    ST_Y(geomout) AS lat,
    pprint_addy(addy) AS padress
FROM
	geocode(
        '1116 Killian Blvd SE, Saint Cloud, MN 56304'
    ) AS g;
```

If you misspell part of the address, fuzzy string matching may remedy the mistake.