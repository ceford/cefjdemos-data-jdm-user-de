<!--
{
  "source": "https://docs.joomla.org/J4.x:Site_Modules",
  "title": "Webseiten-Module",
  "description": "", 
  "author": ""
}
-->

## Einführung

Module sind leichtgewichtige und flexible Erweiterungen, die verwendet werden, um Informationsschnipsel in **Boxen** anzuzeigen, die um eine Komponente auf einer Seite herum angeordnet sind. Ein bekanntes Beispiel ist das Login-Modul. Module werden pro Menüpunkt zugewiesen, sodass Sie entscheiden können, ob ein Modul angezeigt oder verborgen wird, je nachdem, welche Seite der Benutzer gerade betrachtet.

Einige Module sind mit Komponenten verknüpft. Zum Beispiel ist das Modul **Neueste Nachrichten** mit der Inhaltskomponente verknüpft, um Links zu den neuesten Beiträgen anzuzeigen. Module müssen nicht mit Komponenten verknüpft sein. Sie müssen überhaupt nicht mit irgendetwas verknüpft sein und können einfach statisches HTML oder Text sein.

Es kann mehrere Instanzen desselben Moduls geben. Zum Beispiel können Sie eine Instanz des Moduls Zufallsbild für einige Seiten und eine andere Instanz für andere Seiten verwenden, wobei jeweils ein anderer Bilderordner zum Auswählen der Bilder genutzt wird.

## Modulpositionen

Module werden einer Position auf einer Seite zugewiesen, die durch das verwendete Template definiert ist. Die folgende Abbildung zeigt ein schematisches Layout des Cassiopeia-Templates:

![Diagramm der Cassiopeia-Template-Positionen](../../../en/images/modules/site-modules/01-cassiopeia-template-positions.png)

Und die folgende Liste zeigt die verfügbaren Modulpositionen nach Namen:

```xml
    <positions>
        <position>topbar</position>
        <position>below-top</position>
        <position>menu</position>
        <position>search</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
```

## Ein Kernmodul hinzufügen

Kernmodule sind diejenigen, die mit einer neuen Joomla-Installation geliefert werden. Es gibt Tausende zusätzlicher Module von Drittanbietern. Angenommen, Sie möchten ein zufälliges Bild anzeigen, um Ihre Website für Besucher interessanter zu machen. Wählen Sie im Administrator-Menü **Inhalt → Seiten-Module**, um die Liste der bereits verwendeten Seiten-Module zu sehen:

![Liste der Seiten-Module](../../../en/images/modules/site-modules/02-cassiopeia-modules-list.png)

Wählen Sie die Schaltfläche "Neu", um eine Liste der verfügbaren Seiten-Module zur Installation anzuzeigen:

![Verfügbare Seiten-Module](../../../en/images/modules/site-modules/03-cassiopeia-modules-available.png)

Scrollen Sie nach unten und wählen Sie das Modul "Zufälliges Bild". Dadurch wird das Formular **Module: Zufälliges Bild** zur Bearbeitung geöffnet, das Sie ausfüllen können.

![Modul Zufälliges Bild](../../../en/images/modules/site-modules/04-cassiopeia-module-random-image.png)

- **Titel** Dies ist ein Pflichtfeld.
- **Bildtyp** Standard ist jpg.
- **Bilder-Ordner** Geben Sie einen Pfad zu einem Ordner ein, der tatsächlich Bilder des ausgewählten Typs enthält.
- **Link** Eine URL, auf die umgeleitet wird, wenn das Bild ausgewählt wird.
- **Breite** Erzwingt die Anzeige aller Bilder mit dieser Breite in Pixeln.
- **Höhe** Leer lassen, um das Seitenverhältnis des Bildes beizubehalten.
- **Position** Wählen Sie eine Modulposition, damit das Modul tatsächlich auf einer Seite angezeigt wird. Im Beispiel wurde sidebar-right ausgewählt.
- **Speichern & Schließen** Oder nutzen Sie die Schaltfläche "Hilfe" in der Symbolleiste, um herauszufinden, was die anderen Felder bedeuten.

## Modulreihenfolge

Nach dem Speichern müssen Sie möglicherweise die Reihenfolge der Module in der ausgewählten Position ändern. Gehen Sie wie folgt vor:

- Wählen Sie in der Modulübersicht das Symbol für die Spaltenreihenfolge in der Tabellenüberschrift der Module aus. Es ist ein kombiniertes Auf-/Ab-Dreieck. Dadurch wird die Tabelle sortiert und die Symbole zum Verschieben der Elemente angezeigt, ein vertikales Auslassungszeichen. Wählen Sie erneut, um die Sortierfolge umzukehren! Das Sortiersymbol in der Spalte ändert sich: Aufwärtsdreieck zur Anzeige der normalen Sortierreihenfolge, Abwärtsdreieck zur Anzeige der umgekehrten Sortierreihenfolge.
- Ziehen Sie das Auslassungssymbol des Zufallsbildes, um es nach oben oder unten zu verschieben. Lassen Sie los, wenn es sich in der von Ihnen bevorzugten Position befindet.

