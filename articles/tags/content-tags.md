<!--
{
  "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
  "title": "Inhalts-Tags",
  "description": "", 
  "author": ""
}
-->

## Einführung

Tags bieten eine einfache und effiziente Möglichkeit, Inhalte zu organisieren und darzustellen. Die **Tags-Komponente** ermöglicht die Verwendung von Tags über verschiedene Inhaltstypen hinweg, einschließlich Beiträge, Kategorien, Kontakte und Newsfeeds. Sie bietet auch die Erstellung von übergeordneten und untergeordneten Tags.

Im Gegensatz zu Joomla **Kategorien**, bei denen nur eine Kategorie einem Element zugewiesen werden kann, können mehrere Tags einem einzelnen Element zugewiesen werden, aber es ist keine Voraussetzung, Tags zuzuweisen.

Sobald ein Element mit einem bestimmten Tag versehen ist, führt das Klicken auf den Tag-Button bei der Anzeige von Inhalten mit Tags zu einer Seite, die eine Liste aller Elemente anzeigt, die mit diesem bestimmten Tag versehen wurden. Aus diesem Grund werden Tags oft als eine Möglichkeit verwendet, um *gefilterte* Listen von Inhalten zu präsentieren.

Tags können an mehreren Stellen hinzugefügt werden, was Flexibilität bei der Erstellung von Tags bietet.

## Überlegungen

Bevor Sie starten, denken Sie über den Zweck von Tags auf der Website nach, insbesondere wenn andere Inhalte hinzufügen werden. Wenn sie nicht korrekt hinzugefügt und verwaltet werden, können Tags kontraproduktiv werden. Häufige Probleme beinhalten, dass Inhaltsautoren neue unnötige Tags hinzufügen und schlecht buchstabierte Tag-Namen erstellen. Einige Seitenadministratoren könnten sich dafür entscheiden, die Zugriffsberechtigungen so anzupassen, dass nur bestimmte Benutzer neue Tags hinzufügen können.

Wenn Tags erstellt werden, werden sie als Links in den markierten Beiträgen angezeigt. Die Tag-Stile und Positionen werden durch das Website-Template definiert. Sie werden oft als Buttons oder Labels gestaltet.

Die Tag-Anzeige kann deaktiviert werden! Dies mag unlogisch erscheinen, ist aber eine nützliche Funktion, wenn Tags verwendet werden, um beispielsweise Inhalte für spezifische Anwendungsfälle zu filtern.

## Die Liste der Tags

- Wählen Sie **Komponenten → Tags** aus dem Administrator-Menü.

![die Tags-Liste Seite](../../../en/images/tags/content-tags/01-tags-list.png)

Unabhängig davon, wie Tags erstellt werden, können sie in dieser Liste gefunden werden.

## Hinzufügen von Tags

### Über die Tag-Liste

Wählen Sie die Schaltfläche **Neu** in der Symbolleiste der Tag-Liste.

![neuer Tag namens predator](../../../en/images/tags/content-tags/02-new-tag-predator.png)

- **Titel** Dies ist das einzige *Pflichtfeld*.
- **Alias** Dieser wird beim Speichern aus dem Titel erstellt.
- **Beschreibung** Es ist immer am besten, eine Beschreibung hinzuzufügen. Sie wird in Administratorformularen angezeigt und kann hilfreich sein, wenn viele Tags verwendet werden.
- **Eltern** Wenn dies ein Stamm-Eltern-Tag ist, lassen Sie dies auf *Keine* eingestellt. Oder wählen Sie ein Eltern-Tag aus der Liste, wenn dies ein Untertag ist.
- **Status** Dieses Feld ist standardmäßig auf *Veröffentlicht* gesetzt. Es kann auf *Unveröffentlicht*, *Archiviert* oder *Papierkorb* eingestellt werden.
- **Zugriff** Die Zugriffsebene ist standardmäßig Öffentlich.
- **Hinweis** und **Versionshinweis:** Bei Bedarf können Sie Anmerkungen hinzufügen.
- **Speichern & Schließen** Der neue Tag erscheint in der Tag-Liste. Wenn Sie mehrere Tags erstellen, können Sie stattdessen auf **Speichern & Neu** klicken, um einen weiteren zu erstellen.

Nach dem Speichern steht der Tag zur Verwendung in den verschiedenen Inhaltstypen zur Verfügung, die sie nutzen.

### Innerhalb eines Beitrags

Es ist möglich, neue Tags hinzuzufügen, während Sie einen Beitrag erstellen oder bearbeiten. Im Reiter Inhalts-**Tags-Feld** geben Sie den Namen des neuen Tags ein und drücken **Enter**, um das Tag zu speichern und dem Beitrag zuzuweisen.

### Innerhalb einer Kategorie

Tags können beim Erstellen oder Bearbeiten einer Kategorie hinzugefügt werden. Im **Kategorie**-Reiter geben Sie den Tag-Namen im **Tags-Feld** ein und drücken **Enter**, um das neue Tag zu erstellen und zuzuweisen.

### Innerhalb eines Kontakts

