<!--
{
  "source": "https://docs.joomla.org/J4.x:Media:_Uploading_SVG_files",
  "title": "Hochladen von SVG-Dateien ",
  "description": "", 
  "author": ""
}
-->

## Einführung

SVG-Dateien (Scalable Vector Graphics) werden in Joomla standardmäßig nicht unterstützt. Es sind einige Schritte erforderlich, um die Unterstützung im Medienkomponent zu ermöglichen.

## Medienoptionen

Im Administrator-Menü:

* Wählen Sie **Medien** aus dem *Start-Dashboard* oder aus dem *Inhalt*-Menü.
* Wählen Sie die **Optionen**-Taste in der Medien-*Symbolleiste*.

Es gibt 3 Felder, die aktualisiert werden müssen. Alle sind kommaseparierte Listen, sodass Sie einfach ein Komma und den entsprechenden Wert hinzufügen müssen:

- In *Erlaubte Erweiterungen* fügen Sie am Ende der bereits vorhandenen Liste hinzu: `,svg`.
- In *Zulässige Bildformate* fügen Sie am Ende der bereits vorhandenen Liste hinzu: `,svg`.
- In *Zulässige MIME-Typen* fügen Sie am Ende der bereits vorhandenen Liste hinzu: `,image/svg+xml`.
- **Speichern & Schließen**

Ab jetzt sollten Sie in der Lage sein, SVG-Dateien in den Medien-Manager hochzuladen. Es sei denn...

## Joomla verhindert immer noch das Hochladen von SVG-Dateien?

SVG ist kein Rasterbildformat (wie PNG-Dateien, die Pixel enthalten), 
es wird in XML (Extensible Markup Language) geschrieben. Es ist textbasiert, direkt 
im DOM (Document Object Model) verwendbar, CSS kann Eigenschaften ändern und 
JavaScript kann Interaktivität hinzufügen.

Als solches sind SVG-Dateien anfällig für alle XML-bezogenen Angriffsmuster:

- Cross-Site Scripting – oder XSS (durch sein `<script>`-Tag und Ereignisse).
- HTML-Injektionen (durch das `<foreignObject>`-Element – foreignObject erlaubt 
die Einbindung von Elementen aus einem anderen XML-Namespace).
- Denial of Service (wenn das `<xlink:href>`-Element missbraucht wird).

Ab Joomla 4.1 wird ein Desinfektionstool verwendet, um den Inhalt jeder 
SVG-Datei zu überprüfen, die über den Medien-Manager hochgeladen wird. Die Regeln 
sind streng und stellen sicher, dass Dateien die Seite nicht schädigen können. Daher 
kann es notwendig sein, einige Dateien manuell **zu bereinigen** (denken Sie daran, 
SVG-Dateien sind Textdateien und können in einem Texteditor bearbeitet werden) oder 
mit einem externen Tool, bevor sie erfolgreich hochgeladen werden können.

**Tipp:** Diese Websites bereinigen SVG-Dateien, die in *Inkscape* erstellt wurden:

* [SVG Sanitizer Test](https://svg.enshrined.co.uk/)
* [SVG Cleaner & Optimizer](https://iconly.io/tools/svg-cleaner)
* [SVGminify.com](https://www.svgminify.com/)

*Übersetzt von openai.com*

