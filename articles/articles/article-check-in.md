<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Check-out_and_Check-in",
  "title": "Beitrag: Check-in ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Viele Joomla-Websites haben mehrere Benutzer, die die Berechtigung haben, Beiträge zu bearbeiten. Um zu verhindern, dass zwei Benutzer versuchen, denselben Beitrag gleichzeitig zu bearbeiten, hat jeder Beitrag ein **checked_out**-Datenbankfeld, das anzeigt, ob er gerade in Bearbeitung ist oder nicht. Dieses Feld wird gesetzt, wenn ein Beitrag zum Bearbeiten geöffnet wird, und wieder zurückgesetzt, wenn das Bearbeitungsformular entweder mit den Schaltflächen *Speichern & Schließen* oder *Schließen* geschlossen wird.

Manchmal wird ein Bearbeitungsformular für einen Beitrag nicht ordnungsgemäß geschlossen, beispielsweise durch die Verwendung der Zurück-Taste des Browsers oder wenn die Benutzersitzung abläuft. In diesem Fall bleibt das checked_out Feld gesetzt. Dies wird in der Beitragsliste mit einem kleinen Vorhängeschloss-Symbol angezeigt. Das Vorhängeschloss-Symbol ist auch dort sichtbar, wo sich ein Bearbeitungslink befinden sollte, wenn man im Frontend der Seite eingeloggt ist.

Um den normalen Betrieb wiederherzustellen, müssen ausgecheckte Elemente eingecheckt werden.

## Beitrag-Check-in

Es gibt mehrere Methoden, um einen Beitrag einzuchecken.

- Wenn Sie die letzte Person waren, die den Beitrag bearbeitet hat, können Sie den Beitrag im Backend oder Frontend bearbeiten, ohne ihn einchecken zu müssen.
- Wenden Sie sich an die letzte Person, die den Beitrag bearbeitet hat, um zu sehen, ob sie damit fertig ist. Sie können den Mauszeiger über das Vorhängeschloss bewegen, und das Tooltip-Popup zeigt den Namen des Benutzers an, der den Beitrag ausgecheckt hat.
- Wenn Sie ein Super-Benutzer oder Administrator sind, können Sie das Vorhängeschloss-Symbol auswählen, um diesen Beitrag einzuchecken.
- Sie können auch mehrere Beiträge auswählen und den *Einchecken*-Punkt aus dem *Aktionen*-Button in der Toolbar verwenden.
- Wenn Sie den Beitrag nicht selbst einchecken können, bitten Sie einen Super-Benutzer oder Administrator, dies zu tun.

## Globaler Check-in

Wenn Sie ein Superbenutzer oder Administrator sind, können Sie das Globaler Check-in-Tool verwenden, um Elemente zur Rückgabe auszuwählen.

Dieses Tool sollte sehr vorsichtig verwendet werden, insbesondere in Mehrbenutzerumgebungen. Es checkt alle zuvor ausgecheckten Elemente ein, unabhängig davon, ob sie von Ihnen oder jemand anderem ausgecheckt wurden. Mögliche unerwünschte Nebeneffekte könnten sein, dass mehrere Editoren am selben Dokument arbeiten. In diesem Fall wird die Version desjenigen, der zuletzt auf die Schaltfläche Speichern klickt, als endgültige Kopie gespeichert.

Sie sollten auch darauf achten, dass viele andere Erweiterungen **Checked_out**-Felder haben. Beispielsweise können Module und Kategorien zur Bearbeitung ausgecheckt und versehentlich in diesem Zustand belassen werden.

Aus dem Administrator-Menü:

- Wählen Sie **Home Dashboard → Globaler Check-in** oder
  **System → Wartungspanel → Globaler Check-in**.
- Die Liste zeigt die Anzahl der ausgecheckten Elemente.

![Globale Check-in-Seite](../../../en/images/articles/article-check-in/01-global-checkin.png)

- Wählen Sie in der Liste der Datenbanktabellen das Kontrollkästchen für den Typ des auszucheckenden Elements aus.
- Wählen Sie *Check-in* aus der Toolbar.

Alle in dieser Tabelle ausgecheckten Elemente werden eingecheckt.  

## Tabellen mit checked_out-Feld

Sie können herausfinden, welche Tabellen eine checked_out-Spalte haben, indem Sie diese Abfrage in phpMyAdmin verwenden:

```sql
SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('checked_out') AND TABLE_SCHEMA='j423sd';
```

Und das Ergebnis sollte so aussehen:

```sql
TABLE_NAME
bi2hb_banner_clients
bi2hb_banners
bi2hb_categories
bi2hb_contact_details
bi2hb_content
bi2hb_extensions
bi2hb_fields
bi2hb_fields_groups
bi2hb_finder_filters
bi2hb_menu
bi2hb_modules
bi2hb_newsfeeds
bi2hb_scheduler_tasks
bi2hb_tags
bi2hb_update_sites
bi2hb_user_notes
bi2hb_workflow_stages
bi2hb_workflow_transitions
bi2hb_workflows
```

*Übersetzt von openai.com*

