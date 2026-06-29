<!--
{
  "source": "https://docs.joomla.org/Search_Engine_Friendly_URLs",
  "title": "Suchmaschinenfreundliche URLs",
  "description": "", 
  "author": ""
}
-->

## Pfade und Routen

SEF-URLs (Suchmaschinenfreundliche URLs) sind sowohl für Menschen als auch für Suchmaschinen sinnvoll, da sie den Pfad zur spezifischen Seite, auf die sie verweisen, erklären. Ein **Pfad** ist der Ort einer Datei in einem Verzeichnisbaum oder seine Simulation im Code. Intern wird der lokale Teil einer SEF-URL (der Teil nach dem Domainnamen) als **Route** bezeichnet. Das Erstellen und Verarbeiten von SEF-URLs wird daher als **Routing** bezeichnet, und der entsprechende Code wird als **Router** bezeichnet.

Suchmaschinenfreundliche URLs können mit den folgenden Schritten aktiviert werden:
* In der **Globalen Konfiguration**
    - die Option **Suchmaschinenfreundliche URLs** auf **Ja** setzen.
    - Die Option **URL-Umschreiben verwenden** auf **Ja** setzen.
    - Optional: Die Option **Suffix zur URL hinzufügen** auf **Ja** setzen.
* Im Stammverzeichnis der Seite htaccess.txt in .htaccess umbenennen, wenn Sie einen Apache-Server verwenden, oder die externe Dokumentation für NginX oder andere Server konsultieren.

Ein Beispiel für Routing kann man in der schrittweisen Veränderung der URL der **Beiträge**-Kategorie-Blogseite in den Beispieldaten sehen.

- Wenn SEF-URLs in der globalen Konfiguration ausgeschaltet und .htaccess deaktiviert ist, ist die URL etwa `https://www.beispiel.com/index.php?option=com_content&view=category&layout=blog&id=16&Itemid=125` und die Breadcrumbs zeigen:<br>
 *Sie sind hier: Startseite / Beispiel-Layouts / Beiträge*
- Mit aktivierten SEF-URLs, aber ohne URL-Umschreibung wird sie zu:
  `https://www.beispiel.com/index.php/beispiel-layouts/beitraege`
- Mit aktivierten SEF-URLs, aktivierter URL-Umschreibung und aktiviertem .htaccess wird sie zu
  `https://www.beispiel.com/beispiel-layouts/beitraege.html` (Suffix zur URL hinzufügen auf Ja gesetzt).

## Zahlen in nicht-SEF-URLs

In dem Teil der URL, der `id=16&Itemid=125` sagt, sind die Zahlen die Parameter, die benötigt werden, um die interne URL zu lokalisieren und die erforderliche Seite anzuzeigen. In diesem Fall ist die erste Zahl die ID einer Kategorie und die zweite Zahl die ID des Kategorie-Blog-Menüpunkts für diese Kategorie.

*Übersetzt von openai.com*

