<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Laragon f\u00fcr Windows",
    "description": "",
    "author": ""
}
-->

## Einrichten einer lokalen Joomla-Umgebung mit Laragon

Laragon ist ein schlankes Windows-Tool, das Apache, MySQL und
PHP in einer einfachen Installation bereitstellt. Keine
Konfigurationsdateien, keine manuelle Einrichtung – einfach
herunterladen, ausführen und mit der Entwicklung bzw. dem Testen von
Joomla beginnen. Lesen Sie diesen Beitrag im Joomla Community Magazine:
[Laragon: Der unkomplizierte, leistungsstarke AMP-Server für
Windows](https://magazine.joomla.org/all-issues/october-2025/laragon-the-effortless,-high-performance-amp-server-for-windows).

Dieser Leitfaden führt Sie von Grund auf zu einer funktionierenden
lokalen Joomla-Website und behandelt außerdem eine kleine
Besonderheit der Benutzeroberfläche in der neuesten Version, die sich
leicht beheben lässt, sobald Sie wissen, was passiert.### Laragon herunterladen und installieren

Rufen Sie zunächst die offizielle [Laragon-Downloadseite](https://laragon.org/download) auf. Laden Sie die Laragon-Full-Version (derzeit v8.6.1) herunter, da sie alles enthält, was Sie sofort benötigen (z. B. Apache, MySQL und die neuesten PHP-Versionen).
Alternativ können Sie den [Installer](https://github.com/leokhoa/laragon/releases/download/8.6.1/laragon-wamp.exe) direkt herunterladen.

Sobald die `.exe`-Datei heruntergeladen wurde, doppelklicken Sie darauf, um die Installation zu starten.

**Hinweis zu Windows Defender:** Da Laragon ein leistungsstarkes Entwickler-Tool ist, blockiert Windows Defender SmartScreen möglicherweise den Start und zeigt einen blauen Warnbildschirm an. Das ist normal – klicken Sie einfach auf **Weitere Informationen** und anschließend auf die Schaltfläche **Trotzdem ausführen**, die unten angezeigt wird.

![laragon setup windows protected warning](../../../en/images/hosting-local/laragon-setup-windows/01-laragon-setup-windows-protected-warning.png)

Klicken Sie sich durch den Setup-Assistenten. Die Standardeinstellungen sind völlig ausreichend,aber achten Sie auf diese beiden wichtigen Details:

1.  **Installationsort:** Belassen Sie den Installationsordner bei
    `C:\laragon`. Wenn Sie die Installation tief in `Program Files` oder
    `Dokumente` vornehmen, kann dies später zu Berechtigungsproblemen führen.
2.  **Einrichtungsoptionen:** Stellen Sie sicher, dass das Kontrollkästchen **Automatische virtuelle Hosts** aktiviert ist. Diese Funktion gibt Ihrer lokalen Joomla-Website eine saubere Adresse (wie `http://myjoomla.test`) anstelle einer unverarbeiteten IP-Adresse.

![Laragon-Einrichtungsoptionen](../../../en/images/hosting-local/laragon-setup-windows/02-laragon-setup-options.jpg)

Starten Sie Ihren Computer nach Abschluss der Installation neu. (Der
Installationsassistent fordert Sie dazu ebenfalls auf.)### Starten Ihres Servers und Firewall-Berechtigungen

Öffnen Sie Laragon über Ihr Startmenü und klicken Sie auf die Schaltfläche **Alle starten**.

Da Sie zum ersten Mal einen lokalen Server ausführen, muss Windows
überprüfen, ob er sicher ist. Es werden Aufforderungen der Windows Defender-Firewall
angezeigt, in denen Sie um Netzwerkzugriff für Dienste wie **Apache HTTP
Server**, **MySQL** und **Mailpit** gebeten werden.

- Klicken Sie bei jeder dieser Aufforderungen einfach auf **Zugriff zulassen**.

Sobald der Zugriff erlaubt wurde, startet Laragon Ihre lokale Umgebung. Sie erkennen,
dass sie funktioniert, wenn die Apache- und MySQL-Portnummern im
Laragon-Fenster angezeigt werden.### Die Eigenheit „Bereits ausgeführt“ (und wie man sie behebt)

Wenn Sie mit Ihrer Arbeit fertig sind, klicken Sie möglicherweise auf „Stop All“, um Apache
und MySQL auszuschalten, und anschließend auf das „X“ in der oberen rechten Ecke,
um das Laragon-Fenster zu schließen.

Hier liegt die Eigenheit: Durch Klicken auf das „X“ wird Laragon nicht vollständig
beendet. Es läuft weiterhin unbemerkt im Hintergrund. Wenn Sie versuchen, die
Laragon-App erneut über das Startmenü oder den Desktop zu öffnen, sehen Sie unten
rechts auf Ihrem Bildschirm eine gelbe Warnung mit dem Hinweis:
**„Laragon wird bereits ausgeführt!“**

![Hinweis „Laragon wird bereits ausgeführt“ bei der Laragon-Einrichtung](../../../en/images/hosting-local/laragon-setup-windows/03-laragon-setup-already-running-notice.png)

**Die Falle:** Wenn Sie auf das „X“ in dieser kleinen gelben Warnung klicken, um sie
zu schließen, verschwindet auch das Hauptfenster von Laragon, sodass Sie keinen
Zugriff mehr auf das Bedienfeld haben. (Hinweis: Gelegentlich kann auch ein
Lizenz-Pop-up erscheinen, das dazu führt, dass die Benutzeroberfläche auf ähnliche
Weise einfriert.)

**Die Lösung:** Wenn Ihre Benutzeroberfläche verschwindet oder einfriert, müssen Sie lediglich
Beende den Hintergrundprozess zwangsweise und starte neu. Es ist ganz einfach:

1.  Drücke `Ctrl + Shift + Esc` auf deiner Tastatur, um den **Windows-
    Task-Manager** zu öffnen.
2.  Suche in der Liste der laufenden Prozesse nach **Laragon**.
3.  Klicke mit der rechten Maustaste darauf und wähle **Task beenden**.

Das war's! Du hast den festgefahrenen Hintergrundprozess sicher beendet. Du kannst Laragon nun über dein Startmenü öffnen. Es wird einwandfrei geladen, sodass du ohne Fehler auf „Alle starten“ klicken kannst.### Umgang mit den Lizenz-Pop-ups (den „Nag“-Bildschirmen)

Laragon kann für die nichtkommerzielle Entwicklung und zum Testen
kostenlos verwendet werden, ohne eine Lizenz zu erwerben. Nach einer
gewissen Nutzungsdauer werden Sie jedoch wahrscheinlich auf eine
Aufforderung zur Eingabe eines „Lizenzschlüssels“ stoßen, in der Sie
aufgefordert werden, das Projekt zu unterstützen.

Da Sie die kostenlose Version verwenden, können Sie diese Bildschirme
einfach schließen. Es gibt jedoch eine bestimmte Reihenfolge, die Sie
erwarten können:

1.  Das Hauptfenster **Lizenzschlüssel** wird über Ihrer Laragon-
    Oberfläche angezeigt. Klicken Sie auf den Text **Schließen** oder auf
    das „X“.<br>
    ![Laragon-Setup-Fenster für den Lizenzschlüssel](../../../en/images/hosting-local/laragon-setup-windows/04-laragon-setup-license-key-window.png)

2.  Unmittelbar nach dem Schließen wird ein zweites **Warnung**-Pop-up
    angezeigt, das Sie daran erinnert, dass Laragon ohne Lizenz ausgeführt
    wird. Klicken Sie auf **OK** oder auf das „X“.<br>
    ![Laragon-Setup-Warnung ohne Lizenz](../../../en/images/hosting-local/laragon-setup-windows/05-laragon-setup-no-license-warning.png)

3.  Sobald Sie diese zweite Warnung schließen, öffnet Laragon möglicherweise automatisch
    Ihren Webbrowser öffnen und Sie zu `https://laragon.org/key` weiterleiten. Sie
    können diesen Browser-Tab einfach schließen.
4.  Wenn Sie zur Laragon-Oberfläche zurückkehren und auf **Alle starten** klicken, um
    Ihren Server wieder hochzufahren, müssen Sie möglicherweise noch einmal durch
    genau dieselben beiden Pop-ups klicken.

Nachdem Sie sie dieses zweite Mal geschlossen haben, verschwinden die Pop-ups, und
Sie können Laragon völlig uneingeschränkt verwenden!

*(Hinweis: Falls Ihre Laragon-Oberfläche während dieser Pop-ups irgendwann
einfriert und nicht mehr angeklickt werden kann, denken Sie einfach an den
`Strg + Umschalt + Esc`-Trick mit dem Task-Manager aus dem vorherigen Schritt,
um den Hintergrundprozess zu beenden und neu zu beginnen.)*### Erstellen einer Datenbank für Joomla

Vor der Installation von Joomla benötigen Sie eine leere Datenbank zum Speichern der Daten.
Laragon enthält einen integrierten Datenbankmanager namens HeidiSQL, sodass
bereits alles vorhanden ist, was Sie benötigen.

1.  Stellen Sie sicher, dass Ihre Laragon-Dienste ausgeführt werden (klicken Sie auf **Alle starten**).
2.  Klicken Sie auf die Schaltfläche **Datenbank** in der Laragon-Hauptoberfläche.
3.  Ein Fenster zur Sitzungsverwaltung wird geöffnet. Laragon trägt automatisch
    die Standardanmeldedaten für die lokale Umgebung ein (Benutzer: `root`, Passwort:
    *\[leer lassen\]*).
4.  Klicken Sie unten auf die Schaltfläche **Öffnen**.<br>    
    **Fehlerbehebung: Fehler „Zugriff für Benutzer 'root'@'localhost'
    verweigert“: ** Wenn Sie auf die Schaltfläche **Öffnen** klicken und sofort eine
    Fehlermeldung über eine fehlgeschlagene Verbindung erhalten, machen Sie sich keine Sorgen! Das bedeutet normalerweise, dass ein
    anderes MySQL-Programm (wie XAMPP oder MySQL Workbench) im
    Hintergrund ausgeführt wird und Laragons Zugriff auf den Datenbankport
    (Port 3306) blockiert.<br>    ![Fehlerbehebung beim Laragon-Setup-Zugriff](../../../en/images/hosting-local/laragon-setup-windows/06-laragon-setup-troubleshooting.jpg)

    **Die Lösung:**
    1.  Drücken Sie die Windows-Taste, geben Sie **Dienste** ein und drücken Sie die Eingabetaste.
    2.  Scrollen Sie in der Liste nach unten, um **MySQL**, **MySQL80** oder **MariaDB** zu finden.
    3.  Klicken Sie mit der rechten Maustaste auf den laufenden Dienst und wählen Sie **Beenden**.
    4.  Gehen Sie zurück zu Laragon, klicken Sie auf **Alle stoppen**, dann auf **Alle starten** und
        versuchen Sie erneut, im Sitzungsmanager auf **Öffnen** zu klicken. Die Verbindung sollte
        nun ohne Fehler hergestellt werden.
5.  Sobald Sie erfolgreich verbunden sind und sich im HeidiSQL-Datenbankmanager befinden, sehen Sie sich die linke Spalte an. Klicken Sie mit der rechten Maustaste auf den
    Servernamen (normalerweise `Laragon.MySQL` oder `127.0.0.1`).
6.  Bewegen Sie den Mauszeiger über **Neu erstellen** und wählen Sie **Datenbank** aus.
7.  Eine kleine Eingabeaufforderung wird angezeigt. Geben Sie im Feld
    „Name“ einen einfachen Namen für Ihre Datenbank ein (zum Beispiel: `joomla_dev`). Das
    Dropdown-Menü „Sortierung“ können Sie auf der Standardeinstellung belassen.
8.  Klicken Sie auf **OK**.Ihre neue Datenbank wird in der Liste auf der linken Seite angezeigt. Das
war's! Sie können das Datenbankmanagerfenster nun vollständig schließen.### Ihre Joomla-Dateien abrufen

Nachdem Ihr Server und Ihre Datenbank bereit sind, ist es an der Zeit, die Joomla-
Dateien bereitzustellen. Wie Sie dabei vorgehen, hängt ganz davon ab, was Sie mit
dieser lokalen Einrichtung erreichen möchten:

**Methode 1: Zum Erstellen einer Standardwebsite** Wenn Sie lediglich eine
Website erstellen oder Erweiterungen testen möchten, benötigen Sie die stabile
Standardversion.

- Rufen Sie die offizielle [Joomla-Downloadseite](https://downloads.joomla.org) auf
  und laden Sie die aktuelle `.zip`-Datei des **Full Package** herunter.

**Methode 2: Zum Testen von Community-PRs (Patch-Tests)** Wenn Sie die Community
durch das Testen von Patches und Pull Requests unterstützen möchten, benötigen Sie
ein vorkompiliertes Paket, das den allerneuesten Code enthält.

- **Der Nightly Build:** Laden Sie den aktuellen `.zip`-Nightly-Build von
  [Nightly Builds](https://developer.joomla.org/nightly-builds.html) herunter.
  Diese Builds werden jede Nacht erstellt und eignen sich perfekt für die Verwendung
  mit der Joomla-Komponente Patch Tester.- **Das vorgefertigte PR-Paket:** Wenn Sie alternativ einen
  bestimmten PR auf GitHub testen, scrollen Sie zum unteren Ende der PR-Seite,
  klicken Sie auf **Alle Prüfungen anzeigen** und suchen Sie nach dem Link
  **Vorgefertigte Pakete herunterladen**.
  ![Link zum vorgefertigten Paket für die Laragon-Einrichtung](../../../en/images/hosting-local/laragon-setup-windows/07-laragon-setup-prebuilt-package-link.png)

**Methode 3: Für das Beitragen von Core-Code** Wenn Sie Code schreiben und
eigene Pull Requests einreichen möchten, benötigen Sie den unkompilierten
Quellcode.

- Klonen Sie das [Joomla-CMS-GitHub-Repository](https://github.com/joomla/joomla-cms)
  direkt mit Git in Ihre Laragon-Umgebung.
- *Wichtig:* Ein unveränderter GitHub-Klon funktioniert nicht sofort – Sie müssen
  Laragons Terminal öffnen und in Ihrem Ordner `composer install` und `npm ci` ausführen, um die
  PHP-Abhängigkeiten und CSS/JS-Assets zu erstellen. (Da Sie die Vollversion von
  Laragon installiert haben, sind Composer und NPM bereits auf Ihrem System
  installiert.)### **Ablegen der Dateien in Laragon:**

Unabhängig davon, für welche Methode Sie sich entschieden haben, ist das Ausführen der Dateien in Laragon immer derselbe Vorgang:

1.  Öffnen Sie Ihre Laragon-Oberfläche und klicken Sie auf die Schaltfläche **Root**. Dadurch wird automatisch der Ordner `C:\laragon\www` auf Ihrem Computer geöffnet.
2.  Erstellen Sie in diesem `www`-Ordner einen neuen Ordner für Ihr Projekt. Halten Sie den Ordnernamen einfach, kleingeschrieben und ohne Leerzeichen (zum Beispiel: `joomla_dev` oder `joomla_pr_test`).
3.  Legen Sie Ihre Joomla-Dateien in diesem neuen Ordner ab. (Wenn Sie in Methode 1 oder 2 eine `.zip`-Datei heruntergeladen haben, extrahieren Sie den gesamten Inhalt direkt in diesen Ordner. Wenn Sie in Methode 3 Git verwenden, klonen Sie das Repository in diesen Ordner.)
4.  Da Sie während der Installation „Automatische virtuelle Hosts“ aktiviert haben, verwendet Laragon automatisch Ihren Ordnernamen, um Ihre lokale Webadresse zu erstellen. Ein Ordner mit dem Namen `joomla_dev` ist daher in Ihrem Browser unter `http://joomla_dev.test` erreichbar.
    <br>    **Tipp: Halten Sie Ihre Umgebungen sauber:** Es ist eine gute Idee, 
    verschiedene Ordner für unterschiedliche Joomla-Versionen oder spezifische PR-Tests zu erstellen
    (z. B. einen Ordner namens `joomla5_stable` und einen anderen namens
    `joomla4_dev`). Laragon führt sie problemlos alle parallel mit ihren
    eigenen sauberen `.test`-URLs aus und verhindert so, dass Ihr Code und Ihre Datenbanken
    durcheinandergeraten!
    <br>
    ![Laragon-Einrichtung der Projektordner](../../../en/images/hosting-local/laragon-setup-windows/08-laragon-setup-project-folders.png)## Joomla-Installer ausführen

Sie haben Ihre Datenbank, und Ihre Joomla-Dateien befinden sich in ihrem neuen
Ordner (zum Beispiel `C:\laragon\www\joomla_dev`). Jetzt ist es an der Zeit,
Joomla tatsächlich zu installieren!

**Wichtiger Schritt: Apache neu laden!** Wenn Laragon bereits ausgeführt wurde,
während Sie Ihren neuen Projektordner erstellt haben, weiß Laragon noch nicht,
dass der Ordner existiert.

- Öffnen Sie die Laragon-Oberfläche.

- Klicken Sie oben rechts auf **„Reload“**. *(Dadurch wird Laragon gezwungen, den
  Ordner `www` zu scannen und die neue Adresse `http://joomla_dev.test` zu
  generieren.)*

**Einrichtung abschließen:**

1. Öffnen Sie Ihren Webbrowser und geben Sie die automatisch generierte URL
   Ihres Projekts ein (z. B. `http://joomla_dev.test`).
2. Nun sollte sofort die Seite des Joomla-Webinstallationsprogramms angezeigt werden.
3. Wählen Sie Ihre Sprache aus und geben Sie einen Namen für Ihre Joomla-Website ein.
4. Richten Sie Ihr Super-User-Konto ein (denken Sie an diese Anmeldedaten – Sie
   benötigen sie, um auf das Joomla-Administrator-Dashboard zuzugreifen!).5.  Geben Sie auf dem Bildschirm **Datenbankkonfiguration** die Zugangsdaten für
    die zuvor erstellte Laragon-Datenbank ein:
    - **Datenbanktyp:** `MySQLi` (Standard)
    - **Hostname:** `localhost`
    - **Benutzername:** `root`
    - **Passwort:** *\[Lassen Sie dieses Feld vollständig leer\]*
    - **Datenbankname:** Der genaue Name, den Sie zuvor in HeidiSQL eingegeben haben
      (z. B. `joomla_dev`).
    ![Datenbankeinstellungen des Laragon-Joomla-Installationsprogramms](../../../en/images/hosting-local/laragon-setup-windows/09-laragon-setup-joomla-installer-database.png)

6.  Klicken Sie auf **Joomla installieren.**

Sobald der Fortschrittsbalken vollständig geladen ist, wird eine Erfolgsmeldung
angezeigt – Sie können nun auf **Website öffnen** klicken, um Ihre lokale Live-Website
anzuzeigen, oder auf **Administration öffnen**, um sich im Joomla-Backend anzumelden.

Das war's – Ihre lokale Joomla-Website ist live und einsatzbereit.

*Übersetzt von openai.com*