<!--
{
  "source": "https://docs.joomla.org/J4.x:Deleting_an_Article",
  "title": "Beiträge: Löschen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

In Joomla ist das Löschen eines Beitrags ein zweistufiger Prozess. Die erste Stufe verschiebt ihn in den *Papierkorb*, von wo aus er wiederhergestellt werden kann. Die zweite Stufe löscht ihn aus dem Papierkorb, danach wird der Beitrag dauerhaft entfernt.

## Überlegungen

Überlegen Sie, warum Sie den Beitrag löschen möchten:

- Wird er nicht mehr benötigt? In diesem Fall ist das Löschen
  wahrscheinlich der richtige Schritt.
- Ist es ein Beitrag, der in der Zukunft wiederverwendet werden könnte? Es kann sehr frustrierend sein zu wissen, dass Sie einen Beitrag hatten, der ein guter Ausgangspunkt für einen anderen gewesen wäre, aber Sie ihn gelöscht haben - überlegen Sie, ihn stattdessen zu archivieren.

## Beitrag in den Papierkorb verschieben

- Wählen Sie **Inhalte -> Beiträge** aus dem Administratormenü aus.
- Wählen Sie das Kontrollkästchen aus, um den Beitrag auszuwählen, den Sie löschen möchten. Ein Beitrag **muss** ausgewählt werden, um die Schaltfläche **Aktionen** in der Symbolleiste zu aktivieren.
- Wählen Sie die Schaltfläche **Aktionen** in der Symbolleiste.
- Wählen Sie **Papierkorb** im Dropdown-Menü.

![Beitrag zum Löschen ausgewählt](../../../en/images/articles/articles-delete/01-articles-selected-to-trash.png)

Es wird eine Bestätigungsmeldung angezeigt, und der Beitrag wird aus der aktuellen Liste der Beiträge verschwunden sein, da diese normalerweise keine gelöschten Elemente enthält.

## Filtern zum Wiederherstellen oder Löschen

An diesem Punkt im Prozess wurde der Beitrag noch nicht vollständig entfernt. Diese Funktion ist hilfreich, falls Sie den Beitrag versehentlich gelöscht haben.

Um die Liste der gelöschten Beiträge anzuzeigen:

- Wählen Sie die Schaltfläche **Filteroptionen**, um die Liste der Filter zu öffnen.
- Wählen Sie **Gelöscht** aus der Liste *-- Status auswählen --*.

![Anzeige der gelöschten Beiträge](../../../en/images/articles/articles-delete/02-articles-trash-list.png)

### Wiederherstellen

Wenn Sie Ihre Entscheidung geändert haben, können Sie das **Gelöscht**-Symbol in der Spalte *Status* auswählen. Der Beitrag wird in den Zustand *Veröffentlicht* zurückkehren und aus der Liste der gelöschten Beiträge verschwinden.

### Löschen

Wählen Sie das Kontrollkästchen in der linken Spalte der Beitragsdaten. Dadurch werden die Schaltflächen *Aktionen* und *Löschen* in der Toolbar aktiviert. Die Schaltfläche *Aktionen* ermöglicht es Ihnen, die gleiche Aktion auf alle ausgewählten Beiträge anzuwenden. Wenn Sie sich wirklich sicher sind:

1. Wählen Sie die Schaltfläche *Löschen* in der Toolbar. Ein Nachrichtenfeld erscheint:<br>
   <div class="alert alert-light">
   Sind Sie sicher, dass Sie löschen möchten? Durch die Bestätigung wird/werden der/die ausgewählte(n) Beitrag/Beiträge dauerhaft gelöscht!</div>
2. Wählen Sie **OK**, um zu bestätigen, und der Beitrag wird aus dem Papierkorb gelöscht. Der Beitrag wird aus der Datenbank gelöscht. Es ist endgültig weg!
3. Wählen Sie die Schaltfläche **Leeren** neben **Filteroptionen**, um zur ungefilterten **Beiträge**-Liste zurückzukehren.

## Tipps

- Denken Sie daran, das Löschen eines Beitrags ist nicht dasselbe wie das Archivieren eines Beitrags. Sobald er aus dem Papierkorb gelöscht wurde, ist er endgültig weg.
- Wenn Sie einen Beitrag versehentlich löschen, ihn aber noch nicht aus dem Papierkorb gelöscht haben, können Sie seinen Status ändern. Sie haben die Möglichkeit, ihn als *Archiviert*, *Veröffentlicht* oder *Unveröffentlicht* festzulegen.
- Joomla lässt Sie nicht mehr als einen Beitrag mit demselben Alias speichern. Wenn ein Beitrag gelöscht, aber im Papierkorb belassen wird, existiert er noch. Falls Sie versuchen, einen Beitrag zu speichern, und eine Fehlermeldung erhalten, die besagt, dass der Alias bereits existiert, könnte er im Papierkorb sein! Sie sollten ihn daher entweder aus dem Papierkorb leeren oder einen anderen Alias für Ihren neuen Beitrag eingeben.
- Joomla bewahrt frühere Versionen eines Beitrags auf, es sei denn, die Funktion "Versionen" ist deaktiviert. Wenn Sie einen Beitrag löschen, weil er irgendwie „kaputt“ ist, versuchen Sie, ihn auf eine frühere Version zurückzusetzen.

*Übersetzt von openai.com*

