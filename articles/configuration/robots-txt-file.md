<!--
{
  "source": "https://docs.joomla.org/Robots.txt_file",
  "title": "Die robots.txt-Datei",
  "description": "", 
  "author": ""
}
-->

## Über Roboter

Webroboter, auch bekannt als Crawler, Web-Wanderer oder Spider, sind Programme, die das Web automatisch durchlaufen. Unter vielen Anwendungen nutzen Suchmaschinen sie, um Webinhalte zu indexieren.

Die robots.txt-Datei implementiert das [Robots Exclusion Protocol](https://de.wikipedia.org/wiki/Robots_Exclusion_Standard), das es einem Website-Administrator ermöglicht, zu definieren, welche Teile der Seite von bestimmten Roboter-Benutzeragenten nicht inspiziert werden sollten. Beispielsweise ist der Zugriff auf Inhalte öffentlicher Seiten normalerweise erlaubt, aber der Zugriff auf cgi, private und temporäre Verzeichnisse, die keinen indizierten Inhalt haben sollten, wird oft untersagt.

## Wo die *robots.txt*-Datei platziert werden sollte

Eine standardmäßige *robots.txt*-Datei ist im Joomla-Root enthalten. Die *robots.txt*-Datei muss im Stammverzeichnis der Domain oder Subdomain liegen und muss den Namen `robots.txt` tragen.

### Joomla in einem Unterverzeichnis

Eine robots.txt-Datei, die sich in einem Unterverzeichnis befindet, ist nicht gültig. Suchmaschinen-Roboter prüfen diese Datei nur im Stammverzeichnis der Domain. Wenn die Joomla-Site in einem Unterverzeichnis wie *example.com/joomla/* installiert ist, **muss** die *robots.txt*-Datei in das Stammverzeichnis der Site unter *example.com/robots.txt* verschoben werden.

**Hinweis:** Im robots.txt-Datei **muss** der Unterverzeichnisname jedem untersagten Joomla-Pfad vorangestellt sein. Zum Beispiel muss die Disallow-Regel für das `/administrator/`-Verzeichnis in `Disallow: /joomla/administrator/` geändert werden.

## Joomla *robots.txt* Inhalt

Dies ist der Inhalt einer [standardmäßigen Joomla robots.txt-Datei](https://raw.githubusercontent.com/joomla/joomla-cms/refs/heads/5.2-dev/robots.txt.dist):

```
# Wenn die Joomla-Website in einem Ordner installiert ist,
# z.B. www.beispiel.com/joomla/ dann muss die robots.txt-Datei
# in das Stammverzeichnis der Seite verschoben werden
# z.B. www.beispiel.com/robots.txt
# UND der Joomla-Ordnername muss allen
# Pfaden vorangestellt werden.
# z.B. muss die Disallow-Regel für den /administrator/ Ordner
# in folgendes geändert werden
# Disallow: /joomla/administrator/
#
# Weitere Informationen zum robots.txt-Standard finden Sie unter:
# https://www.robotstxt.org/orig.html

User-agent: *
Disallow: /administrator/
Disallow: /api/
Disallow: /bin/
Disallow: /cache/
Disallow: /cli/
Disallow: /components/
Disallow: /includes/
Disallow: /installation/
Disallow: /language/
Disallow: /layouts/
Disallow: /libraries/
Disallow: /logs/
Disallow: /modules/
Disallow: /plugins/
Disallow: /tmp/
```

## Roboterausschluss

Sie können Verzeichnisse ausschließen oder Robots von Ihrer Seite blockieren, indem Sie eine Disallow-Regel in die *robots.txt*-Datei einfügen. Um beispielsweise alle Robots daran zu hindern, das */tmp*-Verzeichnis zu besuchen, fügen Sie folgende Regel hinzu:

    Disallow: /tmp/

Siehe auch:

- [Zugriff auf Ihre Inhalte blockieren](https://support.google.com/webmasters/topic/4598466?hl=de&amp;ref_topic=9427949)
  im Google-Hilfezentrum.

## Syntaxüberprüfung

Zur Syntaxüberprüfung können Sie einen Validator für *robots.txt*-Dateien verwenden. Versuchen Sie einen der folgenden:

- [Testen Sie Ihre <em>robots.txt</em> mit dem robots.txt Tester](https://support.google.com/webmasters/answer/6062598) bei Google.
- [<em>robots.txt</em> Prüfer](http://www.searchenginepromotionhelp.com/m/robots-text-tester/robots-checker.php) von Search Engine Promotion Help.

### Allgemeine Informationen

- [Die Web Robots Seiten](http://www.robotstxt.org/) ist die Hauptwebsite für *robots.txt*.
- [Ein Standard für den Roboterausschluss](http://www.robotstxt.org/orig.html) ist der ursprüngliche Standard.
- [Meta-Tag für Robots, data-nosnippet und X-Robots-Tag-Spezifikationen](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

*Übersetzt von openai.com*  

