# WP-docker-devEnv

A ready to use docker enviroment for develop wordpress sites, plugins or templates. inspired by the [official docker wordpress docker-compose example
](https://hub.docker.com/_/wordpress/)

it use mariadb, and wordpress fpm / linux alpine docker images.

## Note

**This is a dev enviroment and it's not optimise for use in production. Use it at your own risk**

## Getting Started
- first set the **.env** file. go to the root of this project:

  ```` bash
    cp .env.model .env
  ````
  .env contains 4 variables:
  - WORDPRESS_DB_USER (database user for connect database and wordpress)
  - WORDPRESS_DB_PASSWORD (User password)
  - WORDPRESS_DB_NAME (database name)
  - MYSQL_ROOT_PASSWORD (maria server root password)

  the user and database will be set in mariadb and wordpress automatically.

- Create the diectory src:

  ````` bash
    «mkdir src
  `````

- The directories:
  - src: Here should be the wordpress code, if you left empty a new wordpress installation will be automatically installed. usefull for dev templates and/or plugins. or you can fill this directory with your entire worpress site, it will run automatically and your wp-comfig file will be automatically update with the values from .env file.

  - db_dump: here you can put a sql file containing your site, this file will be automatically apply at first run. really practique for charge a database copy from your site.

  - db_data: this will be automatically fill by mariadb with the database data. practique for deep database debug and preserve database data.

## RUN
Mariadb image need a moment for start running create the database, user and apply the sql files. So for prevent errors during the first UP I recommend start mariadb service first, waith a 5 minutes (you can see at db_data directory when your database is complete charge) and after run wordpress service.

`````
docker-compose up -d mariadb
`````

wait 5 min and after run:

`````
docker-compose up -d wordpress
`````

Done, you're ready for use this dev enviroment for create amazing wordpress things!!

The next times you can run both containers at the same time, just use

`````
docker-compose up -d
`````





