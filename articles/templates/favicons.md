<!--
{
  "source": "https://docs.joomla.org/J4.x:Favicons",
  "title": "Favicons  ",
  "description": "", 
  "author": ""
}
-->

## Die Joomla!-Favicons

Favicons sind die kleinen Symbole, die im Browser-Tab neben dem Namen Ihrer Website erscheinen. Nahe am Anfang der Template-Datei index.php befinden sich drei Anweisungen, um Favicons in die Seite zu laden:
```php
    // Browser unterstützen SVG-Favicons
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Für das Cassiopeia-Template sucht Joomla die Favicons in den folgenden Verzeichnissen:

1.  **media/templates/site/cassiopeia/images** - Dort sind sie nicht vorhanden, daher schaut Joomla im nächsten Verzeichnis nach.
2.  **media/system/images** - Dort sind sie vorhanden, also wird Joomla sie von dort verwenden.

Wenn Sie eigene Favicons anstelle der Joomla-Favicons verwenden möchten, laden Sie sie in das erste Verzeichnis hoch: **media/templates/site/cassiopeia/images**. Dies können Sie über das Formular "Vorlagen anpassen" tun. Sie werden von keinem Update des Cassiopeia-Templates betroffen sein.

Favicons werden manchmal in größeren Größen und an anderen Stellen als dem Browser-Tab verwendet. Zum Beispiel zeigt ein Screenshot eines Teils einer Firefox-Startseite einige der bevorzugten Standorte des Benutzers:

![Beispiele für Favicons von der Firefox-Startseite](../../../en/images/templates/favicons/01-favicons-firefox-start-collection.png)

Alle modernen Browser unterstützen SVG-Symbole, daher sollten Sie die Erstellung eines SVG-Symbols priorisieren.  

## Über SVG

SVG ist ein Akronym für Scalable Vector Graphics. Eine SVG-Datei enthält Text in einem Format, das die Positionen und Formen von Linien mit Linienfarben, Füllfarben und so weiter definiert. Der folgende Screenshot zeigt die Datei *joomla-favicon.svg* in einem Texteditor geöffnet. Die Zeilennummern werden vom Texteditor erstellt und sind nicht in der Datei enthalten. Die langen Zeilen stellen Kurven dar und sind hier aus Darstellungsgründen gekürzt.

![joomla favicon textinhalt](../../../en/images/templates/favicons/02-favicons-joomla-favicon-svg-text.png)

Um eine SVG-Datei zu erstellen, müssen Sie eine geeignete Anwendung wie Inkscape verwenden. Rastergrafikanwendungen wie Photoshop oder GIMP sind dafür nicht geeignet. Wenn Sie lieber ein Symbol in einer Rastergrafikanwendung entwerfen möchten oder ein bestehendes Rastergrafik-Logo haben, das für ein Symbol angepasst werden kann, können Sie die resultierende PNG-Datei in Inkscape importieren und dort nachzeichnen, um eine SVG-Datei zu erstellen. Das nachgezeichnete Bild muss nach dem Nachzeichnen gelöscht werden!

Die eigentliche Erstellung eines SVG-Favicons liegt außerhalb des Umfangs dieses Beitrags. Die Erstellung einer Standard-*favicon.ico*-Datei, beginnend mit einer *joomla-favicon.svg*-Datei, ist sehr einfach - viele Websites bieten dies online kostenlos an.

## So erstellen Sie Favicons

Wenn Sie Ihre eigenen Favicons erstellen möchten, ist es am besten, ein SVG-Favicon zu erstellen und dann ein Onlinetool zu verwenden, um alle anderen Formate mit diesem als Eingabe zu erzeugen. In diesem Beispiel wird ein Symbol benötigt, das zu einer Kindvorlage mit dem Namen Cassiopeia Green passt. Ein Symbol sollte quadratisch und nicht zu komplex sein, da die minimale Anzeigengröße 16x16 Pixel beträgt. Einige Geräte benötigen höhere Auflösungen, wie 32x32 oder 180x180, und Google empfiehlt Vielfache von 48x48 Pixel. Wenn Sie mit einem SVG beginnen, müssen Sie sich darüber keine Sorgen machen - erstellen Sie einfach ein nahezu quadratisches Bild mit einem passenden Design. In diesem Beispiel wird das Favicon die Buchstaben *J4* in Dunkelgrün darstellen.

### Inkscape

Inkscape ist eine kostenlose, quelloffene, plattformübergreifende Vektorgrafik-Anwendung, die zum Arbeiten mit SVG-Dateien verwendet wird. Sie funktioniert unter Linux, Mac und Windows. Gehen Sie zur Inkscape-Website (inkscape.org), um eine Kopie für Ihre Plattform herunterzuladen. Die folgenden Abbildungen zeigen den Inkscape-Bildschirm während der folgenden Anweisungen.

![inkscape mit vorbereitendem favicon](../../../en/images/templates/favicons/03-favicons-inkscape-favicon.png)

### Erstellen eines SVG

1. Starten Sie Inkscape und passen Sie das Fenster auf eine angenehme Größe an: Wählen Sie Ansicht / Zoom / Zoom Seite
2. Wählen Sie das Textwerkzeug, mit dem Buchstaben A in der linken Symbolleiste gekennzeichnet
3. Wählen Sie Arial, Normal, 48 und px
4. Ziehen Sie, um ein Kästchen auf der Seite zu definieren
5. Geben Sie den Text ein: J4
6. Wählen Sie Ansicht / Auswahl Zoomen
7. Wählen Sie Pfad / Objekt in Pfad umwandeln - keine sichtbaren Änderungen, aber die Worte sind nicht mehr Text
8. Wählen Sie Datei / Dokumenteneigenschaften
9. Wählen Sie Anpassung an Inhalt
10. Zoomen Sie heraus für eine bessere Ansicht - aber stellen Sie sicher, dass alle Buchstaben noch ausgewählt sind
11. Setzen Sie das Höhenfeld auf denselben Wert wie das Breitenfeld. Tippen Sie es!
12. Schließen Sie das Dialogfeld Dokumenteneigenschaften
13. Nochmals Ansicht / Zoom Seite - die Zeichen müssen zentriert werden
14. Bearbeiten / Alle auswählen
15. Objekte / Ausrichten und Verteilen
16. Bewegungsauswahl als Gruppe / Relativ zur Seite / Im Horizontalen zentrieren - Sie sollten J4 zum vertikalen Mittelpunkt verschieben sehen
17. Wählen Sie die Füllung und den Strich rechts - das rechte Panel hat eine Dropdown-Liste, die mit einem Chevron nach unten markiert ist
18. Im Panel Füllung und Strich wählen Sie Füllung und das erste ausgefüllte Quadrat
19. Im RGB-Panel geben Sie 006400ff im RGBA-Feld unten rechts ein - der Code für die CSS-Stil *darkgreen*
20. Datei / Speichern
21. Im Speicherdialog geben Sie einen geeigneten Dateinamen ein, zum Beispiel green-favicon-j4.svg
22. Wählen Sie einen geeigneten Speicherort, zum Beispiel
    *~/Dokumente/joomla-dev/svgs*
23. Wählen Sie Optimiertes SVG (*.svg*) aus der Dropdown-Liste unten im Formular.
24. Wählen Sie *Speichern*
25. Wählen Sie *OK* für alle Standardeinstellungen im Optimierten SVG-Ausgabeformular
26. Schließen Sie das SVG, an dem Sie arbeiten - es besteht die Gelegenheit, das Bild im Inkscape-Format zu speichern, aber das ist nicht wirklich notwendig.

### Bearbeiten des SVG mit einem Texteditor

Starten Sie Ihren bevorzugten Texteditor, um einige Änderungen vorzunehmen, die in Inkscape nicht möglich waren.

1. Öffnen Sie Ihre neu erstellte SVG-Datei - beachten Sie, dass die erste Zeile eine XML-Spezifikation ist
2. Sie können die zweite Zeile löschen - ein Kommentar, der mit Inkscape erstellt wurde
3. Wenn vorhanden, können Sie die Zeile löschen, die enthält, da es keinen Text gibt
4. Öffnen Sie die original joomla-favicon.svg Datei - sie befindet sich in *joomla_root/media/system/images*
5. Kopieren Sie den Stilblock und fügen Sie ihn in Ihr SVG auf der Zeile nach der SVG-Anweisung ein
6. Schließen Sie die originale *joomla-favicon-svg* Datei, um versehentliche Änderungen zu vermeiden
7. Ändern Sie im Stilblock Ihrer eigenen SVG-Datei path {fill: \#000;} zu path {fill: \#006400;}, dem Wert in der Zeile
8. Entfernen Sie *fill="#006400"* aus der Zeile
9. Speichern
10. Öffnen Sie das Bild in Ihrem Browser. Für Firefox ist das Datei / Datei öffnen...

Sie sollten das Bild in Ihrem Browser sehen können. Das Beispiel zeigt J4 mit 47 Pixeln Quadrat. Der nächste Schritt ist, die anderen benötigten Symboltypen zu erstellen, indem Sie Ihr neu erstelltes SVG als Master verwenden.

### Online-Verarbeitung

Gehen Sie zur Real Favicon Generator-Website.
Andere Websites sind verfügbar, aber diese scheint besonders umfassend zu sein.

1. Wählen Sie die Schaltfläche mit der Beschriftung *Wählen Sie Ihr Favicon-Bild*
2. Die Website zeigt Ihnen Ihr Master-Bild. Es sagt auch *Ihr Bild ist nicht quadratisch (688x512). Wir können dies beheben, indem wir transparente Ränder hinzufügen*
3. Wählen Sie die Schaltfläche *Mit diesem Bild fortfahren* unter dem Master-Bild.
4. Es gibt Unterformulare mit hellblauem Hintergrund für verschiedene Symboltypen - füllen Sie jedes aus und überprüfen Sie, ob die Vorschau Ihnen gefällt.
5. Am besten bleiben Sie bei den Standardeinstellungen der Favicon-Generator-Optionen, es sei denn, Sie wissen es besser. Außer:
6. Pfad, wählen Sie die Ich kann nicht ...-Option und geben Sie ein:
    *media/templates/site/cassiopeia-green/images*
7. Wählen Sie die Schaltfläche *Ihre Favicons und HTML-Code generieren*
8. Nach einer kurzen Verzögerung gibt es ein neues Formular, wählen Sie die Schaltfläche Download Ihr Paket: *Favicon*-Paket
9. Speichern Sie den Download...
10. Wählen und kopieren Sie den Link-Block, um ihn irgendwo zu speichern.
11. Schließen Sie die Website der Online-Verarbeitung

Der Download ist eine *zip*-Datei, die 10 Elemente enthält: *favicon.ico*, *safari-pinned-tab.svg*, sechs PNG-Dateien, *browserconfig.xml* und *site.webmanifest*.

### Bereitstellung

Um das Standardsatz von Joomla-Favicons zu verwenden, müssen Sie die Symbole umbenennen und in *joomla_root/media/templates/yourtemplate/images* verschieben:

- Ihr Master-SVG-Bild, *green-favicon-j4.svg*, muss in *joomla-favicon.svg* umbenannt werden
- Die heruntergeladene *safari-pinned-tab.svg* Datei muss in *joomla-favicon-pinned.svg* umbenannt werden
- Die heruntergeladene *favicon.ico* Datei muss nur verschoben werden

### Der Link-Block

Der zuvor kopierte Link-Block enthält:

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/site/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/site/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/site/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/site/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/site/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/site/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/site/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Sie müssen ihn wahrscheinlich nicht verwenden!

*Übersetzt mit openai.com*

