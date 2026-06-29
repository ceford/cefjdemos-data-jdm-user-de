<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "URL-Feld",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das URL-Feld bietet einen URL-Link zu einem anderen Dokument. Wenn Sie lieber ein Anker-Tag wie `<a href="url">Erklärungstext</a>` verwenden möchten, nutzen Sie ein Textfeld.

## Felderstellung

Besondere Optionen innerhalb dieses Feldes sind:

- **Schemes** Die erlaubten Schemes sind HTTP, HTTPS, FTP, FTPS, MAILTO, URL und FILE. Alle sind standardmäßig erlaubt. Alle in der Liste ausgewählten Schemes sind erlaubt, während nicht ausgewählte Schemes nicht erlaubt sind. Dies wird bei der Dateneingabe deutlich: Wenn ein nicht ausgewählter Typ eingegeben wird, zum Beispiel http://, erscheint eine Fehlermeldung und das Feld wird nicht gespeichert.
- **Relative** Verwenden Sie diese Option, um festzulegen, ob relative URLs erlaubt sind oder nicht.
- **URL anzeigen** Wenn auf *Nein* gesetzt, wird beim Anzeigen von Beiträgen die URL durch die Worte *Seite besuchen* ersetzt.

![url felderstellung](../../../en/images/fields/adding-custom-fields-url-field/01-fields-url-edit.png)

**Hinweis:** In diesem Beispiel dient die Aufnahme des Feldtyps im Titel nur zu Demonstrationszwecken. Lassen Sie es in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Einfach: Geben Sie einfach eine Ziel-URL ein.

![url Feld Dateneingabe](../../../en/images/fields/adding-custom-fields-url-field/02-fields-url-data-entry.png)

Make sure to adjust the image path if necessary.

## Datenanzeige

Der folgende Screenshot der Seite zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist für die Position des Feldes verantwortlich und Ihr Template ist für das Design des Feldes verantwortlich.

![url field site display](../../../en/images/fields/adding-custom-fields-url-field/03-fields-url-site.png)

Die URL folgt der Feldbezeichnung.

