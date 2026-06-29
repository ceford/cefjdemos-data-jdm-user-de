<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=migration&filename=migration-basics.md",
  "title": "Grundlagen der Migration",
  "description": "", 
  "author": ""
}
-->

## Terminologie

Joomla-Dokumente verwenden verschiedene Begriffe, um den Wechsel von einer älteren zu einer neueren Version zu beschreiben:

* **Migration oder Mini-Migration** ist ein Begriff, der normalerweise für den Wechsel von einer älteren zu einer neueren *Major*-Version verwendet wird, manchmal über mehrere Zwischen-*Major*-Versionen hinweg.
* **Upgrade** ist ein Begriff, der normalerweise für den Wechsel von einer aktuellen Version zur nächsten Version in einer Abfolge von *Minor*-Versionen verwendet wird.
* **Update** ist ein Begriff, der normalerweise für den Upgrade-Prozess mit der Joomla-Update-Komponente verwendet wird. Es ist das Wort, das in der Administratoroberfläche in Joomla! 3, 4 und 5 zu sehen ist. Von nun an wird der Begriff *Update* in diesem Beitrag verwendet.

Es ist auch wichtig zu wissen, dass Joomla dem Standard der Semantischen Versionierung folgt. Kurz gesagt, bei einer Versionsnummer MAJOR.MINOR.PATCH, wie zum Beispiel 5.1.0:

* Die **MAJOR**-Version erlaubt Rückwärtsinkompatibilitäten.
* Die **MINOR**-Version erlaubt zusätzliche Funktionen in einer rückwärtskompatiblen Weise innerhalb der Major-Version.
* Die **PATCH**-Version erlaubt rückwärtskompatible Fehlerbehebungen.

Es kann zusätzliche Suffixe wie *alpha*, *beta* oder *rc* geben, jedoch nicht in stabilen Versionen, die für Produktivseiten gedacht sind.

## Gründe für ein Update

Die Gründe für ein Update sind zahlreich und vielfältig:

* **Sicherheit** Obwohl Joomla! als ein sehr sicheres CMS anerkannt ist, werden gelegentlich Schwachstellen entdeckt und in Minor- oder Patch-Releases behoben.
* **Änderungen im Hosting** Joomla verwendet die Skriptsprache *PHP* und einen Datenbankserver wie *MySQL*, *MariaDB* oder *PostGres*. Diese entwickeln sich weiter, und Hosting-Dienste müssen auf dem neuesten Stand bleiben. Daher kann es vorkommen, dass eine ältere Version von Joomla nicht mehr funktioniert oder ausfällt, wenn Sie den Hosting-Dienst wechseln.
* **Designänderungen** Sie möchten vielleicht, dass Ihre Website besser aussieht, besser mit mobilen Geräten funktioniert und bei Suchmaschinen eine höhere Punktzahl erzielt. Möglicherweise müssen Sie gesetzliche *Barrierefreiheits*-vorgaben erfüllen.
* **Funktionalität** Vielleicht möchten Sie eine Joomla-Erweiterung verwenden, die Funktionen bietet, die von den Joomla-Kern-Erweiterungen nicht bereitgestellt werden. Die Auswahlmöglichkeiten können durch Ihre aktuelle Major-Version eingeschränkt sein.

## Sicherung vor dem Update

**Das ist wirklich wichtig!** Selbst wenn Sie mehrere Zwischenaktualisierungen durchgeführt haben, ist es möglich, dass während des Aktualisierungsprozesses etwas schiefgeht. Dies kann dazu führen, dass Ihre Website nicht mehr funktioniert. Der Standardrat, der in den Foren angeboten wird, lautet: Kehren Sie zu Ihrem letzten Backup zurück, finden Sie heraus, warum das Backup fehlgeschlagen ist, beheben Sie das Problem und versuchen Sie es dann erneut.

