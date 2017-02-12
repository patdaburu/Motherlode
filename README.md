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
For more information on the [createuser](https://www.postgresql.org/docs/devel/static/app-createdb.html) and [createdb](https://www.postgresql.org/docs/devel/static/app-createdb.html) client applications, check out the [PostgreSQL Client Applications](https://www.postgresql.org/docs/devel/static/app-createdb.html) reference page.

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

####Install pgAdmin
While it's not required, [pgAdmin](https://www.pgadmin.org) is an extremely helpful GUI tool for managing PostgreSQL.

You can [download](https://www.pgadmin.org/download/) installers for the supported platforms, or on Ubuntu you can use `apt-get`.
```sh
sudo apt-get install pgadmin3
```

####Connect pgAdmin to the Mother Database
1. Open pgAdmin.
2. Click _Add a connection to a server._
3. More information coming soon...

###Python Setup
#### Installing and Upgrading `pip` for Python 2.7
`pip` is the preferred Python package manager.  You can get more information about installing and upgrading pip [here](https://packaging.python.org/installing/).


On Ubuntu, you can install `pip` from using `apt-get`.
```sh
sudo apt-get install python-pip
```

You can use `pip` itself to update installed version.
```sh
pip install -U pip setuptools
```

You may see a notification indicating that there is a newer version of `pip` to which you can upgrade.
```sh
pip install --upgrade pip
```

<!--
#### Installing and Upgrading `pip` for Python 3
`pip` is the preferred Python package manager.  You can get more information about installing and upgrading pip [here](https://packaging.python.org/installing/).


On Ubuntu, you can install `pip` from using `apt-get`.
```sh
sudo apt-get install python3-pip
```

You can use `pip` itself to update installed version.
```sh
pip install -U pip setuptools
```

You may see a notification indicating that there is a newer version of `pip` to which you can upgrade.
```sh
pip install --upgrade pip
```

On Ubuntu, `pip` for Python 3 installs into `/usr/lib/python3/dist-packages/pip`.
-->

###GeoAlchemy2
[GeoAlchemy2](http://geoalchemy-2.readthedocs.io/en/latest/) is an object-relational mapper (ORM) for Python and PostGIS.  You can install it using `pip`.

####Install GeoAlchemy2 Dependencies
#####libpq-dev
We need the header files and static library for compiling C programs to work with the libqp library in order to communicate with a PostgreSQL database backend.
```sh
sudo apt-get install libpq-dev
```
#####psycopg2
[Psycopg](http://initd.org/psycopg/) is a PostgreSQL adapter for the Python programming language. 
```sh
sudo pip install psycopg2
```

#####Now We Can Install GeoAlchemy2
```sh
sudo pip install geoalchemy2
```
The GeoAlchemy2 project has a couple of [tutorials](http://geoalchemy-2.readthedocs.io/en/latest/#tutorials) you can use to get started if you're new to the library. 

###Numpy
[NumPy](http://www.numpy.org/) is the fundamental package for scientific computing with Python.

Have a look at the [numpy quickstart tutorial](https://docs.scipy.org/doc/numpy-dev/user/quickstart.html) to get stared.
```sh
sudo pip install numpy
```

###Shapely
[Shapely](https://pypi.python.org/pypi/Shapely) is a BSD-licensed Python package for manipulation and analysis of planar geometric objects. It is based on the widely deployed GEOS (the engine of PostGIS) and JTS (from which GEOS is ported) libraries.

For more information, check out the [Shapely manual](https://toblerity.org/shapely/manual.html).

To install Shapely on Ubuntu, you can use `pip`.
```sh
sudo pip install shapely[vectorized]==1.6b2
```
