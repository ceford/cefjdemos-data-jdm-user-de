<!--
{
  "source": "https://docs.joomla.org/Smart_Search_quickstart_guide",
  "title": "Schnellstart für die intelligente Suche ",
  "description": "", 
  "author": ""
}
-->

## Hintergrund

Die Suche ist seit den frühen Tagen von Joomla! ein Bestandteil der Plattform. Sie ermöglichte Nutzern, die Datenbank nach Wörtern oder Phrasen zu durchsuchen und Ergebnisse in der Reihenfolge des ersten Auftretens zurückzugeben. Diese Suchform wurde entfernt und durch die intelligente Suche (Smart Search) ersetzt, die signifikante Wörter vorab indexiert und Algorithmen zur Bewertung und Filterung nutzt, um die besten Ergebnisse zu liefern. Die intelligente Suche ist standardmäßig in Joomla 4 und 5 aktiviert.

### Warnhinweis

Wenn Sie Beiträge haben, die nicht öffentlich sichtbar sind, wird die Autovervollständigungsfunktion dennoch Begriffe anzeigen, die in diesen Beiträgen enthalten sind. Die Beiträge selbst können nicht angezeigt werden und werden nicht in den Suchergebnissen aufgeführt, aber wenn es Ihnen wichtig ist, dass das Vorhandensein eines Wortes oder einer Phrase in einem eingeschränkten Beitrag nicht offenbart wird, sollten Sie die Autovervollständigung deaktivieren. Um die Autovervollständigung zu deaktivieren, verwenden Sie folgende Vorgehensweise:

1. Melden Sie sich beim Administrator an.
2. Wählen Sie **Komponenten → Intelligente Suche**.
3. Wählen Sie die **Optionen**-Schaltfläche in der Toolbar.
4. Ändern Sie *Suchvorschläge* von **Anzeigen** zu **Ausblenden**.
5. Wählen Sie **Speichern & Schließen**.

## Vorbereitung von Smart Search Plugins

Damit Inhalte in den Suchergebnissen angezeigt werden, müssen sie zuerst von einem der Smart Search Plugins indiziert werden. Bevor der Indexer gestartet wird, wird empfohlen, die verfügbaren Plugins zu überprüfen und alle zu deaktivieren, die für Ihre Website nicht notwendig sind. Um die verfügbaren Smart Search Plugins zu überprüfen, verwenden Sie die folgende Vorgehensweise:

1. Melden Sie sich beim Administrator an.
2. Wählen Sie **Plugins** aus dem *Home Dashboard*.
3. Filtern Sie die Plugins, indem Sie das **finder**-Element aus der **- Typ auswählen -** Liste auswählen.
4. Überprüfen Sie die Liste der Plugins und deaktivieren Sie alle, die für Ihre Website nicht notwendig sind, indem Sie auf das grüne Häkchen-Symbol in der Statusspalte des Plugins klicken. Dieses sollte sich in ein graues Kreuz/Kreis ändern, um anzuzeigen, dass das Plugin deaktiviert ist.

## Ausführen des Indexers

Nachdem Sie die Such-Plugins überprüft haben, ist es an der Zeit, den Smart-Search-Indexer zu starten. Dieser wird den Inhalt Ihrer Website scannen und einen Index erstellen, der es Ihren Besuchern ermöglicht, schnell und intelligent zu suchen. Es gibt zwei Möglichkeiten, den Indexer auszuführen:

* Über das Menü **Administrator / Smart Search / Index**. Dies ist für kleinere Websites geeignet.
* Über die Befehlszeile. Dies ist für größere Websites geeignet und sollte keine Zeitüberschreitungsfehler verursachen. Sehr große Websites benötigen möglicherweise tatsächlich einen externen Suchdienst.

### Index aus der Administrator-Oberfläche

1. Melden Sie sich beim Administrator an.
2. Wählen Sie die Menüeinträge **Komponenten → Smart Search → Index**.
3. Wählen Sie die **Index**-Schaltfläche in der Werkzeugleiste, um den Indexer zu starten. Dies
    wird dazu führen, dass ein modales Fenster mit einigen Indexer-Statusinformationen
    und einem Fortschrittsbalken geladen wird.

Abhängig von der Größe Ihrer Website kann das Indizieren von wenigen Minuten bis zu mehreren Stunden dauern. Der Indexer verwendet AJAX-Anfragen, um den gesamten Prozess in kleinen Schritten abzuschließen und Zeitüberschreitungen und Speicherprobleme zu vermeiden. Die Indizierung ist abgeschlossen, wenn der Fortschrittsbalken verschwindet und das modale Fenster geschlossen wird.

