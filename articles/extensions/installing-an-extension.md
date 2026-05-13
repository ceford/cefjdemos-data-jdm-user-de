<!--
{
  "source": "https://docs.joomla.org/Installing_an_extension",
  "title": "Eine Erweiterung installieren  ",
  "description": "", 
  "author": ""
}
-->

## Erweiterungsdokumentation

Bevor man beginnt, ist es immer sinnvoll, die Dokumentation zu einer Erweiterung zu lesen. Die meisten Erweiterungen haben Startseiten und Foren, und es ist eine gute Idee, diese zuerst anzusehen. Wenn eine README-Datei mit der Erweiterung enthalten ist, sollten Sie sie lesen. Es könnten spezielle Anweisungen zur Installation oder Konfiguration vorhanden sein.

## Systemerweiterungen installieren

Das Formular System / Installieren / Erweiterungen ist in der Hilfebildschirm recht gut dokumentiert. Was nicht so offensichtlich ist, ist, dass jede der Installationsmethoden ein Plugin ist. In den frühen Ausgaben von Joomla 4 war das Plugin "Installieren aus dem Web" an erster Stelle in der Liste, und es ist möglich, dass dies auch in aktualisierten Versionen noch der Fall ist. Diese Methode als erste zu haben, ist unpraktisch, wenn Sie normalerweise eine der anderen Methoden verwenden, da es ein paar Sekunden dauert, um Daten von der Joomla Extensions Directory-Website abzurufen.

Um die Reihenfolge zu ändern:

- Gehen Sie zu **Start-Dashboard / Plugins**
- Wählen Sie **installer** aus dem Filter **Typ auswählen**.
- Wählen Sie das **Sortierreihenfolge**-Icon, um die Sortiergriffe
  (vertikale Ellipse) anzuzeigen.
- Ziehen Sie das Element **Installer - Installieren aus dem Web** an das
  Ende der Liste.
- Gehen Sie zurück zu **System / Installieren / Erweiterungen**, um das Ergebnis anzusehen.

Sie sind dann bereit, eine der Standard-Installationsmethoden zu verwenden.

### Paketdatei hochladen

Für die meisten Erweiterungen und die meisten Benutzer wird das Verfahren wie folgt sein:

- Laden Sie die Erweiterung als Zip-Datei-Paket auf Ihren lokalen Rechner herunter.
- Wählen Sie im Backend Ihrer Joomla-Website (Administration)
  **System → Installieren → Erweiterungen**.
- Wählen Sie auf der Registerkarte **Paketdatei hochladen** die Schaltfläche *Datei durchsuchen*
  und wählen Sie das Erweiterungspaket auf Ihrem lokalen Computer aus oder ziehen Sie
  die Datei aus Ihrem Dateimanager.
- Der Upload- und Installationsprozess beginnt automatisch.
- Einige Erweiterungen können weitere Anweisungen zur Installation bieten.
- Beachten Sie, dass Module und Plugins normalerweise aktiviert werden müssen,
  bevor sie funktionieren.

### Installation aus Verzeichnis

Einige Erweiterungen können zu groß sein, um die Methode "Paketdatei hochladen" zu verwenden, normalerweise aufgrund eines Limits der *maximalen Dateiuploadgröße*, das von Ihrem Host festgelegt wird. In diesem Fall können Sie die Methode "Installation aus Verzeichnis" verwenden.

- Erstellen Sie ein temporäres Verzeichnis auf Ihrer lokalen Festplatte und entpacken Sie die
  Archivdatei der Erweiterung in dieses temporäre Verzeichnis.
- Laden Sie mit FTP die Inhalte dieses Verzeichnisses (einschließlich Dateien und
  Unterverzeichnisse) in das /tmp-Verzeichnis des Joomla-Root-Verzeichnisses auf Ihrem Server hoch, sodass
  Sie einen Pfad wie /tmp/acmeextension haben.
