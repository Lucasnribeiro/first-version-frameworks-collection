# Use an official PHP 5.3 image with Apache as the base image
FROM orsolin/docker-php-5.3-apache:latest

# Set the working directory inside the container
WORKDIR /var/www/html

# Install mod_rewrite for Apache URL rewriting
RUN a2enmod rewrite

# Copy the entire project into the container
COPY . .

ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Expose the port on which Apache will listen (optional, as it's already exposed in the base image)
EXPOSE 80