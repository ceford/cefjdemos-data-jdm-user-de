<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Cassiopeia-Anpassung -->

## Einführung

Cassiopeia ist die mit Joomla 4 gelieferte Vorlagen-Website. Es ist eine ausgezeichnete **zugängliche** und **responsive** Vorlage für allgemeine Zwecke. Sie kann über die Vorlagenoptionen und die *user.css*-Datei von Nutzern mit ein wenig Kenntnis von HTML und CSS angepasst werden.

Die folgende Abbildung zeigt das Erscheinungsbild einer Joomla 4-Website mit einem Beitrag und einigen erstellten Menüpunkten.

![Cassiopeia Einzelbeitragsansicht](../../../en/images/templates/cassiopeia-customisation-article-view.png)

## Vorlagen: Stil bearbeiten

Sie können mit dem Erscheinungsbild der Website experimentieren, indem Sie das Formular Stil bearbeiten öffnen. Gehen Sie zu **System → Vorlagen → Vorlagenstil der Website** und wählen Sie den Titel der Vorlage in der Spalte Stil, Cassiopeia - Standard. Der Tab „Erweitert“ enthält Einstellungen, die Sie anpassen können:

![Cassiopeia Stil bearbeiten Erweitert-Tab](../../../en/images/templates/cassiopeia-customisation-edit-style.png)

Um die Optionen auszuprobieren, öffnen Sie einen Browser-Tab oder ein Fenster mit der Administrator-Schnittstelle und einen zweiten Tab oder Fenster mit der Website-Schnittstelle und wechseln Sie nach jeder gespeicherten Änderung hin und her.

### Marke

- **Ja** die Standardoption. Die Cassiopeia-Logoleiste mit einem Logo oder Markennamen wird mit einem dunklen Hintergrund angezeigt, standardmäßig in Blau.
- **Nein** Die Logoleiste wird nicht angezeigt. Die Optionen zum Auswählen eines Logos, Titels und Slogans verschwinden.

Das Standard-Markenbild ist das Wort Cassiopeia als Bild in einer SVG-Datei. Das wird in der ersten Abbildung oben angezeigt.

Sie könnten die Marke auf Nein setzen, wenn Sie ein Branding in einem benutzerdefinierten HTML-Modul bereitstellen möchten.

### Logo

- **Keines** Das Standard-Cassiopeia-Logobild wird verwendet, es sei denn, es ist ein Titel definiert.
- **Logobild** Das ausgewählte Logo erscheint anstelle des Cassiopeia-Logos, auch wenn ein Titel definiert ist.

### Titel (Alternative zum Logo)

- **Mein Markenname** Wenn vorhanden und kein Logobild ausgewählt wurde, erscheinen die Worte im Titelfeld, jedoch unterstrichen in der blauen oberen Leiste.

### Slogan

- **Stets zu Ihren Diensten** Wenn vorhanden, erscheinen die Worte im Sloganfeld in kleiner Schriftgröße unter dem Logobild oder Markennamen.

![Cassiopeia Marke mit Slogan](../../../en/images/templates/cassiopeia-customisation-brand-with-tagline.png)

### Schriftarten-Schema

- **Keines** die Standardeinstellung. Die in dem Vorlagen-Stylesheet angegebene Schriftfamilie wird verwendet, was normalerweise bedeutet, dass die Website die Ihnen vertrauten Schriftarten verwendet, die auf Ihrem eigenen Computer verfügbar sind.
- **Andere** Eine Schriftfamilie, die sich im Vorlagen-Ordnerverzeichnis befindet oder aus dem Internet heruntergeladen wurde, wird verwendet. Sie können das veränderte Erscheinungsbild des Textes auf einer Seite sehen, wenn Sie die Seite nach Ändern dieser Option neu laden.

### Farbthema

- **Standard** Eine dunkelblaue Hintergrundfarbe für die Markenleiste und andere Funktionen wie die Login-Taste.
- **Alternative** Eine kastanienbraune Hintergrundfarbe statt Dunkelblau.

