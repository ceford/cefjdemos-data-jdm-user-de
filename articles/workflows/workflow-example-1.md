<!--
{
  "source": "https://docs.joomla.org/J6.x:Workflow_Scenarios_Example_1",
  "title": "Arbeitsablauf Beispiel 1",
  "description": "", 
  "author": ""
}
-->

## Einführung

Ein Workflow besteht aus *Phasen* und *Übergängen* zwischen diesen Phasen. Für jeden Beitrag wird die aktuelle Phase in der Datenbank gespeichert und verwendet, um den Workflow und die von diesem Workflow genutzten Übergänge zu identifizieren.

Eine einzelne Website kann viele Workflows haben. Hier wird ein *Newsletter-Workflow* als Beispiel verwendet, um zu erklären, wie drei Personen mit unterschiedlichen Rollen an der Erstellung eines Newsletter-Beitrags beteiligt sein können. Das Beispiel nutzt die Joomla-Standardbenutzergruppen Autor, Redakteur und Verleger. Das hat ein Problem: Ein Autor kann nur veröffentlichte Beiträge sehen und kann unveröffentlichte Beiträge nicht erneut bearbeiten. Eine Methode, um dieses Problem zu vermeiden, wird in [Beispiel 2](jdocmanual?article=user/workflows/workflow-example-2) behandelt.

![Workflows-Liste](../../../en/images/workflows/workflow-example-1/01-example-1-workflows-list.png)

Beachten Sie, dass der *Basis-Workflow* als *Standard* festgelegt ist. Das kann später in diesem Beitrag problematische Folgen haben!

## Die Benutzer

- *Arthur* ist ein Benutzer, der der Joomla **Autorengruppe** zugewiesen ist. Er kann neue
  Beiträge erstellen und seine eigenen Beiträge bearbeiten, aber er kann keine Beiträge bearbeiten, die von anderen Nutzern geschrieben wurden, oder den Status von Beiträgen ändern. Daher kann er seine eigenen Beiträge nicht veröffentlichen. Seine Aufgabe ist es, neue Beiträge zu entwerfen.
- *Eddie* ist ein Benutzer, der der Joomla **Editorgruppe** zugewiesen ist. Er kann
  Beiträge bearbeiten, die von jedem anderen Benutzer erstellt wurden, einschließlich Arthur und sich selbst. Auch er kann den Status eines Beitrags nicht ändern. Seine Aufgabe besteht darin, die von Eddie eingereichten Beiträge zu überprüfen, die Genauigkeit, Rechtschreibung und Grammatik, die Qualität der Bilder und so weiter zu prüfen.
- *Pru* ist eine Benutzerin, die der Joomla **Publisher-Gruppe** zugewiesen ist. Sie kann alles, was Eddie und Arthur können. Darüber hinaus kann sie den Status eines Beitrags ändern. Es ist ihre Aufgabe zu entscheiden, ob ein Beitrag für die Veröffentlichung geeignet ist und ihn zu veröffentlichen.

## Die Phasen

Dieser Workflow hat vier Phasen:

![Liste der Workflows](../../../en/images/workflows/workflow-example-1/02-example-1-workflow-stages.png)

- **Entwurf** ist die Phase, die von Arthur für einen neuen Beitrag erstellt wird.
- **Überprüfung** ist die Phase, in der Eddie den Inhalt korrekturliest.
- **Genehmigung** ist die Phase, in der Pru entscheidet, ob der Beitrag gut genug ist, um veröffentlicht zu werden.
- **Veröffentlichen** ist die Phase, in der der Beitrag genehmigt und veröffentlicht wird.

Die Formulare zur Dateneingabe für die Phasen erfordern wenig Erklärung, nur einen Namen und eine Beschreibung.

## Die Übergänge

Zwei Übergänge sind zwischen jeder Phase erforderlich: einer, um die Phase zurückzusetzen, wenn in der vorherigen Phase noch mehr Arbeit erforderlich ist; und ein zweiter, um in die nächste Phase zu wechseln. Zusätzliche Übergänge sind erforderlich, um das Ende eines Beitrags zu behandeln:

![Liste der Workflows](../../../en/images/workflows/workflow-example-1/03-example-1-workflow-transitions.png)

- **Entwurf/Überprüfung** um die Phase von Entwurf zu Überprüfung zu wechseln.
- **Überprüfung/Entwurf** um die Phase von Überprüfung zu Entwurf zurückzusetzen.
- **Überprüfung/Genehmigung** um die Phase von Genehmigung zu Überprüfung zu wechseln.
- **Genehmigung/Überprüfung** um die Phase von Genehmigung zu Überprüfung zurückzusetzen.
- **Überprüfung/Veröffentlichen** um die Phase zu Veröffentlicht zu wechseln und den Status des Beitrags auf *Veröffentlicht* zu ändern.
- **Veröffentlichen** um den Status des Beitrags auf *Veröffentlicht* zu setzen, wenn der Übergang von einem Autor oder Redakteur ausgeführt wird.
- **Nicht veröffentlichen** um den Status des Beitrags auf *Nicht veröffentlicht* zu ändern.
- **Archivieren** um den Status des Beitrags auf *Archiviert* zu ändern.
- **Papierkorb** um den Status des Beitrags auf *Gelöscht* zu ändern.

Die letzten drei Übergänge ermöglichen es Pru, den Status eines Beitrags zu ändern, wenn er nicht mehr benötigt wird.

### Übergang bearbeiten

Das Dateneingabeformular hat vier Registerkarten, beginnend mit der Registerkarte *Übergang*:

![Liste der Workflows](../../../en/images/workflows/workflow-example-1/04-example-1-edit-transition.png)

- **Name** Es ist am besten, die aktuelle und die Zielphase im Namen zu verwenden.
- **Aktuelle Phase** Die Phase vor dem Übergang.
- **Zielphase** Die Phase nach dem Übergang.
- **Anmerkung** Jegliche erläuternden Anmerkungen, um den Übergang zu erklären.

#### Die Registerkarte *Übergangsaktionen*:

![Liste der Workflows](../../../en/images/workflows/workflow-example-1/05-example-1-edit-transition-actions.png)

- **Hervorgehobenen Status** Definieren Sie den hervorgehobenen Status, den ein Element nach Ausführung dieses Übergangs haben soll. Lassen Sie dies auf *-Nicht ausgewählt-* wenn der Benutzer, der diesen Übergang wahrscheinlich ausführt, keine Berechtigung hat, Beiträge hervorzuheben.
- **Veröffentlichungsstatus** Definieren Sie den veröffentlichten Status, den ein Element nach Ausführung dieses Übergangs haben soll. Lassen Sie dies auf *-Nicht ausgewählt-* wenn der Benutzer, der diesen Übergang wahrscheinlich ausführt, keine Berechtigung hat, den Beitragstatus zu ändern.

#### Die Registerkarte *Benachrichtigungen*:

![Liste der Workflows](../../../en/images/workflows/workflow-example-1/06-example-1-edit-transition-notification.png)

- **Benachrichtigung senden** Stellen Sie dies auf *Ja*, wo Benachrichtigungen erforderlich sind, zum Beispiel wenn Arthur Eddie benachrichtigen muss, dass ein Beitrag zur Überprüfung bereit ist.
- **Zusätzlicher Nachrichtentext** Dies ist generischer zusätzlicher Text, um dem Empfänger zu helfen.
- **Benutzergruppen** Sie können wählen, die Benachrichtigung an eine oder mehrere Benutzergruppen zu senden oder keine und stattdessen Benachrichtigungen an Einzelpersonen zu senden.
- **Benutzer** Wählen Sie einzelne Benutzer aus der Liste der Benutzer aus.

#### Die Registerkarte *Berechtigungen*:

Beachten Sie, dass *Autor* die Berechtigung *Übergang ausführen* auf Erlaubt (Geerbt) gesetzt hat. Ändern Sie diese Einstellungen nicht für andere Übergänge, die ein Autor nicht verwenden sollte, da dies auch Redakteure und Verleger betreffen wird.

## Die Beitragskategorie

