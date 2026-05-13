<!--
{
  "source": "https://docs.joomla.org/How_do_you_block_direct_hot_linking_to_image_files_using_htaccess%3F",
  "title": "Hotlinking von Bildern verbieten ",
  "description": "", 
  "author": ""
}
-->

## Definition

Hotlinking ist die Praxis, ein Bild auf einer Website von einem Beitrag auf einer anderen Website zu verlinken. Es kann eine sehr nützliche Praxis sein. Diese Website verwendet viele Bilder, die tatsächlich auf der docs.joomla.org-Website gespeichert sind. Dadurch spart man Zeit und Aufwand für die Erstellung von Screenshots sowie die Bandbreite dieser Seite. Es kann jedoch Urheberrechtsprobleme geben, und Sie möchten möglicherweise verhindern, dass Ihre Bilder auf diese Weise verwendet werden.

Die hier beschriebene Methode verwendet eine *.htaccess* Datei, eine Funktion des Apache-Servers. Andere Webserver können andere Methoden zum Verhindern von Hotlinking bieten.  

## Anweisungen

Fügen Sie den folgenden Code in die *.htaccess*-Datei Ihres Stammverzeichnisses ein.
```
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?yourdomain.com [NC]
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?google.com [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

### Erklärung

* Die erste RewriteCond erlaubt direkte Anfragen über eine URL - ohne Referer.
* Die zweite RewriteCond erlaubt Anfragen von Ihrer eigenen Domain. Das *\[NC\]*
    Flag bedeutet *No Case*, das heißt, es werden sowohl Groß- als auch Kleinbuchstaben berücksichtigt.
* Die dritte RewriteCond erlaubt Anfragen von Google, sodass Ihre Bilder
    dennoch in den Suchergebnissen erscheinen können. Sie können ähnliche Zeilen für andere
    Seiten hinzufügen, die Sie zulassen möchten.
* Die RewriteRule blockiert Anfragen für Bilddateien von allen Domains, die
    zuvor nicht erlaubt wurden. Das F-Flag weist den Browser an, einen Verboten-Header (403) zurückzugeben. L steht für die letzte Regel.

### Hotlinking von bestimmten Domains blockieren

Um Hotlinking nur von bestimmten Domains wie *myspace.com*,
*blogspot.com* und *livejournal.com* zu verhindern, während andere Websites
auf Ihre Bilder verlinken dürfen, verwenden Sie den folgenden Code:

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?myspace\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?blogspot\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?livejournal\.com/ [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```
Sie können so viele verschiedene Domains hinzufügen, wie Sie möchten. Jede *RewriteCond*-
Zeile außer der letzten sollte mit den *\[NC,OR\]* Flags enden. *NC*
bedeutet, die Groß- und Kleinschreibung zu ignorieren. *OR* bedeutet „Oder Nächste“, also diese Zeile
**oder** die nächste Zeile matchen. Die letzte *RewriteCond* lässt das *OR*-Flag weg, um
das Matching nach der letzten *RewriteCond* zu beenden.

*Übersetzt von openai.com*

