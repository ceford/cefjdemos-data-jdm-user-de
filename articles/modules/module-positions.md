<!--
{
  "source": "https://docs.joomla.org/J4.x:Module_Positions",
  "title": "Modulpositionen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Template-Modulpositionen sind in einer templateDetails.xml-Datei definiert und werden in einer Template-index.php-Datei verwendet. Mehrere Module können einer einzelnen Position zugewiesen werden, sodass es selten notwendig ist, weitere Positionen zu erstellen. Wenn Sie jedoch mehr Positionen möchten, müssen Sie Ihr eigenes Template erstellen, was hier nicht abgedeckt wird.

## Vorschau der Modulpositionen

Es gibt eine Template-Option, die es Ihnen ermöglicht, Modulpositionen in Site- und Administrator-Templates zu sehen, einschließlich Positionen, denen keine Module zugewiesen sind. Um diese Funktion zu aktivieren:

- Wählen Sie **System**→**Site-Templates** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche `Optionen` aus der Werkzeugleiste.
- Setzen Sie im Formular Template: Optionen die Einstellung **Vorschau der Modulpositionen** auf **Aktiviert**.
- Speichern und schließen.

Um Modulpositionen anzuzeigen, müssen Sie entweder ?tp=1 oder &tp=1 zur URL hinzufügen.

- Wenn die URL kein Fragezeichen enthält, fügen Sie ?tp=1 hinzu.
- Wenn die URL bereits ein Fragezeichen enthält, fügen Sie &tp=1 hinzu.

### Atum Administrator-Template Positionen

![templates atum template positions](../../../en/images/modules/module-positions/01-template-positions-templates-page.png)

### Cassiopeia Site-Template Positionen

![templates cassiopeia template positions](../../../en/images/modules/module-positions/02-template-positions-site-page.png)

Dieses Modulpositionsdiagramm könnte ebenfalls hilfreich sein:

![cassiopeia template position diagram](../../../en/images/modules/module-positions/03-cassiopeia-template-positions.png)

## Produktionsstandorte

Denken Sie daran, die **Vorschau der Modulpositionen** auf **Deaktiviert** in Produktionsstandorten zu ändern.

*Übersetzt von openai.com*

