<!--
{
  "source": "https://docs.joomla.org/J4.x:Privacy_Setup",
  "title": "Datenschutzeinstellungen",
  "description": "", 
  "author": ""
}
-->

## Datenschutzkomponente

Die Datenschutzkomponente wird verwendet, um Datenschutzinformationen zu verwalten, um Anfragen nach Informationen oder Anfragen zur Löschung von Informationen zu sammeln. Sie basiert auf E-Mail-Adressen und gilt daher offensichtlich für registrierte Benutzer, die bei der Registrierung eine E-Mail-Adresse angeben müssen. Sie gilt auch für Daten von nicht registrierten Benutzern, deren E-Mail-Adressen über die Kontakte-Komponente bereitgestellt wurden. Sie implementiert nicht die Erlaubnis zur Verwendung von Cookies oder Tracking, die gemäß der DSGVO erforderlich sind.

Wenn persönlich identifizierbare Informationen gesammelt werden, sollten Sie sicherstellen:

- Der Benutzer wird in klarer und leicht verständlicher Sprache darüber informiert, warum Sie diese Informationen anfordern.
- Der Benutzer weiß, welche Daten Sie über ihn sammeln.
- Der Benutzer weiß, wofür Sie die Daten verwenden werden.
- Der Benutzer hat aktiv in die Nutzung der Daten eingewilligt.

In der Regel werden diese Informationen in einem Datenschutzrichtlinienbeitrag beschrieben.

## Datenschutz-Dashboard

Das Datenschutz-Dashboard bietet eine Zusammenfassung der **Datenschutzanfragen** und des **Datenschutzstatus** der Website. Um darauf zuzugreifen:

- Wählen Sie **Benutzer → Datenschutz** im Administrator-Menü.

![Datenschutz-Dashboard](../../../en/images/privacy/privacy-setup/01-privacy-dashboard.png)

Im Datenschutz-Dashboard werden standardmäßig zwei Module angezeigt:

### Datenschutzanfragen

Dieses Modul bietet eine Zusammenfassung der aktuellen Informationsanfragen.

### Datenschutzstatus

Dieses Modul zeigt den Status der Optionen an, auf die sich die Website-Betreiber konzentrieren sollten:

- **Veröffentlichte Datenschutzerklärung** legt einen Beitrag zur Datenschutzerklärung im
  **System - Datenschutz-Zustimmung**-Plugin fest.
- **Veröffentlichtes Antragsformular-Menüelement** richtet ein Menüelement ein, damit authentifizierte Benutzer Anfragen einreichen können.
- **Offene dringende Anfragen** überprüft bestätigte Anfragen, die älter sind als das im Komponentenparameter angegebene Alter (standardmäßig 14 Tage), und informiert den Website-Betreiber über Anfragen, die dringend Aufmerksamkeit erfordern.
- **Mail-Versand aktiviert** die Website muss in der Lage sein, E-Mails zu senden, um Informationsanfragen zu bearbeiten.
- **Datenbankverschlüsselung** dies ist relevant, wenn eine externe Datenbank verwendet wird.

## Plugin: System - Datenschutz-Einwilligung

Wenn dieses Plugin deaktiviert ist, zeigt das Datenschutz-Statuspanel im Dashboard an, dass die Datenschutzrichtlinie **Nicht Verfügbar** ist, und bietet einen Link zum Bearbeitungsformular des Plugins an. Wenn es aktiviert ist, fordert das Plugin jeden neuen Benutzer, der sich auf Ihrer Website registriert, dazu auf, der Datenschutzrichtlinie zuzustimmen. Alle bestehenden Benutzer werden zu ihrem Benutzerprofil weitergeleitet, damit sie ihre Zustimmung geben können.

Um Einwilligungen einzurichten:

- Wählen Sie **Home Dashboard** → **Plugins** im Administrator-Menü aus.
- Finden Sie das Plugin **System - Datenschutz-Einwilligung** (nicht zu verwechseln mit dem Datenschutz - Einwilligungen Plugin).
- Wählen Sie aus, um das Datenformular des Plugins zu öffnen.

![plugin system privacy consent](../../../en/images/privacy/privacy-setup/02-plugin-system-privacy-consent.png)

