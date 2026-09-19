<!--
{
    "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
    "title": "Inhalts-Tags",
    "description": " ",
    "author": ""
}
-->

## Einführung

Tags bieten eine einfache und effiziente Möglichkeit, Inhalte zu organisieren und anzuzeigen. 
Die **Tags-Komponente** ermöglicht die Verwendung einzelner Tags für verschiedene 
Inhaltstypen, einschließlich Beiträgen, Kategorien, Kontakten und Newsfeeds. Außerdem können übergeordnete und untergeordnete Tags erstellt werden.

Im Gegensatz zu Joomla-**Kategorien**, bei denen einem Element nur eine Kategorie zugewiesen werden kann, können einem einzelnen Element mehrere Tags zugewiesen werden. Es ist jedoch nicht erforderlich, Elementen Tags zuzuweisen.

Sobald ein Element mit einem bestimmten Tag versehen wurde, gelangen Sie durch Klicken auf die Tag-Schaltfläche bei Inhalten, die Tags anzeigen, zu einer Seite mit einer Liste aller Elemente, die mit diesem Tag versehen wurden. Aus diesem Grund werden Tags häufig verwendet, um *gefilterte* Inhaltslisten darzustellen.

Tags können an mehreren Stellen hinzugefügt werden, was Flexibilität bei der Erstellung von Tags bietet.

## Überlegungen

Bevor Sie beginnen, sollten Sie den Zweck der Tags auf der Website bedenken, insbesondere wenn andere Personen Inhalte hinzufügen. Wenn Tags nicht korrekt hinzugefügt und verwaltet werden, können sie kontraproduktiv sein. Häufige Probleme sind, dass Autoren neue, unnötige Tags hinzufügen oder Tag-Namen falsch schreiben. Einige Website-Administratoren entscheiden sich möglicherweise dafür, die Zugriffsberechtigungen so zu ändern, dass nur bestimmte Benutzer neue Tags hinzufügen können.

Der folgende Screenshot zeigt Tags auf einer Website mit Beiträgen über UNESCO-Welterbestätten. In diesem Fall hat jeder Tag eine eigene Farbe.

![die Seite mit der Tag-Liste](../../../en/images/tags/content-tags/01-tags-example.png)

Wenn Tags erstellt werden, werden sie in den markierten Elementen als Links angezeigt. 
Die Stile und Positionen der Tags werden durch das Website-Template festgelegt. Häufig werden sie als Schaltflächen oder Beschriftungen gestaltet.

Die Anzeige von Tags kann für einzelne Beiträge oder für alle Beiträge deaktiviert werden! Dies mag unlogisch erscheinen, ist jedoch eine nützliche Funktion, wenn Tags beispielsweise dazu verwendet werden, Inhalte für bestimmte Anwendungsfälle zu filtern.

## Die Tag-Liste

- Wählen Sie im Administrator-Menü **Komponenten → Tags**.

Dieser Screenshot zeigt Tags in einer Struktur, die für eine mehrsprachige Website verwendet wird.
Für jede Sprache gibt es eine Liste von Tags mit einem Sprach-Tag als übergeordnetem Tag.
Der übergeordnete Tag wird in den Modulen *Beliebte Tags* und *Ähnliche Tags* verwendet.

![die Seite mit der Tag-Liste](../../../en/images/tags/content-tags/02-tags-list.png)

Unabhängig davon, wie Tags erstellt wurden, sind sie in dieser Liste zu finden.

- Wählen Sie die Schaltfläche **Neu** in der Symbolleiste, um einen neuen Tag zu erstellen.
- Wählen Sie einen **Titel** eines Tags, um einen vorhandenen Tag zu bearbeiten.

### Die Registerkarte „Tag-Details“

![Bearbeitungsformular für Tags, Registerkarte „Optionen“ mit Bootstrap-CSS-Klassen](../../../en/images/tags/content-tags/03-edit-tag-details-tab.png)

- **Titel** Dies ist das einzige *erforderliche* Feld.
- **Alias** Dieser wird beim Speichern aus dem Titel erstellt.
- **Beschreibung** Es ist immer empfehlenswert, eine Beschreibung hinzuzufügen. Sie wird in den Administratorformularen angezeigt und kann hilfreich sein, wenn viele Tags verwendet werden.
- **Übergeordnet** Lassen Sie *Keine* ausgewählt, wenn dieser Tag keinen übergeordneten Tag besitzt. Oder wählen Sie einen übergeordneten Tag aus der Liste aus, um diesen Tag zu einem untergeordneten Tag zu machen.
- **Status** Dieses Feld ist standardmäßig auf *Veröffentlicht* gesetzt. Es kann auf *Unveröffentlicht*, *Archiviert* oder *Papierkorb* gesetzt werden.
- **Zugriff** Die Zugriffsebene ist standardmäßig „Öffentlich“.
- **Notiz** und **Versionshinweis:** Bei Bedarf können Sie Notizen hinzufügen.
- **Speichern & Schließen** Wenn Sie mehrere Tags erstellen, können Sie **Speichern & Neu** auswählen, um einen neuen Tag zu erstellen.

### Die Registerkarte „Optionen“

- **Layout** Es stehen möglicherweise mehrere Layouts zur Auswahl, und Sie können mit einer Template-Überschreibung ein eigenes Layout erstellen.
- **CSS-Klasse für Tag-Link** Standardmäßig werden Tags als blaue Schaltfläche angezeigt. Sie können hier Klassenangaben eingeben, um das Erscheinungsbild der Tags anzupassen und verschiedenen Tags unterschiedliche Farben zu geben. Beispiel: `bg-danger-subtle border border-danger` sind Bootstrap-Klassen, die eine rosafarbene Schaltfläche mit rotem Rand erzeugen.
- **Teaserbild und vollständiges Bild** Legen Sie Bilder für den Tag fest – ein Teaserbild für die Tag-Liste und/oder ein vollständiges Bild für die Tag-Seite.