Jedem Beitrag wird beim ersten Speichern ein Workflow zugewiesen. Wird der Beitrag zuerst einer Kategorie zugewiesen, die einen Workflow ausgewählt hat, wird er diesem Workflow zugeordnet. Andernfalls wird er dem Standard-Workflow zugewiesen. Das kann problematisch sein, da die Workflow-Komponente keine Methode zur Änderung des Workflows nach der Zuweisung bietet. Er kann von einem Super User mithilfe der Stapelaktion auf der Beitragsliste-Seite geändert werden.

### Eine Newsletter-Kategorie erstellen

Eine neue Newsletter-Kategorie wird benötigt, um den Newsletter als Kategorie-Blog anzuzeigen und sicherzustellen, dass die Newsletter-Beiträge dem Newsletter-Workflow zugeordnet werden.

![Workflows Liste](../../../en/images/workflows/workflow-example-1/07-example-1-newsletter-category.png)

## Der Menüpunkt Newsletter

Damit Besucher der Website den Newsletter sehen können, muss er entweder die Startseite sein oder mit einem Menüpunkt verlinkt werden. Um diesem Beispiel zu folgen, erstelle einen neuen Menüpunkt des Typs *Kategorie-Blog* mit der Kategorie *Newsletter*.

Probiere den Menüpunkt auf der Website aus. Es wird wahrscheinlich eine leere Seite mit folgender Nachricht angezeigt:

<div class="alert alert-info">
Es gibt keine Beiträge in dieser Kategorie. Wenn Unterkategorien auf dieser Seite angezeigt werden, können sie Beiträge enthalten.
</div>

## Als Arthur einloggen

Erinnerst du dich an Arthur, den Autor? Nach dem Login sollte die Newsletter-Seite eine Schaltfläche mit der Bezeichnung **Neuer Beitrag** haben. Wähle diese Option, um einen neuen Beitrag zu verfassen.

### Einen Beitrag verfassen

Fülle das Bearbeitungsformular für Beiträge so aus, wie du es für jeden Beitrag tun würdest. Bevor du jedoch das erste Mal speicherst, sieh dir die Registerkarte *Veröffentlichung* an.

- **Workflow-Phase** sollte auf **Übergang ausführen** *Entwurf/Überprüfung* gesetzt werden.
- **Kategorie** sollte auf *Newsletter* gesetzt werden.

Wenn du mit der Bearbeitung des Beitrags fertig bist, wähle *Speichern* oder *Speichern & Schließen*.

<div class="alert alert-danger">Nach dem Schließen des Beitrags kann Arthur ihn nicht mehr bearbeiten, da Benutzer in der Gruppe Autor unveröffentlichte Beiträge nicht anzeigen können.</div>

## Als Eddie einloggen

Eddie, der Redakteur, hat die Berechtigung, Unveröffentlichte Beiträge anzusehen, sodass die Newsletter-Seite alle Unveröffentlichten Elemente anzeigt, die er bearbeiten kann.

### Den Beitrag überprüfen

Wählen Sie den Beitrag aus, den Eddie verfasst hat, und nehmen Sie alle erforderlichen Änderungen vor, um ihn zu verbessern. Wenn Sie zufrieden sind, im *Veröffentlichungs-Tab*:

- **Workflow-Stufe** sollte auf **Übergang ausführen** *Überprüfen/Genehmigen* gesetzt werden.

Anders als Arthur, der seinen Beitrag nach dem Speichern nicht mehr sehen kann, kann Eddie den Beitrag erneut sehen und bearbeiten. Er kann auch den Übergang für die nächste Stufe auf Genehmigen/Veröffentlichen setzen. Der Übergang wird funktionieren, aber der Beitrag wird nicht veröffentlicht, da Eddie keine Veröffentlichungsberechtigung hat.

## Als Pru anmelden

Als die Genehmigungsphase im Workflow festgelegt wurde, sollte Pru eine Nachricht zur Aktionsergreifung erhalten haben. Melden Sie sich also als Pru an, um den Beitrag zu überprüfen und dessen Workflow-Phase auf **Übergang durchführen** *Veröffentlichen* zu setzen. *Speichern & Schließen* Sie den Beitrag, um das veröffentlichte Ergebnis zu sehen. Melden Sie sich ab, um das Ergebnis ohne den Bearbeiten-Link zu sehen.

