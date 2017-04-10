FROM php:5.6-apache
MAINTAINER "Olivier Perez <olivier@olivierperez.fr>"

ARG branch=master

RUN apt-get update && \
	apt-get install -y \
                git && \
# PHP extensions
	apt-get install -y \
		libfreetype6-dev \
	        libjpeg62-turbo-dev \
	        libmcrypt-dev \
	        libpng12-dev \
	        zlib1g-dev libicu-dev g++ \
	        php5-mysqlnd && \

	docker-php-ext-install -j$(nproc) iconv mcrypt && \
	
	docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
	docker-php-ext-install -j$(nproc) gd && \

	docker-php-ext-install mysqli mysql pdo pdo_mysql && \

	docker-php-ext-configure intl && \
	docker-php-ext-install intl && \

# Framadate
	git clone https://framagit.org/framasoft/framadate.git ./ && \
	git checkout ${branch} && \
	curl https://getcomposer.org/installer | php -- --quiet && \
	php composer.phar install && \
	mkdir tpl_c && \
	chown -R www-data:www-data . && \

# Clean
	apt-get autoremove -y --purge git