- Setzen Sie den **Status** auf **Aktiviert**.
- Optional: Wählen oder erstellen Sie einen Beitrag, der im Registrierungsformular verlinkt wird. Oder setzen Sie den Datenschutzt-Typ auf Menüpunkt und wählen oder erstellen Sie einen Menüpunkt.
- Wählen Sie die Registerkarte **Ablauf** und **Hilfe inline umschalten** für eine Erklärung zu jedem Feld. Aktivieren und passen Sie die Parameter an, **wenn** Sie möchten, dass die Einwilligungen nach einer ausgewählten Anzahl von Tagen ablaufen.

### Hinweise zur Datenschutzeinwilligung für mehrsprachige Seiten:

**Kurze Datenschutzrichtlinie und Umleitungsnachricht** Wenn Sie den Standardtext verwenden, wird dieser in der Sprache des Benutzers angezeigt. Es ist nicht möglich, den benutzerdefinierten Text zu übersetzen. Wenn Sie den Text anpassen und in mehreren Sprachen anzeigen möchten, lassen Sie dieses Feld leer und verwenden Sie die Joomla-Sprachüberschreibungsfunktion, um die Sprachzeichenketten `PLG_SYSTEM_PRIVACYCONSENT_NOTE_FIELD_DEFAULT` und `PLG_SYSTEM_PRIVACYCONSENT_REDIRECT_MESSAGE_DEFAULT` für jede installierte Sprache anzupassen.

**Datenschutzbeitrag** und **Datenschutz-Menüpunkt** Wenn Sie diesen Beitrag oder Menüpunkt mit Alternativen in anderen Sprachen verknüpfen, wird die Datenschutzrichtlinie in der korrekten Sprache für den Benutzer angezeigt.

## Plugin: Benutzer - Allgemeine Geschäftsbedingungen

Wenn dieses Plugin aktiviert ist, wird von jedem neuen Benutzer, der sich auf Ihrer Seite registriert, verlangt, den Allgemeinen Geschäftsbedingungen für die Nutzung Ihrer Seite zuzustimmen. Alle bestehenden Benutzer werden zu ihrem Benutzerprofil weitergeleitet, damit sie zustimmen können.

Dieses Plugin ist standardmäßig nicht aktiviert. So aktivieren Sie es:

- Wählen Sie **Start-Dashboard → Plugins** aus dem Administrator-Menü.
- Suchen Sie das Plugin **Benutzer - Allgemeine Geschäftsbedingungen**.
- Wählen Sie, um das Formulareingabe-Feld des Plugins zu öffnen.
- Setzen Sie den **Status** auf **Aktiviert**.
- Optional: Wählen Sie einen Beitrag aus oder erstellen Sie einen neuen, den Sie im Registrierungsformular verlinken möchten.

### Hinweise zu Benutzer - Allgemeine Geschäftsbedingungen für mehrsprachige Seiten

**Kurze Allgemeine Geschäftsbedingungen** Wenn Sie den Standardtext verwenden, wird dieser in der Sprache des Benutzers angezeigt. Es ist nicht möglich, den benutzerdefinierten Text zu übersetzen. Falls Sie den Text anpassen und in mehreren Sprachen anzeigen möchten, sollten Sie dieses Feld leer lassen und die Joomla-Sprachüberschreibung nutzen, um die Sprachzeichenketten `PLG_USER_TERMS_NOTE_FIELD_DEFAULT` für jede installierte Sprache anzupassen.

**Beitrag zu Allgemeinen Geschäftsbedingungen** Wenn Sie diesen Beitrag mit Alternativen in anderen Sprachen verknüpfen, wird die Datenschutzerklärung in der richtigen Sprache für den Benutzer angezeigt.

## Anzeige der Einwilligung zur Benutzerregistrierung

Zusammen erscheinen die beiden Plugins im Benutzerregistrierungsformular wie im folgenden Screenshot:

![privacy consents site view](../../../en/images/privacy/privacy-setup/03-privacy-consents-site.png)

## Menüpunkt: Anfrage nach Datenschutzinformationen

Registrierte Benutzer können eine Informationszusammenfassung oder eine Entfernung über einen Menüpunkt anfordern. Einrichten wie folgt:

