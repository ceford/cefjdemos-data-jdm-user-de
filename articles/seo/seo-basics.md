<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=seo&filename=seo-basics.md",
  "title": "SEO-Grundlagen ",
  "description": "", 
  "author": ""
}
-->

## Definition

Suchmaschinenoptimierung ist der Prozess der Verbesserung einer Vielzahl von Merkmalen einer Website mit der Absicht, die Position zu verbessern, in der sie in Suchmaschinen eingestuft wird.

Der Prozess der Optimierung einer Website ist facettenreich, da es viele Faktoren gibt, die beeinflussen, wo eine Seite in einer Suchmaschine eingestuft werden könnte.

- Sicherstellen, dass Inhalte mithilfe von semantischem HTML eine geeignete Struktur haben
- Verbesserung der Qualität der Inhalte einzelner Seiten.
- Sicherstellen, dass die Website Anfragen schnell bearbeiten kann.
- Aktivieren von suchmaschinenfreundlichen URLs, um die Webadresse von Seiten *menschlich lesbar* zu machen.
- Hinzufügen von kontextuellem semantischem Markup mithilfe von Schema-Daten.

Ressource: [Search Engine Optimization (SEO) Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

## Seitenstruktur und beschreibende URLs

In den frühen Tagen waren Websites als einzelne HTML-Dateien in einer Baum-Hierarchie strukturiert. Einige Websites sind immer noch so strukturiert. CMSs sind anders. Einzelne Seiten werden aus Inhalten zusammengestellt, die in Datenbanktabellen gespeichert sind. Die URLs für die früheren und letzteren sind unterschiedlich, vielleicht so:

```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```

Eindeutig ist das erste leichter zu merken und einfacher zu tippen. Suchmaschinen bevorzugen sie.

Im Joomla CMS kann eine URL der ersten Form wie folgt eingerichtet werden:

1. Erstellen Sie eine Inhaltskategorie namens **Benutzer**.
2. Erstellen Sie eine Inhaltskategorie namens **SEO**, die eine Unterkategorie von *Benutzer* ist.
3. Erstellen Sie einen Beitrag und ordnen Sie ihn der *SEO*-Kategorie zu.
4. Erstellen Sie ein **Benutzer**-Menüelement vom Typ **Kategorie-Liste** unter Verwendung der *Benutzer*-Kategorie.
5. Erstellen Sie ein Menüelement **SEO** vom Typ **Kategorie-Liste** unter Verwendung der *SEO*-Kategorie.
6. Richten Sie die Joomla-SEO-Funktionalität in der *Globalen Konfiguration* ein.

Teste es mit deiner SEO-URL: Navigiere über die Benutzer- und SEO-Listen zur Seite SEO-Grundlagen. Die Breadcrumbs sollten anzeigen: `Sie sind hier: Startseite / Benutzer / SEO / SEO-Grundlagen`. Aber nicht, wenn du einen Einzelbeitrag-Menüpunkt-Typ für *SEO-Grundlagen* erstellt hast!

## Reduzierung von Doppelungen

Das Problem mit CMSs ist, dass derselbe Inhalt unter verschiedenen URLs verfügbar gemacht werden kann. Im obigen Beispiel werden beide URLs funktionieren (aber nicht auf dieser Seite), ebenso wie `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Nur eine dieser URLs sollte von Suchmaschinen erkannt und als die **kanonische** URL festgelegt werden. Aber welche und wie?

Das **System - SEF** Plugin bietet einige Hilfestellungen. Es hat drei Einstellungen:

- **Site Domain** Wenn Ihre Website über mehr als eine Domain zugänglich ist, tragen Sie hier die bevorzugte (manchmal als kanonisch bezeichnete) Domain ein. **Hinweis:** `https://example.com` und `https://www.example.com` sind verschiedene Domains.
- **Strikte Handhabung von index.php** Diese Option ermöglicht eine strengere Handhabung von `index.php` in URLs, wenn **URL-Umschreibung verwenden** in der globalen Konfiguration aktiviert ist. Sie entfernt `index.php`, wenn eine URL es noch enthält, und leitet eingehende Anfragen mit `index.php` zur Version ohne `index.php` weiter.
- **Schrägstrich am Ende für URLs** Zwingt Joomla, nur URLs mit oder ohne Schrägstrich am Ende zu verwenden. Wenn eingestellt, erzwingt dies die richtige URL mit Weiterleitungen und wird nur angewendet, wenn 'Suffix zur URL hinzufügen' deaktiviert ist.

Andernfalls siehe die Erklärung der **Canonical Tags** von [Daniel Morell](https://www.danielmorell.com/blog/how-to-create-joomla-canonical-tags).

## Inhaltsqualität

Machen Sie das, was Sie schreiben, interessant und leicht lesbar. Lange Absätze sind oft überwältigend und schwer zu lesen. Einzeilige Absätze sehen falsch aus! Vielleicht sollten sie wirklich Aufzählungspunkte sein. Streben Sie nach Absätzen von etwa drei Zeilen. Lesen Sie, was Sie schreiben, und streichen Sie alle unnötigen Wörter.

Halten Sie Ihre Inhalte auf dem neuesten Stand und vermeiden Sie, Informationen von anderen Seiten zu kopieren. Wenn möglich, überprüfen Sie Ihre Inhalte.

### Semantisches HTML

Inhalt sollte aus einer Hierarchie von Überschriften und Absätzen bestehen, zusammen mit anderen erforderlichen Elementen (Listen, Tabellen usw.). Verwechseln Sie nicht die Struktur mit dem Aussehen – verwenden Sie also keine Überschrift, um Text fett zu machen, oder fetten Text, um eine Überschrift zu erstellen. Dies ist ein Beispiel für semantisches Markup eines Beitrags:

```html
  <h2>Using headings</h2>
  <p>This is an article about the importance of headings.</p>

  <h2>Why use headings?</h2>
  <p>It is important to use headings so that search engine bots can tell what
  is an <strong>important</strong> part of your article.</p>

  <h3>Types of headings</h3>
  <p>You can use set types of headings, but they should be ordered, and
  structured, within your page.  H1 will be the page title inserted by Joomla,
  with H2 being used for sub-headings of the page.  Any headings within your
  sub-headings should cascade using H3, H4, and H5 as appropriate.</p>

  <h2>Is it hard to implement headings?</h2>
  <p>It is really easy to implement headings, you just use the appropriate
  HTML code.</p>
```

Beachten Sie, dass ein Beitrags*Titel* bei Bedarf zu einer `<h1>`-Überschrift wird, verwenden Sie ihn daher nicht im Beitragsinhalt.

## Suchbegriffe antizipieren

Wählen Sie klare Titel für Ihre Seiten und Überschriften innerhalb der Seiten. Zum Beispiel, wenn Sie nicht wissen, was *Semantisches HTML* ist, oder mehr Informationen zu diesem Thema wünschen, wären das die Wörter, die Sie in eine Suchmaschine eingeben. Denken Sie an die Menschen, die an den Informationen interessiert sein könnten, die Sie bereitstellen. Wonach werden sie suchen? Halten Sie Titel und Überschriften jedoch relativ kurz – einige Quellen sagen, nicht mehr als 60 Zeichen.

## Vorsicht mit Werbeanzeigen

Nichts wird Besucher der Website mehr abschrecken als Werbeanzeigen, die hier, dort und überall erscheinen und die echten Informationen vor Ihren Augen verschieben. Anzeigen, die alle paar Sekunden wechseln, sind ebenfalls störend und belasten die Ressourcen des Endbenutzers. Viele werden Ad-Blocker verwenden!

## Vorsicht mit Links

Links sind sowohl ein Segen als auch ein Fluch! Sie können das SEO-Ranking Ihrer Website positiv oder negativ beeinflussen, je nachdem, ob Sie Links zu seriösen oder unseriösen Quellen haben. Und sie müssen gepflegt werden. Möglicherweise haben Sie Links zu internen oder externen Beiträgen, die verschwunden sind, veraltete Informationen präsentieren oder nicht mehr relevant sind. Beste Empfehlung: Verlinken Sie, wenn das Ziel einen echten Nutzen für Ihre Website-Besucher bietet, und verwenden Sie das `nofollow`-Link-Attribut, wenn Sie nicht möchten, dass die Zielseite mit Ihrer Website in Verbindung gebracht wird.

Es gibt viele Link-Checker-Tools, einige kostenlos oder freemium, andere kostenpflichtig, oft als Teil eines Website-Überwachungsdienstes.

## Seitentitel und Beschreibung

Im `<head>` jeder Seite sollte ein `<title>`-Tag und ein `<description>`-Tag vorhanden sein. Joomla macht es sehr einfach, einen unterschiedlichen Titel für jede Seite festzulegen. Leider macht es auch sehr einfach, es zu versäumen, einen geeigneten Titel und eine Beschreibung auf jeder Seite festzulegen.

Als Beispiel nehmen Sie die oben erwähnte **SEO**-Kategorielistenseite. Der Seitenquellcode `<title>` sagt **SEO** und die `<description>` fehlt. Im Formular **Menüs: Artikel Bearbeiten** für diesen Menüpunkt gibt es eine Registerkarte **Seitendarstellung** mit einem Feld **Browser-Seitentitel**. Dort `SEO - Liste der Beiträge` einfügen, und das erscheint im `<title>`-Tag und im Browsertab.

Im **Metadaten**-Tab wird mit dem **Meta-Beschreibung**-Feld, das auf `Liste der Beiträge zur Suchmaschinenoptimierung.` gesetzt ist, genau das im `<description>`-Feld angezeigt. Die Beschreibung wird manchmal verwendet, um einen Seitentitel in den Suchergebnissen zu begleiten, daher sollte es sich lohnen, sie relevant zu gestalten.

Weitere Informationen:
* Magazinbeitrag: [Joomla SEO-Titel-Tags](https://magazine.joomla.org/all-issues/september/joomla-seo-title-tags)
* [Erkunde den Kern: Natürliche SEO-Optionen](https://magazine.joomla.org/all-issues/june/explore-the-core-native-seo-options)

## Bilder optimieren

Es versteht sich von selbst, dass attraktive Bilder eine Website enorm verbessern können. Aber zu viele, die zu groß sind, ziehen SEO-Strafen nach sich. Hier sind einige Tipps:

- Platziere Bilder neben dem Text, den sie illustrieren.
- Verwende beschreibenden **alt**-Text.
- Verwende mit Minuszeichen getrennte Wörter für die Bildnamen, zum Beispiel cat-on-hot-tin-roof.jpg.
- Verwende den richtigen Bildtyp für die jeweilige Aufgabe: png für Poster, jpg für Fotografien.
- Verwende responsive Bilder - es gibt ein [Joomla-Plugin](https://responsive-images.dgrammatiko.dev/), das dynamisch WebP-Versionen von png- und jpg-Bildern in mehreren Größen erstellt.

*Übersetzt von openai.com*

