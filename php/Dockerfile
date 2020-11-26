FROM php:7.4-fpm

RUN apt-get update && apt-get install -y sudo

# Install xdebug
RUN pecl install xdebug-3.0.0 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.client_host=172.17.0.1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.force_display_errors=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#    && echo "xdebug.client_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.discover_client_host=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.max_nesting_level=500" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini


# Add user and group
RUN groupadd -g 1000 app && \
    useradd -g 1000 -u 1000 -d /var/www -s /bin/bash app


RUN echo "app ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/app && \
    chmod 0440 /etc/sudoers.d/app

USER app
WORKDIR /var/www/html
