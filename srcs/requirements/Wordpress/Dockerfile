FROM		debian:bullseye

RUN		apt-get update && apt-get upgrade -y

RUN		apt-get install -y wget\
		php7.4-fpm\
		php7.4-mysql\
		mariadb-client \
		curl 

EXPOSE		9000

COPY		./conf/www.conf /etc/php/7.4/fpm/pool.d/

RUN		mkdir -p /var/run/php

WORKDIR		/var/www/html

RUN		curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
		&& php wp-cli.phar --info 

RUN     	chmod +x wp-cli.phar

RUN     	mv wp-cli.phar /usr/local/bin/wp

RUN		wp --info

COPY		./conf/wp_config.sh .

ENTRYPOINT	["bash", "wp_config.sh"]

