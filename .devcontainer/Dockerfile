FROM almalinux:9.4

# Install dependencies
RUN dnf install -y epel-release \
    && dnf install -y dnf-utils \
    && dnf config-manager --set-enabled crb \
    && dnf install -y \
        sudo \
        httpd \
        mariadb-server \
        php \
        php-cli \
        php-common \
        php-fpm \
        php-mysqlnd \
        php-pdo \
        php-pgsql \
        php-sqlite3 \
        php-bcmath \
        php-bz2 \
        php-calendar \
        php-ctype \
        php-curl \
        php-dom \
        php-exif \
        php-ffi \
        php-fileinfo \
        php-filter \
        php-ftp \
        php-gd \
        php-gettext \
        php-hash \
        php-iconv \
        php-intl \
        php-json \
        php-ldap \
        php-mbstring \
        php-memcached \
        php-msgpack \
        php-mysqli \
        php-openssl \
        php-pcntl \
        php-pcre \
        php-phar \
        php-posix \
        php-readline \
        php-redis \
        php-session \
        php-shmop \
        php-simplexml \
        php-soap \
        php-sockets \
        php-sodium \
        php-spl \
        php-sqlite3 \
        php-sysvmsg \
        php-sysvsem \
        php-sysvshm \
        php-tidy \
        php-tokenizer \
        php-xml \
        php-xmlreader \
        php-xmlwriter \
        php-xsl \
        php-zip \
        php-zlib \
        php-opcache \
        php-xdebug \
        git \
        unzip \
        curl \
        wget \
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
