<!--
{
  "source": "https://docs.joomla.org/J4.x:Updating_from_an_existing_version",
  "title": "Versionsaktualisierung",
  "description": "", 
  "author": ""
}
-->

## Einführung

**Denken Sie daran: Sichern Sie Ihre Website immer, bevor Sie Updates durchführen.**

Die empfohlene Methode zum Aktualisieren von Joomla!-Installationen ist die Verwendung der *Joomla Update-Komponente*.

Eine Standardinstallation von Joomla 4 und höher enthält nach dem Login ein hilfreiches Benachrichtigungsfeld auf dem Home-Dashboard. Auf einen Blick können Sie sehen, ob ein Update verfügbar ist und welche Versionsnummer es hat.

Die Update-Nachricht, die im Benachrichtigungsfeld erscheint, hängt vom in der *Joomla Update: Optionen*-Seite eingestellten *Update-Kanal* und der aktuellen *Minor*-Version ab. Bei einem **Update-Kanal**, der auf **Standard** eingestellt ist, werden Updates innerhalb der aktuellen *Major*-Version gemeldet. Wenn der Parameter auf *Joomla Next* eingestellt ist, können Sie auf die neueste aktuelle Version aktualisieren und dann die **Nach Updates suchen**-Schaltfläche wählen, um zu sehen, ob die nächste *Major*-Version verfügbar ist.

Obwohl Joomla Sie benachrichtigt, wenn ein Update verfügbar ist, müssen Sie das Update selbst durchführen. Es ist ein einfacher Prozess, der schnellstmöglich durchgeführt werden sollte, um die Website auf dem aktuellen Stand zu halten.

## Zugriff auf die Aktualisierungskomponente

Wenn das Benachrichtigungsfenster im Home-Dashboard angezeigt wird, wähle die
Schaltfläche **x.y.z verfügbar - Jetzt aktualisieren!**, um zur Aktualisierungskomponente zu gelangen.

![Joomla-Aktualisierungsbenachrichtigung im Home-Dashboard](../../../en/images/migration/version-update/01-version-update-notification-home-dashboard.png)

Alternativ kannst du auf die Aktualisierungskomponente aus dem Administrator-Menü zugreifen, indem du **System** wählst, um über das **System-Dashboard** zu gehen.

![Joomla-Aktualisierungsbenachrichtigung im System-Dashboard](../../../en/images/migration/version-update/02-version-update-notification-system-dashboard.png)

Das System-Dashboard verfügt über ein *Aktualisierungspanel*, das einen Joomla-Link enthält, der die verfügbare Versionsnummer der Aktualisierung anzeigt. Wähle den **Joomla**-Link, um zur Aktualisierungskomponente zu gelangen.

## Durchführung des Updates

Joomla! 4 und 5 bieten eine Vorab-Prüfung für Updates zu Minor-Versionen. Diese Ansicht der Joomla-Update-Komponente zeigt technische Spezifikationen des Servers, auf dem sich die Seite befindet, und listet Kern- und Drittanbieter-Erweiterungen auf, die den Update-Server verwenden.

**Hinweis:** Der Bildschirm *Vorab-Prüfung* wird nicht angezeigt, wenn die Seite sich auf der aktuellen **Minor-Version** befindet.

![joomla vorab prüfung](../../../en/images/migration/version-update/03-version-update-pre-update-check.png)

Achten Sie sorgfältig auf die Prüfungsergebnisse und ergreifen Sie Maßnahmen zur Behebung von hervorgehobenen Problemen, bevor Sie ein Update durchführen. Möglicherweise müssen Sie inkompatible Erweiterungen aktualisieren, deaktivieren oder deinstallieren, bevor Sie Joomla aktualisieren.

Es ist nicht ungewöhnlich, Warnungen zu *Empfohlenen Einstellungen* zu sehen, da diese oft serverspezifisch und hostingspezifisch sind. Es ist wahrscheinlich, dass sie bereits vorhanden waren, als Sie Joomla installiert haben, und höchstwahrscheinlich verhindern sie nicht den Abschluss des Updates.

*Beachten Sie die Erinnerung, dass Sie dringend empfohlen werden, ein Backup zu erstellen, falls Sie dies noch nicht getan haben!*

