<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Joomla 5 auf 6 Schritt f\u00fcr Schritt",
    "description": "",
    "author": ""
}
-->

<div class="alert alert-warning">
<p class="h3">Warnung</p>

Dieser Leitfaden geht davon aus, dass Sie mit Joomla 5.4.x beginnen. Wenn Sie eine frühere Version verwenden, stellen Sie sicher, dass Sie vor dem Upgrade auf Joomla 6.x auf Joomla 5.4.x migrieren oder aktualisieren.
</div>

## Einführung

Gute Nachrichten für Joomla 5.4.x bis 6.x: Es handelt sich um ein Upgrade, keine Migration. Warum? Zwei Hauptgründe:

- Erweiterungen für Joomla 5 (J5), bei denen alle veralteten Codebestandteile entfernt wurden, die aktuellen Joomla-Code verwenden und für die das Plugin „Verhalten – Abwärtskompatibilität“ nicht aktiviert sein muss, funktionieren in Joomla 6 (J6).
- Die meisten anderen funktionieren, wenn das neue Plugin „Verhalten – Abwärtskompatibilität 6“ aktiviert ist.

Diese Dokumentation trägt dem einfacheren Prozess Rechnung, indem sie die Planung und die Schritt-für-Schritt-Anleitung in einem Dokument zusammenfasst. Dennoch benötigen Sie einige Kenntnisse. Bitte lesen Sie die [[Migration Step by Step Self Assessment|Selbsteinschätzung]], um festzustellen, ob Sie das Upgrade selbst durchführen sollten oder nicht.

<div class="alert alert-info">
<p class="h3">Entwicklerdokumentation für Entwickler von Erweiterungen von Drittanbietern zum Upgrade von 5.4 auf 6.0.</p>

