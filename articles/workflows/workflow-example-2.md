<!--
{
  "source": "https://docs.joomla.org/J6.x:Workflow_Scenarios_Example_2",
  "title": "Workflow-Beispiel 2 ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Dieses Beispiel betrifft zwei Benutzer, Alice und Bob, die jeweils die Vorsitzende und der Sekretär eines Ausschusses sind. Der Arbeitsablauf umfasst die Vorbereitung und Genehmigung von Tagesordnungen und Protokollen von Ausschusssitzungen. Charlie ist ein Ausschussmitglied, das Zugang zu den Ausschusspapieren haben wird, wenn diese veröffentlicht werden. Der Arbeitsablauf verwendet ausschließlich das Frontend.

## Benutzergruppen

Erstellen Sie zuerst neue Benutzergruppen, alle Kinder von *Registriert*.

- **Komitee** Ein Kind von *Registriert*
- **Vorsitzender** Ein Kind von *Komitee*
- **Sekretär** Ein Kind von *Komitee*

![Benutzerdefinierte Benutzergruppen](../../../en/images/workflows/workflow-example-2/01-example-2-user-groups.png)

## Benutzerzugriffsebene

- Erstellen Sie eine neue Ebene, **Komitee**, und fügen Sie *Komitee* den Benutzergruppen mit Zugriff auf Beiträge hinzu.
- Fügen Sie in der *Speziellen* Zugriffsebene *Komitee* den Benutzergruppen mit Zugriff auf Beiträge hinzu.

![Zugriffsebenen ansehen](../../../en/images/workflows/workflow-example-2/02-example-2-viewing-access-levels.png)

## Benutzer erstellen

- **Alice** in der *Chair*-Gruppe.
- **Bob** in der *Sekretär*-Gruppe.
- **Charlie** in der *Ausschuss*-Gruppe.

## Erstellen Sie den Workflow

- **Name** *Ausschuss-Workflow*
- **Beschreibung** *Workflow zur Vorbereitung von Ausschusspapieren.*
- **Berechtigungen**
  - **Ausschuss** Alle auf *Geerbt* gesetzt Nicht erlaubt (geerbt).
  - **Vorsitzender** Alle auf *Erlaubt* gesetzt, außer *Löschen*. Vielleicht...
  - **Sekretär** Alle auf *Erlaubt* gesetzt, außer *Löschen* und *Status bearbeiten*.

![Liste der Workflows](../../../en/images/workflows/workflow-example-2/03-example-2-workflows-list.png)

### Erstellen Sie die Workflow-Phasen

- **Entwurf** 
  - **Hinweis** *Papiere in Vorbereitung.* 
  - **Berechtigungen** Alle auf *Geerbt* belassen.
- **Überprüfung**
  - **Hinweis** *Papiere warten auf Genehmigung.* 
  - **Berechtigungen** Alle auf *Geerbt* belassen.
- **Veröffentlichen**
  - **Hinweis** *Papiere veröffentlicht.* 
  - **Berechtigungen** Alle auf *Geerbt* belassen.

![Workflow-Phasen](../../../en/images/workflows/workflow-example-2/04-example-2-stages-committee-workflow.png)

### Erstellen Sie die Workflow-Übergänge

#### Entwurf zu Überprüfung

Dies ist der normale Vorwärtsübergang in der Abfolge der Phasen.

- **Name** *Entwurf/Überprüfung*
- **Übergangs-Tab**
  - **Aktuelle Phase** *Entwurf*
  - **Zielphase** *Überprüfung*
  - **Hinweis** *Übergang zur nächsten Phase.*
- **Übergangsaktionen-Tab**
  - **Präsentationszustand** *- Keine Auswahl -*
  - **Veröffentlichungszustand** *- Keine Auswahl -*
- **Benachrichtigungs-Tab**
  - **Benachrichtigung senden** *Ja* Empfänger müssen *System-E-Mails empfangen* aktiviert haben, um E-Mail-Benachrichtigungen zu erhalten.
  - **Zusätzlicher Nachrichtentext** Gibt es etwas Spezifisches zu diesem Workflow?
  - **Benutzergruppen** *Vorsitzender*
  - **Benutzer** Eine Alternative zur Verwendung von Benutzergruppen.
- **Berechtigungen-Tab** Alle auf **Geerbt** gesetzt.

#### Überprüfung zu Entwurf

Dies ist die Rückkehr zu einer vorherigen Phase in der Abfolge, die aufgerufen wird, wenn der Vorsitzende mehr Arbeit vom Sekretär benötigt. Die Formularfelder sind ähnlich wie bei den Entwurf/Überprüfungs-Feldern, außer dass die Hinweise und die *Aktuelle Phase* und *Zielphase* umgekehrt sind.

#### Überprüfung zu Veröffentlichen

Dies ist der Übergang, der den Status eines Artikels von *Unveröffentlicht* zu *Veröffentlicht* ändert. Nur der Vorsitzende hat die Berechtigung, diese Änderung vorzunehmen.

- **Name** *Überprüfung/Veröffentlichen*
- **Übergangs-Tab**
  - **Aktuelle Phase** *Überprüfung*
  - **Zielphase** *Veröffentlichen*
  - **Hinweis** *Der letzte Übergang zur Veröffentlichung.*
- **Übergangsaktionen-Tab**
  - **Präsentationszustand** *- Keine Auswahl -*
  - **Veröffentlichungszustand** *Veröffentlicht*
- **Benachrichtigungs-Tab**
  - **Benachrichtigung senden** *Ja* Empfänger müssen *System-E-Mails empfangen* aktiviert haben, um E-Mail-Benachrichtigungen zu erhalten. 
  - **Zusätzlicher Nachrichtentext** *Ein Ausschusspapier wurde veröffentlicht und ist jetzt zur Ansicht verfügbar.*
  - **Benutzergruppen** *Ausschuss*
  - **Benutzer** Eine Alternative zur Verwendung von Benutzergruppen.
- **Berechtigungen-Tab**
  - **Sekretär** Setzen Sie *Übergang ausführen* auf *Verweigert*.

#### Veröffentlichen zu Überprüfung

Dies ist ein Wechsel von Veröffentlichen zurück zu Überprüfung. Ist das wirklich notwendig? Ein veröffentlichtes Dokument kann weiterhin vom Sekretär oder Vorsitzenden bearbeitet werden. Vielleicht wurde ein Ausschusspapier mit sensiblen Daten irrtümlich veröffentlicht.

Falls erforderlich, erstellen Sie einen Übergang ähnlich dem Übergang *Überprüfung zu Veröffentlichen*, jedoch mit den umgekehrten Phasen, den *Übergangsaktionen / Veröffentlichungszustand* auf *Unveröffentlicht* gesetzt und eine generische *Zusätzlicher Nachrichtentext* Nachricht.

#### Archivieren

Dies ist der Übergang, der ausgeführt wird, wenn ein Ausschusspapier nicht mehr benötigt wird. Im Workflow bleibt es in der Phase Veröffentlichen, aber der Dokumentenzustand wird von Veröffentlicht zu Archiviert geändert.

- **Name** *Archivieren*
- **Übergangs-Tab**
  - **Aktuelle Phase** *Veröffentlichen*
  - **Zielphase** *Veröffentlichen*
  - **Hinweis** *Dokumentenzustand von Veröffentlicht zu Archiviert ändern.*
- **Übergangsaktionen-Tab**
  - **Präsentationszustand** *- Keine Auswahl -*
  - **Veröffentlichungszustand** *Archiviert*
- **Benachrichtigungs-Tab**
  - **Benachrichtigung senden** *Nein* Dies ist kein Übergang, der eine Aktion erfordert. 
- **Berechtigungen-Tab**
  - **Sekretär** Setzen Sie *Übergang ausführen* auf *Verweigert*.

![Workflow-Übergänge](../../../en/images/workflows/workflow-example-2/05-example-2-transitions-committee-workflow.png)

## Eine neue Kategorie erstellen

<div class="alert alert-warning">Dieser Schritt ist wirklich wichtig! Neue Komitee-Beiträge müssen mit dieser Kategorie erstellt werden, ansonsten nehmen sie den Standard-Workflow an, der eine Änderung durch einen Super-User erfordert.</div>

- **Titel** *Komitee*
- **Workflow** Wählen Sie *Komitee-Workflow* aus der Liste der Workflows aus.
- **Berechtigungen**
  - Autor, Redakteur und Verleger: Alle auf *Nicht erlaubt* setzen oder bei 
    *Nicht erlaubt (geerbt)* belassen.
  - Komitee: Alle bei *Geerbt* belassen.
  - Vorsitzender: Alle außer *Löschen* auf *Erlaubt* setzen.
  - Sekretär: Alle außer *Löschen* und *Zustand bearbeiten* auf *Erlaubt* setzen.

## Ein Menüpunkt erstellen

- **Titel** *Ausschusspapiere*
- **Menüpunkt-Typ** Kategorieliste
- **Kategorie auswählen** *Ausschuss*
- **Zugriff** *Ausschuss*

![Ausschusspapiere Menüpunkt](../../../en/images/workflows/workflow-example-2/06-example-2-menu-item.png)

## Überprüfen Sie die Seite

Melden Sie sich der Reihe nach als Alice, Bob, Charlie und ein Super User an, um zu sehen, was sie sehen können:

Alice, Bob und Charlie können das Menüelement sehen, aber sonst niemand, nicht einmal ein Super User. Nach der Auswahl des Menüelements können Alice und Bob eine Tabelle mit Ausschusspapieren sehen, einschließlich derjenigen, die nicht veröffentlicht wurden. Charlie kann nur eine Tabelle der veröffentlichten Ausschusspapiere sehen oder eine erklärende Nachricht, wenn keine veröffentlicht wurden.

Alice und Bob können auch einen Bearbeitungslink für jeden Beitrag und einen **Neuen Beitrag**-Button sehen. Dies wird normalerweise von Bob verwendet, um ein Ausschusspapier zu erstellen, aber Alice kann das auch tun.

![Bobs Ansicht der Kategorieliste der Ausschusspapiere](../../../en/images/workflows/workflow-example-2/07-example-2-committee-papers.png)

### Um ein Ausschusspapier zu erstellen und zu veröffentlichen

- Melden Sie sich als Sekretärin an und wählen Sie den **Neuen Beitrag**-Button auf der 
  *Ausschusspapiere*-Seite.
- Geben Sie den Text ein und *speichern* Sie. Dies kann über mehrere Bearbeitungssitzungen hinweg geschehen, vielleicht über mehrere Tage oder Wochen. Der Beitrag bleibt unveröffentlicht und im Entwurfsstadium bis...
- Wählen Sie die Registerkarte *Veröffentlichung* im Bearbeitungsformular und setzen Sie die *Workflow-Stufe* auf 
  Übergang ausführen **Entwurf/Überprüfung**. 
- Wählen Sie **Speichern & Schließen**, um den Übergang auszuführen.
- Die Arbeit der Sekretärin ist vorerst abgeschlossen, und eine Nachricht wurde an den Ausschussvorsitzenden gesendet.
- Der Vorsitzende meldet sich an, überprüft das Papier, das zur Überprüfung bereit ist, und verwendet den 
  **Überprüfung/Veröffentlichung**-Übergang, um das Papier *veröffentlicht* zu machen. Die Arbeit des
  Vorsitzenden ist vorerst abgeschlossen, und eine Nachricht wird an die Ausschussmitglieder gesendet.
- Die Ausschussmitglieder können sich anmelden und auf das veröffentlichte Papier zugreifen.

*Übersetzt von openai.com*

