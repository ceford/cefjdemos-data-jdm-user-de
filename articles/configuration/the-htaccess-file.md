<!--
{
  "source": "https://docs.joomla.org/Preconfigured_htaccess",
  "title": "Die htaccess.txt Datei ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Ein Apache-Webserver verwendet eine .htaccess-Datei für die spezifische Konfiguration einer Website. Eine vorkonfigurierte htaccess-Datei (`htaccess.txt`) wird mit Joomla ausgeliefert. Sie befindet sich im Joomla-Stammverzeichnis und enthält Anweisungen, um gängige Hacker-Exploits zu vermeiden und SEF-URLs zu implementieren. Wenn Joomla in einem Unterverzeichnis installiert ist, kann es eine zusätzliche `.htaccess`-Datei im übergeordneten Verzeichnis geben. Apache verarbeitet jede von ihnen der Reihe nach.

Die übliche Vorgehensweise besteht darin, die von Joomla bereitgestellte `htaccess.txt` in `.htaccess` umzubenennen, zusammen mit der Auswahl der SEO-Einstellungen im Global Configuration-Panel. Ihr Hosting-Service kann weitere Einstellungen zur .htaccess hinzufügen, daher ist es möglicherweise am besten, Ihre .htaccess-Datei mit einer vorhandenen, systembereitgestellten .htaccess-Datei zusammenzuführen.

### Plattformkonfiguration

Die aktive Datei wird in einer der httpd.conf-Dateien mit folgendem Befehl festgelegt:
```
    AccessFileName .htaccess
```
Standardmäßig ist dies .htaccess (was sie auf Unix-ähnlichen Dateisystemen versteckt macht). Es besteht keine Notwendigkeit, das zu ändern.

Auf der Windows-Plattform könnten Sie es ändern zu:

    AccessFileName htaccess.ini

damit Sie es einfacher bearbeiten können.

Nehmen Sie keine Änderungen an `htaccess.txt` vor, da diese durch ein Joomla-Update überschrieben werden könnte und alle Änderungen verloren gehen.

## Joomla-Updates

Die Datei htaccess.txt kann sich von einer Joomla-Version zur nächsten ändern. Im Zweifelsfall oder wenn nach einem Update seltsame Probleme auftreten, stellen Sie sicher, dass Ihre .htaccess-Datei auf dem neuesten Stand ist. Dies ist der Inhalt der Datei `htaccess.txt`, die mit Joomla 5.1 enthalten ist:

```bash
##
# @package    Joomla
# @copyright  (C) 2005 Open Source Matters, Inc. <https://www.joomla.org>
# @license    GNU General Public License version 2 or later; see LICENSE.txt
##

##
# READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE!
#
# The line 'Options +FollowSymLinks' may cause problems with some server configurations.
# It is required for the use of Apache mod_rewrite, but it may have already been set by
# your server administrator in a way that disallows changing it in this .htaccess file.
# If using it causes your site to produce an error, comment it out (add # to the
# beginning of the line), reload your site in your browser and test your sef urls. If
# they work, then it has been set by your server administrator and you do not need to
# set it here.
##

## MISSING CSS OR JAVASCRIPT ERRORS
#
# If your site looks strange after enabling this file, then your server is probably already
# gzipping css and js files and you should comment out the GZIP section of this file.
##

## OPENLITESPEED
#
# If you are using an OpenLiteSpeed web server then any changes made to this file will
# not take effect until you have restarted the web server.
##

## Can be commented out if causes errors, see notes above.
Options +FollowSymlinks
Options -Indexes

## No directory listings
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>

## Suppress mime type detection in browsers for unknown types
<IfModule mod_headers.c>
    Header always set X-Content-Type-Options "nosniff"
</IfModule>

## Protect against certain cross-origin requests. More information can be found here:
## https://developer.mozilla.org/en-US/docs/Web/HTTP/Cross-Origin_Resource_Policy_(CORP)
## https://web.dev/why-coop-coep/
#<IfModule mod_headers.c>
#    Header always set Cross-Origin-Resource-Policy "same-origin"
#    Header always set Cross-Origin-Embedder-Policy "require-corp"
#</IfModule>

## Disable inline JavaScript when directly opening SVG files or embedding them with the object-tag
<FilesMatch "\.svg$">
  <IfModule mod_headers.c>
    Header always set Content-Security-Policy "script-src 'none'"
  </IfModule>
</FilesMatch>

## These directives are only enabled if the Apache mod_rewrite module is enabled
<IfModule mod_rewrite.c>
    RewriteEngine On

    ## Begin - Rewrite rules to block out some common exploits.
    # If you experience problems on your site then comment out the operations listed
    # below by adding a # to the beginning of the line.
    # This attempts to block the most common type of exploit `attempts` on Joomla!
    #
    # Block any script trying to base64_encode data within the URL.
    RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
    # Block any script that includes a <script> tag in URL.
    RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
    # Block any script trying to set a PHP GLOBALS variable via URL.
    RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
    # Block any script trying to modify a _REQUEST variable via URL.
    RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
    # Return 403 Forbidden header and show the content of the root home page
    RewriteRule .* index.php [F]
    #
    ## End - Rewrite rules to block out some common exploits.

    ## Begin - Custom redirects
    #
    # If you need to redirect some pages, or set a canonical non-www to
    # www redirect (or vice versa), place that code here. Ensure those
    # redirects use the correct RewriteRule syntax and the [R=301,L] flags.
    #
    ## End - Custom redirects

    ##
    # Uncomment the following line if your webserver's URL
    # is not directly related to physical file paths.
    # Update Your Joomla! Directory (just / for root).
    ##

    # RewriteBase /

    ## Begin - Joomla! core SEF Section.
    #
    # PHP FastCGI fix for HTTP Authorization, required for the API application
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
    # -- SEF URLs for the API application
    # If the requested path starts with /api, the file is not /api/index.php
    # and the request has not already been internally rewritten to the
    # api/index.php script
    RewriteCond %{REQUEST_URI} ^/api/
    RewriteCond %{REQUEST_URI} !^/api/index\.php
    # and the requested path and file doesn't directly match a physical file
    RewriteCond %{REQUEST_FILENAME} !-f
    # and the requested path and file doesn't directly match a physical folder
    RewriteCond %{REQUEST_FILENAME} !-d
    # internally rewrite the request to the /api/index.php script
    RewriteRule .* api/index.php [L]
    # -- SEF URLs for the public frontend application
    # If the requested path and file is not /index.php and the request
    # has not already been internally rewritten to the index.php script
    RewriteCond %{REQUEST_URI} !^/index\.php
    # and the requested path and file doesn't directly match a physical file
    RewriteCond %{REQUEST_FILENAME} !-f
    # and the requested path and file doesn't directly match a physical folder
    RewriteCond %{REQUEST_FILENAME} !-d
    # internally rewrite the request to the index.php script
    RewriteRule .* index.php [L]
    #
    ## End - Joomla! core SEF Section.
</IfModule>

## These directives are only enabled if the Apache mod_rewrite module is disabled
<IfModule !mod_rewrite.c>
    <IfModule mod_alias.c>
        # When Apache mod_rewrite is not available, we instruct a temporary redirect
        # of the start page to the front controller explicitly so that the website
        # and the generated links can still be used.
        RedirectMatch 302 ^/$ /index.php/
        # RedirectTemp cannot be used instead
    </IfModule>
</IfModule>

## GZIP & BROTLI
## These directives are only enabled if the Apache mod_headers module is enabled.
## This section will check if a .gz file exists and if so will stream it
##     directly or fallback to gzip any asset on the fly
## If your site starts to look strange after enabling this file, and you see
##     ERR_CONTENT_DECODING_FAILED in your browser console network tab,
##     then your server is already gzipping css and js files and you don't need this
##     block enabled in your .htaccess
<IfModule mod_headers.c>
    # Serve gzip compressed CSS files if they exist
    # and the client accepts gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.css" "$1\.css\.gz" [QSA]

    # Serve gzip compressed JS files if they exist
    # and the client accepts gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.js" "$1\.js\.gz" [QSA]

    # Serve correct content types, and prevent mod_deflate double compression.
    RewriteRule "\.css\.gz$" "-" [T=text/css,E=no-gzip:1,E=no-brotli:1]
    RewriteRule "\.js\.gz$" "-" [T=text/javascript,E=no-gzip:1,E=no-brotli:1]

    <FilesMatch "(\.js\.gz|\.css\.gz)$">
        # Serve correct encoding type.
        Header set Content-Encoding gzip

        # Force proxies to cache gzipped &
        # non-gzipped css/js files separately.
        Header append Vary Accept-Encoding
    </FilesMatch>
</IfModule>
```

*Übersetzt von openai.com*
