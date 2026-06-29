<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=news&filename=news-feeds.md",
  "title": "Nachrichtenfeeds",
  "description": "", 
  "author": ""
}
-->

## Einführung in News-Feeds

Es war einmal gängige Praxis, dass eine Website Nachrichtenbeiträge von entfernten Websites auf einer Seite oder einem Panel anzeigte. Sogar Browser hatten eingebaute News-Reader, um genau das zu tun. Die Zeiten ändern sich und die großen Browser bieten diese Option nicht mehr an. Es gibt neue Methoden, um Website-Inhalte zu teilen, insbesondere mit sozialen Netzwerken.

Die Methode, um Nachrichten zu teilen, ist *Really Simple Syndication*, gewöhnlich abgekürzt als **RSS**, und diese hat immer noch einen Platz in der Website-Promotion. Der folgende Screenshot zeigt *NetNewsWire*, einen freien und quelloffenen RSS-Reader für Mac. Andere RSS-Reader sind für andere Plattformen verfügbar. Die Abbildung zeigt den **Joomla! Ankündigungen** RSS-Feed ausgewählt. Zehn Ankündigungen werden mit Titel und kurzer Beschreibung aufgelistet. Die ausgewählte Ankündigung wird vollständig in der rechten Spalte angezeigt.

![RSS-Feed von Joomla Ankündigungen](../../../en/images/news-feeds/news-feeds/01-news-netnewswire-display.png)

Stellen Sie sich vor, was ein oder mehrere RSS-Feeds für Ihre Website tun könnten!

## Einrichten eines News Feeds

Ihre Website hat News Feeds von Haus aus eingerichtet. Eine neu installierte Joomla 5-Website enthält diese beiden Zeilen nahe dem Anfang des Home-Seiten-Quelltexts:

```
<link href="/j51/index.php?format=feed&amp;type=rss" rel="alternate" type="application/rss+xml" title="Home">
<link href="/j51/index.php?format=feed&amp;type=atom" rel="alternate" type="application/atom+xml" title="Home">
```
Diese Zeilen ermöglichen es automatisierten Systemen, entweder RSS- oder Atom-Feeds zu verwenden. Atom ist eine spätere und leicht unterschiedliche News-Syndication-Spezifikation. Die Zeilen werden auf allen **Featured**-Seiten und **Category Blog**-Seiten vorhanden sein, jedoch nicht auf den meisten anderen Seitentypen. Sie können die Einbeziehung dieser RSS-Feeds deaktivieren, wenn Sie möchten.

## RSS-Feed-Link umschalten

Die globale Einstellung des RSS-Feed-Links befindet sich auf der Seite **Integration** im Reiter Optionen der Beiträge. Stellen Sie sie auf *Anzeigen* oder *Ausblenden* ein, je nach Bedarf. Die Standardeinstellung ist **Anzeigen**.

Die globale Einstellung kann in einem Menüpunkt des Kategorie-Blogs überschrieben werden. Wählen Sie erneut den Reiter *Integration* und setzen Sie den *RSS-Feed-Link* auf *Anzeigen* oder *Ausblenden*.

Der RSS-Feed kann auf einer Startseite mit hervorgehobenen Beiträgen nicht ausgeblendet werden (Bug?)!

## Das Syndikations-Feeds Modul

Es gibt ein Kernmodul, das Sie auf Hervorgehobene oder Kategorie-Blog-Seiten platzieren können, um einen Syndikationslink bereitzustellen. Füllen Sie die Felder im Modul-Tab aus. Die meisten haben geeignete Standardwerte. Wenn das Feld für die Bezeichnung leer gelassen wird, lautet die Standardbezeichnung auf Englisch *Feed Entries*. Wählen Sie im Tab *Menüzuweisung* die Option **Auf allen Seiten**. Das Modul wird nur auf Hervorgehobenen und Kategorie-Blog-Seiten angezeigt.

![Syndikations-Feeds Daten-Eingabe](../../../en/images/news-feeds/news-feeds/02-news-syndication-feeds-form.png)

Denken Sie daran, das Modul einer *Position* zuzuweisen und es auf *Veröffentlicht* zu setzen.

In der Site-Seitenansicht zeigt das Modul einen Link an. Er ist nicht zum Anklicken vorgesehen, es sei denn, Sie haben einen lokalen Newsreader konfiguriert. Der Link muss kopiert werden, um ihn in einem Newsreader auf einer anderen Seite oder einer Newsreader-Anwendung zu verwenden.

![Syndikations-Feeds Anzeige](../../../en/images/news-feeds/news-feeds/03-news-syndication-feeds-display.png)

Beachten Sie, dass der Link für die Beiträge auf dieser Seite ist. Wenn Ihre Seite mehrere Kategorie-Blog-Seiten hat, werden Sie mehrere unterschiedliche RSS-Feeds haben.
*Übersetzt von openai.com*

