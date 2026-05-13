<!--
{
  "source": "https://docs.joomla.org/J6.x:_Article_Publishing",
  "title": "Beitrag: Bearbeiten - Veröffentlichen  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Ein wichtiger Bestandteil eines Content-Management-Systems (CMS) ist seine Fähigkeit, Inhalte an ausgewählte Benutzer für ausgewählte Zeiträume bereitzustellen. Joomla! macht das mit Zugriffsebenen und Start- und Enddaten der Veröffentlichung.

Start- und Enddaten können sowohl für *hervorgehobene* als auch für *nicht hervorgehobene* Beiträge festgelegt werden. Zum Beispiel könnte ein neuer Beitrag für einen festgelegten Zeitraum, sagen wir 30 Tage, hervorgehoben werden, danach würde er zu einem gewöhnlichen nicht hervorgehobenen Beitrag werden. Er würde aus den hervorzuhebenden Beitrag-Layouts verschwinden, aber weiterhin in anderen Blog- oder Einzelbeitrag-Layouts angezeigt werden.

Meistens werden Beiträge am Tag ihrer Erstellung veröffentlicht und bleiben dies, bis sie nicht mehr veröffentlicht, archiviert oder gelöscht werden.

## Screenshot

![The article edit form publishing tab](../../../en/images/articles/article-publishing/01-articles-edit-publishing-tab.png)

Das *Metadaten*-Panel wird in einem separaten Beitrag erklärt. Dieser Beitrag behandelt das *Veröffentlichungs*-Panel.

## Veröffentlichungsbereich

Einige der Felder im Formular sind nur zur Information gedacht und können nicht direkt im Formular geändert werden. Sie werden mit grauem Hintergrund angezeigt. Andere Felder können bei Bedarf geändert werden.

### Start Veröffentlichung

Dieses Feld wird auf das aktuelle Datum und die aktuelle Uhrzeit gesetzt, wenn der Beitrag erstmals gespeichert wird. Wenn Sie möchten, dass der Beitrag bis zu einem zukünftigen Datum und einer Uhrzeit gesperrt wird, können Sie dessen Wert mit dem Kalender-Tool festlegen oder die Feldwerte direkt bearbeiten.

### Ende Veröffentlichung

Standardmäßig ist dieses Feld leer. Wenn der Beitrag nach einem bestimmten Datum und einer bestimmten Uhrzeit verschwinden soll, verwenden Sie das Kalender-Tool oder geben Sie ein zukünftiges Datum und eine Uhrzeit direkt in das Feld ein. Zu diesem Zeitpunkt wird der Beitrag von der Seite verschwinden. In der Beitragsliste wird er als *Veröffentlicht, aber abgelaufen* markiert.

### Start Hervorgehoben

Wenn der Beitrag als ein *Hervorgehobener Beitrag* markiert ist, kann dieses Feld so eingestellt werden, dass er an einem bestimmten Datum in einem *Hervorgehobene Beiträge*-Layout erscheint. Beachten Sie, dass das Datum nicht gespeichert wird, wenn der Beitrag nicht als *Hervorgehobener Beitrag* markiert ist.

### Ende Hervorgehoben

Wenn der Beitrag als Hervorgehobener Beitrag markiert ist, kann dieses Feld so eingestellt werden, dass er an einem bestimmten Datum aus einem *Hervorgehobene Beiträge*-Layout verschwindet. Der Beitrag bleibt weiterhin veröffentlicht und kann in anderen Layouts erscheinen. In der Beitragsliste wird er als *Hervorgehoben, aber abgelaufen* markiert.

### Erstellungsdatum

Dieses Datum wird festgelegt, wenn der Beitrag erstmals gespeichert wird. Möglicherweise möchten Sie es ändern, wenn Sie eine Reihe von Beiträgen in zufälliger Reihenfolge erstellt haben und diese in eine Erstellungsdaten-Reihenfolge sortieren möchten.

### Erstellt von

Die Benutzer-ID des Erstellers wird zum Zeitpunkt der Erstellung gespeichert und der Name dieses Benutzers erscheint in diesem Feld. Sie können den Ersteller ändern, indem Sie das Personensymbol auswählen, um ein *Benutzer auswählen*-Popup-Dialogfeld zu öffnen, in dem Sie einen anderen Benutzer suchen und auswählen können.

### Erstellt von Alias

Wenn Sie nicht möchten, dass der Benutzername des Erstellers im Informationsblock des Beitrags erscheint, können Sie hier ein Alias einfügen. Geben Sie Ihr Alias ein, speichern Sie den Beitrag und sehen Sie ihn sich mit der Vorschau-Schaltfläche in der Symbolleiste an.

## Planung der Veröffentlichung eines Beitrags

Standardmäßig werden Beiträge als **Veröffentlicht** gesetzt, sobald sie gespeichert werden. Das initiale Speichern des Beitrags erstellt das **Erstellungsdatum** und das **Veröffentlichungsbeginn**-Datum.

Die Planung eines Beitrags beinhaltet das manuelle Festlegen eines **Veröffentlichungsbeginn**-Datums und -Zeitpunkts, um die Veröffentlichung zu verzögern. Sie können auch Daten und Zeiten zum **Beendigen der Veröffentlichung** festlegen.

**Hinweis:** Damit die Planung funktioniert, muss der **Status** des Beitrags auf **Veröffentlicht** gesetzt sein.

Vor dem Veröffentlichungsbeginn-Datum werden Beiträge als **Ausstehend** betrachtet und nach dem Beendigen-Datum der Veröffentlichung als **Abgelaufen**. Obwohl der Beitrag selbst auf veröffentlicht gesetzt ist, nutzt Joomla die Einstellungen für den Beginn und das Ende der Veröffentlichung, um den Standardveröffentlichungsstatus zu überschreiben.

Die Datums- und Zeitwerte können in die Datumsfelder eingegeben oder mit dem Kalender-Tool ausgewählt werden, das durch Auswahl des Kalender-Symbols am Ende jedes Datumsfeldes geöffnet wird.

![Veröffentlichungsdaten](../../../en/images/articles/article-publishing/02-article-schedule-publishing.png)

Der Kalender bewegt sich zwischen Tagen, Monaten und Jahren mit den Vorwärts-, Rückwärts-, Hoch- und Runter-Pfeiltasten auf der Tastatur. Der **Heute**-Button setzt das aktuelle Datum. Der **Löschen**-Button löscht Datum und Uhrzeit.

* Wählen Sie das erforderliche Datum.
* Stellen Sie die Zeit mit den Dropdown-Feldern ein.
* Wählen Sie den **Schließen**-Button des Kalenders, um das ausgewählte Datum und die Zeit zu speichern.
* Wählen Sie **Speichern** oder **Speichern & Schließen** in der Werkzeugleiste, um die Änderungen zu speichern.

## Listenansicht-Symbole

In der Beitragsliste ist das *Hervorgehoben*-Symbol normalerweise entweder ein grauer Kreis oder ein gelber Stern. Ähnlich ist das *Status*-Symbol normalerweise ein grüner Haken oder ein graues Kreuz. Jedes hat ein Tooltip, und die übliche Aktion besteht darin, den Zustand umzuschalten.

- Veröffentlicht und Aktuell: <span class="icon-publish" aria-hidden="true"></span>
- Unveröffentlicht: <span class="icon-unpublish" aria-hidden="true"></span>
- Hervorgehoben: <span class="icon-featured" aria-hidden="true"></span>
- Nicht hervorgehoben: <span class="icon-unfeatured" aria-hidden="true"></span>

Die Symbole für Beiträge mit geplanten Start- und Enddaten sind unterschiedlich.

- Veröffentlicht, aber ausstehend: <span class="icon-pending" aria-hidden="true"></span>
- Veröffentlicht, aber abgelaufen: <span class="icon-expired" aria-hidden="true"></span>
- Hervorgehoben, aber ausstehend: <span class="icon-pending" aria-hidden="true"></span>
- Hervorgehoben, aber abgelaufen: <span class="icon-expired" aria-hidden="true"></span>

In jedem Fall zeigt ein Tooltip zusätzliche Informationen über die geplanten Daten.

## Tipps

- Du kannst das Veröffentlichen von Beiträgen auch über das Frontend planen.
- Es ist auch möglich, die Planung über den Menüpunkt für den Beitrag vorzunehmen.
- Die Planung ist auch für Kontakte und Module verfügbar.

*Übersetzt von openai.com*

