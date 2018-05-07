# PHP 7.0 - apache - composer

Install php7.0 plus all dependecies, enable PECL repository from ppa:ondrej/php, install composer and "prestissimo" package to speedup the installation of packages.

For development purpose mount the volume under the "app" folder, so the files updated there are reloaded in the container running php.

To override php.ini or vhost.conf mount the files when running the container.

----

## build the Dockerfile

```
docker build -t php7-apache .
```

## run

```
docker run -d -p 8090:80 --rm --name php7-apache -v $(pwd)/app/:/var/www/webapp -v $(pwd)/vhost.conf:/etc/apache2/sites-available/000-default.conf -v $(pwd)/php.ini:/etc/php/7.0/apache2/php.ini php7-apache
```

----


## run a shell in the container

```
docker exec -it php7-apache bash
```

From here we can use for example:
```
composer install
```
to install dependecies 
