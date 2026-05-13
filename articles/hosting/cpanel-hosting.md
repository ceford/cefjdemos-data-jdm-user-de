<!--
{
  "source": "https://docs.joomla.org/J4.x:Hosting_Setup",
  "title": "cPanel-Hosting ",
  "description": "", 
  "author": ""
}
-->

## Einführung

## cPanel-Hosting

Wenn Sie sich bei Ihrem cPanel-Hosting-Dienst anmelden, sollten Sie Folgendes sehen:

![cpanel hosting control panel](../../../en/images/hosting/cpanel-hosting/01-cpanel-hosting.png)

### Datenbankeinrichtung

Das Datenbanken-Panel wird verwendet, um eine Datenbank und einen Datenbankbenutzer für Joomla zu erstellen.

Wählen Sie den Eintrag MySQL-Datenbanken und geben Sie einen Datenbanknamen im Formular ein. Der erste Teil des Formulars ist vordefiniert. Der Rest liegt bei Ihnen. Es sollte kurz und vielleicht nicht offensichtlich sein - *jblog* zum Beispiel.

Im selben Formular gehen Sie zum Abschnitt *Neuen Benutzer hinzufügen*. Geben Sie einen Benutzernamen ein. Dieser kann nach Belieben gewählt werden. Er wird in Ihrer Joomla-Konfigurationsdatei verwendet, daher ist es nichts, was Sie sich merken müssen. Verwenden Sie den Passwort-Generator, um ein unmerkbares Passwort zu erstellen, und kopieren Sie es in einen Texteditor - Sie werden es während der Joomla-Installation benötigen.

Im selben Formular gehen Sie zu *Benutzer zur Datenbank hinzufügen*. Wählen Sie den Benutzer, den Sie erstellt haben, und die Datenbank, die Sie erstellt haben, aus den Dropdown-Listen und klicken Sie dann auf die Schaltfläche Hinzufügen. Ein Formular zur Verwaltung der Privilegien öffnet sich. Wählen Sie das Kontrollkästchen *Alle Privilegien* und klicken Sie dann auf die Schaltfläche *Änderungen vornehmen*.

Das war's - Sie haben jetzt eine Datenbank bereit für die Joomla-Installation.

### Joomla-Quellcode hochladen

Zu einem bestimmten Zeitpunkt werden Sie die Joomla-Quellcode-Zip-Datei auf Ihren eigenen Laptop oder Desktop-Computer heruntergeladen haben. Sie müssen nun entscheiden, wie Sie Ihre Website strukturieren möchten. Das Dokumenten-Root für Ihre Seite ist der *public_html*-Ordner. Sie könnten Joomla dort platzieren. Das verhindert jedoch, dass Sie eine andere Anwendung auf derselben Seite verwenden. Zum Beispiel könnten Sie zwei völlig separate Joomla-Installationen haben, eine für die Produktion (öffentliche Ansicht) und eine für Tests (private Ansicht). Sie könnten also einen Ordner innerhalb von *public_html* erstellen, zum Beispiel namens *j4*, und Joomla dort hochladen. Sie könnten einen weiteren Ordner namens *j4test* haben und eine andere Kopie von Joomla dort platzieren. Die untenstehende Abbildung zeigt eine solche Einrichtung mit zwei Joomla-Websites.

![cpanel hosting file manager](../../../en/images/hosting/cpanel-hosting/02-cpanel-file-manager.png)

Wenn Sie sich für Ihre Struktur entschieden haben, wählen Sie den gewünschten Joomla-Ordner im Datei-Manager aus und klicken Sie auf die Schaltfläche Hochladen. Wählen Sie im Upload-Formular die Joomla-Quell-Zip-Datei auf Ihrem lokalen Computer aus, um sie in den ausgewählten Ordner hochzuladen. Nach dem Hochladen kehren Sie zum Datei-Manager zurück, wählen die *zip*-Datei und klicken auf die Schaltfläche Extrahieren. Nach dem Extrahieren können Sie die *zip*-Datei auswählen und löschen.

Das war's! Sie sind bereit, Joomla zu installieren.

*Übersetzt von openai.com*