![Cassiopeia alternatives Farbschema](../../../en/images/templates/cassiopeia-customisation-alt-color-scheme.png)

### Layout

- **Statisch** die Standardeinstellung. Die maximale Breite ist auf 1320px eingestellt. Auf breiteren Bildschirmen wird der Rand einfach breiter.
- **Fließend** Es gibt keine maximale Breite.

Die Ansicht auf einem mobilen Gerät mit schmalem Bildschirm:

![Cassiopeia mobile Ansicht](../../../en/images/templates/cassiopeia-customisation-mobile-view.png)

### Fixierter Header

- **Nein** die Standardeinstellung. Header-Elemente und Inhalte scrollen nach oben aus dem Ansichtsfeld hinaus.
- **Ja** Mit Ausnahme von schmalen Bildschirmen bleiben Header-Elemente am oberen Rand des Ansichtsfeldes fixiert, während sich die Inhaltselemente nach oben scrollen. Das ist nur dann sichtbar, wenn der Seiteninhalt höher ist als das Ansichtsfeld.

### Zurück-zum-Anfang-Link

- **Nein** die Standardeinstellung. Es gibt keinen Zurück-zum-Anfang-Link.
- **Ja** Wenn der Inhalt höher ist als das Ansichtsfeld, befindet sich unten rechts auf der Seite eine Schaltfläche mit einem Pfeil nach oben. Wählen Sie diese aus, um zurück zum Seitenanfang zu scrollen.

![Cassiopeia Zurück-zum-Anfang](../../../en/images/templates/cassiopeia-customisation-back-to-top.png)

## Cassiopeia-Vorlagenpositionen

Beim Erstellen einer Website mit Cassiopeia ist es sehr nützlich, die Standorte der Positionen zu kennen, die Sie für Module verwenden können. Einige sind beschreibend, wie *menu* und *bottom-a*, aber es ist nicht sofort ersichtlich, wo sie sich befinden, bis sie verwendet werden. Diese Abbildung sollte helfen:

![Cassiopeia-Vorlagenpositionen](../../../en/images/templates/cassiopeia-template-positions.png)

Versuchen Sie Folgendes:

### Verschieben Sie das Menümodul in die Position *menu*

Eine neu installierte Joomla 4-Website hat ein Menü in der Position *sidebar-right*, wie in der ersten Abbildung oben zu sehen. Für dieses Tutorial wurden einige Menüeinträge hinzugefügt, von denen einer ein übergeordneter Eintrag mit zwei untergeordneten Einträgen ist. Um dieses Menü in die Menüposition zu verschieben, gehen Sie im Administratormenü zu **Inhalt** → **Modulpositionen**. In der Liste gibt es drei Module, einschließlich des Hauptmenüs. Wählen Sie es aus, um das Modul-Menü-Bearbeitungsformular zu öffnen.

Im Tab "Modul" ändern Sie das Feld "Position" rechts auf Menü \[menu\]. Speichern Sie und werfen Sie einen Blick auf das Ergebnis in der Website-Anzeige. Das Menü sieht gut aus, aber die untergeordneten Einträge sind nicht vorhanden.

Wählen Sie im Menü-Bearbeitungsformular die Registerkarte "Erweitert" aus und scrollen Sie zum Feld "Layout". Es ist eine Dropdown-Liste mit vier Optionen. --Aus Modul-- / Standard ist standardmäßig ausgewählt. Probieren Sie die anderen Optionen aus und sehen Sie sich das Ergebnis an. (Denken Sie daran, im Bearbeitungsformular zu *speichern* und im Website-Ansichtsbereich neu zu laden.) Keine der --Aus Modul-- Optionen zeigt die untergeordneten Menüeinträge an, aber beide --Aus Cassiopeia-Vorlage-- tun dies.

![Cassiopeia-Menüpositionen](../../../en/images/templates/cassiopeia-customisation-menu-position.png)

Welchen Unterschied macht also **Collapsible**?

