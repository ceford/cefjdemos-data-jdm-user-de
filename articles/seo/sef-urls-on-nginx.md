<!--
{
  "source": "https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx",
  "title": "SEF-URLs auf Nginx ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Suchmaschinenfreundliche (SEF), lesbare oder saubere URLs sind solche, die sowohl für Menschen als auch für Suchmaschinen verständlich sind, da sie den Pfad zur spezifischen Seite erklären, auf die sie verweisen. Joomla! ist in der Lage, URLs in jedem Format zu erstellen und zu interpretieren, einschließlich SEF-URLs. Dies ist unabhängig vom URL-Umschreiben, das normalerweise vom Webserver ausgeführt wird, sodass es funktioniert, auch wenn Joomla! auf einem Server läuft, der kein Apache mit dem mod_rewrite-Modul ist. Die SEF-URLs folgen einem bestimmten festen Muster, aber der Benutzer kann für jedes Segment der URL einen kurzen, beschreibenden Text (Alias) definieren.

Intern wird der lokale Teil einer SEF-URL (der Teil nach dem Domainnamen) als Route bezeichnet. Das Erstellen und Verarbeiten von SEF-URLs wird daher als Routing bezeichnet, und der zugehörige Code wird als Router bezeichnet.

Dieser Beiträge befasst sich mit SEF-URLs unter dem beliebten, quelloffenen Nginx-Webserver.

## Schritte für NginX-Server¶

- Fügen Sie den folgenden Code zu Ihrer Server- (vhost) Konfiguration in der nginx.conf-Datei hinzu:

```
    # Unterstützung für Clean (auch Suchmaschinenfreundliche) URLs
    location / {
       try_files $uri $uri/ /index.php?$args;
    }
```
- Wenn das oben genannte nicht funktioniert, fügen Sie den folgenden Code zu Ihrer Serverkonfiguration in der nginx.conf-Datei hinzu: (Dies funktionierte mit nginx 1.4.6 auf Ubuntu.)
```
    server {
      ....
      location / {
      expires 1d;

      # Ermöglichen Sie Joomla SEF URLs in Nginx
      try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```
- Melden Sie sich in Ihrem Backend an und öffnen Sie die Globale Konfiguration
- Aktivieren Sie die Option **Suchmaschinenfreundliche URLs** und speichern Sie. Diese Option konvertiert die URLs vom nativen Joomla!-Format in das SEF-Format. Überprüfen Sie, ob Ihre Website korrekt funktioniert. Ihre URLs sollten nun aussehen wie `http://www.example.com/index.php/the-news/1-latest-news/1-welcome-to-joomla`. Wenn Ihre Website nicht korrekt funktioniert, siehe [Warum wird Ihre Seite durcheinander, wenn Sie SEF (Suchmaschinenfreundliche URLs) einschalten?](https://docs.joomla.org/Why_does_your_site_get_messed_up_when_you_turn_on_SEF_(Search_Engine_Friendly_URLs)%3F)
- Aktivieren Sie die Option **Verwenden Sie Apache mod_rewrite/URL-Umschreibung** und speichern Sie. Diese Option verwendet die Apache mod_rewrite-Funktion, um den Teil *index.php* der URL zu entfernen. Überprüfen Sie, ob Ihre Website korrekt funktioniert. Ihre URLs sollten nun aussehen wie `http://www.example.com/the-news/1-latest-news/1-welcome-to-joomla`. Wenn diese Option Fehler verursacht, siehe [Wie überprüft man, ob mod_rewrite auf Ihrem Server aktiviert ist](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server). Wenn es nicht aktiviert ist und Sie Zugriff auf die Datei `apache/conf/httpd.conf` haben, öffnen Sie diese Datei und überprüfen Sie, ob die Zeile `LoadModule rewrite_module modules/mod_rewrite.so` nicht auskommentiert ist. Falls erforderlich, heben Sie die Auskommentierung der Zeile auf und starten Sie den Apache-Webserver neu. Wenn *mod_rewrite* nicht aktiviert werden kann, lassen Sie diese Option deaktiviert. Es spielt keine Rolle, ob Sie die `.htaccess`-Datei umbenennen.
- *Falls Sie dies für notwendig halten*, aktivieren Sie **Suffix zu URLs hinzufügen** und *speichern Sie*. Diese Option fügt `.html` am Ende der URLs hinzu. Es gibt unterschiedliche Meinungen darüber, ob dies notwendig oder sogar nützlich ist. Suchmaschinen scheint es egal zu sein, ob Ihre URLs mit `.html` enden oder nicht.
- Öffnen Sie den Plugin-Manager und aktivieren Sie das Plugin **System - SEF**. Dieses Plugin fügt SEF-Unterstützung zu Links in Ihren Joomla-Beiträgen hinzu. Es arbeitet direkt auf dem HTML und erfordert keine spezielle Markierung.

*Übersetzt von openai.com*

