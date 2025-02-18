FROM debian:latest

RUN apt update && apt install -y apache2 openssl && rm -rf /var/lib/apt/lists/*

RUN  a2enmod ssl 
RUN  a2ensite novositio.conf
RUN systemctl restart apache2
# Copiar configuración de Apache
COPY config/novositio.conf /etc/apache2/sites-available/novositio.conf
COPY web/novositio.lan/htdocs /var/www/html

RUN a2ensite novositio.conf && a2enmod ssl
CMD ["apachectl", "-D", "FOREGROUND"]
