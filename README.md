# docker-framadate
Docker images for Framadate

# How to run

## Run the image Framadate PHP Apache
docker run -it -d --name framadate-apache \
	-v "$PWD"/php.ini:/var/www/html/php.ini \
	-p 8080:80 \
	framadate-php5-apache

# How to build

## Build the image Framadate PHP Apache
docker build -t framadate-php-apache:<TAG> \
	--build-arg branch=<TAG> \
	framadate-php-apache

docker build -t framadate-php-apache:latest \
	--build-arg branch=develop \
	framadate-php-apache
