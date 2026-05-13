<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Preview",
  "title": "Beitrag: Vorschau ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Es kann nützlich sein, einen Beitrag vor der Veröffentlichung zu sehen. Dafür gibt es eine *Vorschau*-Schaltfläche in der Werkzeugleiste des Backends im Formular *Beitrag: Bearbeiten*. Diese Funktion verwendet jedoch den gespeicherten Beitrag und nicht den Inhalt des Editor-Formulars. Die Vorschaufunktion ist im Frontend-Editor-Formular nicht verfügbar. 

Möglicherweise möchten Sie einen Beitrag nicht sichtbar machen, bevor er fertig ist. Dafür werden unterschiedliche Strategien für Frontend- und Backend-Editoren benötigt.  

## Frontend-Vorschau

Die einzige Möglichkeit, einen Beitrag von der Frontend halb-privat zu halten, besteht darin, seinen Zugriff auf *Registriert* zu setzen, sodass nur angemeldete Benutzer ihn sehen können.

- Melden Sie sich beim Frontend der Website an.
- Wählen Sie den *Bearbeiten*-Link für einen Beitrag, der aktualisiert werden soll. Oder...
- Wählen Sie die Schaltfläche *Neuer Beitrag* unter den Blog-Layouts.
  - Setzen Sie das Zugriffslevel des Beitrags auf *Registriert*, bis er zur Veröffentlichung bereit ist.
  - Sie könnten eine *Warnung* hinzufügen, die darauf hinweist, dass der Beitrag in Bearbeitung ist: `<div class="alert alert-warning">In Bearbeitung</div>`.
- *Speichern & Schließen*, um den Beitrag zu sehen.

## Backend-Vorschau

Nach dem Einloggen in die Administratoroberfläche:

- Wählen Sie einen Beitrag zur Bearbeitung aus oder erstellen und speichern Sie einen neuen.
- Um einen neuen Beitrag vorerst privat zu halten, setzen Sie den Status auf *Unveröffentlicht* oder lassen Sie ihn *Veröffentlicht* und passen Sie das *Start-Publishing*-Datum an.
- Nehmen Sie Änderungen vor und *speichern* Sie den Beitrag.
- Wählen Sie die *Vorschau*-Schaltfläche in der Werkzeugleiste. Ein Popup-Vorschaufenster sollte erscheinen.
- Wenn Sie die Nachricht *Die angeforderte Seite kann nicht gefunden werden* erhalten, loggen Sie sich ins Frontend ein und versuchen Sie es erneut.
- Um das Vorschaufenster zu schließen, wählen Sie die *X*-Schaltfläche in der oberen rechten Ecke.

![Das Vorschaufenster](../../../en/images/articles/article-preview/01-article-edit-preview.png)

*Übersetzt von openai.com*

