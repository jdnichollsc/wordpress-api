# wordpress-api
Create a REST API without code using Wordpress &amp; Plugins with docker

## Getting Started

- Run app
```sh
$ docker-compose up -d
$ docker-compose ps # view containers
```
- Update wordpress
```sh
$ docker-compose down
$ docker-compose pull && docker-compose up -d
```

- Stop app
```sh
$ docker-compose stop
$ docker-compose down # removes the containers, keep volumes
$ docker-compose down --volumes # removes the containers, default network, and the WordPress database.
```

- Manage containers manually
```sh
$ docker run -d --name wordpress-db \
        --restart unless-stopped
        --mount source=wordpress-db,target=/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=wordpress \
        -e MYSQL_USER=manager \
        -e MYSQL_PASSWORD=secret
$ docker run -d --name wordpress \
    --link wordpress-db:mysql \
    --mount type=bind,source="$(pwd)"/target,target=/var/www/html \
    -e WORDPRESS_DB_USER=manager \
    -e WORDPRESS_DB_PASSWORD=secret \
    -p 8080:80 \
    wordpress:latest
$ docker container ls # List active containers
$ docker container stop wordpress wordpress-db
$ docker container rm wordpress wordpress-db
$ docker volume rm wordpress_files db_data
```

## Plugins
- Custom Post Type UI: https://wordpress.org/plugins/custom-post-type-ui/
- Advanced Custom Fields: https://wordpress.org/plugins/advanced-custom-fields/
- Advanced Custom Routes: https://wordpress.org/plugins/advanced-custom-routes-custom-endpoints-for-wp-rest-api/

## Docker

- Images:
  * https://hub.docker.com/_/wordpress
  * https://hub.docker.com/_/mysql
  
## Supporting 🍻
I believe in Unicorns 🦄
Support [me](http://www.paypal.me/jdnichollsc/2), if you do too.

## Happy coding
Made with <3

<img width="150px" src="https://github.com/jdnichollsc/jdnichollsc.github.io/blob/master/assets/nicholls.png?raw=true" align="right">
