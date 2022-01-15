# Webserver Image
This image is intended for PHP applications running on amd64 (PC) and armv7 (Raspberry).

It includes the following components:
 - php (Modules see below)
 - apache (Module see below)
 - composer
 - node.js and yarn
 - imagemagick and ghostscript (for image and pdf manipulation)

## [PHP Modules]
        bcmath
        Core
        ctype
        curl
        date
        dom
        fileinfo
        filter
        ftp
        gd
        hash
        iconv
        imagick
        intl
        json
        libxml
        mbstring
        mongodb
        mysqli
        mysqlnd
        openssl
        pcre
        PDO
        pdo_mysql
        pdo_sqlite
        Phar
        posix
        readline
        Reflection
        session
        SimpleXML
        sockets
        sodium
        SPL
        sqlite3
        standard
        tokenizer
        xdebug
        xml
        xmlreader
        xmlwriter
        zip
        zlib

## [Apache Modules]
        core_module (static)
        so_module (static)
        watchdog_module (static)
        http_module (static)
        log_config_module (static)
        logio_module (static)
        version_module (static)
        unixd_module (static)
        access_compat_module (shared)
        alias_module (shared)
        auth_basic_module (shared)
        authn_core_module (shared)
        authn_file_module (shared)
        authz_core_module (shared)
        authz_host_module (shared)
        authz_user_module (shared)
        autoindex_module (shared)
        deflate_module (shared)
        dir_module (shared)
        env_module (shared)
        filter_module (shared)
        headers_module (shared)
        mime_module (shared)
        mpm_prefork_module (shared)
        negotiation_module (shared)
        php_module (shared)
        proxy_module (shared)
        proxy_http_module (shared)
        reqtimeout_module (shared)
        rewrite_module (shared)
        setenvif_module (shared)
        socache_shmcb_module (shared)
        ssl_module (shared)
        status_module (shared)

