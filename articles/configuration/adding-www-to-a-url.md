<!--
{
  "source": "https://docs.joomla.org/Adding_www_to_a_url",
  "title": "Hinzufügen von www zu einer URL ",
  "description": "", 
  "author": ""
}
-->

## Apache .htaccess Reguläre Ausdrücke

Für eine einfache Lösung fügen Sie Folgendes zu Ihrer `.htaccess`-Datei hinzu:

```bash
    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$ [NC]
    RewriteRule (.*) https://www.example.com/$1 [R=301,L]
```

In diesem Fall wird eine URL der Form `https://example.com/index.php?item=1` zu `https://www.example.com/index.php?item=1` umgeleitet.

Im obigen Beispiel:

* `RewriteCond` definiert eine Testbedingung.
* `%{HTTP_HOST}` verwendet die Host-Variable aus der Anfrage (example.com).
* `!` bedeutet NICHT und `^` bedeutet START - also beginnt nicht mit www.example.com
* `(` und `)` erfassen alles, was zwischen den Klammern für die Rückreferenzverwendung steht.
* `\` verwandelt das nächste Zeichen von einem Steuerzeichen in ein tatsächliches Zeichen
* `.` bedeutet normalerweise jedes Zeichen, aber vorangestellt durch \ bedeutet einen Punkt.
* `?` macht die Übereinstimmung optional
* `$` bedeutet ENDE (des optionalen Abgleichs).
* `[NC]` steht für No Case, also Groß-/Kleinschreibung ignorieren.
* `RewriteRule` ist gültig, wenn die URL nicht mit www. beginnt.
* `(.*)` ist ein Muster, in diesem Fall ein einzelnes Zeichen, das 0- oder mehrmals wiederholt wird und den Pfadteil der URL bedeutet. Es wird als $1 erfasst.
* `https://www.example.com/` ist der Ersatz für den Hostteil der URL.
* `$1` ist der erfasste Pfad.
* `[]` enthält Flags - Anweisungen, was zu tun ist.
* `R=301` ist eine Anweisung, einen "Moved Permanently"-Header zu senden.
* `L` bedeutet Letzte im Satz - wenn eine Übereinstimmung gefunden wurde, ignorieren Sie alle nachfolgenden Regeln.

Eine vollständigere Lösung, die gleichzeitig mehrere andere Kanonisierungsthemen behebt:

```bash
    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]
```

Wenn Sie verstehen möchten, was all dies bedeutet, könnten Sie diese Beiträge lesen:

* [Apache mod_rewrite Einführung](https://httpd.apache.org/docs/2.4/rewrite/intro.html)
* [Einführung in .htaccess-Weiterleitungen](https://www.danielmorell.com/guides/htaccess-seo/redirects/introduction-to-redirects)

*Übersetzt von openai.com*

