<!--
{
  "source": "https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache",
  "title": "SEF-URLs auf Apache ",
  "description": "", 
  "author": ""
}
-->

## Überprüfen, ob .htaccess aktiviert ist

Stellen Sie sicher, dass Ihre Apache-Konfigurationsdatei .htaccess-Overrides zulässt. Sie müssen sicherstellen, dass Overrides aktiviert sind, da die .htaccess-Datei im Stammverzeichnis Ihres Joomla! ignoriert wird oder einen Fehler verursacht. In dem Abschnitt Ihrer virtuellen Host-Konfigurationsdatei oder in der Hauptkonfigurationsdatei (`httpd.conf`) müssen Sie etwas Ähnliches wie im folgenden Beispiel haben, das Overrides aktiviert:

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[eine Option],[eine Option],...
</Directory>
```

Es gibt andere Möglichkeiten, um zu testen, ob `.htaccess` aktiviert ist, wenn Sie keinen Zugriff auf die Konfigurationsdateien Ihrer Website haben. Bitte beziehen Sie sich auf das <a href="http://httpd.apache.org/docs/current/howto/htaccess.html" rel="nofollow noreferrer noopener">.htaccess-Tutorial</a>, das auf der Website der <a href="http://www.apache.org/" rel="nofollow noreferrer noopener">Apache Software Foundation</a> zu finden ist, um zusätzliche Informationen zu erhalten.

## Schritt für Schritt

Dies sind Schritt-für-Schritt-Anleitungen. Bitte befolgen Sie sie in der hier angegebenen Reihenfolge. Wenn ein Schritt fehlschlägt, **fahren Sie nicht fort**, bis Sie das Problem gelöst haben.

1. Benennen Sie die Datei `"htaccess.txt"` in Ihrem Joomla!-Basisordner in `".htaccess"` um.
2. *Dieser Schritt ist möglicherweise nicht notwendig.* Öffnen Sie `.htaccess` in einem Texteditor. Entfernen Sie den Kommentar bei `RewriteBase /` (entfernen Sie das erste Zeichen, \#). Wenn Joomla in einem eigenen Ordner installiert ist, geben Sie den Joomla-Ordnernamen nach dem Schrägstrich ein, z.B. `RewriteBase /ihrjoomlaordner`.
3. Melden Sie sich am Backend an und öffnen Sie die Globale Konfiguration.
4. Aktivieren Sie die Option **Apache mod_rewrite/URL-Umschreiben verwenden** und *speichern* Sie. Diese Option nutzt die Apache *mod_rewrite*-Funktion, um den "index.php"-Teil der URL zu eliminieren.

    Überprüfen Sie, ob Ihre Website korrekt funktioniert. Ihre URLs sollten jetzt so aussehen:

        http://www.beispiel.com/the-news/1-latest-news/1-welcome-to-joomla

    Wenn diese Option Fehler verursacht, sehen Sie bitte
    [How to check if mod rewrite is enabled on your server](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server).

    - Falls es nicht aktiviert ist und Sie Zugang zur Datei `apache/conf/httpd.conf` haben, öffnen Sie diese Datei und prüfen Sie, ob die Zeile `LoadModule rewrite_module modules/mod_rewrite.so` nicht auskommentiert ist. Falls notwendig, kommentieren Sie die Zeile aus und starten Sie den Apache-Webserver neu.
    - Wenn *mod_rewrite* nicht aktiviert werden kann, lassen Sie diese Option deaktiviert. Es spielt keine Rolle, wenn Sie die `.htaccess`-Datei umbenannt lassen.
5. *Wenn Sie dies für notwendig erachten*, aktivieren Sie **Suffix zu URLs hinzufügen** und *speichern* Sie. Diese Option fügt `.html` am Ende der URLs hinzu. Es gibt verschiedene Meinungen darüber, ob dies notwendig oder sogar nützlich ist. Suchmaschinen scheint es egal zu sein, ob Ihre URLs auf `.html` enden oder nicht.
6. Öffnen Sie den Plugin-Manager und aktivieren Sie das **System - SEF-Plugin**. Dieses Plugin fügt Ihren Joomla-Beiträgen SEF-Unterstützung hinzu. Es arbeitet direkt am HTML und benötigt keinen speziellen Tag.

*Übersetzt von openai.com*  