- [Entfernt und abwärtsinkompatibel](https://manual.joomla.org/60/removed-backward-incompatibility)
- [Neue veraltete Funktionen](https://manual.joomla.org/60/new-deprecations)
- [Dokumentation zu Migrationen](https://manual.joomla.org/migrations)
- [Neue Funktionen](https://manual.joomla.org/60/new-features/)
</div>

## Planung von 5.4.x auf 6.x

### Hosting/Technische Spezifikation

1. Stellen Sie fest, ob Ihre Hosting-Umgebung die Anforderungen erfüllt. Sie können 
nicht auf Joomla 6 aktualisieren, wenn Ihre Serverumgebung die [technischen Anforderungen](https://manual.joomla.org/docs/get-started/technical-requirements/) 
nicht erfüllt. Die Option zum Aktualisieren wird in der Joomla-Update-Komponente 
nicht angezeigt.
    - PHP 8.3
    - MySQL 8.0.13
    - MariaDB 10.6.x
    - PostgreSQL 14.0

Sie können Ihre Systeminformationen in einer Joomla-5-Website überprüfen, indem Sie auf System -> Systeminformationen klicken. Wenden Sie sich an Ihren Hosting-Anbieter, wenn Ihr Server die Anforderungen nicht erfüllt.

![System-Dashboard mit hervorgehobenem Link zu den Systeminformationen](../../../en/images/migration/joomla-5-to-6-steps/01-steps-5-to-6-system-dashboard.png)

Das Folgende ist ein Beispiel für eine Umgebung, die die technischen Anforderungen erfüllt. Es werden MySQL 8.0.43, PHP 8.3, Joomla 5.4.x und das deaktivierte Plugin für Abwärtskompatibilität angezeigt.![Systeminformationen mit Anzeige der Joomla-Version, PHP-Version, Datenbanktyp, Datenbankversion und deaktiviertem Abwärtskompatibilitäts-Plugin](../../../en/images/migration/joomla-5-to-6-steps/02-steps-5-to-6-system-information.png)

2. Überprüfen Sie alle Ihre Erweiterungen auf Kompatibilität mit Joomla 6. Für dieses Upgrade gibt es mehrere Szenarien für Erweiterungen von Drittanbietern.

    1. Die Erweiterung kann MIT und OHNE Verwendung des Abwärtskompatibilitäts-Plugins mit J5 und J6 kompatibel sein.
    2. Die Erweiterung kann MIT Verwendung des Abwärtskompatibilitäts-Plugins mit J5 und J6 kompatibel sein.
    3. Die Erweiterung scheint in J6 zu funktionieren, ist aber defekt, sobald Sie versuchen, sie zu verwenden.
    4. Die Erweiterung kann die gesamte Website lahmlegen.

Keine Sorge! Es ist nicht so schlimm, wie es klingt! Sprechen wir zunächst über die Abwärtskompatibilitäts-Plugins.

<div class="alert alert-warning">
<p class="h3">Warnung</p>

Für das Upgrade von Joomla 5.4.x auf 6.x MUSS das Abwärtskompatibilitäts-Plugin für Joomla 5 DEAKTIVIERT werden.
</div>

### Die Plugins für Abwärtskompatibilität

Das in Joomla 5.4.x enthaltene Plugin [Behaviour – Backward Compatibility 6](https://manual.joomla.org/60/compat-plugin/) dient dazu, die Abwärtskompatibilität zwischen Joomla 5 und Joomla 6 zu verbessern. Das Plugin unterstützt Erweiterungen von Drittanbietern bei der Verwendung von Klassen, die in Joomla 6 nicht mehr enthalten sind. Es ist als Plugin-Typ „Behaviour“ implementiert, um zu gewährleisten, dass es vor allen anderen Plugins geladen wird.

![Plugin-Seite mit den Plugins für Abwärtskompatibilität](../../../en/images/migration/joomla-5-to-6-steps/03-steps-5-to-6-bc-plugins.png)

Das obige Bild zeigt zwei Plugins für Abwärtskompatibilität:

1. Behaviour – Backward Compatibility und
2. Behaviour – Backward Compatibility 6

Das Plugin Behaviour – Backward Compatibility (ohne Zahl im Plugin-Namen) wird mit Joomla 4.4.x bereitgestellt, um eine Abwärtskompatibilitätsschicht für Joomla-5-Erweiterungen zu erstellen. **Dieses Plugin muss vor dem Upgrade auf J6 deaktiviert werden.**Das Plugin „Verhalten – Abwärtskompatibilität 6“ wird mit Joomla 5.4.x bereitgestellt, um eine Abwärtskompatibilitätsschicht für Joomla-6-Erweiterungen zu erstellen.

Beide können während des Upgrades auf J6 nicht aktiviert sein.

Vor dem Upgrade von Joomla 5 auf Joomla 6 muss das Plugin „Verhalten – Abwärtskompatibilität“ (ohne eine Zahl im Plugin-Namen) deaktiviert werden. Sie müssen sicherstellen, dass alle Erweiterungen von Drittanbietern auf Ihrer Website ausgeführt werden können, ohne dass das Plugin „Verhalten – Abwärtskompatibilität“ aktiviert ist, bevor Sie auf J6 upgraden können.

Nachdem Sie festgestellt haben, dass jede einzelne Ihrer Erweiterungen von Drittanbietern ohne aktiviertes Plugin „Verhalten – Abwärtskompatibilität“ in J5 kompatibel und voll funktionsfähig ist, können Sie es deaktivieren. Dennoch empfehlen wir, mit Vorsicht vorzugehen. Bevor Sie das Plugin für die Abwärtskompatibilität deaktivieren, empfiehlt es sich, eine der folgenden beiden Maßnahmen zu ergreifen:1. Führen Sie dies auf einer Entwicklungs-/Testseite durch. So führt es nicht zum Ausfall Ihrer Produktionsseite, wenn Sie versehentlich eine Erweiterung übersehen haben, durch die Ihr Backend nicht mehr zugänglich ist.
2. Stellen Sie sicher, dass Sie Zugriff auf die Datenbank haben. So können Sie das Plugin bei Bedarf schnell wieder über die Datenbank aktivieren. Weitere Informationen dazu finden Sie weiter unten.

Wenn Sie ein Upgrade auf J5.4.x durchführen, wird das Plugin „Verhalten – Abwärtskompatibilität 6“ automatisch aktiviert. Bei neuen Installationen von J6 ist das Plugin für die Abwärtskompatibilität standardmäßig deaktiviert.

Das Plugin „Verhalten – Abwärtskompatibilität 6“, das Erweiterungen unterstützt, die unter J5 funktionieren, bleibt während J6 verfügbar. In J7 werden J5-Erweiterungen durch das Plugin nicht mehr abwärtskompatibel gemacht. Dadurch erhalten Entwickler von Erweiterungen zwei zusätzliche Jahre, um ihre Erweiterungen ohne das Plugin für die Abwärtskompatibilität mit J6 kompatibel zu machen. Die Absicht ist, dass bei jeder Veröffentlichung eines Lebenszyklus ein Plugin für die Abwärtskompatibilität den vorherigen Lebenszyklus bis zum darauffolgenden Lebenszyklus unterstützt.Kann man das Plugin „Behaviour – Backward Compatibility 6“ in J6 deaktivieren? Gute Frage. Nachdem Sie festgestellt haben, dass alle Ihre Drittanbieter-Erweiterungen kompatibel und ohne aktiviertes Rückwärtskompatibilitäts-Plugin vollständig funktionsfähig sind, können Sie das Plugin „Behaviour – Backward Compatibility 6“ deaktivieren. Dennoch empfehlen wir, dabei vorsichtig vorzugehen. Bevor Sie das Plugin „Behaviour – Backward Compatibility 6“ deaktivieren, sollten Sie eine der folgenden beiden Maßnahmen ergreifen:

1. Tun Sie dies auf einer Entwicklungs-/Testwebsite. Falls Sie versehentlich eine Erweiterung übersehen haben, durch die Ihr Backend nicht mehr zugänglich ist, wird dadurch Ihre Produktivwebsite nicht beeinträchtigt.
2. Stellen Sie sicher, dass Sie Zugriff auf die Datenbank haben. So können Sie das Plugin bei Bedarf schnell wieder aktivieren. Weiter unten erfahren Sie mehr dazu.

### Vorab-Aktualisierungsprüfung oder Erweiterungen verwalten

Theoretisch würde Ihnen die Vorab-Aktualisierungsprüfung mitteilen, ob Ihre Erweiterungen von Drittanbietern mit J6 kompatibel sind. Die Vorab-Aktualisierungsprüfung ist jedoch nur hilfreich, wenn alle Erweiterungsentwickler ihre Erweiterungen so angepasst haben, dass deren Kompatibilität korrekt angegeben wird. In einer perfekten Welt würde der Abschnitt **Erweiterungen** der Vorab-Aktualisierungsprüfung Ihnen mitteilen, ob eine Erweiterung:

* ohne aktiviertes Abwärtskompatibilitäts-Plugin aktualisiert werden kann
* mit aktiviertem Abwärtskompatibilitäts-Plugin aktualisiert werden kann
* vor dem Upgrade von J5 auf J6 eine Aktualisierung der Erweiterung erfordert
* vollständig inkompatibel istTests haben Unterschiede zwischen kompatiblen und nicht kompatiblen Erweiterungen gezeigt. Dies ist kein Problem der Komponente für die Vorab-Update-Prüfung. Stattdessen übermitteln Erweiterungsentwickler über ihre Erweiterungen Informationen, anhand derer die Vorab-Update-Prüfung korrekt ausgefüllt wird. Wenn ihre Erweiterungen nicht so programmiert sind, dass sie der Vorab-Update-Prüfung die korrekten Informationen mitteilen, kann die Vorab-Update-Prüfung – und auch das Joomla!-Projekt – nur sehr wenig (nichts) dagegen tun. Eine gute Informationsquelle ist möglicherweise die Website des Entwicklers der Drittanbieter-Erweiterung, um zu überprüfen, wie die jeweilige Erweiterung während des Upgrades von J5 auf J6 behandelt werden sollte.

Das weiter unten in diesem Abschnitt gezeigte Bild zeigt ein Beispiel der Komponente für die Vorab-Update-Prüfung im Bereich „Erweiterungen“ von Joomla 5.4.x.

Im oberen Bereich werden die Erweiterungen angezeigt, für die ein Update erforderlich ist. Bitte gehen Sie zu System -> Aktualisierung -> Erweiterungen und aktualisieren Sie Ihre Erweiterungen.Der mittlere Abschnitt zeigt Erweiterungen, für die keine Informationen zu Aktualisierungen vom Erweiterungsentwickler verfügbar sind. Sie werden nicht wissen, ob diese kompatibel sind oder nicht, ohne sie zu testen oder den Entwickler zu kontaktieren.

Der untere Abschnitt zeigt die Erweiterungen, für die keine Aktualisierung erforderlich ist. Das bedeutet, dass die Erweiterungen Joomla mitteilen, dass sie mit Joomla 6 kompatibel sind. Es ist nicht angegeben, ob sie das Plugin für die Abwärtskompatibilität benötigen oder nicht.

Bitte beachten Sie, dass diese Erweiterungen vom Joomla-Projekt nicht bevorzugt werden. Diese Erweiterungen werden nur als Beispiel angezeigt. Sie wurden für einen Test zufällig aus dem JED ausgewählt.

![Abschnitt „Erweiterungen“ der Prüfung vor der Aktualisierung](../../../en/images/migration/joomla-5-to-6-steps/04-steps-5-to-6-pre-update-check.png)

Es wird empfohlen, nur den Bereich **Erweiterungen** der Komponente für die Prüfung vor der Aktualisierung als äußerst allgemeinen Überblick zu verwenden, jedoch nicht als 100%ig verlässliche Quelle. Anders ausgedrückt: Je nachdem, welche Erweiterungen Sie verwenden, können Sie der Komponente für die Prüfung vor der Aktualisierung möglicherweise nicht vertrauen.*Was ist dann die maßgebliche Quelle?* Systeme -> Erweiterungen verwalten

![System-Dashboard mit hervorgehobener Option „Erweiterungen verwalten“](../../../en/images/migration/joomla-5-to-6-steps/05-steps-5-to-6-system-dashboard-manage.png)

Auf der Seite „Erweiterungen: Verwalten“ können Sie alle auf der Website verwendeten Erweiterungen von Drittanbietern sehen. Im nachstehenden Screenshot sehen Sie die Hauptseite. In der Spalte „Autor“ sehen Sie in mehreren Zeilen den Namen eines bekannten Entwicklers von Erweiterungen. Außerdem sehen Sie in mehreren Zeilen den Autor des Joomla-Projekts.

![Die Hauptseite „Erweiterungen verwalten“](../../../en/images/migration/joomla-5-to-6-steps/06-steps-5-to-6-extensions-manage.png)

Überprüfen Sie Ihre Erweiterungen von Drittanbietern. Als Nächstes müssen Sie feststellen, ob sie mit J6 kompatibel sind (mit oder ohne das Plugin für Abwärtskompatibilität) oder nicht. Wenn sie nicht kompatibel sind, wird das Upgrade nicht erfolgreich sein.

### Drei Möglichkeiten, Ihre Erweiterungen von Drittanbietern auf J6-Kompatibilität zu prüfen

1. Überprüfen Sie die Website des Entwicklers.
2. Erstellen Sie ein Backup/eine Kopie Ihrer J5-Website, stellen Sie sie auf einer Subdomain wieder her, aktivieren Sie den Debug-Modus und führen Sie die unten beschriebenen Schritte aus, um auf J6 zu aktualisieren. Prüfen Sie, ob etwas nicht funktioniert. Falls etwas nicht funktioniert, deaktivieren Sie jede Erweiterung, die einen Fehler verursacht, und notieren Sie sich die jeweilige Erweiterung. Sie müssen den Entwickler diesbezüglich kontaktieren, da die Erweiterung nicht mit J6 kompatibel ist.
3. Installieren Sie ein sauberes J6-Paket auf einer Subdomain, aktivieren Sie das Plugin „Verhalten – Abwärtskompatibilität“, installieren Sie alle von Ihnen verwendeten Erweiterungen und prüfen Sie, ob sie funktionieren.

HINWEIS: Das Joomla!-Erweiterungsverzeichnis JED zeigt für Erweiterungen, die mit oder ohne Verwendung des Plugins für Abwärtskompatibilität kompatibel sind, entsprechende Abzeichen für die Kompatibilität mit Joomla 6 an.Sie könnten eine Kombination der oben genannten Möglichkeiten anwenden. Beginnen Sie mit einer sauberen Installation und testen Sie Ihre Erweiterungen. Wenn Sie wissen, welche funktionieren und welche nicht, können Sie mit den Entwicklern klären, wie weit sie mit ihrer Entwicklung für J6 sind. **DANN** wissen Sie, sobald alle Ihre Erweiterungen auf einer sauberen Website funktionieren, dass Sie ein vollständiges Upgrade von J5.4.x auf 6.x **testen** können.

Möglicherweise möchten Sie feststellen, ob eine Erweiterung funktioniert, ohne dass das Plugin für Abwärtskompatibilität aktiviert ist. Wenn das der Fall ist, benötigen Sie Zugriff auf die Datenbank. Planen Sie entsprechend. Stellen Sie sicher, dass Sie Zugriff auf die Datenbank haben.

Nach der Installation einer neuen J6-Installation ist das Plugin für Abwärtskompatibilität deaktiviert. Installieren Sie jede Erweiterung einzeln. Wenn dadurch Ihre Website ausfällt, aktivieren Sie das Plugin für Abwärtskompatibilität über die Datenbank.Das Plugin für die Abwärtskompatibilität befindet sich in der Datenbank in der Tabelle #__extensions. Es heißt plg_behaviour_compat6. Setzen Sie das Feld „Enabled“ auf 0, um das Plugin zu deaktivieren, und auf 1, um es zu aktivieren. Durch die erneute Aktivierung des Plugins für die Abwärtskompatibilität erhalten Sie möglicherweise wieder Zugriff auf das Backend von Joomla (solange die Erweiterung mit dem Plugin für die Abwärtskompatibilität funktioniert).

ODER

Sie können einzelne Erweiterungen in der Datenbank deaktivieren, damit Sie Ihre anderen Erweiterungen weiter testen können, um festzustellen, ob sie ohne aktiviertes Kompatibilitäts-Plugin funktionieren. Diese Einträge befinden sich in der Tabelle #__extensions. Ändern Sie das Feld „Enabled“ in 0, um die Erweiterung zu deaktivieren.In einigen Fällen müssen Sie, wenn Sie eine Erweiterung in J6 installieren, die bei aktiviertem oder deaktiviertem Rückwärtskompatibilitäts-Plugin nicht kompatibel ist, die Einträge für diese Erweiterung in der Datenbank (es können wenige oder viele sein) finden und deaktivieren, bis Sie wieder Zugriff auf das Backend haben. Diese Einträge befinden sich in der Tabelle `#__extensions`. Sie ändern das Feld „Enabled“ in 0, um die Erweiterung zu deaktivieren. Sobald Sie wieder auf das Joomla-Backend zugreifen können, können Sie sie ordnungsgemäß unter System -> Verwalten -> Erweiterungen deinstallieren. Fragen Sie anschließend beim Entwickler nach.

### Cassiopeia und Weblinks

#### Cassiopeia

Cassiopeia bleibt das Frontend-Template für Joomla 6. Ihre Anpassungen sollten weiterhin funktionieren. Dennoch empfehlen wir, sie auf einer Entwicklungswebsite zu testen, um sicherzugehen.

#### com_weblinks

Die Weblinks-Erweiterung funktioniert in J6 ohne aktiviertes Abwärtskompatibilitäts-Plugin ab Version 5.4.0:

- [Weblinks weiterentwickelt im JCM](https://magazine.joomla.org/all-issues/september-2025/joomla-weblinks-evolved-insights-from-gsoc-2025). 
- [Weblinks im JED](https://extensions.joomla.org/extension/weblinks/).

### Testlauf

Im Rahmen Ihrer Planung wird empfohlen, das Upgrade auf einer Subdomain oder lokal zu testen, um festzustellen, ob es einwandfrei funktioniert. Achten Sie darauf, alle Schritte zu dokumentieren, die Sie durchführen müssen, damit Ihr Upgrade **einwandfrei** abgeschlossen werden kann.

Sobald Sie Ihr Upgrade auf einer Subdomain oder auf Localhost getestet haben und es **einwandfrei** funktioniert, können Sie ein Backup Ihrer produktiven Website erstellen und das Upgrade dort durchführen. Eine Schritt-für-Schritt-Anleitung finden Sie weiter unten.

## Schrittweise Aktualisierung

Die Website, die Sie aktualisieren möchten, muss alle technischen Anforderungen erfüllen und Joomla 5.4.x ausführen, um aktualisiert werden zu können. Wenn Ihre Website noch nicht Joomla 5.4.x ausführt, aktualisieren Sie sie vor dem Upgrade auf J6 auf 5.4.x.

1. Befolgen Sie vor der Aktualisierung alle Anweisungen im Abschnitt „Planung“ (siehe oben).
2. **Sichern Sie Ihre Website.**
3. Aktualisieren Sie alle Erweiterungen, für die eine Aktualisierung erforderlich ist.
4. Deaktivieren oder deinstallieren Sie alle Erweiterungen, die nicht mit J6 kompatibel sind.
5. Aktivieren Sie den Debug-Modus (Globale Konfiguration -> Registerkarte „System“ -> Einstellung „System debuggen“ auf „Ja“ setzen).
6. **Sichern Sie Ihre Website erneut.**
7. **Testen Sie Ihre Sicherung, um sicherzustellen, dass sie wiederhergestellt werden kann.** (Ja, tun Sie das. Sie werden sich besser fühlen.)
8. Gehen Sie zu System -> Aktualisieren -> Joomla
![Das System-Dashboard mit hervorgehobener Option „Joomla aktualisieren“](../../../en/images/migration/joomla-5-to-6-steps/07-steps-5-to-6-system-dashboard-joomla.png)

9. Klicken Sie rechts in der oberen Symbolleiste auf die Schaltfläche „Optionen“.
![Die Joomla-Aktualisierungsseite mit hervorgehobener Schaltfläche „Optionen“](../../../en/images/migration/joomla-5-to-6-steps/08-steps-5-to-6-joomla-update.png)10. Ändern Sie den Aktualisierungskanal zu Joomla Next.
![Joomla-Aktualisierungsoptionen mit hervorgehobenem Aktualisierungskanal](../../../en/images/migration/joomla-5-to-6-steps/09-steps-5-to-6-joomla-update-options.png)
11. Klicken Sie in der oberen Symbolleiste auf Speichern & Schließen.
12. Wenn Ihr Server die technischen Spezifikationen erfüllt, wird der folgende Bildschirm mit Links in der linken Seitenleiste für Erforderliche Einstellungen, Empfohlene Einstellungen und Erweiterungen angezeigt.
![Vorabprüfung mit hervorgehobener Seitenleiste](../../../en/images/migration/joomla-5-to-6-steps/10-steps-5-to-6-pre-update-check-for-6.png)
13. Die Wahrscheinlichkeit ist hoch, dass Ihre Erforderlichen Einstellungen und Empfohlenen Einstellungen in Ordnung sind, da dieser Bildschirm nicht angezeigt wird, wenn Ihre Umgebung die technischen Anforderungen nicht erfüllt. Bei den Erweiterungen kann dies anders sein. Weitere Informationen finden Sie im Abschnitt unter Planung (oben) über die Vorabprüfung und darüber, warum sie möglicherweise kein grünes Häkchen anzeigt, aber dennoch alle kompatiblen Erweiterungen enthält. Sie haben Ihre Tests bereits durchgeführt (richtig?), wissen also bereits, ob sie kompatibel sind oder nicht.14. Das Plugin „Rückwärtskompatibilität 6“ ist in Joomla 5.4.x aktiviert. Um auf J6 zu aktualisieren, muss das Plugin „Verhalten – Rückwärtskompatibilität“ deaktiviert werden.
15. **Wenn Sie die Anweisungen unter Planung (oben) für den Testlauf nicht befolgt haben, halten Sie jetzt an, gehen Sie zurück zum Abschnitt Planung und befolgen Sie die Anweisungen. Die Planung ist der wichtigste Teil dieses Upgrades.**
16. Sobald Sie sicher sind, dass alle Ihre Erweiterungen mit J6 kompatibel sind, Sie das Upgrade getestet haben und das Ergebnis einwandfrei war, können Sie das Kontrollkästchen aktivieren, um die Warnungen zu potenziell inkompatiblen Erweiterungen zu bestätigen und mit der Aktualisierung fortzufahren. Klicken Sie im Popup-Fenster auf OK und anschließend auf die Schaltfläche Aktualisieren.
![Warnungen bestätigen – Hinweis](../../../en/images/migration/joomla-5-to-6-steps/11-steps-5-to-6-pre-update-warnings.png)
17. Anschließend werden Sie auf Ihrer Website erneut aufgefordert zu bestätigen, dass Sie ein Backup erstellt haben (was Sie getan und dessen Wiederherstellung Sie getestet haben).
![Seite „Hochladen und Aktualisieren“ für Joomla 6](../../../en/images/migration/joomla-5-to-6-steps/12-steps-5-to-6-upload-and-update.png)
18. Ihre Website führt das Upgrade auf J6 durch.
![Seite mit Upgrade-Fortschritt](../../../en/images/migration/joomla-5-to-6-steps/13-steps-5-to-6-joomla-update-progress.png)
19. Bei einem erfolgreichen Upgrade wird ein Bildschirm wie dieser angezeigt:
![Seite mit Update-Status, die den Erfolg anzeigt](../../../en/images/migration/joomla-5-to-6-steps/14-steps-5-to-6-joomla-update-success.png)
20. Oben rechts auf dem Bildschirm sehen Sie, dass Ihre Website jetzt Joomla 6 verwendet.
21. Testen Sie das Frontend Ihrer Website.
22. Testen Sie das Backend Ihrer Website.
23. Deaktivieren Sie das Debugging unter System -> Globale Konfiguration -> Registerkarte Server.
24. Beheben Sie bei Bedarf Probleme mit Ihrer neuen Smart Search.
25. Genießen Sie ein schönes Getränk und staunen Sie darüber, wie großartig Sie sind.

## Was tun, wenn etwas schiefgeht?

Wenn Sie alles im Vorfeld getestet haben, sollte das nicht passieren. Es ist jedoch möglich, dass sich etwas in der Umgebung geändert hat oder dass sich der Code einer Erweiterung zwischen dem Zeitpunkt Ihres Tests und Ihrem Upgrade geändert hat.

Da Sie Debug aktiviert haben, bevor Sie begonnen haben, sollten Sie die Erweiterung erkennen können, die das Problem verursacht, und sie deaktivieren können (dies muss möglicherweise über die Datenbank geschehen, wenn Sie nicht mehr auf das Backend zugreifen können, um sie zu deaktivieren). Auf diese Weise ist Ihre Website weiterhin betriebsbereit, während Sie herausfinden, was schiefgelaufen ist, und das Problem beheben.

Im schlimmsten Fall stellen Sie Ihr Backup wieder her, damit Sie Zeit haben, das Geschehene in einer Testumgebung zu untersuchen.

Database Fix kann einige Ihrer Probleme beheben. Navigieren Sie zum System-Dashboard und klicken Sie auf Database.

![System-Dashboard mit umrandetem Database-Link](../../../en/images/migration/joomla-5-to-6-steps/15-steps-5-to-6-system-dashboard-database.png)

Auf der Seite „Wartung: Datenbank“ werden alle Probleme mit der Datenbankstruktur Ihrer Website angezeigt. Aktivieren Sie das entsprechende Kontrollkästchen und klicken Sie anschließend in der oberen Symbolleiste auf die Schaltfläche „Struktur aktualisieren“.

![Wartungsseite der Datenbank mit einem angezeigten Problem](../../../en/images/migration/joomla-5-to-6-steps/16-steps-5-to-6-maintenance-database.png)

## Weitere Anlaufstellen für Hilfe

- [Joomla-Forum: Board „Migration & Upgrade“ 6.x](https://forum.joomla.org/viewforum.php?f=866&sid=47959551fb677ee3690f8b61eece277b)
- [Joomla-Community auf Mattermost](https://joomlacommunity.cloud.mattermost.com/main/channels/town-square)

*Übersetzt von openai.com*