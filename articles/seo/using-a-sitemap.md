<!--
{
  "source": "https://docs.joomla.org/Using_A_Sitemap",
  "title": "Die Verwendung einer Sitemap ",
  "description": "", 
  "author": ""
}
-->

## Verwendung einer Sitemap

Während Suchmaschinen Ihre Seiten normalerweise über Links von anderen Orten im Internet finden können, ist es eine gute Praxis, eine Sitemap zu erstellen, die Suchmaschinen-Bots eine Liste der Seiten auf Ihrer Website gibt - denken Sie daran als eine Karte, um alle Inhalte auf Ihrer Website zu finden. Sitemaps sind nicht nur für Suchmaschinen wichtig, sie sind auch sehr hilfreich für Menschen mit Behinderungen, die möglicherweise eine einfache Benutzeroberfläche benötigen, um die Struktur Ihrer Website zu sehen und sich ohne Ihre Menüstrukturen auf der Website zu bewegen. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html" rel="nofollow noreferrer noopener">W3C Working Group Note zu Sitemaps</a>

Eine Sitemap erfüllt mehrere Zwecke:

- Bietet eine strukturierte Liste, die einen Überblick über alle Inhalte auf Ihrer Website zeigt
- Ermöglicht es einem Besucher, schnell einen Überblick über die Struktur Ihrer Website zu erhalten
- Bietet eine alternative Möglichkeit, auf Ihrer Website zu navigieren, ohne komplexe Menüstrukturen zu nutzen
- Bietet Suchmaschinen eine Möglichkeit, Inhalte zu finden, die möglicherweise nicht über Ihre Menüstrukturen zugänglich sind (z. B. Landing Pages)

### Arten von Sitemaps

Es ist möglich, Sitemaps für bestimmte Arten von Informationen bereitzustellen, einschließlich:

- Video <a href="https://support.google.com/webmasters/answer/80471" rel="nofollow noreferrer noopener">Google-Hilfe zu Video-Sitemaps</a>
- Bilder <a href="https://support.google.com/webmasters/answer/answer.py?answer=178636" rel="nofollow noreferrer noopener">Google-Hilfe zu Bild-Sitemaps</a>
- Nachrichten <a href="https://support.google.com/news/publisher/answer/75717" rel="nofollow noreferrer noopener">Google-Hilfe zu Nachrichten-Sitemaps</a>
- International <a href="https://support.google.com/webmasters/answer/2620865?hl=en&amp;ref_topic=2370587" rel="nofollow noreferrer noopener">Google-Hilfe zu internationalen Sitemaps</a>

Diese speziellen Sitemaps ermöglichen es Ihnen, Informationen in Bezug auf den spezifischen Medientyp bereitzustellen - zum Beispiel können Sie bei einer Video-Sitemap Informationen über die Laufzeit, Kategorie und familienfreundlichen Status bereitstellen; bei Bild-Sitemaps können Sie das Motiv des Bildes, seine Nutzungslizenz und den Bildtyp angeben.

### Erstellen einer Sitemap

Bei einer statischen Website besteht das Erstellen einer Sitemap einfach darin, eine XML-Datei manuell zu erstellen, die den entsprechenden Standards entspricht, und sie als XML-Datei zu speichern. Bei einer dynamischen Website, auf der sich die Inhalte regelmäßig ändern, ist dies keine wirkliche Option - Sie müssten die Sitemap-Datei manuell aktualisieren, jedes Mal wenn Sie einen neuen Inhalt hinzufügen!

Aus diesem Grund gibt es mehrere Sitemap-Erweiterungen im Joomla Extensions Directory (<a href="https://extensions.joomla.org/category/structure-a-navigation/site-map" rel="noreferrer noopener">Sitemap-Kategorie im Joomla Extensions Directory</a>), die es ermöglichen, dynamisch eine Sitemap zu erstellen, die den Sitemap-Standards entspricht, die von Suchmaschinen erwartet werden. <a href="https://www.sitemaps.org/" rel="nofollow noreferrer noopener">Sitemaps-Protokoll</a>

Die meisten dieser Erweiterungen arbeiten, indem sie Menüelemente auswählen, die Sie in eine Sitemap aufnehmen möchten, und angeben, wie oft sie geändert werden (siehe Aktualisierungshäufigkeit). Es ist auch möglich, Unterseiten dieser Menüelemente aufzunehmen (zum Beispiel könnte ein Menüpunkte zu einer Kategoriebogenseite führen, aber Sie möchten alle Beiträge anzeigen, die auf dieser Seite als einzelne Elemente gezeigt werden - ein weiteres Beispiel könnte ein Menüpunkte sein, der auf eine Shop-Kategorieseite zeigt, und in der Sitemap möchten Sie die Kategorie auflisten und dann jedes Produkt darin als separaten Link).

