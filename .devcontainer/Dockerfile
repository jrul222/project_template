FROM almalinux:9.4

# Install dependencies
RUN dnf install -y epel-release && \
    dnf install -y \
    sudo \
    httpd-2.4.57 \
    mariadb-server-10.5.25 \
    php-8.3.9 php-cli php-common php-fpm php-mysqlnd php-pdo php-pgsql php-sqlite3 \
    php-bcmath php-bz2 php-calendar php-ctype php-curl php-dom php-exif php-ffi \
    php-fileinfo php-filter php-ftp php-gd php-gettext php-hash php-iconv php-igbinary \
    php-imagick php-imap php-intl php-json php-ldap php-libxml php-mbstring php-memcached \
    php-msgpack php-mysqli php-mysqlnd php-newrelic php-openssl php-pcntl php-pcre \
    php-phar php-posix php-random php-readline php-redis php-reflection php-session \
    php-shmop php-simplexml php-soap php-sockets php-sodium php-spl php-sqlite3 \
    php-standard php-sysvmsg php-sysvsem php-sysvshm php-tidy php-tokenizer php-uploadprogress \
    php-xml php-xmlreader php-xmlrpc php-xmlwriter php-xsl php-zip php-zlib php-opcache \
    php-xdebug \
    phpmyadmin \
    git unzip curl wget \
    jq \
    nano \
    vim \
    which \
    lsof \
    strace \
    && dnf clean all

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Drush
RUN composer global require drush/drush
ENV PATH="/root/.composer/vendor/bin:$PATH"

# Enable services
RUN systemctl enable httpd mariadb php-fpm

# Expose necessary ports
EXPOSE 80 443 3306 9003

# Start services
CMD ["/usr/sbin/init"]