Tags können beim Erstellen oder Bearbeiten eines Kontakts hinzugefügt werden. Im Reiter **Neuer/Editierter Kontakt** geben Sie den Tag-Namen im **Tags-Feld** ein und drücken **Enter**, um das neue Tag zu erstellen und zuzuweisen. Sie können auch neue Tags hinzufügen, wenn Sie Kontakt-Kategorien erstellen.

### Innerhalb eines Newsfeeds

Tags können beim Erstellen oder Bearbeiten eines neuen Newsfeeds hinzugefügt werden. Im Reiter **Neuer/Editierter Newsfeed** geben Sie den Tag-Namen im **Tags-Feld** ein und drücken **Enter**, um das neue Tag zu erstellen und zuzuweisen. Sie können auch neue Tags hinzufügen, wenn Sie Newsfeed-Kategorien erstellen.

## Verwalten von Tags

Wo auch immer Sie neue Tags in Joomla hinzufügen, werden sie alle in der Tag-Liste erscheinen. Verwenden Sie die Tag-Liste, um Tags zu finden, zu öffnen und deren Einstellungen anzupassen.

### Der Tag-Liste-Filter

![Tags Liste Filter nach Typ](../../../en/images/tags/content-tags/03-tags-list-filter.png)

Sie können die Liste auf verschiedene Weise beeinflussen:

- Suchen Sie nach einem Tag, indem Sie einen Teil oder den gesamten Titel im Suchfeld eingeben.
- Ordnen Sie die Liste neu, indem Sie Drag & Drop verwenden, um die Ausgabe-Reihenfolge zu optimieren.
- Veröffentlichen oder deaktivieren Sie Tags mit der Schaltfläche in der Spalte Status.
- Wählen Sie ein oder mehrere Tags aus und verwenden Sie die **Aktionen**-Schaltfläche, um die ausgewählten Tags zu veröffentlichen, zu deaktivieren, zu archivieren, einzuchecken oder in den Papierkorb zu verschieben.
- Wählen Sie ein oder mehrere Tags aus und verwenden Sie die Schaltfläche **Aktionen → Stapel**, um die Sprache oder die Zugriffsebene festzulegen.

### Tag-Einstellungen

- Wählen Sie einen Tag-**Titel**, um Änderungen an dessen Einstellungen vorzunehmen.

Im Tag-Bearbeitungsformular:

- Die Einstellungen auf der Registerkarte **Tag Details** wurden oben behandelt.
- Die Registerkarte **Optionen**:
  - Ändern Sie das Layout der Tag-Seite (die Seite, die erscheint, wenn Sie auf den Tag-Link klicken - beispielsweise mysite.com/tags/mein-tag). Dieses Layout ist normalerweise die Standardeinstellung und abhängig von der Vorlage.
  - Fügen Sie eine CSS-Klasse hinzu, um einen anderen Stil (Erscheinungsbild) für den Link des Tags anzuwenden. Dies wird normalerweise nur vom Site-Administrator verwendet.
  - Setzen Sie Bilder für den Tag fest - ein Teaser-Bild für die Tag-Liste und/oder ein vollständiges Bild für die Tag-Seite.
- Die Registerkarte **Veröffentlichung**: Setzen Sie Metadaten für die Tag-Seite für die Suchmaschinenoptimierung (SEO).

## Wie Joomla Tags Ausgibt

Sobald Tags auf Ihrer Website erstellt wurden, können sie nicht nur in Inhalten, sondern auch in einigen nützlichen Modulen wie **Beliebte Tags** und **Ähnliche Tags** verwendet werden. Die folgenden Beispiele zeigen, wie diese auf einer Standardinstallation mit dem Standard-Template **Cassiopeia** aussehen.

![Beispiel zur Nutzung von Tags auf der Website, gelber Labrador](../../../en/images/tags/content-tags/04-tag-examples-yellow-labrador.png)

Wenn Sie auf eines der Tags klicken, gelangen Sie zu einer Seite, die alle Beiträge auflistet, die diesem bestimmten Tag zugewiesen sind:

![Beispiel zur Nutzung von Tags auf der Website, schwarzer Labrador](../../../en/images/tags/content-tags/05-tag-examples-black-labrador.png)

Ein Klick auf einen Tag führt Sie zu einer Seite, die eine Liste aller mit diesem speziellen Tag versehenen Beiträge ausgibt. Im Grunde ist es eine gefilterte Liste Ihrer getaggten Website-Inhalte. Ein Filterfeld wird bereitgestellt, um das Auffinden von Beiträgen zu erleichtern, wenn die Liste wächst. Sie können auch die Anzahl der Ergebnisse festlegen, die Sie in einer einzelnen Ansicht sehen möchten.

## Konfiguration der Tags

Einzelne Tags erben Einstellungen von den Optionen der Tags-Komponente. Dies wird in einem separaten Tutorial behandelt. [ToDo] Wählen Sie die Schaltfläche **Optionen** in der Symbolleiste der Tag-Liste.

Die Konfiguration der Tags-Komponente kann auf Menüebene überschrieben werden.

## Tipps

- Denke daran, dass Tags über mehrere Inhaltstypen hinweg verwendet werden
- Du kannst einem Beitrag mehrere Tags hinzufügen
- Verwende die Hilfeschaltfläche, wenn du unsicher bist

*Übersetzt von openai.com*

