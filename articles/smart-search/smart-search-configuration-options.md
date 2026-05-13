<!--
{
  "source": "https://docs.joomla.org/Smart_Search_configuration_options",
  "title": "Intelligente Suchoptionen ",
  "description": "", 
  "author": ""
}
-->

## Über Optionen

Optionen ermöglichen es Ihnen, die globalen Einstellungen der Smart Search zu verwalten. Die Optionseinstellungen werden von Ansichten geerbt, aber die Einstellungen in einem Menüpunkt überschreiben die globalen Einstellungen.

Das Optionsfeld ist in zwei Teile unterteilt. Wenn Sie die Anpassungen abgeschlossen haben, wählen Sie die Schaltfläche Speichern, andernfalls wählen Sie die Schaltfläche Abbrechen, um Änderungen zu verwerfen.

## Suchoptionen

Die Suchoptionen steuern das Verhalten der Suchformulare und Suchergebnisse für die Finder-Frontend.

- **Ergebnisbeschreibung** - Diese Option steuert, ob Suchergebnisse mit Beschreibungen angezeigt werden sollen. Standardmäßig auf Anzeigen eingestellt.
- **Beschreibungs-Länge** - Diese Option steuert die maximale Zeichenlänge der Suchergebnisbeschreibungen. Die Beschreibungen werden auf die maximale Länge abgeschnitten, wobei das Abschneiden immer beim letzten Leerzeichen erfolgt, um nicht mitten in einem Wort abzuschneiden. Nur wirksam, wenn die Option Ergebnisbeschreibung auf Anzeigen eingestellt ist. Standardmäßig auf 255 Zeichen eingestellt.
- **Ergebnis-URL** - Diese Option steuert, ob Suchergebnisse mit URLs unterhalb der Beschreibung (falls aktiviert) angezeigt werden sollen. Standardmäßig auf Anzeigen eingestellt.
- **Erweiterte Suche** - Diese Option steuert, ob die erweiterten Suchoptionen angezeigt werden sollen. Standardmäßig auf Anzeigen eingestellt.
- **Erweiterte Suche erweitern** - Die erweiterten Suchoptionen werden in einem klappbaren Container gehalten. Diese Option steuert, ob der Container für erweiterte Suchoptionen standardmäßig erweitert sein soll. Standardmäßig auf Nein.
- **Datumsfilter** - Diese Option steuert, ob die Datumsfilter in den erweiterten Suchoptionen angezeigt werden sollen. Standardmäßig auf Ausblenden eingestellt.
- **Ergebnisetiketten** - Diese Option steuert, ob Suchergebnisse mit Etiketten angezeigt werden sollen. Erfordert, dass JXtended Labels installiert ist. Standardmäßig auf Anzeigen eingestellt.
- **Suchbegriffe hervorheben** - Diese Option steuert, ob Suchbegriffe in den Suchergebnissen hervorgehoben werden sollen. Standardmäßig auf Ja.

## Index-Optionen

Die Index-Optionen steuern das Verhalten des Indexers, der zur Verarbeitung und Analyse von Inhalten für die Suche verwendet wird. Die meisten Einstellungen wie der Gewichtsmultiplikator und die Stemmer-Optionen führen nicht zu sofortigen Änderungen, da sie während der Indizierung verwendet werden und die Auswirkungen dieser Änderungen erst sichtbar werden, nachdem der Index gelöscht und erneut ausgeführt wurde.

- **Größe des Indexer-Batches** - Diese Option steuert die Größe des Indexer-Batches. Der Smart Search-Indexer teilt den gesamten Indizierungsprozess in mehrere Batches auf, um die Serverbelastung zu verringern und die Speicher- und Ausführungszeitlimits von PHP zu vermeiden. Wenn die zu indizierenden Inhalte besonders kurz sind und/oder der Server besonders schnell ist, kann der Indexer mehr Beiträge pro Batch verarbeiten. Wenn die zu indizierenden Inhalte jedoch besonders lang sind und/oder der Server besonders langsam ist, muss der Indexer weniger Beiträge pro Batch verarbeiten. Standardmäßig 50.
- **Speichertabellenlimit** - Diese Option steuert das Speichertabellenlimit. Der Smart Search-Indexer verwendet MySQL-Speichertabellen, um Inhaltsdaten vorübergehend zu speichern, anstatt die Daten in den Speicherpuffern von PHP zu speichern, da große Inhaltsobjekte schnell die Standard-Speicherlimit-Einstellungen von PHP erschöpfen würden. Allerdings haben auch MySQL-Speichertabellen anpassbare Größenlimits, deren Anpassung nicht zuverlässig ist. Diese Einstellung dient dazu, mit kleiner als üblich bemessenen Speichertabellen umzugehen und sollte nur angepasst werden, wenn während der Indizierung "Tabelle voll" Fehler auftreten. Standardmäßig 30.000. Wenn Sie auf "Tabelle voll" Fehler stoßen, versuchen Sie, diesen Parameter **zu reduzieren**. Der optimale Wert sollte zu Speichertabellen führen, die etwas kleiner sind als der <a href="http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_max_heap_table_size" rel="nofollow noreferrer noopener"><em>max_heap_table_size</em></a> Parameter in MySQL, der standardmäßig 16 Megabyte beträgt.
- **Gewichtsmultiplikator für Titeltext** - Diese Option steuert, wie stark der Titeltext den gesamten Relevanzwert eines Suchergebnisses beeinflusst. Standardmäßig 1,7.
- **Gewichtsmultiplikator für Body-Text** - Diese Option steuert, wie stark der Body-Text den gesamten Relevanzwert eines Suchergebnisses beeinflusst. Standardmäßig 0,7.
- **Gewichtsmultiplikator für Meta-Daten** - Diese Option steuert, wie stark der Meta-Daten-Text den gesamten Relevanzwert eines Suchergebnisses beeinflusst. Standardmäßig 1,2.
- **Gewichtsmultiplikator für Pfadtext** - Diese Option steuert, wie stark der Pfad/URL-Text den gesamten Relevanzwert eines Suchergebnisses beeinflusst. Standardmäßig 2,0.
- **Gewichtsmultiplikator für sonstigen Text** - Diese Option steuert, wie stark der sonstige Text den gesamten Relevanzwert eines Suchergebnisses beeinflusst. Standardmäßig 0,3.
- **Stemmer** - Diese Option steuert, welcher Sprach-Stemmer während der Indizierung verwendet werden soll. Der "nur Englisch" Stemmer ist eine reine PHP-Implementierung, die keine Abhängigkeiten hat. Der Snowball Stemmer erfordert die Stem PHP-Erweiterung, bietet jedoch Unterstützung für 14 Sprachen, darunter Dänisch, Deutsch, Englisch, Spanisch, Finnisch, Französisch, Ungarisch, Italienisch, Norwegisch, Niederländisch, Portugiesisch, Rumänisch, Russisch und Türkisch. Standardmäßig nur Englisch.
- **Protokollierung aktivieren** - erstellt während des Indexprozesses eine Protokolldatei. Standardmäßig nein.

*Übersetzt von openai.com*

