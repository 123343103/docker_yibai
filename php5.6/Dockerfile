FROM php:5.6-fpm
RUN echo "deb http://ftp.cn.debian.org/debian stretch main" > /etc/apt/sources.list \
	&& echo "deb http://ftp.cn.debian.org/debian-security stretch/updates main" >> /etc/apt/sources.list \
	&& echo "deb http://ftp.cn.debian.org/debian stretch-updates main" >> /etc/apt/sources.list \
	&& apt update \
	&& apt -y install libxml2-dev libzip-dev libjpeg-dev libpng-dev libfreetype6-dev libssl-dev librabbitmq-dev \ 
	&& docker-php-ext-install -j$(nproc) mysqli pdo_mysql bcmath soap zip sockets \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd \
	&& pecl install xdebug-2.5.5 \
	&& pecl install redis-4.3.0 \
	&& pecl install mongo-1.6.16 \
	&& pecl install mongodb-1.5.5 \
	&& pecl install amqp-1.9.4 \
	&& docker-php-ext-enable redis mongo mongodb amqp \
	&& rm -rf /tmp/*
# mongo 依赖 libssl-dev