### Aktualisierungshäufigkeit

Während Sie manuell in Ihrer Sitemap angeben können, wie häufig Suchmaschinen-Spider Ihre Website besuchen sollten, haben die meisten Suchmaschinen integrierte Systeme, die die Häufigkeit der Rückkehrbesuche automatisch anpassen, basierend darauf, wie oft sich die betreffende Seite geändert hat.

Zum Beispiel, wenn Sie den Suchmaschinen-Bots sagen, dass sie Ihre Seite täglich besuchen sollen, aber wenn der Bot die Seite besucht, sich nichts für eine Woche geändert hat, könnte er die Häufigkeit der erneuten Besuche entsprechend anpassen und nicht so oft zurückkehren, wie Sie es ihm gesagt haben. Sie können über die verschiedenen Webmaster-Portale beantragen, dass die Rückbesuchrate bei Bedarf angepasst wird.

Dies würde daher darauf hinweisen, dass, wenn Sie regelmäßig sich ändernde Inhalte haben, Ihre Website häufiger von "Spiderbots" besucht wird - was dazu führt, dass Inhalte schneller indiziert werden als auf Websites, die sich nicht oft ändern.

Es ist generell sinnvoll, anzugeben, dass statische Seiten weniger häufig aufgerufen werden sollen als solche, die sich regelmäßig ändern. Zum Beispiel könnte ein statischer Textbeitrag mit einer Aktualisierungshäufigkeit von einmal im Monat eingestellt werden, während Ihre Blog- oder Nachrichtenseite mit einer Aktualisierungshäufigkeit von einmal am Tag oder einmal pro Woche eingestellt werden könnte, abhängig davon, wie oft Sie neuen Inhalt hinzufügen.

### HTML-Sitemaps

Eine HTML-Sitemap ist im Wesentlichen ein Inhaltsverzeichnis für Ihre Website, das Sie den Besuchern Ihrer Website zur Verfügung stellen können. Dies hat zwei Zwecke:

1. Sie bietet einen Ort, an den Besucher gehen können, um leicht zu jedem Inhalt auf Ihrer Website zu gelangen, selbst wenn dieser nicht unbedingt leicht zugänglich über andere Navigationshilfen auf der Website ist
2. Sie bietet einen zentralen Speicher von Links zu den Inhalten auf Ihrer Website, die von Suchmaschinen leicht indiziert werden können
3. Sie ermöglicht es Nutzern mit Behinderungen, Ihre Website schnell mit einer einfachen Liste von Links zu navigieren, anstatt durch komplexe Menüs

Mindestens sollte eine Sitemap Links zu den Hauptabschnitten und Seiten innerhalb Ihrer Website enthalten, aber je detaillierter Sie sie gestalten können, desto besser.

Es gibt bereits erwähnte Erweiterungen, die Sitemaps automatisch basierend auf Joomla-Inhalten erstellen.

### XML-Sitemaps

XML-Sitemaps sind eine einfache Möglichkeit für Webmaster, Suchmaschinen über neue und bestehende Seiten auf ihren Websites zu informieren, die für das Crawlen verfügbar sind. In ihrer einfachsten Form ist eine Sitemap eine XML-Datei, die URLs für eine Website zusammen mit zusätzlichen Metadaten über jede URL auflistet (wann sie zuletzt aktualisiert wurde, wie oft sie sich normalerweise ändert und wie wichtig sie im Vergleich zu anderen URLs auf der Website ist), sodass Suchmaschinen die Website intelligenter crawlen können.

Die Verwendung des Sitemap-Protokolls garantiert nicht, dass Webseiten in Suchmaschinen enthalten sind, bietet jedoch Hinweise für Webcrawler, um Ihre Website besser zu durchsuchen.

1. Eine XML-Sitemap stellt eine Liste von Links zu den Inhalten auf Ihrer Website bereit, die von Suchmaschinen leicht indiziert werden können
2. Es ist möglich, spezifische XML-Sitemaps für Nachrichten, Mobile-URLs, Bilder und Videos zu erstellen

Es gibt bereits verfügbare Erweiterungen, die XML-Sitemaps automatisch basierend auf Joomla-Inhalten erstellen.

*Übersetzt von openai.com*

