# Local development with docker

When developing with docker all functionality is the same as before, 
expect that you don't need to run a LAMP/WAMP/MAMP/XXAMP stack on your machine.

## Prerequisites
- Docker engine 17.06.0+


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


The setup above is tested on macOS Mojave.

## Windows without hyper-v
Windows user without hyper-v can use docker toolbox (https://docs.docker.com/toolbox/toolbox_install_windows/).

The steps below assumes that docker toolbox is installed:
1. Mount doma-folder as a shared volume into the VM with name `default` in virtual box. If the folder path is `D:\projects\doma` then folder name should be `/d/projects/doma`. 
1. Run the `Docker Quickstart Terminal`. Take note of the IP that is printed (`docker is configured to use the default machine with IP <ip>`).
1. Navigate to the folder where doma is placed.
1. Run the project with `docker-compose up`
1. Navigate to `<ip from above>:8080/index.php` or `phpinfo.php`.


Note: debugging is not tested with this setup, yet.