Unterhalb der Update-Schaltfläche befindet sich ein Link. In den meisten Fällen können Sie diesen Link ignorieren. Er bietet die Möglichkeit, die Update-Dateien manuell hochzuladen, falls Ihr Server hinter einer Firewall steht oder anderweitig nicht in der Lage ist, die Joomla-Update-Server zu kontaktieren.

Wenn Sie die Vorab-Prüfung überprüft haben und zufrieden sind, wählen Sie **Update**.

### Bestätigung des Updates

![update starten seite](../../../en/images/migration/version-update/04-version-update-start-update.png)

Aktivieren Sie das Kontrollkästchen, um zu bestätigen, dass Sie ein Backup erstellt und überprüft haben, ob Erweiterungen kompatibel sind, und klicken Sie dann auf **Start Update**.

### Update-Fortschritt

![update-fortschritt seite](../../../en/images/migration/version-update/05-version-update-progress.png)

Sobald das Update beginnt, erscheint ein Fortschrittsbalken, während die Joomla-Dateien aktualisiert werden.

### Abschluss

![update abgeschlossen seite](../../../en/images/migration/version-update/06-version-update-completion.png)

Wenn der Fortschrittsbalken 100 % erreicht hat, bestätigt eine Systemmeldung, dass Ihre Seite aktualisiert wurde und die Versionsnummer. Die Versionsnummer wird auch in der oberen Symbolleiste neben dem Seitennamen aktualisiert.

Klicken Sie auf die **Zurück**-Schaltfläche und Sie werden zur Joomla-Update-Komponente zurückgeführt, wo es möglich ist, erneut nach Updates zu suchen.

## Überprüfungen nach der Beitragsaktualisierung

Sobald das Update abgeschlossen ist, sollten Sie einige Überprüfungen durchführen, um sicherzustellen, dass alles wie erwartet verlaufen ist, keine Fehler vorhanden sind und es keine Änderungen gibt, die weitere Maßnahmen erfordern.

### Frontend-Überprüfung

Gehen Sie zum Frontend der Website und überprüfen Sie, ob es funktioniert und wie vor dem Update angezeigt wird. Verwenden Sie die Kombination *Shift + Reload*, um Ihren Browser dazu zu zwingen, alle Änderungen an Stylesheets und Skripten neu zu laden.

### Systemüberprüfungen

Wählen Sie im Seitenleistenmenü **System**, um zum System-Dashboard zu gelangen. Dies gibt Ihnen einen Überblick über den aktuellen Status Ihrer Joomla-Website.

![System-Dashboard nach Beitragsaktualisierung](../../../en/images/migration/version-update/07-version-update-after-update.png)

In diesem Beispiel sehen wir, dass seit dem Update zwei Elemente vorhanden sind, die Aufmerksamkeit erfordern. Diese sind mit einem Etikett versehen, das eine Zahl enthält. Die Zahl bezieht sich darauf, wie viele Elemente Aufmerksamkeit erfordern. Durch Klicken auf jedes Element können Sie diese beheben.

**Hinweis:** Das System-Dashboard führt bei jedem Laden der Seite eine Überprüfung durch. Bedenken Sie, dass die Einstellungen des Browser-Cachings dies beeinflussen könnten. Es ist eine gute Praxis, den Cache des Browsers zu leeren, wenn Sie mit *Shift + Reload* überprüfen.

### Datenbank-Überprüfung

Navigieren Sie zu **System → Wartung → Datenbank**. Wenn Ihre Datenbank auf dem neuesten Stand ist, sollten Sie einen ähnlichen Bildschirm wie den untenstehenden sehen:

![Datenbanküberprüfung nach Beitragsaktualisierung ohne Probleme](../../../en/images/migration/version-update/08-version-update-after-update-database-check-no-problems.png)

Wenn Ihre Datenbank nicht auf dem neuesten Stand ist, wird ein Bildschirm angezeigt, der die gefundenen Probleme auflistet, ähnlich wie der untenstehende:

![Datenbanküberprüfung nach Beitragsaktualisierung mit Problemen](../../../en/images/migration/version-update/09-version-update-after-update-database-check-problems.png)