- Einklappbares Dropdown: Auf mobilen Geräten mit schmalem Bildschirm wird das Menü bis zur Auswahl zu einem Hamburger-Symbol zusammengeklappt. Bei Auswahl wird es erweitert, um eine vertikale Liste anzuzeigen.
- Dropdown: Das Menü erscheint immer als vertikale Liste.

### Verschieben Sie das Menümodul in die Position *topbar*

Setzen Sie im Modul-Tab des Bearbeitungsformulars die Position auf Top Bar \[topbar\] und betrachten Sie das Ergebnis. Es gibt ein Problem - das Menü ist weiter links positioniert als in der Menüposition. Das liegt daran, dass die Menüposition und der Standort des Logos eine CSS-Klasse *grid-child* haben, die Topbar jedoch nicht. Dies kann mit einem Eintrag in der Datei *user.css* behoben werden, siehe unten.

## Cassiopeia anpassen

Was, wenn Ihnen die dunkelblaue Hintergrundfarbe des Headers nicht gefällt? Angenommen, Sie würden ein dunkelgrünes Thema bevorzugen. Um das zu beheben, benötigen Sie ein wenig Wissen über CSS. Gehen Sie zu **System **→** Site Templates **→** Cassiopeia Details und Dateien**, um das Formular Template: Anpassen (Cassiopeia) zu öffnen.

Die Abbildung unten zeigt zwei Ordnergruppen. Die erste Gruppe besteht aus den Template-Ordnern und Dateien, die Sie nicht ändern sollten, zu denen Sie jedoch hinzufügen können. Insbesondere können Sie HTML-Dateien für Template-Overrides zum *html*-Ordner hinzufügen. Die zweite Gruppe enthält die Medien-Dateien des Templates, die Sie nicht ändern sollten. Sie können jedoch eine *user.css*-Datei zum *css*-Ordner und/oder eine *user.js*-Datei zum *js*-Ordner hinzufügen. Dies würden Sie tun, wenn Sie ein paar einfache Änderungen an der Webseitenoptik vornehmen möchten.

![Cassiopeia Dateien bearbeiten](../../../en/images/templates/cassiopeia-customisation-edit-files.png)

Beachten Sie, dass in einer neuen Joomla-Installation keine Datei ***user.css*** im Ordner **css** vorhanden ist. Diese Datei erstellen Sie selbst, um zuvor definierte Styles zu überschreiben. Wenn ***user.css*** bereits vorhanden ist, wählen Sie sie aus, um das Bearbeitungsformular zu öffnen. Ist sie noch nicht vorhanden, erstellen Sie sie jetzt:

1. Wählen Sie die Schaltfläche **New File**.
2. Wählen Sie im Modal-Dialog **New File** den Ordner **css** aus, da die neue Datei sonst am falschen Speicherort erstellt wird.
3. Geben Sie im Feld **File Name** `user` (kleingeschrieben und ohne `.css`) ein und wählen Sie im Feld **File Type** die Option `.css` aus.
4. Wählen Sie die Schaltfläche **Create**, um die Datei zu erstellen.

### Überschriften

Als einfachen Einstieg ändern Sie die Farbe der Überschriften auf Dunkelgrün. Überschriften sind Tags im Bereich *h1, h2, h3, h4, h5* und *h6*. Geben Sie in der *user.css*-Datei die Stildefinition ein:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Speichern Sie und laden Sie die Seite neu, um das Ergebnis zu sehen. Der Seiten- oder Beitragstitel sollte dunkelgrün sein. Wenn nicht, überprüfen Sie, was Sie getippt haben. Die formale Sprache für Joomla-Dokumentation ist britisches Englisch, also colour statt color wie im amerikanischen Englisch. Aber in CSS muss es color sein. Ist die Interpunktion korrekt?