**Akeeba Backup** ist ein kostenloses Tool, das im Joomla Extensions Directory (JED) erhältlich ist, auf das Sie direkten Zugriff über System / Erweiterungen installieren / Aus dem Web installieren haben. Es dauert nur ein oder zwei Minuten, um es herunterzuladen und zu installieren. Es analysiert Ihr System, um mit einem Konfigurationsassistenten ein Profil zu erstellen. Anschließend wird ein Backup erstellt, das Sie zur sicheren Aufbewahrung herunterladen können.

## Selbsteinschätzung

Bevor Sie ein *Major*- oder *Minor*-Versionsupdate durchführen, müssen Sie Ihr System und Ihre vorhandenen Drittanbieter-Erweiterungen auf Kompatibilität mit der Zielversion von Joomla überprüfen. Es ist eine gute Idee, eine Liste der installierten Drittanbieter-Erweiterungen zu erstellen. In Joomla 4 und 5 bietet die Liste *System / Erweiterungen / Verwalten* einen Filter zur Auswahl von **Nicht-Kern-Erweiterungen**. Dies ist in Joomla 3 nicht vorhanden.

Sie könnten auch den **Forum Post Assistant** verwenden. Dies ist ein Werkzeug, das dazu dient, eine Website zu analysieren und einen Bericht zu erstellen, der sich für das Posten in den Joomla-Foren eignet, um den Forumsexperten zu helfen, Probleme mit Ihrer Website zu diagnostizieren. Es hat jedoch eine private Benutzeroberfläche, die Ihnen alles über Ihre Website mitteilt. Seine Erweiterungslisten (Komponenten usw.) zeigen an, welche *Drittanbieter* sind.

Die Probleme, die bei Updates auftreten, stehen in der Regel im Zusammenhang mit Drittanbieter-Erweiterungen, die nicht mit der Zielversion von Joomla kompatibel sind. Sie sollten jede Erweiterung auf Kompatibilität prüfen und alle, die als inkompatibel bekannt sind, **deinstallieren**. Möglicherweise können Sie später kompatible Versionen installieren.

Sie sollten eines der standardmäßigen Site-Templates als Ihr **Standard-Template** festlegen:

* Joomla! 1.5 Standard-Templates sind Rhuk_milkyway, JA Purity, Beez.
* Joomla! 2.5 Standard-Templates sind Atomic, Beez3 und Beez25.
* Joomla! 3 Standard-Templates sind Protostar und Beez3.
* Joomla! 4 Standard-Template ist ausschließlich Cassiopeia.

## Lokales Testen

Wenn möglich, ist es am besten, eine lokale Testumgebung auf Ihrem Laptop oder Ihrer Heimarbeitsstation einzurichten, um Ihr Aktualisierungsverfahren zu testen. Sie können das Backup Ihrer Online-Seite verwenden, um Ihre Testseite zu füllen. Ihre Heimseite muss in der Lage sein, Ihre Kopie der Live-Seite auszuführen und muss über ausreichende PHP- und Datenbankspezifikationen verfügen, um die aktualisierte Seite zu betreiben. Es gibt einen separaten Beitrag, der beschreibt, wie man eine Heimtestumgebung einrichtet.

## Zusätzliche Informationen

Es gibt eine Reihe von Beiträgen, die spezifische Aktualisierungsszenarien beschreiben, die in diesem Handbuch nicht enthalten sind, da sie alt oder repetitiv sind.

* https://docs.joomla.org/Why_Migrate
* https://docs.joomla.org/Migration_Step_by_Step_Self_Assessment
* https://docs.joomla.org/J3.x:Updating_Joomla_(Install_Method)
* https://docs.joomla.org/J3.x:Updating_Joomla_(Update_Method)
* https://docs.joomla.org/Planning_Migration_-_Joomla_1.5_to_4
* https://docs.joomla.org/Planning_for_Migration
* https://docs.joomla.org/Pre-Update_Check
* https://docs.joomla.org/Template_Considerations_During_Migration
* https://docs.joomla.org/J3.x:Update_fails_with_an_error_message
* https://docs.joomla.org/Converting_an_existing_website_to_a_Joomla!_website
* https://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_4

*Übersetzt von openai.com*

