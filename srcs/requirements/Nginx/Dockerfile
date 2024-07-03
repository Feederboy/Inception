FROM	debian:bullseye

RUN	apt-get -y update\
	&& apt-get -y upgrade\
	&& apt-get -y install nginx \
	openssl\
	vim

RUN		mkdir -p /etc/nginx/ssl

COPY	./conf/default /etc/nginx/nginx.conf

EXPOSE	443

RUN chmod 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html

RUN     openssl req -newkey rsa:2048 -x509 -days 365 -nodes -keyout /etc/nginx/ssl/services.key -out /etc/nginx/ssl/services.pem \
        -subj "/C=FR/ST=Paris/L=Paris/O=42, Inc./OU=IT/CN=Inception"

CMD	["nginx", "-g", "daemon off;"]
