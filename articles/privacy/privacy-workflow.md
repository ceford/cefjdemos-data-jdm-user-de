<!--
{
  "source": "https://docs.joomla.org/J4.x:Privacy_Workflow",
  "title": "Datenschutz-Workflow  ",
  "description": "", 
  "author": ""
}
-->

## Anforderung erstellen

Die Bearbeitung von Anfragen zu persönlichen Informationen ist der Hauptzweck der
Datenschutzkomponente. Benutzer können um eine Zusammenfassung ihrer persönlichen Daten bitten oder
verlangen, dass alle ihre persönlichen Daten entfernt werden. Eine Anfrage kann entweder von einem
authentifizierten Benutzer über das Anfrageformular oder von einem Superbenutzer erstellt werden.

In diesem Kontext bezeichnet "Benutzer" jede Einzelperson oder Organisation, die eine Anfrage gestellt hat,
unabhängig davon, ob ein registriertes Benutzerkonto existiert. Anfragen können zum Beispiel vom
Seitenadministrator von Einzelpersonen oder Organisationen gestellt werden, die der Seite als Kontakte
hinzugefügt wurden.

Persönliche Daten basieren auf E-Mail-Adressen und die automatisierte Verarbeitung ist auf Erweiterungen
beschränkt, die Datenschutzfunktionen berichten.

*WICHTIG* Um Informationsanfragen zu erstellen und zu bearbeiten, MUSS Ihre Website in der Lage sein, E-Mails
zu versenden, da der Eigentümer der Informationen die Anfrage bestätigen muss.

### Authentifizierte Benutzeranfrage

Registrierte Benutzer können eine Informationsanfrage über einen *Datenschutz-Informationsantrag*
Menülink einreichen, der nur nach dem Login verfügbar ist. Ein guter Ort für einen solchen Link ist im
gleichen Menü, in dem sich auch ein Link zur **Datenschutzerklärung** der Seite befindet. Ein unteres Menü
im Seitenfuß ist oft ein favorisierter Ort. Bei der Einreichung einer Informationsanfrage muss der Benutzer
folgendes angeben:

- Den Anforderungstyp: Exportieren oder Entfernen, ausgewählt aus der Dropdown-Liste.

![Datenschutz-Workflow Benutzeranfrage](../../../en/images/privacy/privacy-workflow/01-privacy-workflow-user-request.png)

Bei der Einreichung wird eine Nachricht angezeigt, die entweder anzeigt, dass die Anfrage akzeptiert wurde
und eine Bestätigungs-E-Mail auf dem Weg ist:

![Datenschutz-Workflow Benutzeranfrage akzeptiert](../../../en/images/privacy/privacy-workflow/02-privacy-workflow-user-request-accepted.png)

oder dass *Ihre Informationsanfrage konnte nicht erstellt werden. Es gibt bereits eine aktive
Informationsanfrage für diese E-Mail-Adresse und diesen Anforderungstyp. Bitte wenden Sie sich an den
Seiteninhaber, um Updates zu dieser Anfrage zu erhalten.*

### Superbenutzer-Erstellung

Über die Seite **Datenschutz: Anfragen** kann jeder Superbenutzer eine neue Informationsanfrage
erstellen. Dies ist die einzige Möglichkeit, Informationsanfragen für Benutzer zu erstellen, die KEIN Konto
auf der Website haben. Um eine Anfrage zu erstellen:

- Wählen Sie **Benutzer → Datenschutz → Anfragen** aus dem Administrator
  Menü.
- Klicken Sie auf die Schaltfläche **Neu** in der Symbolleiste.
- Geben Sie im Feld **E-Mail** die E-Mail-Adresse des Benutzers ein.
- Wählen Sie im Feld **Anforderungstyp** Exportieren oder Entfernen aus der
  Dropdown-Liste aus.
- **Speichern & Schließen**.

Sobald erstellt, kann die Anfrage nicht bearbeitet werden. Sie kann nur ungültig gemacht oder
verarbeitet werden.

## Anforderung Bestätigen

Sobald eine Anfrage erstellt wurde, unabhängig davon, wie sie erstellt wird, erhält der Benutzer eine E-Mail mit einem Link zu einem Bestätigungsformular.

![privacy workflow user request confirm](../../../en/images/privacy/privacy-workflow/03-privacy-workflow-user-request-confirm.png)

Der Benutzer muss das in der E-Mail enthaltene Token eingeben und das Formular absenden. Das Token ist 24 Stunden gültig. Wenn eine Anfrage in diesem Zeitraum nicht bestätigt wird, wird die Anfrage in der Liste der Datenschutzanfragen als **Ungültig** markiert und eine neue Anfrage muss eingereicht werden.

Sobald der Benutzer die Anfrage bestätigt, wird eine E-Mail an Super-User gesendet, um anzuzeigen, dass eine Aktion erforderlich ist.

- Wählen Sie aus dem Administratormenü **Benutzer → Datenschutz → Anfragen**.
- Anfragen, die eine Aktion erfordern, werden als **Bestätigt** markiert.

![privacy workflow information requests list](../../../en/images/privacy/privacy-workflow/04-privacy-workflow-information-requests-list.png)

