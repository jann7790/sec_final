FROM php:8.2-apache

RUN docker-php-ext-install mysqli
RUN a2enmod rewrite
ENV APACHE_DOCUMENT_ROOT /var/www/html
# Update DocumentRoot in the default site config
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/000-default.conf
# Update the Listen port in ports.conf
RUN sed -ri -e 's/^Listen 80$/Listen 3000/' /etc/apache2/ports.conf
# Update the VirtualHost port in the default site config
RUN sed -ri -e 's/<VirtualHost \*:80>/<VirtualHost \*:3000>/' /etc/apache2/sites-available/000-default.conf

COPY . /var/www/html/
