#Motherlode

##Devopment Tool Chain
This section contains links and information pertaining to the tools we are using on this project.

###Remarkable Markdown Editor

This is a handy [markdown](https://en.wikipedia.org/wiki/Markdown) editor you can use for documentation.  You can get it from the [Remarkable github](https://remarkableapp.github.io).

###PyCharm
PyCharm is a full-featured Python IDE.  You can download it from  [JetBrains' website](https://www.jetbrains.com/pycharm/download/#section=linux).

###Git
We use [Github](https://github.com/patdaburu/Motherlode) for source control.  You can download Git tools at the [Github Desktop](https://desktop.github.com) page.

On Ubuntu, you can use `apt-get`.

```sh
sudo apt-get update
sudo apt-get install git
```

###PostgreSQL 9.5 and PostGIS 2.2
You can download PostgreSQL for any supported platform from the [project download page](https://www.postgresql.org/download/).

On Ubuntu 16.04 you can install from the repositories.
####Install PostgreSQL
You can use `apt-get` to install PostgreSQL.

```sh
sudo apt-get update
sudo apt-get install -y postgresql postgresql-contrib
```

####Create the Mother User and Database
```sh
sudo -u postgres createuser -P mother
sudo -u postgres createdb -O mother mother
```
For development, we use the password _'mary'_ as the default for the mother user.

####Test the Connection to PostgreSQL
```sh
psql -h localhost -U mother mother
```
To exit, type `- \q`

####Add PostGIS 2.2 Support to the Database
```sh
sudo apt-get install -y postgis postgresql-9.5-postgis-2.2
sudo -u postgres psql -c "CREATE EXTENSION postgis; CREATE EXTENSION postgis_topology;" mother
```

####Instal pgAdmin
While it's not required, PgAdmin is an extremely helpful GUI tool for managing PostgreSQL.
```sh
sudo apt-get install pgadmin3
```

####Connect pgAdmin to the Mother Database
1. Open pgAdmin.
2. Click _Add a connection to a server._
3. More information coming soon...