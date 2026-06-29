<!--
{
  "source": "https://docs.joomla.org/J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update",
  "title": "Datenbanktabellenstruktur",
  "description": "", 
  "author": ""
}
-->

## Gemeldete Fehler

Beim Aktualisieren von Joomla! muss die Tabellenstruktur der Datenbank auf dem neuesten Stand sein, bevor der Prozess starten kann. Die *Vorab-Überprüfung für Joomla* meldet einen Fehler, wenn dies nicht der Fall ist.

Wenn du jedoch zu **System → Wartung → Datenbank** gehst, ist kein Eintrag verfügbar. Dies wurde in mehreren Joomla! 4.x-Versionen gemeldet.

## Was ist die Ursache

Das Problem wird durch eine leere `#__schemas`-Tabelle in der Datenbank verursacht. Höchstwahrscheinlich tritt dies auf, wenn die Joomla!-Instanz nicht über das offizielle Joomla!-Installationsprogramm, sondern durch ein angepasstes Skript installiert wurde, das nicht alle erforderlichen Daten eingefügt hat.

## So beheben Sie das Problem

Sie können das Problem beheben, indem Sie den fehlenden Wert zur Tabelle hinzufügen. Verwenden Sie phpMyAdmin (oder einen anderen Datenbank-Client), und gehen Sie zur Tabelle `#__extensions`. Suchen Sie nach name='files_joomla' und notieren Sie die extension_id (in unserem Fall *211*).

Als Nächstes müssen Sie das neueste SQL-Skript kennen, das installiert ist. Gehen Sie zu `administrator/components/com_admin/sql/updates/mysql` und suchen Sie die Datei mit der höchsten Version. In diesem Beispiel nehmen wir an, dass *4.0.3-2021-09-05.sql* der Dateiname mit der höchsten Version ist. Jetzt müssen Sie dies in Ihrer Einfüge-Abfrage als zweiten Wert hinzufügen:

```sql
INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES (211, '4.0.3-2021-09-05');
```

oder für PostgreSQL:

```sql
INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES (211, '4.0.3-2021-09-05');
```

Ersetzen Sie `#__` mit Ihrem Datenbank-Präfix, bevor Sie die Anweisungen ausführen.

Wechseln Sie dann im Administrator-Menü zu **System → Wartung → Datenbank** und reparieren Sie die Tabellen.

Jetzt sollte das Update wie erwartet funktionieren.

*Übersetzt von openai.com*