- Wählen Sie **Menüs** → **Untermenu** im Administrator-Menü (verwenden Sie das Menü, das am bequemsten ist).
- Geben Sie einen passenden **Titel** ein, zum Beispiel: **Anfrage nach Datenschutzinformationen**.
- Verwenden Sie die **Auswählen**-Schaltfläche, um den Popup-Dialog zum Menüpunkttyp zu öffnen.
- Wählen Sie im Abschnitt **Datenschutz** den Punkt **Anfrage erstellen** aus.
- Setzen Sie das Feld **Zugriff** auf **Registriert**.
- **Speichern & Schließen**.

Gehen Sie zu Ihrer Website-Ansicht und überprüfen Sie, dass der Menüpunkt nicht angezeigt wird, wenn Sie nicht eingeloggt sind und dass er angezeigt wird, nachdem Sie sich eingeloggt haben. Verwenden Sie den Link und probieren Sie die **Exportieren**-Option aus. Sie können später die **Entfernen**-Option mit einem Dummy-Konto ausprobieren. Falls bereits eine Anfrage aussteht, erhalten Sie eine Fehlermeldung:

„Ihre Informationsanfrage konnte nicht erstellt werden. Es gibt bereits eine aktive Informationsanfrage für diese E-Mail-Adresse und diesen Anfrage-Typ. Bitte kontaktieren Sie den Website-Besitzer für Updates zu dieser Anfrage.“

## Menüpunkt: Datenschutzanfrage Bestätigen

Für SEF-Zwecke können Sie einen versteckten Menüpunkt erstellen, damit der Benutzer die Anfrage bestätigen kann. Dieser wird im per E-Mail gesendeten Link enthalten sein.

- Wählen Sie **Menüs** → **Verstecktes Menü** aus dem Administrator-Menü (erstellen Sie ein verstecktes Menü ohne zugewiesene Modulposition oder siehe unten).
- Geben Sie einen geeigneten **Titel** ein, Beispiel: **Datenschutzanfrage bestätigen**.
- Verwenden Sie die **Auswählen**-Schaltfläche, um den Dialog für Menüpunkttypen zu öffnen.
- Wählen Sie im **Datenschutz**-Abschnitt den Punkt **Anfrage bestätigen** aus.
- Wenn Sie kein verstecktes Menü haben, verwenden Sie Ihr Hauptmenü und stellen im Reiter "Link-Typ" **Anzeige im Menü** auf **Nein**.
- **Speichern & Schließen**.

## Administrator-Menüelemente

Schauen Sie sich die anderen Menüelemente der Datenschutzerweiterung an.

### Administrator-Datenschutzanfragen

Dieser Bildschirm ist der zentrale Ort für die Bearbeitung und Verwaltung von Benutzerinformationsanfragen. Bitte lesen Sie den zugehörigen Beitrag zum Datenschutz-Workflow für Anleitungen zur Bearbeitung von Anfragen.

![Datenschutzanfragen](../../../en/images/privacy/privacy-setup/04-privacy-information-requests.png)

### Erweiterungsfähigkeiten

Dieser Bildschirm sammelt und zeigt Informationen über die datenschutzbezogenen Fähigkeiten an, die von einzelnen Erweiterungen gemeldet werden. Er soll bei der Erstellung von Dokumentationen wie einem Datenschutzrichtlinienbeitrag oder einem Beitrag zu den Nutzungsbedingungen helfen.

![Datenschutzfähigkeiten der Erweiterung](../../../en/images/privacy/privacy-setup/05-privacy-extension-capabilities.png)

Die Seiteninhalte stammen aus Sprachstrings im Kern, in der Datenschutzerweiterung und in Plugins, die das onPrivacyCollectAdminCapabilities-Ereignis implementieren. Dazu gehören:

- Authentifizierung
- Captcha
- Installer
- Datenschutz
- System
- Benutzer

Die Informationen werden in der Sprache angezeigt, die für die Administratoranmeldung ausgewählt wurde.

### Einwilligungen

Dieser Bildschirm zeigt eine Liste von Einwilligungen an, die neuesten zuerst. Sie wird in der Sprache angezeigt, die im Einwilligungsformular verwendet wurde, üblicherweise während der Registrierung. Sie können nach dem Namen eines bestimmten Benutzers suchen. Beachten Sie, dass die Einwilligung zu den Allgemeinen Geschäftsbedingungen der Seite hier nicht aufgezeichnet wird. Diese ist nur im Protokoll der Benutzeraktionen vorhanden.

![Datenschutzeinwilligungen](../../../en/images/privacy/privacy-setup/06-privacy-consents.png)

*Übersetzt von openai.com*

