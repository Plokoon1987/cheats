Aguamed application notes (From scratch)
==========================


NOTE: All this commands are intended for Debian based distributions (like
Ubuntu).
PENDING TASK: euskera translation.

## Create File: requirements.txt

Write the following text in a file named requirements.txt

	numpy
	scipy
	matplotlib

	pyexcel
	pyexcel-ods3
	pyexcel-xlsx

	django
	psycopg2



## Installation (development enviroment)

#	virtualenvwrapper

Create a virtual Python environment for the application. If you don't have virtualenvwrapper
installed, do this:

    sudo apt install virtualenvwrapper
    export WORKON_HOME=~/.virtualenvs
    mkdir -p $WORKON_HOME

Add this line to ``~/.bashrc``:

    source /usr/share/virtualenvwrapper/virtualenvwrapper.sh

Now the virtualenv can be created:

    mkvirtualenv -p /usr/bin/python3 aguamed


#	install requirements.txt

Then install all the required libraries dependencies in it:

    pip install -r requirements.txt



Optional: In order to run the desktop GUI interface for test graphics you need
to install also the Python 3 Tk libraries. This step is optional and not
required for the web application to work.

    sudo apt install python3-tk

Install PostgreSQL and PostGis. In Debian or Ubuntu:

    sudo apt install postgresql postgresql-client
    sudo apt install postgis

Then postgresql-X.X-postgis-Y.Y has to be installed, but before doing that we must first
find out the version of PostgreSQL and PostGis installed in our computer:

    apt list --installed
    
Once you have the version of PostgreSQL (X.X) and PostGis (Y.Y) install the package:

    sudo apt install postgresql-X.X-postgis-Y.Y
    
If it is not found, use "apt search postgis" to find the correct package


## Create Database Users (Only if they have not been created for previous projects):

Create a superuser in PostgreSQL (if it already doesn't exist'). Change <username> for your actual linux
account username:

    sudo -u postgres createuser -s <username>

Create a user 'django' with the same password specified in the ``settings.py``
file in the application.

    createuser -P django


## Create new empty database and create postgis extensions

Create the database:

    createdb --encoding=UTF8 --owner=django aguamed

Enter the database:
    
    psql aguamed 

Create the extensions in aguamed:
    
    CREATE EXTENSION postgis;
    CREATE EXTENSION postgis_topology;

Exit psql:
    \q

    
## Create django project and set up settings.py for Postgis

You have to be in the virtual environmet "aguamed":


Create project:

    django-admin startproject aguamed


Edit the file aguamed/aguamed/settings.py in DATABASE:

    DATABASES = {
        'sqlite': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        },
        'default': {
            'ENGINE': 'django.contrib.gis.db.backends.postgis',
            'NAME': 'aguamed',
            'USER': 'django',
            'PASSWORD': '***********',
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }

*Information on 18/07/2017 in: https://docs.djangoproject.com/en/1.11/ref/contrib/gis/tutorial/


Prepare the database schema:

    python manage.py migrate

Create a Django superuser:

    python manage.py createsuperuser

Optional: You can import some initial data for test importing test data from a
spreadsheet:

    python manage.py importods test/ho_chi_minh_stations.xlsx


## Restore from existing backup

This step is not neccessary if you want to start with a empty database.
The procedure for restoring a backup involves three steps:

 1. Deleting the previously existing database. WARNING ! DANGER!
    Be EXTREMELY CAREFUL and check that this command is never typed to a
    production server. Otherwise ALL DATA CAN BE LOST !!!

        # WARNING! WARNING! WARNING!
        dropdb appretio

 2. Creating a new empty database.

        createdb --encoding=UTF8 --owner=django appretio

 3. Loading the backup data to this new database.

        cat mybackupfile.psql | psql appretio


## Javascript libraries

Javascript libraries aren't kept inside the git repository.

    sudo apt-get install npm
    cd budget/static/js
    npm install
    cd ../../..


## CSS code

Generate CSS code from SCSS (SASS). (Paths are relative from project directory).

    sudo apt install sass
    sass budget/budget.scss:budget/static/budget.css


## Start the application

Start the local debug server:

    workon appretio
    python manage.py runserver

Access to the main page of application at http://localhost:8000/
