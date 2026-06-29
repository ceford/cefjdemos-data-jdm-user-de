<!--
{
  "source": "https://docs.joomla.org/Joomla_3.x_to_4.x_Step_by_Step_Migration",
  "title": "Joomla 3 zu 4 Schritt für Schritt ",
  "description": "", 
  "author": ""
}
-->

## Einführung

**Warnung:** Diese Anleitung setzt voraus, dass Sie mit Joomla 3.10.x beginnen. Wenn Sie eine frühere Version verwenden, stellen Sie sicher, dass Sie zuerst auf Joomla 3.10 upgraden, bevor Sie zu Joomla 4 wechseln. Es besteht kein Grund zur Eile. Stellen Sie sicher, dass alle Ihre Erweiterungen bereit für Joomla 4.x sind. Joomla 3.10.x wird bis zum 16. August 2023 unterstützt.

Im Folgenden finden Sie eine Schritt-für-Schritt-Anleitung, um eine 3.10.x-Seite auf Joomla! 4.x zu migrieren. Obwohl es Hunderte von verschiedenen Szenarien gibt, wird dies Ihnen die grundlegende Vorgehensweise zeigen. Sehr komplexe Migrationen resultieren wahrscheinlich aus installierten Drittanbieter-Erweiterungen. Es wird empfohlen, die Entwickler der auf Ihrer Joomla-Seite installierten Drittanbieter-Erweiterungen zu kontaktieren, um ihren Vorschlag für den Migrationspfad ihrer Erweiterungen zu erhalten.

## Schritt für Schritt

### Ein Entwicklungsstandort einrichten