In diesem Fall wählen Sie den Namen der Problem-Erweiterung und dann die Schaltfläche Struktur aktualisieren in der Symbolleiste. Joomla wird Ihre Datenbank aktualisieren, um die aufgelisteten Probleme zu beheben, und dann den Bildschirm erneut anzeigen. Wenn die Behebung erfolgreich war, zeigt die Anzeige an, dass die Datenbank auf dem neuesten Stand ist.

**Hinweis:** Wenn weiterhin Fehler bestehen, stellen Sie sicher, dass alle Datenbanktabellen eingecheckt sind.

## System entdecken

In einigen Fällen, wenn Sie auf eine neue Joomla-Version aktualisieren, werden neue Kern-Erweiterungen hinzugefügt. Wenn es Probleme mit der Datenbankaktualisierung gab, wurden diese Erweiterungen möglicherweise nicht korrekt installiert. Um dies zu überprüfen, navigieren Sie zu **System → Entdecken**. Wählen Sie dann das Entdecken-Symbol in der Werkzeugleiste aus. Der Bildschirm sollte wie folgt aussehen:

![Entdecken Screen ohne zu installierende Erweiterungen](../../../en/images/migration/version-update/10-version-update-after-update-discover.png)

Wenn dies der Fall ist, wissen Sie, dass alle neuen Erweiterungen, die während des Updates hinzugefügt wurden, korrekt in der Datenbank installiert wurden.

Wenn es nicht installierte Erweiterungen gibt, werden sie auf dem Bildschirm ähnlich dem folgenden angezeigt:

![Entdecken Screen mit gefundenen Erweiterungen zur Installation](../../../en/images/migration/version-update/11-version-update-after-update-discover-found.png)

In diesem Fall markieren Sie die Kästchen und klicken auf das Installieren-Symbol in der Werkzeugleiste. Joomla installiert die Erweiterung(en) und zeigt dann den Bildschirm an, der keine entdeckten Erweiterungen anzeigt. Zu diesem Zeitpunkt wurden die neuen Erweiterungen in der Datenbank installiert.

## Fehlerbehebung

Wenn Sie vor, während oder nach dem Update Fragen, Probleme oder Fehler haben, stellen Sie diese bitte im [Migrating and Upgrading to Joomla! 4.x Forum](https://forum.joomla.org/viewforum.php?f=812).

Wenn Sie während des Update-Prozesses Probleme oder Fehler haben, hier sind einige Tipps:

- Löschen Sie den Cache Ihres Browsers. Möglicherweise gab es Änderungen im CSS oder Javascript, die nach einem Update von Ihrem Webbrowser neu geladen werden müssen.
- Wenn nach dem Update Fehlermeldungen in der Datenbank angezeigt werden, überprüfen Sie den **System → Wartungspanel → Datenbank**-Link. In einigen Fällen kann ein Datenbankfehler verhindern, dass alle Datenbank-Updates ausgeführt werden. In diesem Fall können Sie sie über den Datenbank-Link ausführen und dann die Methode **System → Installieren → Entdecken** verwenden, um neue Erweiterungen zu überprüfen und zu installieren.
- Der Update-Prozess erstellt oder hängt eine Protokolldatei namens administrator/logs/joomla_update.php an, die Sie mit einem Texteditor öffnen können, um die im Protokoll aufgezeichneten Schritte zu sehen. Es werden die Hauptschritte angezeigt (Zip herunterladen, installieren, SQL-Anweisungen ausführen, aufräumen), etwa so:

```
2024-04-17T09:13:16+00:00    INFO 127.0.0.1    update    Update gestartet von Benutzer Jimmy (139). Alte Version ist 5.0.3.
2024-04-17T09:13:18+00:00    INFO 127.0.0.1    update    Download der Update-Datei von ...
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Datei Joomla_5.1.0-Stable-Update_Package.zip heruntergeladen.
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Installation der neuen Version begonnen.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Finalisierung der Installation.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Start der SQL-Updates.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Die aktuelle Datenbankversion (Schema) ist 5.0.0-2023-09-11.
... Viele einzelne SQL-Abfragen
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Ende der SQL-Updates.
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Deinstallation von Erweiterungen
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Löschen von entfernten Dateien und Ordnern.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Aufräumen nach der Installation.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Update auf Version 5.1.0 abgeschlossen.
```
