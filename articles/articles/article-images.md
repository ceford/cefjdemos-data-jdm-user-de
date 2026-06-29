<!--
{
  "source": "https://docs.joomla.org/Adding_an_image_to_an_article",
  "title": "Beitrag: Bearbeiten - Bilder ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Es ist wichtig zu verstehen, dass Bilder für Webdokumente separat vom HTML-Text gespeichert werden. Wenn eine Webseite angefordert wird, ruft der Browser zuerst den Text sowie separate unterstützende Dateien wie Stylesheets und JavaScript-Skripte ab. Bilder werden später abgerufen. Oft verhandeln der Browser und der Webserver, welche Version eines Bildes abgerufen werden soll, um die Größe und Auflösung des Bildschirms des Browsers zu berücksichtigen. Es gibt sogar eine Joomla-Erweiterung, die mehrere Versionen eines Ursprungsbildes in verschiedenen Größen und Formaten erstellt, um die Geschwindigkeit der Lieferung und Darstellung zu verbessern.

Bilder werden in Webseiten eingebettet, indem entsprechend formatierte Links eingefügt werden. Es gibt zwei verschiedene Mechanismen, um Bilder in Beiträge einzufügen:

- Die Registerkarte *Inhalt* im Bearbeitungsformular ermöglicht das Einfügen eines oder mehrerer Bildlinks direkt in den Text des Beitrags. Das ist das Thema dieses Beitrags.
- Die Registerkarte *Bilder und Links* im Bearbeitungsformular bietet die Möglichkeit, ein Bild als *Intro-Bild* oder *Vollständiges Beitragsbild* oder beides einzufügen. Dies wird in einem separaten Beitrag zu [Bildern und Links](jdocmanual?article=user/articles/article-images-and-links) behandelt.

Es ist ratsam, zwischen lokalen und entfernten Bildern zu unterscheiden:

- **Lokale Bilder** befinden sich auf der gleichen Seite wie die Joomla-Installation, normalerweise im *images*-Ordner. Die Bildlinks müssen nicht das Protokoll und den Domainnamen enthalten, da sie aus den Site-Einstellungen entnommen werden.
- **Entfernte Bilder** befinden sich irgendwo anders im Internet. Sie müssen das Protokoll und den Domainnamen im Link enthalten. Die Verwendung entfernter Bilder durch solches *Hotlinking* kann heute erlaubt sein, aber morgen nicht mehr. Die Verwendung entfernter Bilder ohne Erlaubnis wird als schlechtes Benehmen oder sogar als Diebstahl angesehen.

## Hinzufügen eines lokalen Bildes

Der beste Weg, um lokale Bilder einzufügen, ist die Verwendung des Buttons **CMS Content → Media** in der TinyMCE-Werkzeugleiste. Es öffnet einen Mediadialog, der die Auswahl eines beliebigen Bildes im Bildordner der Website ermöglicht.

**Wichtig:** Setzen Sie zuerst den Cursor an die Stelle, an der das Bild erscheinen soll. Dies könnte am Anfang oder Ende eines Absatzes oder in einem leeren Absatz sein.

![Das Medien-Popup-Dialogfeld](../../../en/images/articles/article-images/01-articles-edit-images-media.png)

Navigieren Sie im Popup-Dialog zu dem Bild, das Sie verwenden möchten, und wählen Sie es aus. Bei der Auswahl erscheint ein Formular, das nach zusätzlichen Daten fragt.

- **Bildbeschreibung (Alt-Text):** Diese ist wichtig für die Barrierefreiheit und die Einhaltung von Webstandards.
- **Bildklasse:** Wenn ein Bild ohne Beschriftung verwendet wird, können hier einige benutzerdefinierte Klassen angewendet werden. Zum Beispiel wird *float-end ms-2 mb-1* das Bild rechts ausrichten und den Text darum herum mit Rändern nach links und unten fließen lassen, um zu verhindern, dass der Text das Bild berührt.
- **Figurklasse:** Wenn eine Beschriftung festgelegt ist, kann eine Ausrichtungsklasse, falls vorhanden, auf die Figur angewendet werden. Beachten Sie, dass in Cassiopeia Ränder durch das Vorlagen-Stylesheet auf die Figur angewendet werden, sodass *float-start* oder *float-end* ausreichend sind.
- **Figurbeschriftung:** Aktiviert die Beschriftung, die den Inhalt dieses Feldes als Beschriftung unter dem Bild anzeigt.

**Wichtig:** Wenn das *Figurbeschriftung*-Feld leer ist, wird das Bild innerhalb eines `<img...>`-Tags eingefügt, und das *Figurklasse*-Feld wird nicht verwendet. Wenn das *Figurbeschriftung*-Feld Text enthält, wird das `<img...>`-Tag in `<figure>...</figure>`-Tags eingebettet. Die nützlichsten Klassen zum Hinzufügen sind *float-start* und *float-end*, um das Bild links oder rechts auf der Seite mit einem umgehenden Text zu platzieren.

Wählen Sie den *Inhalt einfügen*-Button, um das Bild einzufügen. Der Einfügen-Bildschirm wird geschlossen und das Bild wird im Editor angezeigt. Oder wählen Sie den *Abbrechen*-Button, um den Einfügen-Bildschirm zu verlassen.

**Tipp:** Wählen Sie den Button Editor umschalten, um die angewendeten Bild- und Figurenstile zu sehen. Möglicherweise müssen Sie eine Figur oder ein img ausschneiden und einfügen, um sie zu verschieben.

### Verwenden von Drag & Drop für lokale Bilder

Sie können ein Bild vom Desktop oder einem Dateibrowser direkt in den Text eines Beitrags ziehen, und das Bild wird in den Medienordner hochgeladen und im Beitrag platziert. Einziger Nachteil ist, dass alle auf diese Weise hochgeladenen Bilder im selben Medienordner abgelegt werden.

Der Ort des verwendeten *Bilder Verzeichnisses* für den Upload und ob diese Funktion aktiviert ist (standardmäßig eingeschaltet), wird in den Optionen der TinyMCE-Konfiguration festgelegt.

## Hinzufügen eines Remote-Bildlinks

Wenn das Bild, das Sie verwenden möchten, sich nicht im images-Ordner Ihrer Joomla-Installation befindet, ist ein etwas anderes Vorgehen erforderlich.

- Wählen Sie **Einfügen → Bild** aus der TinyMCE-Werkzeugleiste, um ein Dialogfeld zu öffnen.
- Fügen Sie im Feld **Quelle** die Bild-URL ein.
- Füllen Sie die anderen Felder nach Bedarf aus.
- Die Registerkarte **Erweitert** bietet einige Formatierungsoptionen, die als In-Line-Stile angewendet werden. Experimentieren Sie mit 1rem, 2, groove.

![Das Dialogfeld „Bild einfügen“](../../../en/images/articles/article-images/02-articles-edit-images-external-image.png)

### Verwenden von Drag & Drop zum Einfügen von Remote-Bildlinks

Sie können einen Bildlink von einer externen Website direkt in Ihren Beitragstext ziehen. Beachten Sie jedoch, dass hierbei möglicherweise auch der HTML-Container des Bildes mit Klassenanweisungen kopiert wird, die für Ihre Seite ungültig sind.

## Bilder hochladen mit dem Medien-Dialog

Sie können neue Bilder in Ihren Bilderordner von der Seite *CMS-Inhalt -> Medien* hochladen.

- Öffnen Sie den Medien-Dialog und navigieren Sie zu dem Ordner, in dem Sie neue Bilder für den aktuellen Beitrag speichern möchten.
- Wählen Sie die Schaltfläche Hochladen oben links auf dem Medienbildschirm, um einen Dateibrowser zu öffnen.
- Wählen Sie die Bilddateien aus, die Sie hochladen möchten. Klicken Sie im Dateibrowser auf Öffnen, um die Auswahl zu bestätigen. Hinweis: Der Stil und das Layout des Dateibrowsers hängen vom verwendeten Browser und Betriebssystem ab.
- Die ausgewählten Datei(en) erscheinen in alphabetischer Reihenfolge auf dem Medien/Bildschirm.
- Wenn der Upload abgeschlossen ist, erscheint oben auf dem Bildschirm eine grüne Bestätigungsanzeige.

Sie können nun das hochgeladene Bild wie zuvor auswählen und einfügen.

