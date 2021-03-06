# WordPress Devops (with Docker) - Version 0.1.0

This project want to leave the VVV way for developing WordPress projects and to use a more lightweight and easy way to 
develop by using docker. The WP Devops contains an easy environment which is based on docker. It supports site-, plugin- and theme-development. 

Instead of using the standard [docker wordpress container](https://hub.docker.com/_/wordpress/), WP Devops is using a [docker-compose](https://docs.docker.com/compose/production/) container infrastructure
where everything can be setup in detail.

## Setting up environment

### Requirements

For WP Devops [Composer](https://getcomposer.org/download/) and [Docker](https://www.docker.com/) is required. Please 
install before starting.

### Install

Add WP Devops functionality by using composer. 

```bash
composer require awsmug/wp-devops:dev-master
```

Install the environment by setting up config files. Just follow the instructions. If you have setup a theme or a plugin
installation you can put your code to the ./src directory and it will be displayed in the wp-admin theme or plugin 
section or use the initial plugin or theme files.

```bash
vendor/bin/devops.sh init
```

Start the local server (After the first start, just wait a while until you see a ready installed WordPress):

```bash
./devops.sh up
```

Stop the local server:

```bash
./devops.sh down
```

Updating devops scripts:

```bash
./devops.sh update
```

### Open the site

The site can be reached at http://localhost at the browser. The admin can be reached at http://localhost/wp-admin/.

Use the user 'admin' and password 'password' to login.

### WP-CLI

Use the WP CLI with the wp.sh script. Example to list all plugins (see the documentation of WP CLI at https://wp-cli.org):

```bash
./wp.sh plugin list
```

### Debugging

To debug your script we implemented Xdebug to the PHP configuration. To get it running for your project, just add your 
local IP to the php.ini file. This can be done in the 'conf/php/php.ini' file by replacing the *#DEBUG_REMOTE_IP#* 
string with your local IP. The default remote debugging port is *9000*.

### phpMyAdmin

You can reach the phpMyAdmin interface at the URL http://localhost:8080.

## System

### Configuration

For further settings we have added further configuration files for your individual server configuration. This is a list
of files we offer to setup by yourself:

- conf/nginx/default.conf
- conf/nginx/nginx.conf
- conf/php/php.ini
- conf/php/www.conf

Please be careful on editing this files, this can cause issues to your setup.

### Docker environment

In contrast to the one container structure of the WordPress docker container, the WP Devops is based on a docker-compose 
environment which is a lot more configurable. It contains a docker-compose file for the three types of development for 
sites, themes and plugins. 

The environment contains:

* Nginx
* PHP (with Xdebug)
* Mariadb
* WordPress
* WP-CLI
* phpMyAdmin

### OS

The scripts are tested on Mac OSX. If you have informations or issues on other systems, please report on 
[Github](https://github.com/awsmug/wp-devops/issues).

## Roadmap

We want to add further functionalities to the project which helps your on developing. Further options we want to add:

- Codeception for unit-testing and user testing.
- Use of local domains instead of only localhost.
- Xdebug autoconfig or input of IP address.
- Mailcatcher for catching emails from site.
- Deployment scripts.
