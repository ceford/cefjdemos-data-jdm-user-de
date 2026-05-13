<!--
{
  "source": "https://docs.joomla.org/J6.x:Media_File_Locations",
  "title": "Mediendatei-Standorte ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Standardmäßig speichert Joomla sowohl Benutzerbilder als auch Dokumentdateien im Ordner */images* der Joomla-Installation. Links zu solchen Medien werden nicht direkt von Joomla verarbeitet. Der Webserver sendet sie, wenn sie vom Browser angefordert werden.

Wenn Sie viele Dokumente haben, möchten Sie diese möglicherweise in einem separaten Ordner aufbewahren, am offensichtlichsten in einem */files*-Ordner, ebenfalls im Root-Verzeichnis der Joomla-Website.

Um einen Ort für Dateien einzurichten, der getrennt von Bildern ist, erstellen Sie zuerst einen neuen Ordner im Root-Verzeichnis Ihrer Installation, zum Beispiel **files**. Denken Sie daran, dass es Teil eines URL-Links sein wird, also verwenden Sie kleingeschriebene Buchstaben und keine Leerzeichen oder Satzzeichen.

### FileSystem - Lokales Plugin

Finden Sie das *FileSystem - Lokales* Plugin in der Liste der Plugins und öffnen Sie es. Fügen Sie Ihren neu erstellten *files*-Ordner zur Liste der Orte hinzu, an denen Sie Medien aufbewahren können. Klicken Sie einfach auf die + Schaltfläche und wählen Sie **files** aus der Liste der verfügbaren Ordner.

![Dateisystem-Plugin](../../../en/images/media/media-file-locations/01-plugin-group-file-system-local.png)

Die **Miniaturbilder erstellen**-Option auf **Ja** gesetzt, führt zur Erstellung von kleinen Bildern mit einer maximalen Höhe oder Breite von 200 Pixeln in media/cache/com_media/thumbs mit der gleichen Ordnerstruktur wie der Medienordner. Dies sollte die Anzeigegeschwindigkeit eines Ordners mit vielen Bildern erheblich erhöhen. Für Dateien ist dies nicht notwendig, da sie durch Symbole dargestellt werden.

Stellen Sie sicher, dass das Plugin aktiviert ist. **Speichern & Schließen**.

*Übersetzt von openai.com*  

