<!--
{
  "source": "https://docs.joomla.org/Setting_up_automatic_Smart_Search_indexing",
  "title": "Intelligente Suchindizierung ",
  "description": "", 
  "author": ""
}
-->

## Automatisches Indexieren

Obwohl der Smart Search-Index automatisch aktualisiert wird, wenn Inhaltsobjekte geändert werden, gibt es einige Umstände, unter denen Sie den Indexer erneut ausführen müssen. Dies können Sie manuell mit der Schaltfläche "Index" in der Smart Search: Indizierter Inhalt-Seite tun. Wenn Sie jedoch Inhalte automatisch neu indizieren müssen, ist es auch möglich, den Indexer von der Befehlszeile auszuführen. Dies macht es besonders bequem, den Indexer aus einem *cron*-Job heraus auszuführen.

Aus dem CLI-Verzeichnis lautet der Befehl:

```
php joomla.php finder:index
```

Typische Ausgabe des Befehlszeilen-Indexers sieht wie folgt aus:

    Smart Search INDEXER
    ============================

    Starten des Indexers
    Einrichten der Finder-Plugins
    154 Beiträge in 0,094 Sekunden eingerichtet.
     * Batch 1 in 0,213 Sekunden verarbeitet.
     * Batch 2 in 0,182 Sekunden verarbeitet.
     * Batch 3 in 0,177 Sekunden verarbeitet.
     * Batch 4 in 0,009 Sekunden verarbeitet.
    Gesamtverarbeitungszeit: 0,676 Sekunden.

## Bereinigung vor der Indizierung

Normalerweise aktualisiert das Ausführen des Indexers den Index inkrementell. Das bedeutet, dass nur die Indexeinträge für die Inhaltsobjekte aktualisiert werden, die sich seit der letzten Aktualisierung des Indexes geändert haben. Wenn Sie jedoch alle vorhandenen Indexeinträge vollständig löschen müssen, bevor Sie den Index vollständig neu erstellen, müssen Sie eine "Bereinigung und dann Indizierung"-Operation durchführen. Dazu können Sie das Argument `--purge` zur Befehlszeile hinzufügen, so:

    php joomla.php finder:index --purge

Beachten Sie, dass dies versucht, alle von Ihnen eingerichteten statischen Filter zu bewahren, während das Klicken auf die "Bereinigen"-Schaltfläche in der Administrator-Toolbar Ihre statischen Filter **nicht** bewahren wird.

## Einrichten eines *cron*-Jobs

Obwohl die Details den Rahmen dieses Beitrags sprengen, müssen Sie im Allgemeinen lediglich den oben genannten Befehl in den *cron*-Job-Manager eingeben und die Zeit oder Zeiten angeben, zu denen der Job ausgeführt werden soll. Wahrscheinlich müssen Sie den vollständigen Pfad zum Indexer angeben. Zum Beispiel so:

    php /var/www/myjoomla/cli/joomla.php finder:index --purge

Und möglicherweise den vollständigen Pfad zur php-Datei, wie etwa `/usr/local/opt/php@8.2/bin/php`.

## Speicherprobleme

Wenn Ihre Website besonders komplexe Indexierungsanforderungen hat, ist es möglich, dass die standardmäßige Speicherzuweisung nicht ausreicht, damit der Indexierer vollständig ausgeführt werden kann. Sie können den dem Kommandozeilen-Indexierer zugewiesenen Speicher erhöhen, indem Sie einen zusätzlichen Parameter in der Kommandozeile verwenden, wie folgt:

    php -d memory_limit=256M joomla.php finder:index

Ersetzen Sie `256M` durch den für Ihre Gegebenheiten passenden Wert.

Der Kommandozeilen-Indexierer verwendet dieselben Parameter wie der Indexierer auf der Smart Suche: Indizierte Inhalte-Seite. Sie können die Parameter mithilfe der Schaltfläche Optionen in der Toolbar auf dieser Seite ändern. Beachten Sie, dass sowohl das Feld **Indexer Batchgröße** als auch das Feld **Limits für die Speichertabelle** die Menge des vom Indexierer verwendeten Speichers beeinflussen.

