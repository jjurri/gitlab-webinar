FROM registry.rebrainme.com/testdeploy/images:php7.2-fpm-nginx
COPY . /var/www/html
USER root
RUN chown -R www-data:www-data /var/www/html
USER www-data
RUN rm -rf .git