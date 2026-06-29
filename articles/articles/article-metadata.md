<!--
{
  "source": "https://docs.joomla.org/J6.x:_Article_Metadata",
  "title": "Beitrag: Bearbeiten - Metadaten ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Metadaten sind Informationen über eine Webseite, die im ersten Teil der Seite zwischen den `<head>...</head>` Tags enthalten sind. Die meisten dieser Informationen sind für die Besucher der Seite nicht sichtbar, werden jedoch von Suchmaschinen genutzt, um passende Ergebnisse für Suchanfragen zu liefern. Daher liegt es in Ihrem Interesse, informative Metadaten zu verwenden.

Einige der Metadaten-Elemente werden durch die verwendete Vorlage bereitgestellt und müssen nicht von Ihnen selbst festgelegt werden. Häufige Beispiele:

```html
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="generator" content="Joomla! - Open Source Content Management">
```

Es gibt andere Formen von Metadaten wie Open Graph Data, die von Facebook genutzt werden, und Schemata, die verwendet werden, um spezielle Arten von Seiten wie Person, Ort oder Produkt zu beschreiben. Diese werden hier nicht behandelt.

Die oft vernachlässigten Metadatenelemente sind der **Titel** der Seite, der innerhalb der `<title>...</title>` Tags im `<head>` der Seite vorkommt, und die **Beschreibung** der Seite, die innerhalb der `<meta>` Tags vorkommen kann, aber möglicherweise fehlt. Diese werden hier behandelt.

## Der Seitentitel

Ein Beitragstitel ist für jede neue Seite erforderlich. Hier sind einige Richtlinien und Tipps zur Erstellung guter Titel von der Mozilla Developer Network:

>* Vermeiden Sie ein- oder zwei-Wort-Titel. Verwenden Sie eine beschreibende Phrase oder eine Term-Definition-Paarung für Glossar- oder Referenzseiten.
>* Suchmaschinen zeigen in der Regel etwa die ersten 55–60 Zeichen eines Seitentitels an. Text, der darüber hinausgeht, könnte verloren gehen, also versuchen Sie, Titel nicht länger als dieser zu haben. Wenn Sie einen längeren Titel verwenden müssen, achten Sie darauf, dass die wichtigen Teile früher kommen und dass nichts Kritisches in dem Teil des Titels steht, der wahrscheinlich abgeschnitten wird.
>* Verwenden Sie keine "Keyword-Blobs". Wenn Ihr Titel nur eine Liste von Wörtern ist, reduzieren Algorithmen oft die Position Ihrer Seite in den Suchergebnissen.
>* Versuchen Sie sicherzustellen, dass Ihre Titel innerhalb Ihrer eigenen Seite so einzigartig wie möglich sind. Doppelte — oder nahezu doppelte — Titel können zu ungenauen Suchergebnissen führen.

Zusätzliche Empfehlungen von Google:

>- Geben Sie einen einzigartigen Titel für jede Seite an
>- Machen Sie Ihren Titel beschreibend für den Seiteninhalt und prägnant
>- Vermeiden Sie Keyword-Überladung (immer wieder ähnliche Wörter wie "Foobar, foo bar, foobars, foo bars" zu verwenden)
>- Vermeiden Sie generische Titel - jede Seite sollte einen einzigartigen Titel haben, idealerweise dynamisch aktualisiert in Bezug auf den angezeigten Inhalt
>- Marken Sie Ihre Titel, aber tun Sie es prägnant und in Bezug auf den bereitgestellten Inhalt

Es gibt verschiedene Webmaster-Tools, die verwendet werden können, um herauszufinden, ob es Probleme mit Ihren Listings in einer bestimmten Suchmaschine gibt - es lohnt sich immer, darauf zu achten und Probleme zu korrigieren. Ein Beispiel:

[Google-Support-Beitrag über die Verwendung von Titeln für Ihre Webseiten](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

In Joomla wird bei einer einzelnen Seite der Beitragstitel zum Seitentitel im Head und im Browser-Tab angezeigt. Bei einer zusammengesetzten Seite, wie *Ausgewählte Beiträge* oder einem *Kategorie-Blog*, wird der Menüpunkttitel zum Seitentitel. Daher sollten Sie gut darüber nachdenken, wie Sie gute, beschreibende Titel sowohl für Beiträge als auch für Menüeinträge erstellen.

## Die Seitenbeschreibung

Das Feld *Meta-Beschreibung* ist im *Veröffentlichen*-Tab des Datenformulars für Beiträge zu finden:

![Das Bearbeitungsformular des Beitrags im Veröffentlichen-Tab](../../../en/images/articles/article-metadata/01-articles-edit-publishing-tab.png)

Wenn keine Metadatenbeschreibung für den Beitrag vorhanden ist, wird, sofern festgelegt, die Metadatenbeschreibung eines einzelnen Beitrags-Menüeintrags verwendet. Wenn diese nicht vorhanden ist, wird die globale Metabeschreibung der Seite genutzt, falls sie festgelegt ist. Andernfalls wird das Feld für die Metadatenbeschreibung weggelassen.

Google empfiehlt Folgendes, um sicherzustellen, dass Sie das Optimum aus der Indexierung durch Suchmaschinen herausholen:

>- Stellen Sie sicher, dass jede Seite einzigartige, relevante Metabeschreibungen hat.
>- Stellen Sie sicher, dass Sie Metadaten auch für Listen-Seiten (z.B. Blog- & Listenlayouts) anwenden, zusätzlich zu den individuellen Beiträgen – dies wird auf Joomla!-Webseiten häufig übersehen.
>- Fügen Sie, wenn zutreffend, faktische Informationen hinzu (zum Beispiel können Blogbeiträge den Autor enthalten, Produkte möglicherweise den Preis oder Hersteller).
>- Erwägen Sie die Anwendung von automatisch generierten Metadaten - aber stellen Sie sicher, dass sie relevant, lesbar und akkurat sind.
>- Machen Sie Ihre Beschreibungen beschreibend!

Eine andere Referenz:

[Google Support-Beitrag zur Verwendung von Metadaten](http://support.google.com/webmasters/bin/answer.py?hl=de&amp;answer=35624)

## Schlüsselwörter

Es war einmal, dass Suchmaschinen Schlüsselwörter verwendeten, um Inhalte zu klassifizieren. Daher füllten Autoren ihre Schlüsselwort-Metadaten mit einer großen Anzahl von Schlüsselwörtern, in der Hoffnung, ihr SEO-Ranking zu verbessern. Als Reaktion darauf hörte Google auf, Schlüsselwörter für Ranking-Zwecke zu verwenden. Wenn Sie im Internet nach Rat suchen, werden Sie einige Quellen finden, die sagen, dass es sich nicht lohnt, und andere, die sagen, dass sie immer noch einen Wert haben.

Schlüsselwörter werden im Joomla-Kern nicht verwendet. Wenn Sie unsicher sind, lassen Sie es.  

## Roboter

Der Standardwert von *Global verwenden* fügt keinen Meta-Tag in den Kopfbereich der HTML-Seite ein. Andere Werte tun dies. Es gibt eine `robots.txt`-Datei im Stammverzeichnis der Joomla-Seite. Wenn du die Steuerung von Robotern übernehmen möchtest, solltest du diese Datei lesen. Sie enthält eine Erklärung dazu, wie sie verwendet werden kann.

## Autor

Sie könnten den formellen Namen des Autors eingeben, um als Metadaten zu erscheinen. 

## Rechte

Du könntest einen Urheberrechtsvermerk eingeben, der als Metadaten angezeigt wird.

## Beispiel-Metadaten

So sehen die Metadaten in der Quellansicht des Beitrags aus:
Hier ein Beispiel für den Inhalt des `<head>` nach Ausfüllung aller Metadatenfelder:

```html
    <meta charset="utf-8">
    <meta name="rights" content="Charles Darwin © 1859">
    <meta name="author" content="Charles Darwin">
    <meta name="robots" content="noindex, nofollow">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Werbung für Die Entstehung der Arten.">
    <meta name="generator" content="Joomla! - Open Source Content Management">
    <title>Werbung</title>
```
Beachten Sie, dass das Ausgabefeld für Schlüsselwörter fehlt.

*Übersetzt von openai.com*