- Geben Sie im Feld Installationsverzeichnis das Serververzeichnis an, in das Sie
  die Dateien und Unterverzeichnisse des Pakets hochgeladen haben, zum Beispiel
  /home/username/public_html/tmp/acmeextension.
- Wählen Sie die Schaltfläche **Überprüfen und Installieren**, und Joomla! installiert
  den Inhalt des angegebenen Verzeichnisses.

### Installation aus URL

Anstatt eine Zip-Datei auf Ihren lokalen Computer herunterzuladen, können Sie einfach die
Download-URL verwenden. Joomla lädt die Zip-Datei direkt herunter und spart die Download-
und Upload-Schritte der vorhergehenden Methoden.

### Installation aus dem Web

Diese Option ermöglicht es Ihnen, eine Erweiterung direkt aus dem Joomla!
Extensions Directory zu installieren. Die anfängliche Liste ist in der Reihenfolge der Anzahl der Bewertungen, aber
Sie können nach Kategorie auswählen, um schnell eine Liste von Erweiterungen zu finden, die Ihren
Anforderungen entsprechen könnten.

## Systeminstallation entdecken

Wie im Hilfebildschirm beschrieben, ermöglicht die Funktion „Entdecken“ die Installation von Erweiterungen, die für einige Systeme zu groß sind, insbesondere in kostengünstigen Shared-Hosting-Umgebungen. Etwas, das möglicherweise nicht offensichtlich ist, ist, dass Sie möglicherweise Ordner an verschiedenen Stellen auf Ihrem Hosting-Service erstellen müssen, typischerweise:

- Laden Sie die Website-Dateien in siteroot/components/com_mybigcomponent hoch
- Laden Sie die Administrator-Dateien in siteroot/administrator/components/com_mybigcomponent hoch
- Laden Sie Medien (CSS und JavaScript) in siteroot/media/com_mybigcomponent hoch
- Laden Sie die Sprachdateien der Website in siteroot/language/en-GB hoch, falls sie sich nicht in einem Sprachordner im Komponentenverzeichnis der Website befinden.
- Laden Sie die Administrator-Sprachdateien in siteroot/administrator/language/en-GB hoch, falls sie sich nicht in einem Sprachordner im Komponentenverzeichnis des Administrators befinden.

Damit sollte „Entdecken“ die Komponente finden und die Installation ermöglichen, und es könnte tatsächlich funktionieren.

## System-Installationssprachen

Die Standardsprache ist Englisch GB. Sie kann weder entfernt noch installiert werden. Es mag nicht offensichtlich sein, aber jede Seite lädt zunächst die entsprechenden en-GB-Zeichenketten, um sicherzustellen, dass die von Entwicklern verwendeten Sprachschlüssel nicht in der Seitenausgabe erscheinen. Wenn die vom Benutzer ausgewählte Sprache nicht Englisch ist, wird die Benutzersprache geladen und überschreibt die englischen Zeichenketten. Wenn eine Sprache nicht vollständig übersetzt wurde, wird das Ergebnis eine Mischung aus Benutzersprache und englischen Zeichenketten sein. Dies mag seltsam aussehen, ist aber besser als eine Mischung aus Benutzersprache und Entwickler-Schlüsseln.

Wählen Sie aus der Liste der verfügbaren Sprachen diejenige aus, die Sie installieren möchten. Einige sind mit einem grünen Button gekennzeichnet, um anzuzeigen, dass sie auf dem aktuellen Stand der Joomla-Version sind. Andere sind mit einem gelben Button gekennzeichnet, um anzuzeigen, dass sie nicht ganz aktuell sind. Installieren Sie sie trotzdem. Möglicherweise sehen Sie an einigen Stellen englische Wörter, die eigentlich in Ihrer ausgewählten Sprache sein sollten. Dies könnte jedoch selten vorkommen.

*Übersetzt von openai.com*