Weniger offensichtlich ist, dass einige andere Tags als Überschriften gestaltet sein können. Fügen Sie daher dies hinzu:
```css
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Beachten Sie hier, dass der vorangestellte Punkt (.) ein Klassen-Selektor ist, z.B. Dummy-H1 - daher gibt es einen Punkt in der CSS-Datei, aber nicht im Klassennamen.

### Header-Hintergrund

Öffnen Sie im Browser-Tab, das die Seite enthält, die Entwicklerwerkzeuge Ihres Browsers, in diesem Beispiel Firefox, und wählen Sie das header-Tag aus.

![Cassiopeia Entwicklerwerkzeuge](../../../en/images/templates/cassiopeia-customisation-developer-tools.png)

Das zeigt die verwendeten Stile. Der Stil container-header ist dort, wo der background-color und das background-image gesetzt sind. Diese müssen in der *user.css*-Datei überschrieben werden. Probieren Sie dies:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### *topbar* Stil

Erinnern Sie sich an den Kommentar, dass das Menü in der Topbar zu weit links ist? Das liegt daran, dass keine maximale Breite und keine entsprechenden Ränder gesetzt sind. Fügen Sie dies in der *user.css*-Datei hinzu, um das zu beheben:
```css
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Dies ist das funktionierende grüne Thema:

![Cassiopeia grünes Thema](../../../en/images/templates/cassiopeia-customisation-green-theme.png)

### Barrierefreiheit

Beachten Sie, dass es einen ausreichenden Kontrast zwischen Hintergrund- und Vordergrundfarben geben muss, um die Standards für Web-Barrierefreiheit zu erfüllen. Sie können Ihren Kontrast mit dem WebAIM Contrast Checker überprüfen. Dunkelgrün ist \#006400.

## Überschreibungen

Der Tab „Überschreibungen erstellen“ im Formular „Templates: Anpassen (Cassiopeia)“ zeigt die Liste der Erweiterungen, für die Sie eine Überschreibung erstellen können. Beachten Sie die unterschiedlichen Symbole: Wählen Sie ein Ordnersymbol, um eine Liste der enthaltenen Ordner und Dateien anzuzeigen; wählen Sie ein Mehrfachdateisymbol, um sofort eine Überschreibung für diese Erweiterung zu erstellen; das erstellte Element verschwindet aus der Liste - wählen Sie den Reiter „Editor“ und suchen Sie die erstellte Überschreibung im *html*-Ordner. Es können mehr als eine Datei erstellt werden - die erstellten Dateien werden aus der ursprünglichen Erweiterung kopiert, damit Sie sie bearbeiten können. Dafür benötigen Sie einige Kenntnisse in HTML und PHP!

Dies ist der Tab „Überschreibungen erstellen“:

![Cassiopeia Überschreibungen erstellen](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Wenn Sie nur experimentieren und eigentlich keine Überschreibung möchten, können Sie das Bearbeitungsformular *schließen*, die Schaltfläche „Ordner verwalten“ in der Symbolleiste auswählen und die Schaltfläche „Löschen“ am unteren Rand des Formulars „Ordner verwalten“ auswählen.

Überschreibungen betreffen wirklich die Anpassung von Erweiterungen und nicht das Cassiopeia-Template, und das ist eine andere Geschichte.

## Kindvorlagen

Wenn Sie größere Änderungen am Erscheinungsbild der Website vornehmen möchten, können Sie eine Kindvorlage erstellen. Diese kopiert nur eine kleine Auswahl an Ordnern und Dateien, die Sie ändern oder hinzufügen können, während sie ansonsten weiterhin die Ordner und Dateien der übergeordneten Vorlage verwendet. Durch die Verwendung von Kindvorlagen können Sie einige Seiten mit einer Farbthematik und andere Seiten mit einer zweiten Farbthematik gestalten. Kindvorlagen werden an anderer Stelle behandelt. Hier ist eine Darstellung der Dateistruktur in einem Kind von Cassiopeia:

![Cassiopeia Kindvorlagendateien](../../../en/images/templates/cassiopeia-customisation-child-template-files.png)

*Übersetzt von openai.com*

