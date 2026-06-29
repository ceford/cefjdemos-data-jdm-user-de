<!--
{
  "source": "https://docs.joomla.org/Nginx",
  "title": "Nginx",
  "description": "", 
  "author": ""
}
-->

<a href="http://nginx.org/" rel="nofollow noreferrer noopener">Nginx</a> ist ein leichtgewichtiger Webserver, der etwa <a href="https://en.wikipedia.org/wiki/Nginx" rel="nofollow noreferrer noopener">33%</a> der Webserver über alle Domains hinweg antreibt. Es sei denn, Sie haben spezielle Anforderungen, die einen umfangreicheren Webserver wie Apache erfordern, sind Sie mit Nginx viel besser bedient.

Im Folgenden finden Sie Anweisungen, wie Sie Joomla! mit dem <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">PHP FastCGI-Beispiel</a> zum Laufen bringen.
## Nginx installieren

Für Ubuntu, führen Sie *aptitude install Nginx* aus. Für andere Distributionen verwenden Sie den entsprechenden Paketmanager oder besuchen Sie die <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">Nginx-Installationsseite</a>.

## PHP FastCGI installieren

Für Ubuntu lesen Sie das <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">PHP FastCGI Beispiel</a>.

Für Gentoo wird PHP als FastCGI-Dienst (FPM) ausgeführt, sodass der Nginx-Server PHP als separaten Prozess ausführt:

    # echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
    # emerge php

Die Standardeinstellungen von PHP-FPM sind für die meisten Server gut geeignet. Für spezielle Konfigurationen besuchen Sie die
<a href="http://php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">PHP FPM Seite</a>.

## Konfigurieren von Nginx

Die Nginx-Konfigurationsdateien befinden sich in:

- `/etc/nginx/sites-available/` auf Ubuntu (für Sites, die auf dieser
  Nginx-Instanz laufen)
- `/etc/nginx/nginx.conf` auf Gentoo und Raspbian (Debian optimiert für
  Raspberry Pi)

Hier ist eine Beispielkonfigurationsdatei von Nginx, *joomla.conf*, die Sie
auf all Ihren Nginx-aktivierten Sites wiederverwenden können.

    server {
      listen 80;
        server_name IHRE_DOMAIN;
        server_name_in_redirect off;

        access_log /var/log/nginx/localhost.access_log;
        error_log /var/log/nginx/localhost.error_log info;

        root PFAD_AUF_SERVER;
        index index.php index.html index.htm default.html default.htm;
        # Unterstützung für saubere (auch als Suchmaschinenfreundlich bekannte) URLs
        location / {
            try_files $uri $uri/ /index.php?$args;
        }

        # globale x-content-type-options Header hinzufügen
        add_header X-Content-Type-Options nosniff;

        # Ausführen von Skripten in beschreibbaren Verzeichnissen verweigern
        location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
            return 403;
            error_page 403 /403_error.html;
        }

        location ~ \.php$ {
          fastcgi_pass  127.0.0.1:9000;
          fastcgi_index index.php;
          include fastcgi_params;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include /etc/nginx/fastcgi.conf;
        }

        # Caching von Dateien
        location ~* \.(ico|pdf|flv)$ {
            expires 1y;
        }

        location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
            expires 14d;
        }

    }

Achten Sie auf ein paar Dinge:

1.  Der Parameter *fastcgi_pass* ist auf *127.0.0.1:9000* gesetzt,
    was dem Port entspricht, auf dem FPM zur Abhörung konfiguriert ist. Dies
    bedeutet, dass Sie die PHP-Prozesse auf separaten Servern ausführen können. Auf Gentoo
    können Sie diese Konfiguration in der Datei
    */etc/php/fpm-php5.3/php-fpm.conf/* finden.
2.  Vergessen Sie nicht, IHRE_DOMAIN & PFAD_AUF_SERVER oben je nach
    Ihrer Domain und dem Pfad von Joomla auf Ihrem Server zu ersetzen.

## GZip-Unterstützung

Wenn Sie GZip-Komprimierungsunterstützung benötigen, fügen Sie den folgenden Abschnitt zum *http*-Bereich der Haupt-Nginx-Konfigurationsdatei hinzu:

    gzip on;
    gzip_http_version 1.1;
    gzip_comp_level 6;
    gzip_min_length 1100;
    gzip_buffers 4 8k;
    gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
    gzip_proxied any;
    gzip_disable "MSIE [1-6]\.";

## Quellen

- <a href="https://wiki.gentoo.org/wiki/Nginx"
rel="nofollow noreferrer noopener">Nginx in Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/"
  rel="nofollow noreferrer noopener">Nginx für Windows</a>
- <a
  href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview"
  rel="nofollow noreferrer noopener">Nginx in Ubuntu</a>
- <a
  href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html"
  rel="nofollow noreferrer noopener">Nginx in Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php"
  rel="nofollow noreferrer noopener">PHP-FPM Installation und
  Konfiguration</a>
- <a
  href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/"
  rel="nofollow noreferrer noopener">Komprimierung und Dekomprimierung</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/"
  rel="nofollow noreferrer noopener">Erstellen von NGINX Rewrite-Regeln</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html"
  rel="nofollow noreferrer noopener">Wie Nginx eine Anfrage verarbeitet</a>

*Übersetzt von openai.com*

