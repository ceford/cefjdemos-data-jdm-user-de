<!--
{
  "source": "https://docs.joomla.org/Article_Images_and_Links",
  "title": "Beitrag: Bearbeiten - Bilder und Links  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Andere Beiträge haben beschrieben, wie man Bilder und Links in den Inhalt eines Beitrags einbettet. Dieser Beitrag beschreibt die Verwendung des Tabs *Bilder und Links*, um zwei Arten von Bildern und bis zu drei Links für standardisierte Layouts hinzuzufügen. Kurz gesagt:

- Das *Intro-Bild* wird in Kategoriebog- oder Listen-Layouts als zusätzliches visuelles Vorschaubild verwendet, um einen Vorgeschmack auf den Inhalt zu geben, den man erwarten kann.
- Das *Vollbild im Artikel* wird oben im vollständigen Beitrag als visuelle Einführung in den Inhalt platziert.
- Die Links: Link A, Link B und Link C werden oberhalb des Beitragstextes platziert.

## Screenshot

Für diesen Beitrag, angefangen mit einem Bild eines grünen Laubfrosches, das 1024 Pixel breit war, wurden zwei kleinere Bilder in 128 und 256 Pixel Breite erstellt. Hinweis: Es ist am besten, Bilder in Ihrem bevorzugten Bildbearbeitungsprogramm wie *Gimp* vorzubereiten. Die kleinen und mittelgroßen Bilder wurden verwendet, um die folgenden Screenshots zu erstellen.

![Beitragsbearbeitungsformular, Bilder- und Links-Tab](../../../en/images/articles/article-images-and-links/01-articles-edit-images-and-links-tab.png)

## Formularfelder

### Einführungsbild

- **Einführungsbild** Wählen Sie ein geeignetes Bild aus, das in Bloglayouts verwendet wird, wo es normalerweise über dem Beitragstitel erscheint. Dies ist optional. Wenn leer gelassen, wird es kein Einführungsbild im Bloglayout geben.
- **Bildbeschreibung (Alt-Text)** Geben Sie eine geeignete Bildbeschreibung für Screenreader ein.
- **Dekoratives Bild** Wenn es keine *Bildbeschreibung* gibt und dieser Button nicht aktiviert ist, wird die Seite die Barrierefreiheitstests nicht bestehen. Wenn dieser Button aktiviert ist, wird ein leeres `alt` Attribut hinzugefügt. Dies kann es der Seite ermöglichen, die Barrierefreiheitstests zu bestehen. Es ist wahrscheinlich am besten, immer eine gute, kurze Beschreibung des Bildes zu verwenden.
- **Bildklasse** Die Standardklasse ist *left*, was float-left bedeutet. Aber jeder andere Float-Wert hat hier keine Wirkung, da er nicht auf Raster- oder Flex-Elemente angewendet werden kann.
- **Bildunterschrift** Die hier eingegebenen Wörter erscheinen als Bildunterschrift unter dem Bild. **Warnung:** Verwenden Sie nicht exakt dieselben Wörter sowohl für den Alt- als auch für den Bildunterschriftstext. Screenreader würden die Informationen zweimal ansagen.
  - Der Alt-Text sollte eine knappe Beschreibung dessen liefern, was im Bild ist.
  - Die Bildunterschrift sollte normalerweise Kontext liefern, um das Bild mit dem umgebenden Inhalt zu verknüpfen, oder auf ein bestimmtes Stück Informationen aufmerksam machen.

### Vollständiges Beitragsbild

Die gleichen Felder wie für das Einführungsbild, aber das Bild wird in einem anderen Kontext verwendet. Siehe die Screenshots der Website unten.

### Link A

- **Link A** Fügen Sie die vollständige URL der Zielseite ein. Die vollständige URL muss verwendet werden, auch wenn sich die Zielseite auf dieser Website befindet.
- **Link A Text** Geben Sie den Text ein, der für den Ziellink verwendet werden soll.
- **URL-Zielfenster** Wählen Sie eine der Zieloptionen:
  - **Global verwenden (Im Elternelement öffnen)**
  - **Im Elternelement öffnen** Dies ist das bevorzugte Verhalten, da der Browser *Zurück*-Button verwendet werden kann, um zur vorherigen Seite zurückzukehren.
  - **In neuem Fenster öffnen** Einige Benutzer mögen dies, aber es verwirrt mobile Benutzer, da es nicht offensichtlich ist, dass ein neues Fenster geöffnet wurde, und es keinen *Zurück*-Button gibt.
  - **In Popup öffnen** Ein kleines Popup-Fenster erscheint. Das Hauptfenster bleibt verfügbar. Jeder Klick auf den Link öffnet eine weitere Instanz des Popup-Fensters.
  - **In Modal öffnen** Ein modaler Dialog öffnet sich in der Mitte des Bildschirms und ist inaktiv, bis das Dialogfeld geschlossen wird.

### Links B und C

Genau die gleiche Dateneingabe wie bei Link A.

## Website-Screenshots

Der Screenshot unten zeigt ein Kategorie-Blog-Layout mit dem *Einführungsbild*. Es wäre möglicherweise besser gewesen, ein Panoramabild mit gleicher Höhe, aber wesentlich größerer Breite zu verwenden, um den ungenutzten weißen Raum auszufüllen.

![Amphibien-Kategorie-Blog-Seite](../../../en/images/articles/article-images-and-links/02-articles-site-amphibians-blog.png)

Der Screenshot unten zeigt die einzelne Beitragsseite mit dem *Vollständigen Beitragsbild* und dem Link A. Das Bild wurde nach rechts verschoben, und die sichtbare Bildunterschrift fügt etwas zur Beschreibung hinzu, damit es für Screenreader logisch klingt.

![Frösche einzelne Beitragsseite](../../../en/images/articles/article-images-and-links/03-articles-site-amphibians-frogs.png)

*Übersetzt von openai.com*

