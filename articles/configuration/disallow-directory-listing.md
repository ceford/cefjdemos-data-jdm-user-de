<!--
{
  "source": "https://docs.joomla.org/How_do_you_block_directory_scans_using_htaccess%3F",
  "title": "Verzeichnisauflistung verbieten  ",
  "description": "", 
  "author": ""
}
-->

## Hintergrund

Standardmäßig zeigt ein Apache-Webserver bei einem Verzeichnis, das keine konfigurierte Indexdatei (index.html oder index.php) enthält, eine Liste aller Dateien und Unterverzeichnisse im Verzeichnis an. Dies kann auf einem persönlichen Testserver nützlich sein, stellt jedoch ein erhebliches Sicherheitsrisiko auf einem Live-Produktionsserver dar.

Früher war es gängige Praxis, in allen Joomla-Verzeichnissen eine leere index.html-Datei zu platzieren, um dieses Problem auf schlecht konfigurierten Servern zu verhindern. Dies ist nicht mehr der Fall. Es wird erwartet, dass der Server ordnungsgemäß konfiguriert ist, entweder in den Serverkonfigurationsdateien oder in einzelnen .htaccess-Dateien. Ersteres wird bevorzugt, da es auf alle Websites auf dem Server angewendet wird.

Jedoch können Websites in einer Shared-Hosting-Umgebung erwarten, dass jede Website die Serverkonfiguration mit .htaccess-Dateien ändert. Der Server muss auf "AllowOverride Options" oder "AllowOverride All" gesetzt sein, um Überschreibungen in .htaccess zu aktivieren.

## Verwendung von .htaccess

Die mit Joomla gelieferte Datei htaccess.txt kann auf Apache-Servern verwendet werden, indem sie in .htaccess umbenannt oder dorthin kopiert wird. Sie enthält viele Einstellungen, um Hackerangriffe auf Joomla-Seiten abzuwehren. Unter anderem finden Sie die folgenden Einstellungen, um das Auflisten von Verzeichnissen zu verhindern:

```
Options -Indexes

## Keine Verzeichnisauflistungen
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>
```

## Testen Sie Ihre Website

Eine Möglichkeit, Ihre Website zu testen, besteht darin, die URL Ihres Bilderordners in die Adressleiste des Browsers einzugeben: `https://yourdomain.com/images/`. Da der Bilderordner normalerweise keine index.html- oder index.php-Datei enthält, sollten Sie eine völlig leere Seite sehen. Wenn Sie eine Liste aller Dateien und Ordner sehen, verhindern Sie keine Verzeichnis-Scans für irgendeinen Teil Ihrer Website. Beheben Sie das!

*Übersetzt von openai.com*