## Bearbeitung einer Exportanforderung

Sobald eine Exportanforderung bestätigt wurde, stehen Superbenutzern zwei Aktionen zur Verfügung.

- Daten exportieren: Dies sammelt alle Daten zum Thema der Informationsanforderung und erstellt eine XML-Datei, die auf Ihren Computer heruntergeladen wird. Dies ist nützlich, um es Website-Betreibern zu ermöglichen, den Datenexport zu überprüfen, bevor er an den Benutzer gesendet wird.
- Datenexport per E-Mail: Dies sammelt alle Daten zum Thema der Informationsanforderung, erstellt eine XML-Datei (die gleiche wie durch die Aktion Daten exportieren generiert) und sendet eine E-Mail an den Benutzer mit der angehängten exportierten Datendatei.

**Wichtig:** Die Exportaktion kann nur Daten von Erweiterungen sammeln, die über Unterstützung für den Datenschutz verfügen. Daher sollte der Superbenutzer, der auf die Anfrage reagiert, den Export überprüfen und, falls notwendig, Daten von Erweiterungen einbeziehen, die persönliche Daten speichern, aber keine Unterstützung für den Datenschutz bieten.

## Bearbeitung eines Löschantrags

Sobald ein Löschantrag bestätigt wurde, steht Supernutzern nur eine Aktion zur Verfügung.

- Daten löschen: Dieser Prozess wird die relevanten Daten der betroffenen Person anonymisieren und/oder entfernen. Bei Anträgen, bei denen der Dateninhaber auch ein registriertes Benutzerkonto hat, wird dieser Prozess den Namen, Benutzernamen und die E-Mail-Adresse des Kontos anonymisieren sowie das Konto sperren, sodass es nicht mehr eingeloggt werden kann, und den Benutzer von der Seite abmelden, falls er zum Zeitpunkt der Bearbeitung des Antrags eingeloggt ist.

**Wichtig:** Die Löschaktion kann nur Daten von Erweiterungen erfassen, die Datenschutzunterstützung bieten. Daher sollte der Supernutzer, der den Antrag bearbeitet, den Export prüfen und gegebenenfalls manuell Daten anonymisieren oder entfernen, die in Erweiterungen gespeichert sind, die persönliche Daten enthalten, aber keine Datenschutzunterstützung haben.

Bei Auswahl der Schaltfläche **Daten löschen** erscheint eine Bestätigungsnachricht **Daten entfernt**, aber die Liste Privatsphäre: Informationsanfragen bleibt ansonsten unverändert. Die Benutzerdaten werden entfernt oder anonymisiert, aber nicht die Daten in den Tabellen \#\_\_action_logs, \#\_\_messages und \#\_\_privacy_requests (siehe unten).

## Abschluss einer Anfrage

Nachdem die Anfrage bearbeitet wurde, sollte sie als abgeschlossen markiert werden. Dies zeigt an, dass die Anfrage erfüllt wurde und keine weiteren Maßnahmen erforderlich sind.

- Wählen Sie in der Liste **Datenschutz: Informationsanfragen** die E-Mail-Adresse der Anfrage aus, die bearbeitet wird.
- Im Formular **Datenschutz: Informationsanfrage prüfen**:
  - Überprüfen Sie die Daten.
  - Wählen Sie den entsprechenden **Export**, **E-Mail** oder **Löschen** Button in der Toolbar, wenn dies nicht bereits aus der Listenansicht geschehen ist.
- Wählen Sie den **Abschließen** Button in der Toolbar (oder den **Ungültig erklären** Button, falls dies als ungültige Anfrage beurteilt wird).

![Datenschutz-Workflow Informationsanfrage überprüfen](../../../en/images/privacy/privacy-workflow/05-privacy-workflow-review-information-request.png)

## Abschließend

Um Daten aus dem Benutzeraktionsprotokoll zu entfernen:

- Wählen Sie **Benutzer → Benutzeraktionsprotokoll** im Administratormenü.
- Suchen Sie nach dem Benutzernamen oder der E-Mail-Adresse des gelöschten Benutzers.
- Aktivieren Sie das Kontrollkästchen **Alle Elemente auswählen**.
- Wählen Sie die Schaltfläche **Löschen** in der Symbolleiste.

Um Daten aus privaten Nachrichten und Datenschutzanfragen zu entfernen:

- Es gibt keine einfache Möglichkeit, diese Arten von Daten gesammelt aus Joomla zu entfernen. Der schnellste Weg ist, nach dem Benutzernamen (E-Mail-Adresse) in der Datenbank mit phpMyAdmin zu suchen und die Datensätze dort zu löschen. Hier ist ein Beispiel-Screenshot:

![Datenschutz-Workflow mit phpMyAdmin löschen](../../../en/images/privacy/privacy-workflow/06-privacy-workflow-delete-with-phpmyadmin.png)

## Zusätzliche Ressourcen

- [Entwicklerhandbuch für das Datenschutz-Toolset](https://docs.joomla.org/Special:MyLanguage/J3.x:Integrate_Extensions_with_the_Privacy_Component)

*Übersetzt von openai.com*