1. Stellen Sie sicher, dass Sie die neueste Joomla 3.10.x-Version ausführen, bevor Sie fortfahren.
2. Machen Sie ein Backup Ihrer Live-Website 3.10.x. Sie können ein vorgeschlagenes Tool verwenden (siehe die *Vorgeschlagenen Tools* am Ende der Seite) oder dies manuell erledigen.
   - [Backup-Grundlagen für eine Joomla! Webseite](https://docs.joomla.org/Special:MyLanguage/Backup_Basics_for_a_Joomla!_Web_Site)
   - [Was sind die bewährten Verfahren für Site-Backups?](https://docs.joomla.org/Special:MyLanguage/What_are_the_best_practices_for_site_backups%3F)
3. Stellen Sie sicher, dass Ihre Umgebung die
   [technischen Anforderungen für Joomla 4](https://downloads.joomla.org/technical-requirements) erfüllt, bevor Sie fortfahren.
4. Erstellen Sie eine neue Datenbank und einen neuen Benutzer, um Ihre 3.10.x-Seite wiederherzustellen.
5. Erstellen Sie eine Testseite oder einen Entwicklungsbereich, um dort zu arbeiten, und stellen Sie das Backup Ihrer 3.10.x-Seite an einer der folgenden Stellen wieder her:
   - Eine Subdomain
   - Ein Unterverzeichnis
   - Ein lokales Gerät. Joomla hat ein ausführliches Tutorial zur Installation von XAMPP. Allerdings sind auch [WAMP](https://www.wampserver.com/en/), [MAMP](https://www.mamp.info/en/windows/) und [LAMP](https://sourceforge.net/projects/lampas/) geeignete Alternativen.
   - Ein neues Hosting-Konto auf einer temporären Domain im Root. (Wenn Sie während der Migration den Host wechseln möchten.)
     - Wiederherstellen einer Seite auf einem lokalen Gerät. Siehe [Installieren von Joomla lokal](https://docs.joomla.org/Special:MyLanguage/Installing_Joomla_locally) sowie [Einrichten des Arbeitsplatzes für die Joomla-Entwicklung](https://docs.joomla.org/Special:MyLanguage/Setting_up_your_workstation_for_Joomla_development).
     - Wiederherstellen einer Seite mit einem am Seitenende aufgeführten Tool. (Lesen Sie die Entwicklerdokumentation.)
6. Aktualisieren Sie in Ihrem Teststandort Ihre Joomla! 3.10.x-Instanz auf die neueste Wartungsversion.
7. Stellen Sie sicher, dass Ihr Datenbankschema auf die neueste Version 3.10.x aktualisiert ist, indem Sie auf die Registerkarte **Erweiterungs-Manager → Datenbank** gehen. Wenn Ihr Schema nicht aktuell ist, wie im folgenden Bild, klicken Sie auf die Schaltfläche **Reparieren**:<br>
   ![joomla 3 extensions database](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/01-admin-extension-database-fix.png)
8. Papierkorb leeren: Haben Sie noch Beiträge im Papierkorb? Wenn ja, löschen Sie sie (und alle zugehörigen Medien, die möglicherweise nicht an anderer Stelle auf der Seite verwendet werden). Beiträge (ebenfalls Kategorien und Menüelemente), die im Papierkorb verbleiben, können Probleme bei der Migration verursachen, sodass sie ohne Fehler abgeschlossen werden kann.
9. Testen.
10. Nochmals sichern.

### Jede Erweiterung bewerten

In Ihrer Planung haben Sie bestimmt, welche Drittanbieter-Erweiterungen bleiben oder entfernt werden sollen und wie sie migriert werden. Für diesen Abschnitt verwenden Sie zwei verschiedene Bereiche der Seite intensiv: den *Vorab-Update-Check* in **Komponenten → Joomla! Update** und **Erweiterungen → Verwalten → Verwalten**. Sie werden jede einzelne auf Ihrer Seite installierte Erweiterung untersuchen. Sie bestimmen, ob sie auf die neueste Version aktualisiert oder deinstalliert werden müssen. Weitere Details finden Sie im [Vorab-Update-Check](https://docs.joomla.org/Special:MyLanguage/:Pre-Update_Check).

1. Verwenden Sie den **Vorab-Update-Check**, um den Vorab-Update-Check zu nutzen, müssen Sie die Joomla! Update-Komponente auf Joomla 4 einstellen. Dazu folgen Sie:
2. Gehen Sie zu **Komponenten → Joomla Update**. Es sollte sagen, dass keine Updates gefunden wurden. Wenn nicht, aktualisieren Sie Joomla auf die neueste Version (muss 3.10.x sein) und testen Sie. Dann nochmal sichern. Klicken Sie auf die Schaltfläche Optionen in der oberen rechten Ecke.
3. Wählen Sie *Joomla Next* aus dem Dropdown-Menü für den Update-Kanal.<br>
   ![update options channel selection](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/02-update-options-channel.png)
4. Klicken Sie auf **Speichern & Schließen**.
5. Sie werden dann Ihre installierte Joomla-Version, die neueste Joomla!-Version und die URL für das Update-Paket sehen. Joomla wird Ihnen die Anforderungen erneut für Joomla 4 zeigen. Wenn es anzeigt, dass Sie ein inkompatibles System oder Erweiterungen haben, wird es Ihnen hier mitgeteilt. Nehmen Sie sich einen Moment Zeit, um diese Seite zu überprüfen.<br>
   ![update to 4 pre update check](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/03-update-to-4-pre-update-check.png)
   <div class="alert alert-warning"><strong>Hinweis:</strong> Aktualisieren Sie jetzt NICHT auf Joomla! 4.
   Dies dient nur dazu, Ihre Drittanbieter-Erweiterungen vorzubereiten und die Seite mit Joomla! 4 kompatibel zu machen.</div>
6. Schauen Sie sich den Vorab-Update-Check und den Erweiterungs-Vorab-Update-Check in der Registerkarte Vorab-Update-Check der Joomla Update-Komponente an. Wenn eine Erweiterung hier aufgeführt ist, die nicht in Ihrer Planung enthalten ist, fügen Sie sie Ihrer Liste der zu untersuchenden Erweiterungen hinzu.
7. Wenn Sie in der Vergangenheit von Joomla 2.5 auf 3.x migriert sind, gibt es möglicherweise einige übrig gebliebene Erweiterungen, die bereinigt werden müssen. Die folgenden sind ältere 2.5 oder 3.x-Erweiterungen, die vor dem Update auf Joomla 4 deinstalliert werden müssen:
   - plg_content_geshi
   - Bluestork Administrator Template
   - Beez_20
   - Beez5
   - Atomic
   1. Bei Vorlagen deinstallieren Sie alle Kern-Frontend- oder Backend-Vorlagen außer Protostar und Beez3 (Frontend-Vorlagen) und Isis oder Hathor (Administrator-Vorlagen). **HINWEIS: Protostar ist NICHT kompatibel mit Joomla 4**. Nach der Migration wird es verschwinden. Sie müssen eine Vorlage als *Standard* auswählen und können Protostar oder Beez3 verwenden. Protostar wird bei der Migration zu Joomla 4.x verschwinden.
   2. Wenn Sie auf andere Dateien stoßen, die deinstalliert werden müssen, fügen Sie sie bitte dieser Seite hinzu. Dies ist ein Wiki, sodass jeder die Seite ergänzen kann. Vielen Dank im Voraus für Ihren Einsatz.
8. Sie werden die Tags bemerken, ob eine Erweiterung kompatibel ist oder nicht. Diese Tags sagen in der Regel die Wahrheit, wenn sie Nein oder Ja sagen. Wenn sie *Fehlendes Kompatibilitäts-Tag* sagen, bedeutet das, dass der Erweiterungsentwickler kein Tag in seiner Erweiterung verwendet hat, sodass wir nicht wissen, ob es mit Joomla 4 kompatibel ist oder nicht. Sprechen Sie mit dem Entwickler zur Verifizierung.
9. **Erweiterungen aktualisieren:** Aktualisieren Sie alle Erweiterungen, die Sie auf Ihrer Website behalten möchten. In Joomla! 3.10.x können Sie zu **Erweiterungs-Manager → Registerkarte Aktualisieren** gehen und auf **Updates suchen** klicken, wodurch ein Tooltip in der Versionsspalte unter der Registerkarte Verwalten hinzugefügt wird, der einige Kompatibilitätsinformationen aus dem Backend liefert. Diese Funktionalität unterstützt nur Erweiterungen, die über die Registerkarte Erweiterungs-Manager aktualisiert werden. Wenn Sie Erweiterungen installiert haben, die das Joomla-Erweiterungsupdate nicht verwenden, müssen diese manuell bewertet werden, wie unten beschrieben. Dasselbe gilt für diese Erweiterungen, die einen Tooltip haben. Sie müssen dennoch die Art des Pakets und den Migrationspfad mit dem Erweiterungsentwickler prüfen, um zu verifizieren, wie ein Upgrade/Migration durchzuführen ist.
10. Untersuchen und Deinstallieren von Erweiterungen: Gehen Sie zu **Erweiterungs-Manager → Verwalten**
11. Klicken Sie auf die Schaltfläche *Suchtools*, um die Filteroptionen anzuzeigen.
12. Wählen Sie Paket aus dem Dropdown-Menü *Typ auswählen*.<br>
    ![extensions manage page](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/04-extensions-manage.png)
    <div class="alert alert-info">Es wird empfohlen, zuerst Paket auszuwählen, da, wenn es etwas gibt, das Sie in einem Paket deinstallieren müssen, es automatisch die zugehörigen Module, Plugins oder alles andere im Paket gleichzeitig deinstalliert.</div>
13. Deinstallieren Sie alle Pakete, die nicht mehr benötigt oder nicht nach Joomla 4 migriert werden.
14. Wiederholen Sie diesen Vorgang, indem Sie durch die Registerkarte Verwalten für alle Typen im Dropdown gehen: Komponente, Datei, Sprache, Bibliothek, Modul, Plugin und Vorlage. Wenn der Autor Joomla! Project angibt, lassen Sie diese Erweiterungen in Ruhe. Stellen Sie für alle anderen sicher, dass Sie diejenigen deinstallieren, die nicht verwendet oder nicht kompatibel mit Joomla! 4.x sind.
    <div class="alert alert-danger"><strong>HINWEIS!</strong> Sie werden keine Vorlage deinstallieren können, die als Standard festgelegt ist. Sie müssen eine unterstützte Kernevorlage wie Beez3 oder Protostar auswählen und dann die Vorlage deinstallieren, wenn Sie es tun müssen.
    <em>Ein weiterer Hinweis:</em> <strong>Protostar ist nicht mit Joomla 4 kompatibel</strong>. Nach der Migration wird es verschwinden. Die Auswahl als Standard bringt Sie einfach zu Joomla 4.x.</div>
15. Notieren Sie sich alle Versionen von Paketen und Komponenten, die derzeit ausgeführt werden und die Sie auf Ihrer Website behalten möchten. Sie können sie in ein Dokument kopieren/einfügen zur Referenz.
16. Für alle Erweiterungen, die Sie behalten, aber nicht den Erweiterungs-Manager für ein-Klick-Updates verwenden (**Erweiterungen → Verwalten → Aktualisieren**), aktualisieren Sie alle Erweiterungen auf die neuesten Versionen.
17. Vor und während des Updates notieren Sie, ob die Erweiterungen sowohl 3.10.x & 4.x-Versionen im selben Paket haben. Wenn ja, sind sie bereit, *ein-Klick-Updates* durchzuführen. Wenn nicht und 3.10 und 4.x unterschiedliche Pakete haben, müssen Sie sie Fall für Fall untersuchen. Sie fallen normalerweise in eine der folgenden Szenarien:
    - Die Erweiterung hat separate Pakete, aber beim Upgrade auf 4.x erkennen sie dies automatisch und funktionieren weiterhin. Stellen Sie sicher, dass der Entwickler dies bestätigt.
    - Die Erweiterung hat separate Pakete, die in 3.10.x deinstalliert und dann mit der Joomla 4.x-Version installiert werden müssen, sobald die Site migriert ist. Ein Beispiel könnte ein Inhalts-Plugin sein. Es ist sehr einfach, es in 3.10.x zu deinstallieren und dann erneut in 4.x zu installieren.
    - Siehe [Vorlage Überlegungen](https://docs.joomla.org/Special:MyLanguage/Template_Considerations_During_Migration) für spezifischere Informationen über Vorlagen und [Umwandlung einer vorherigen Joomla! Version Vorlage](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template).

#### Hinweise zur Suche (com_search)

Suche (com_search) wird in Joomla 4.x entkoppelt. Suche (com_search) wird zu Joomla 4 migriert. Nach der Migration müssen Sie sie auf die Joomla 4.x-Version über com_installer aktualisieren. Sie wird weiterhin gepflegt, jedoch mehr wie eine Drittanbieter-Erweiterung durch das Erhalten von Updates über com_installer. Es wird empfohlen, in Zukunft die Smartsuche (com_finder) zu verwenden. Die Suche ist weiterhin verfügbar im [Joomla! Extensions Directory](https://extensions.joomla.org/category/official-extensions/).

#### Hinweise zu Weblinks

Weblinks wurden bereits in Joomla 3.4 entkoppelt. Wenn sie auf einer 2.5-Seite verwendet wurde, würde der Migrationsprozess dies bemerken und die Weblinks-Komponente und -Daten migrieren. Bei der Migration von 3.10.x zu 4.x wird es dasselbe sein. Sie ist weiterhin verfügbar und im JED unter [Offizielle Erweiterungen](https://extensions.joomla.org/category/official-extensions) gepflegt.

#### Hinweise zum Legacy-Routing

Legacy-Routing wird in Joomla 4.x nicht verfügbar sein. Nur Modern wird verfügbar sein. Wenn Sie die Migration durchführen, wird das System, wenn Sie das Legacy-Routing verwenden, diese automatisch auf das Modern-Routing ändern. Sie sollten einen defekten Link-Checker auf Ihrer Website ausführen, nachdem Sie auf Joomla 4.x migriert sind und *bevor Sie live gehen*.

### Zu Joomla! 4.x wechseln

Sobald Sie entweder Ihre Drittanbieter-Erweiterungen aktualisiert oder deinstalliert haben, sodass nur diejenigen, die mit Joomla! 4 kompatibel sind, in Ihrer Installation verbleiben, fahren Sie mit den folgenden Schritten fort:

1. Gehen Sie zu **System → Globale Konfiguration → Server-Registerkarte** und ändern Sie die Fehlerberichterstattung von Systemstandard auf Maximum. Stellen Sie sicher, dass Sie auf Speichern & Schließen klicken.<br>
   ![system global configuration server tab](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/05-system-global-configuration-server-tab.png)
2. Machen Sie ein weiteres Backup.
3. Gehen Sie zu **Komponenten → Joomla Update**. (Es sollte sagen, dass keine Updates gefunden wurden. Wenn nicht, aktualisieren Sie Joomla auf die neueste Version und testen. Dann nochmal sichern.) Klicken Sie auf die Schaltfläche Optionen in der oberen rechten Ecke.
4. Wählen Sie *Joomla Next* aus dem Dropdown-Menü für den Update-Kanal.<br>
   ![component joomla update select update channel](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/06-update-select-channel.png)
5. Klicken Sie auf **Speichern & Schließen**.
6. Sie sehen dann Ihre installierte Joomla-Version, die neueste Joomla!-Version und die URL für das Update-Paket. Joomla zeigt Ihnen erneut die Anforderungen für Joomla 4 an. Wenn es anzeigt, dass Sie ein inkompatibles System oder Erweiterungen haben, wird es Ihnen hier mitgeteilt. Nehmen Sie sich einen Moment Zeit, um diese Seite zu überprüfen.<br>
   ![e update check for joomla 4](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/07-update-check.png)
7. Wenn das Update nicht angezeigt wird, gehen Sie zu **Erweiterungs-Manager → Update** und drücken Sie Cache löschen in der Symbolleiste. Jetzt sollte das Update auf Joomla! 4 angezeigt werden.
8. Drücken Sie die Daumen und stellen Sie sicher, dass Sie dieses Backup zur Verfügung haben, falls etwas schiefgeht.
9. Klicken Sie auf die Schaltfläche Installiere das Update.
10. Machen Sie Tee, während die Statusleiste vollständig grün wird. Die Zeit, die dies dauert, hängt von Ihrer Seite, Ihrer Internetverbindung und Ihrer Servergeschwindigkeit ab. Der Vorgang dauert etwa zwei Minuten. Wenn das Update abgeschlossen ist, werden Sie wahrscheinlich aus dem Administrator ausgeloggt. Melden Sie sich erneut an. Zweimal.
11. Wenn alles gut geht, gelangen Sie zu einem völlig neuen Look des Backend-Administrator-Panels.<br>
    ![joomla 4 or 5 home dashboard](../../../en/images/migration/joomla-3-x-to-4-x-step-by-step-migration/08-j4-home-dashboard.png)
12. Gehen Sie zu **System → Wartung → Datenbank** und klicken Sie auf *Reparieren*, wenn Fehler angezeigt werden.
13. Siehe **System → Installieren → Erkennen**, ob es Erweiterungen zum Installieren gibt. (Es sollten keine vorhanden sein!)
14. Gehen Sie zur Frontend Ihrer Seite und sehen Sie, ob sie angezeigt wird, auch wenn es nicht die richtige Vorlage ist. Wenn ja, fahren Sie fort. Wenn nicht, siehe häufige Fehler während der Migration.
15. Machen Sie ein Backup.
16. Installieren Sie Ihre neue Vorlage oder andere Erweiterungen, wenn Sie welche installieren müssen. Sichern Sie oft.
17. Konfigurieren Sie sie. Sichern Sie oft.
18. Führen Sie einen defekten Link-Checker aus und beheben Sie alle defekten Links.
19. Testen Sie alles. Sichern Sie oft.
20. Wenn alles wie erwartet funktioniert, ändern Sie die Fehlerberichterstattung wieder auf Systemstandard (**System → Globale Konfiguration → Server-Registerkarte**). Stellen Sie sicher, **Speichern & Schließen** zu klicken.

### Mit Ihrer Joomla! 4.x-Website live gehen

1. Wenn Sie bereit sind, live zu gehen, sichern Sie Ihre 3.10-Seite zum letzten Mal. Stellen Sie sie in einem Unterverzeichnis oder einer Subdomain wieder her, wenn Sie möchten.
2. Sichern Sie Ihre Joomla! 4.x-Seite und verschieben oder stellen Sie Ihre Joomla! 4.x-Seite in das Root-Verzeichnis zurück (oder ändern Sie die Nameserver, wenn Sie auf einer temporären Domain bei einem neuen Hosting-Konto-Root gearbeitet haben).
3. Testen Sie erneut.
4. Wenn Sie in der Vergangenheit Sicherheitsänderungen an der .htaccess-Datei vorgenommen haben, müssen Sie möglicherweise eine Zeile (oder Zeilen) in dieser Datei ändern, um auf die nächste Version von Joomla 4 zu aktualisieren. Bitte gehen Sie zu [Htaccess-Änderungen nach Joomla 4](https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4), um festzustellen, ob Sie Ihre Datei ändern müssen oder nicht.
5. Entfernen Sie die Joomla! 3.10-Seite innerhalb weniger Tage vom Server, es sei denn, Sie haben Ihre *robots.txt* Datei bearbeitet, um Suchmaschinen-Spider zu blockieren.
6. Entfernen Sie alle Entwicklungsseiten, mit denen Sie gearbeitet haben, oder halten Sie sie auf dem neuesten Stand, wenn sie eine aktuelle Version ausführen, um Hackversuche auf Ihrem Server abzuwenden.

Sollten sich während der Migration zu 4.x auf der 3.10-Seite Daten geändert haben, möchten Sie diese Daten auf die 4.x-Seite verschieben, bevor Sie live gehen. Sie können dies manuell tun (stellen Sie sicher, dass Sie dieselben Benutzer-IDs behalten - gehen Sie der Reihe nach vor) oder indem Sie eine [Drittanbieter-Erweiterung](https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export%20transfer%20tool/third-party%20extension/) verwenden.

## Vorgeschlagene Werkzeuge

- [Akeeba Backup](http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606) ist sehr beliebt für Backup und Wiederherstellung.
- Weitere [Backup-Werkzeuge](https://extensions.joomla.org/tags/backup/).

*Übersetzt von openai.com*