### Index über die CLI

1. Öffnen Sie ein Terminalfenster.
2. Wechseln Sie in das Cli-Verzeichnis im Root Ihrer Website.
3. Verwenden Sie den folgenden Befehl:<br>
    php joomla.php finder:index
4. Wenn der Indexer fertig ist, gehen Sie zur Seite Administrator Smart Search: Indizierte Inhalte.

## Indizierte Inhalte

Die Seite Indizierte Inhalte listet alle indizierten Inhalte auf. Wenn Sie es bevorzugen, dass bestimmte Beiträge nicht in den Suchergebnissen angezeigt werden, können Sie sie aus der Smart Search-Datenbank entfernen, indem Sie das Kontrollkästchen neben dem Titel des Beitrags auswählen und dann die Schaltfläche Unveröffentlichen drücken.

**WICHTIGER HINWEIS**: Wenn Ihre Website eine große Menge an Inhalten, oder besonders große Inhalte hat, oder eingeschränkten Speicherplatz, sollten Sie sich über [Smart Search auf großen Websites](jdocmanual?article=user/smart-search/smart-search-on-large-sites) informieren.

## Smart Search den Seitenbenutzern bereitstellen

Nachdem der Smart Search-Index vorbereitet und einsatzbereit ist, müssen Sie Smart Search den Benutzern Ihrer Website zugänglich machen. Smart Search bietet zwei Möglichkeiten, dies zu tun:

### Die Modul-Schnittstelle

Smart Search enthält ein Modul, das aktiviert werden kann, um ein einfaches Suchformular auf jeder Seite an praktisch jeder Position anzuzeigen. Um das Smart Search-Modul zu aktivieren, verwenden Sie das folgende Verfahren:

1. Melden Sie sich beim Administrator an.
2. Wählen Sie den Menüpunkt Erweiterungen → Modul-Manager.
3. Klicken Sie auf die Schaltfläche Neu in der Modul-Manager-Werkzeugleiste.
4. Wählen Sie "Smart Search-Modul" aus der Liste der angezeigten Modultypen.
5. Konfigurieren Sie das Modul, indem Sie (mindestens) einen Titel eingeben, die Modulposition auswählen und bei Bedarf die Seiten einstellen, auf denen es angezeigt werden soll. Zusätzliche Modulkonfigurationsoptionen sind auf dem Hilfebildschirm des Smart Search-Moduls beschrieben.
6. Wählen Sie die Schaltfläche Speichern in der Werkzeugleiste, um das Modul zu veröffentlichen.

### Die Menüpunkt-Schnittstelle

Smart Search kann auch über einen Joomla-Menüpunkt verlinkt werden, sodass Benutzer direkt zum Hauptsuchformular navigieren können. Um einen Menüpunktlink zu Smart Search zu erstellen, verwenden Sie das folgende Verfahren:

1. Melden Sie sich beim Administrator an.
2. Wählen Sie den Menüpunkt Erweiterungen → Modul-Manager.
3. Drücken Sie die Schaltfläche Neu in der Menü-Manager-Werkzeugleiste.
4. Klicken Sie auf die Schaltfläche Auswählen neben dem Feld Menütitemtyp.
5. Wählen Sie "Suche" unter dem Eintrag "Smart Search" aus der Liste der angezeigten Menütitemtypen.
6. Konfigurieren Sie den Menüpunkt, indem Sie (mindestens) einen Menütitel eingeben und bei Bedarf das übergeordnete Element anpassen.
7. Wählen Sie die Schaltfläche Speichern in der Werkzeugleiste, um den Menüpunkt zu veröffentlichen.

## Testen, Testen, Testen

Um die Smart-Suche zu testen, navigieren Sie zu einem der von Ihnen erstellten Menüeinträge und geben Sie eine Abfrage in das Suchformular ein oder geben Sie eine Abfrage in eine der Instanzen des Smart-Suchmoduls ein. Sie sollten zu einer Liste von Suchergebnissen weitergeleitet werden, wenn für das von Ihnen eingegebene Wort oder den Satz Ergebnisse gefunden werden konnten. Wenn keine Ergebnisse gefunden werden konnten, wird eine Nachricht angezeigt, die darauf hinweist, dass keine Ergebnisse gefunden werden konnten. Wenn keine Ergebnisse gefunden werden konnten und das System basierend auf Ihrem Begriff einen Suchvorschlag hat, wird der vorgeschlagene Suchbegriff über der Nachricht angezeigt, die darauf hinweist, dass keine Ergebnisse gefunden werden konnten.

*Übersetzt von openai.com*

