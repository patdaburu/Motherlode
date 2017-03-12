#Motherlode

##Development Tool Chain (Windows)
This section contains links and information pertaining to the tools we are using on this project.

###Remarkable Markdown Editor

This is a handy [markdown](https://en.wikipedia.org/wiki/Markdown) editor you can use for documentation.  You can get it from the [Remarkable github](https://remarkableapp.github.io).

###PyCharm
PyCharm is a full-featured Python IDE.  You can download it from  [JetBrains' website](https://www.jetbrains.com/pycharm/download/#section=linux).

###Git
We use [Github](https://github.com/patdaburu/Motherlode) for source control.  You can download Git tools at the [Github Desktop](https://desktop.github.com) page.

###PostgreSQL 9.5 and PostGIS 2.2

(Note: This part of the document is a sketch.  Installing on Windows is a little trickier than Linux, so we're working out the simple instruction set.)

####Install PostgreSQL

http://www.bostongis.com/PrinterFriendly.aspx?content_name=postgis_tut01

You can download PostgreSQL for any supported platform from the [project download page](https://www.postgresql.org/download/).

http://www.bostongis.com/PrinterFriendly.aspx?content_name=postgis_tut01

1. Download the installer and run it.
(Used the password 'postgres' for the postgres user.)
2. Use StackBuilder to install the PostGIS stack.
3. Add postgres.exe to the path.

#####Add the PostgreSQL `bin` Directory to Your Path (Optional)
While it's not absolutely necessary to do so, adding the PostgreSQL `bin` directory to your `%PATH` variable makes it a lot simpler to run commands.  (Also, the rest of this document refers to PostgreSQL application without specifying the path.)
It's here on a default install: C:\Program Files\PostgreSQL\9.6\bin

####Create the Mother User and Database

...used PgAdmin for this


For development, we use the password _'mary'_ as the default for the mother user.

####Test the Connection to PostgreSQL
```sh
psql -h localhost -U mother mother
```
To exit, type `- \q`

A helpful PostgreSQL quickstart tutorial is available at [the PostgeSQL wiki](https://wiki.postgresql.org/wiki/First_steps).


####Add PostGIS 2.2 Support to the Database
The PostGIS Bundle was installed from the Stack Builder.

####Install pgAdmin

(pgAdmin was installed when we installed Postgres.)

While it's not required, [pgAdmin](https://www.pgadmin.org) is an extremely helpful GUI tool for managing PostgreSQL.

You can [download](https://www.pgadmin.org/download/) installers for the supported platforms, or on Ubuntu you can use `apt-get`.


####Connect pgAdmin to the Mother Database

On Windows, this seems to be set up already.

1. Open pgAdmin.
2. Click _Add a connection to a server._
3. More information coming soon...

###Python Setup

For better compatibility with ESRI's [arcpy](http://pro.arcgis.com/en/pro-app/arcpy/get-started/what-is-arcpy-.htm) libraries, this project presently targets [Python 2.7](https://www.python.org/ftp/python/2.7.13/python-2.7.13.msi), which you can get from the [Python download page](https://www.python.org/downloads/), or if you have ArcMap or ArcGIS Pro installed on your computer, you can use ESRI's Python interpreter.

In any case, you should consider adding the Python interpreter to your `%PATH` variable.  This document assumes that when you run commands like `pip`, you are referring to the location of the interpreter you're using with Motherlode.

#### Installing and Upgrading `pip` for Python 2.7
`pip` is the preferred Python package manager.  You can get more information about installing and upgrading pip [here](https://packaging.python.org/installing/).

`pip` is installed by default with the [installer](https://www.python.org/ftp/python/2.7.13/python-2.7.13.msi) from python.org.

If you have multiple version of Python installed, you should consider adding the `Scripts` directory (where `pip` lives) for the one you are using with the Motherlode project to your `%PATH%` variable.  The rest of this document assumes that when you run `pip` you are doing so from the correct location.

Run `pip` from a command line with administrator privileges.

You can use `pip` itself to update installed version.
```sh
pip install -U pip setuptools
```

You may see a notification indicating that there is a newer version of `pip` to which you can upgrade.
```sh
pip install --upgrade pip
```



###GeoAlchemy2
[GeoAlchemy2](http://geoalchemy-2.readthedocs.io/en/latest/) is an object-relational mapper (ORM) for Python and PostGIS.  You can install it using `pip`.

####Install GeoAlchemy2 Dependencies

#####psycopg2
[Psycopg](http://initd.org/psycopg/) is a PostgreSQL adapter for the Python programming language. 
```sh
pip install psycopg2
```

#####Now We Can Install GeoAlchemy2
```sh
pip install geoalchemy2
```
The GeoAlchemy2 project has a couple of [tutorials](http://geoalchemy-2.readthedocs.io/en/latest/#tutorials) you can use to get started if you're new to the library. 

###Numpy
[NumPy](http://www.numpy.org/) is the fundamental package for scientific computing with Python.

Have a look at the [numpy quickstart tutorial](https://docs.scipy.org/doc/numpy-dev/user/quickstart.html) to get stared.
```sh
pip install numpy
```

###Shapely
[Shapely](https://pypi.python.org/pypi/Shapely) is a BSD-licensed Python package for manipulation and analysis of planar geometric objects. It is based on the widely deployed GEOS (the engine of PostGIS) and JTS (from which GEOS is ported) libraries.

You can install Shapely from a Python [wheel](http://pythonwheels.com/) from [this website](http://www.lfd.uci.edu/~gohlke/pythonlibs/#shapely).

On Windows 10, using the latest Windows installer from python.org, the `Shapely‑1.5.17‑cp27‑cp27m‑win32.whl` wheel did the trick.

<!--
You can install shapely from a wheel package at http://www.lfd.uci.edu/~gohlke/pythonlibs/#shapely
You probably want Shapely‑1.5.17‑cp27‑cp27m‑win32.whl (<--this one worked with Python 2.7 from python.org) or Shapely‑1.5.17‑cp27‑cp27m‑win_amd64.whl
-->

You can get more information about installing Shapely from the project's [download page](https://pypi.python.org/pypi/Shapely#downloads).

To learn all about Shapely, check out the [Shapely manual](https://toblerity.org/shapely/manual.html).

####measurement
https://pypi.python.org/pypi/measurement

####pytest
http://doc.pytest.org/en/latest/
