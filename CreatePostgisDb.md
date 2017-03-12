####Set the Command Prompt Code Page (Windows)
Before running `psql`, you may need to set the command line code page to prevent a warning and get correct output through the console.
```sh
chcp 1252
```

####Connect to PostgreSQL
```sh
psql -U postgres
```

####Create the `mother` Database
```sh
CREATE DATABASE mother;
```


####Switch to the `mother` Database
```sh
\c mother
```

####Enable PostGIS in the Database
```sh
CREATE EXTENSION postgis;
```

####Verify the Versions of PostgreSQL and PostGIS
```sh
SELECT postgis_full_version();
```