## Website ansehen

![Ansicht des Zufallsbild-Moduls auf der Website](../../../en/images/modules/site-modules/05-cassiopeia-module-random-image-site.png)

Überprüfen Sie das Erscheinungsbild der Website. In diesem Fall könnte es eine gute Idee sein, das Bild zu zentrieren. Das kann wie folgt gemacht werden:

- Gehen Sie zurück zum Bearbeitungsformular und wählen Sie den Reiter „Erweitert“.
- Geben Sie im Feld „Modulklasse“ text-center ein und speichern Sie.
- Sehen Sie sich das Ergebnis an, indem Sie die Website-Seite neu laden.

Alles erledigt?

## Liste der Kernmodule

- **Beiträge - Archiviert** Dieses Modul zeigt eine Liste der Kalendermonate, die archivierte Beiträge enthalten. Nachdem Sie den Status eines Beitrags auf Archiviert geändert haben, wird diese Liste automatisch erstellt.
- **Beiträge - Kategorien** Dieses Modul zeigt eine Liste von Kategorien aus einer übergeordneten Kategorie an.
- **Beiträge - Kategorie** Dieses Modul zeigt eine Liste von Beiträgen aus einer oder mehreren Kategorien an.
- **Beiträge - Neueste** Dieses Modul zeigt eine Liste der kürzlich veröffentlichten und aktuellen Beiträge an.
- **Beiträge - Meistgelesen** Dieses Modul zeigt eine Liste der veröffentlichten Beiträge an, die die höchste Anzahl an Seitenaufrufen haben.
- **Beiträge - Newsflash** Das Newsflash-Modul zeigt eine festgelegte Anzahl von Beiträgen aus einer bestimmten Kategorie an.
- **Beiträge - Verwandt** Dieses Modul zeigt andere Beiträge an, die zu dem gerade betrachteten Beitrag in Beziehung stehen. Diese Beziehungen werden durch die Schlagwörter etabliert. Alle Schlagwörter des aktuellen Beitrags werden mit denen aller anderen Beiträge abgeglichen.
- **Banner** Das Banner-Modul zeigt die aktiven Banner aus der Komponente an.
- **Breadcrumbs** Dieses Modul zeigt die Breadcrumbs an.
- **Benutzerdefiniert** Dieses Modul ermöglicht es Ihnen, Ihr eigenes Modul mit einem WYSIWYG-Editor zu erstellen.
- **Feed-Anzeige** Dieses Modul ermöglicht die Anzeige eines syndizierten Feeds.
- **Fußzeile** Dieses Modul zeigt die Joomla! Copyright-Informationen an.
- **Sprachwechsler** Dieses Modul zeigt einen Sprachwechsler für die auf Ihrer Website verfügbaren Inhalts-Sprachen an.
- **Neueste Benutzer** Dieses Modul zeigt die zuletzt registrierten Benutzer an.
- **Login** Dieses Modul zeigt ein Anmeldeformular mit Benutzername und Passwort an. Es enthält auch einen Link, um ein vergessenes Passwort wiederherzustellen. Wenn die Benutzerregistrierung aktiviert ist (in Benutzer → Verwalten → Optionen),...
- **Menü** Dieses Modul zeigt ein Menü im Frontend an.
- **Zufallsbild** Dieses Modul zeigt ein zufälliges Bild aus Ihrem ausgewählten Ordner an.
- **Smart Search** Dies ist ein Suchmodul für das Smart-Suchsystem.
- **Statistiken** Das Statistikmodul zeigt Informationen über Ihre Serverinstallation zusammen mit Statistiken zu den Website-Nutzern und der Anzahl der Beiträge in Ihrer Datenbank an.
- **Syndikations-Feeds** Smart Syndication Modul, das einen syndizierten Feed für die Seite erstellt, auf der das Modul angezeigt wird.
- **Tags - Beliebt** Dieses Modul zeigt Tags, die auf der Website verwendet werden, entweder in einer Liste oder in einer Cloud-Darstellung. Tags können nach Titel oder nach der Anzahl der getaggten Elemente geordnet und auf einen bestimmten Zeitraum begrenzt werden.
- **Tags - Ähnlich** Das Ähnliche-Tag-Modul zeigt Links zu anderen Elementen mit ähnlichen Tags. Die Nähe der Übereinstimmung kann angegeben werden.
- **Wer ist online** Das Wer ist online-Modul zeigt die Anzahl der anonymen Benutzer (Gäste) und registrierten Benutzer (angemeldete Nutzer) an, die derzeit auf die Website zugreifen.
- **Wrapper** Dieses Modul zeigt ein iframe-Fenster zu einem angegebenen Ort an.