Nachgedanke: Eine weitere Phase ist nötig, damit Pru die Phase von Veröffentlichen zu Überprüfen zurücksetzen kann, falls sie möchte, dass Eddie etwas behebt.

## Backend-Workflow

Die Benutzergruppen Autor, Redakteur und Verleger sind für die Frontend-Nutzung vorgesehen. Das Problem für Arthur ist, dass er von der Frontend-Oberfläche nicht auf seine Entwürfe zugreifen kann, da seine Benutzergruppe keine Zugriffsrechte für unveröffentlichte Beiträge hat.

Sie können den Backend-Zugriff für alle Mitglieder dieser Gruppen wie folgt ermöglichen:

- Gehen Sie zur Seite **Globale Konfiguration**.
- Wählen Sie den Reiter **Berechtigungen**.
- Wählen Sie *Autor* und setzen Sie **Administrator-Anmeldung** auf *Erlaubt*.
- **Speichern**
- Gehen Sie zur Seite **Beiträge: Optionen**.
- Wählen Sie den Reiter **Berechtigungen**.
- Wählen Sie *Autor* und setzen Sie **Zugriff auf Verwaltungsoberfläche** auf *Erlaubt*.

Dadurch können Arthur, Eddie und Pru sich am Backend anmelden und auf die Inhaltselemente zugreifen. Ein stark reduziertes Start-Dashboard:

![Start-Dashboard für Arthur](../../../en/images/workflows/workflow-example-1/08-example-1-backend-home.png)

Aber Arthur hat Zugriff auf seine Entwurfsbeiträge:

![Beitragsliste für Arthur](../../../en/images/workflows/workflow-example-1/09-example-1-backend-articles.png)

Beachten Sie, dass Arthur das letzte Element in der Liste nicht bearbeiten kann, da es nicht einer seiner eigenen Beiträge ist. Der Beitragstitel ist nicht verlinkt. Ebenso kann Arthur keine der vorhandenen Kategorien bearbeiten, da er keine Berechtigung hat, und auch diese sind nicht verlinkt. Er kann eine neue Kategorie erstellen, aber sie ist unveröffentlicht und er kann sie nicht veröffentlichen!

## Korrektur für falschen Workflow

Wenn Sie einem Beitrag den falschen Workflow zuweisen, stehen zwei Methoden zur Verfügung, um das Problem zu beheben.

### Superuser-Methode

- Gehen Sie zur **Beiträge**-Liste.
- Aktivieren Sie das Kontrollkästchen für den problematischen Beitrag.
- Wählen Sie die Schaltfläche **Aktionen** in der Werkzeugleiste.
- Wählen Sie die Schaltfläche **Stapel** aus der Liste.
- Wählen Sie **Stufe ändern** im Dialogfeld *Stapelverarbeitung ausgewählter Beiträge*.
- Wählen Sie einen passenden Ziel-Workflow und eine Stufe.
- Wählen Sie die Schaltfläche **Vorgang ausführen**.

![Beitragsliste für Arthur](../../../en/images/workflows/workflow-example-1/10-example-1-backend-batch.png)

### Alternativmethode

Alternativ können Sie eine Datenbanktabelle mit phpMyAdmin oder einem ähnlichen Tool bearbeiten.

Erforderliche Informationen:

- Die ID des Beitrags aus der letzten Spalte in der Beitragsliste.
- Die ID einer Stufe im gewünschten Workflow aus der letzten Spalte der
  Stufenliste des Workflows, den Sie verwenden möchten.

In phpMyAdmin:

- Durchsuchen Sie die Tabelle #__workflow_associations, um das item_id zu finden, das
  die ID Ihres Beitrags enthält.
- Ändern Sie den Wert von stage_id auf die Stufen-ID, die Sie im gewünschten
  Workflow nachgeschlagen haben.

Gehen Sie zurück zu Ihrer Beitragsliste und überprüfen Sie, ob der problematische Beitrag nun den richtigen Workflow verwendet.

*Übersetzt von openai.com*