![Bearbeitungsformular für Tags, Registerkarte „Optionen“ mit Bootstrap-CSS-Klassen](../../../en/images/tags/content-tags/04-edit-tag-options-tab.png)

### Die Registerkarte „Veröffentlichung“

- Legen Sie Metadaten für die Tag-Seite zur Suchmaschinenoptimierung (SEO) fest.

## Alternative Methoden zur Erstellung

### Aus einem Beitrag

Beim Erstellen oder Bearbeiten eines Beitrags können neue Tags hinzugefügt werden. Geben Sie in der Registerkarte „Inhalt“ des Beitrags im **Tags-Feld** den Namen des neuen Tags ein und drücken Sie **Enter**, um den Tag zu speichern und dem Beitrag zuzuweisen.

### Aus einer Kategorie

Tags können beim Erstellen oder Bearbeiten einer Kategorie hinzugefügt werden. Geben Sie in der Registerkarte **Kategorie** den Namen des Tags in das **Tags-Feld** ein und drücken Sie **Enter**, um den neuen Tag zu erstellen und zuzuweisen.

### Aus einem Kontakt

Tags können beim Erstellen oder Bearbeiten eines Kontakts hinzugefügt werden. Geben Sie in der Registerkarte **Neuer Kontakt/Kontakt bearbeiten** den Namen des Tags in das **Tags-Feld** ein und drücken Sie **Enter**, um den neuen Tag zu erstellen und zuzuweisen. Sie können auch neue Tags erstellen, wenn Sie Kontaktkategorien erstellen.

### Innerhalb eines Newsfeeds

Tags können beim Erstellen oder Bearbeiten eines neuen Newsfeeds hinzugefügt werden. Geben Sie im
Tab **Neuen Newsfeed erstellen/Bearbeiten** den Namen des Tags in das **Tags-Feld** ein und drücken Sie
**Enter**, um den neuen Tag zu erstellen und zuzuweisen. Sie können auch beim
Erstellen von Newsfeed-Kategorien neue Tags hinzufügen.

## Tags verwalten

Unabhängig davon, wo Sie in Joomla neue Tags hinzufügen, werden sie alle in der Tag-Liste angezeigt.
Verwenden Sie die Tag-Liste, um Tag-Einstellungen zu suchen, zu öffnen und anzupassen.

Sie können die Liste auf verschiedene Arten bearbeiten:

- Suchen Sie nach einem Tag, indem Sie im Suchfeld einen Teil oder den gesamten Titel bzw. Alias eingeben.
- Ordnen Sie die Liste per Drag-and-drop neu an, um die Ausgabereihenfolge zu optimieren.
- Veröffentlichen oder deaktivieren Sie Tags über die Schaltfläche in der Spalte Status.
- Wählen Sie einen oder mehrere Tags aus und verwenden Sie die Schaltfläche **Aktionen**, um die ausgewählten Tags zu veröffentlichen, zu deaktivieren, zu archivieren, einzuchecken oder in den Papierkorb zu verschieben.
- Wählen Sie einen oder mehrere Tags aus und verwenden Sie die Schaltfläche **Aktionen → Stapelverarbeitung**, um die
  Sprache oder Zugriffsebene festzulegen.

## Tag-Ausgaben

Sobald Tags auf Ihrer Website erstellt wurden, können sie in Inhalten und in Modulen wie **Beliebte Tags** und **Ähnliche Tags** verwendet werden. Die folgenden Beispiele zeigen, wie dies auf einer Website mit dem standardmäßigen **Cassiopeia**-Template aussehen kann.

![Tags, die in einem Beitrag sowie in den Modulen „Beliebte Tags“ und „Ähnliche Tags“ angezeigt werden](../../../en/images/tags/content-tags/05-tag-modules-site-view.png)

Wenn Sie einen der Tags auswählen, werden Sie zu einer Seite weitergeleitet, auf der
alle Beiträge aufgelistet werden, die diesem bestimmten Tag zugewiesen sind:

![Beispiel für die Verwendung von Tags auf einer Website mit einem schwarzen Labrador](../../../en/images/tags/content-tags/06-items-with-cultural-site-tag.png)

Die Liste der Beiträge ist eine gefilterte Liste der Website-Inhalte mit dem ausgewählten Tag.
Ein Filterfeld erleichtert das Auffinden von Beiträgen, wenn die Liste wächst.
Sie können außerdem die Anzahl der Ergebnisse festlegen, die in einer einzelnen Ansicht angezeigt werden sollen.

## Tag-Konfiguration

Einzelne Tags übernehmen Einstellungen aus den Optionen der Tags-Komponente. Wählen Sie die
Schaltfläche **Optionen** in der Symbolleiste der Tag-Listenseite aus, um die verfügbaren Standardoptionen für
Tags anzuzeigen.

Die Konfigurationsoptionen der Tags-Komponente können auf der Ebene von Beiträgen und/oder Menüeinträgen überschrieben werden.

## Tipps

- Denken Sie daran, dass Tags für mehrere Inhaltstypen verwendet werden.
- Sie können einem Beitrag mehr als einen Tag hinzufügen.
- Verwenden Sie die Hilfe-Schaltfläche der Symbolleiste, wenn Sie unsicher sind.

*Übersetzt von openai.com*