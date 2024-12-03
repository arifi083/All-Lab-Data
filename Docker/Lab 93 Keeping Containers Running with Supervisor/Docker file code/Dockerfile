# Use an official Ubuntu as a parent image
FROM ubuntu:latest

# Install necessary packages (Apache, PHP, MySQL client, supervisor)
RUN apt-get update && \
    apt-get install -y apache2 php libapache2-mod-php mysql-client supervisor && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install MySQL server (choose a root password during installation)
RUN apt-get update && \
    DEBIAN_FRONTEND="noninteractive" apt-get -y install mysql-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Configure Apache
RUN a2enmod rewrite

# Configure supervisord
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Expose ports
EXPOSE 80 3306

# Start supervisord to manage Apache and MySQL services
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
