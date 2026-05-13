<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=extensions&filename=vulnerable-extensions.md",
  "title": "Verwundbare Erweiterungen  ",
  "description": "", 
  "author": ""
}
-->

## Erweiterungsquellen

Jeder kann eine Joomla!-Erweiterung schreiben und verbreiten, um der globalen Gemeinschaft zu dienen. Solche **Drittanbieter**-Erweiterungen können auf den Websites von professionellen Erweiterungsentwicklern, persönlichen Blog-Websites, GitHub und ähnlichen Repositories sowie der Joomla Extensions Directory-Website gefunden werden.

## Verwundbare Erweiterungen

Sehr wenige Quellen bieten absichtlich bösartige Erweiterungen an. In der Regel ist eine **verwundbare Erweiterung** eine, bei der nach der Erstveröffentlichung festgestellt wurde, dass sie eine Sicherheitslücke enthält oder dazu beiträgt.

Verwundbare Erweiterungen sind nicht unbedingt schlecht programmiert. Da sich das Web weiterentwickelt, ändern sich technische Anforderungen und allgemein akzeptierte Programmierpraktiken. Aktive Projekte veröffentlichen neue Versionen ihrer Erweiterungen, sobald sich die Anforderungen ändern, und beheben schnell gemeldete Schwachstellen.

Wenn Sie sich über eine Ihrer Erweiterungen Sorgen machen, sollten Sie die Joomla Liste der verwundbaren Beiträge (VEL) konsultieren, die Informationen zu über 240 meist älteren Erweiterungen enthält.

## Der JED Checker

Wenn Sie sich über eine Erweiterung sorgen, die nicht im VEL erscheint, können Sie den JED Checker verwenden. Dies ist eine Erweiterung, die dazu genutzt wird, die zur Aufnahme in die Joomla Extensions Directory-Liste eingereichten Erweiterungen zu überprüfen. Sie wird wie jede andere Erweiterung installiert. In der Anwendung akzeptiert sie eine Erweiterungs-Zip-Datei und untersucht deren Inhalt auf die Einhaltung der JED-Standards. Sie ist äußerst nützlich, selbst für Erweiterungen, die nicht in der JED-Liste erscheinen. Hier ist ein Beispiel-Screenshot:

![jed checker Ergebnis](../../../en/images/extensions/vulnerable-extensions/01-extensions-jed-checker.png)

Die 400 PHP-Dateien ohne GPL-Lizenzhinweis befinden sich in Drittanbieter-Bibliotheken mit einer anderen Lizenz. Die 30 Dateien, die vom Joomla Anti-Malware Scan Script identifiziert wurden, sind ebenfalls in diesen Drittanbieter-Bibliotheken. Es gibt Arbeit an den Dateien, die die JEXEC-Sicherheit fehlt!

## Entfernen einer anfälligen Erweiterung

### Erstellen Sie eine Liste der zu entfernenden Dateien

Wenn Sie es finden können, lesen Sie die XML-Datei der Erweiterung, um genau festzustellen, welche Verzeichnisse, Dateien und Datenbanktabellen Ihrem System hinzugefügt wurden. Die XML-Datei befindet sich im ursprünglichen Zip-Archiv, das während des Installationsprozesses der Erweiterung verwendet wurde. Zum Beispiel würde das Zip-Archiv für eine Erweiterung namens mod_vulnerable eine XML-Datei namens mod_vulnerable.xml enthalten und könnte eine Liste von Dateien wie die folgende enthalten:

```
    mod_vulnerable.php
    mod_vulnerable/vulnerable_file.txt
    mod_vulnerable/another_vulnerable_file.txt
    mod_vulnerable/yet_another_vulnerable_file.txt
    mod_vulnerable/index.html
```

### Deinstallation über den Joomla Installer

Verwenden Sie den Installer im Joomla! Administrator-Backend, um die anfällige Erweiterung zu deinstallieren. Möglicherweise müssen Sie auch zugehörige Module, Komponenten oder Plugins deinstallieren.

### Überprüfen Sie, ob der Deinstallationsprozess abgeschlossen war

Vertrauen Sie nicht darauf, dass die Erweiterung alle ihre Dateien sicher entfernt. Vergleichen Sie Verzeichnisse und Dateien auf Ihrem System mit der XML-Liste der Erweiterung, um sicherzustellen, dass alle zugehörigen Dateien tatsächlich entfernt wurden.

### Optional: Entfernen Sie die zugehörigen Datenbanktabellen

Überprüfen Sie Ihre Datenbank und entfernen Sie alle von der Erweiterung erstellten Tabellen. Um den Upgrade-Prozess auf neue Versionen zu erleichtern, entfernen viele Deinstallationsskripte keine zugehörigen Datenbanktabellen. Sie finden die Liste der Tabellen in jeder XML-Datei der Erweiterung.

Wenn Sie eine sicherere, kompatible Version derselben Erweiterung installieren möchten und vorhandene Daten wiederverwenden wollen, können Sie die Datenbanktabellen in der Regel belassen, wie sie sind.

### Entfernen Sie Menülinks

Einfach nur die Menülinks zu einer Erweiterung zu entfernen oder ein Modul zu deaktivieren, reicht **nicht** aus, um Ihre Seite zu schützen! Solange die Dateien der Erweiterung auf Ihrem Server existieren, sind Sie anfällig. Beachten Sie, wie ein Angreifer in den folgenden Beispielen die Joomla! Index-Datei umgehen kann, um direkt auf jede Datei einer beliebigen Erweiterung zuzugreifen.

```
    www.ihre_seite.org/components/com_bad_component/vulnerable_file.php
    www.ihre_seite.org/modules/mod_bad_module/vulnerable_file.php
```

*Übersetzt von openai.com*

