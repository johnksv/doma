# Local development with docker

When developing with docker all functionality is the same as before, 
expect that you don't need to run a LAMP/WAMP/MAMP/XXAMP stack on your machine.

## Prerequisites
- Docker (Docker engine 18.06.0+)

## Debug setup:
In IntelliJ IDEA: Open configuration: `xdebug-doma-in-docker`.
- Set up the server as follows:
- host: localhost
- port: 8080
- dir=`/src` absolute path on server=`/var/www/html`

If you are on a linux machine: 
Change the value of `xdebug.remote_host` in `xdebug-config.ini` 
from `host.docker.internal` to `localhost`.


## First time start
`docker-compose up`

PHP and mysql images will be created during the first run. Therefor this might take longer time then usual.

The mysql-container uses a named volume that is persistent between runs. 

### Start with fresh DB:
`docker-compose up -V`

The `-V`-argument will recreate a new volume.

If you want to also recreate the images, you can use the `--build`-argument. E.g. `docker-compose up --build -V`

### Shut down:
`docker-compose down`

To remove the named volume/database, use `-v` as argument: `docker-compose down -v` 
