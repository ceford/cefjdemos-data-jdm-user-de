<!--
{
  "source": "https://docs.joomla.org/https:",
  "title": "Beste Praktiken",
  "description": "", 
  "author": ""
}
-->

## Sicherheitsbeiträge

Es gibt eine beträchtliche Anzahl von Beiträgen zur Joomla-Sicherheit, die viele Jahre zurückreichen. Leider sind viele von ihnen veraltet und möglicherweise irreführend. Zum Beispiel gibt es eine Reihe von Beiträgen zur Sicherheitscheckliste, die nicht alle tatsächlich mit Sicherheit zu tun haben.

Dieser Beitrag basiert auf einem Artikel im Joomla! Community Magazine von Ahmad Moussa in der Ausgabe vom April 2021.

## Beste Praktiken zur Sicherung Ihrer Joomla-Website

Das Joomla Content Management System (CMS) ist weit verbreitet im Internet, da es aufgrund seiner Benutzerfreundlichkeit und Beliebtheit das zweitgrößte CMS ist, das über 110 Millionen Mal heruntergeladen wurde. Aber auch wenn es beliebt ist, enthalten Joomla und alle anderen Websites, Apps, E-Commerce-Seiten oder andere CMSs Sicherheitsrisiken. Sie können diesen nicht entkommen, aber glücklicherweise kann die Umsetzung der richtigen Vorsichtsmaßnahmen von Anfang an sicherstellen, dass Ihre Website geschützt ist.

Wir haben diesen umfassenden und schrittweisen Leitfaden zur Joomla-Sicherheit für Sie zusammengestellt. Er soll leicht nachvollziehbare Schritte bieten, um die Sicherheit Ihrer Joomla-Website zu verbessern. Wenn die Sicherung Ihrer Joomla-Website gegen alle kommenden Angriffe auf Ihrer Agenda steht, dann sollten Sie ihn lesen. Alle in diesem Beitrag genannten Tipps sollen sicherstellen, dass Sie die besten Sicherheits- und Wartungspraktiken umsetzen, um Ihre wichtigsten Online-Ressourcen zu schützen.

## 1. Wählen Sie intelligente Benutzernamen und Passwörter

Seien Sie klug, wenn Sie Ihre Joomla-Admin-Benutzernamen und Passwörter auswählen. Verwenden Sie nicht "admin" als Ihren Benutzernamen und wählen Sie ein komplexes Passwort. Dies ist wahrscheinlich eine der besten Möglichkeiten, um die Sicherheit Ihres Joomla zu verstärken, und ironischerweise ist es eine der einfachsten.

Die Verwendung eines sicheren Passworts ist notwendig für eine gesunde Joomla-Sicherheit. Stellen Sie sicher, dass Ihr Login-Passwort lang genug ist (8-14 Zeichen) und Buchstaben, Zahlen und Symbole enthält. Da Passwörter zwischen Groß- und Kleinschreibung unterscheiden, macht die Verwendung von sowohl Groß- als auch Kleinbuchstaben es noch stärker. Machen Sie es sich außerdem zur Gewohnheit, die Admin-Passwörter mindestens einmal im Monat zu ändern.

## 2. Praktiziere das Prinzip der minimalen Rechtevergabe

Stellen Sie sicher, dass Sie die drei verschiedenen Berechtigungsgruppen verstehen:

1. Manager: Haben den geringsten Zugriff auf das Backend von Joomla. Können Kategorien und Beiträge erstellen und bearbeiten. Haben Zugriff auf den Medienmanager und können Medien hochladen und entfernen. Können keine Erweiterungen installieren oder entfernen.
2. Administratoren: Haben alle Rechte, die Manager haben, zusammen mit einigen zusätzlichen Berechtigungen. Haben Zugriff auf die Benutzerverwaltung, den Menü-Manager und den Erweiterungsmanager. Können nicht auf das Joomla Global Configuration-Menü zugreifen.
3. Super User: Haben vollen Zugriff auf das Joomla Backend. Haben alle Rechte von Managern und Administratoren, zusammen mit dem Zugriff auf die Globale Konfiguration. Nur Super User können Super User hinzufügen, bearbeiten und entfernen.

Es ist wichtig, dass Sie diese Rollen sorgfältig auf Ihre Benutzergruppe verteilen. Jeder mit einer Super User-Rolle kann jede Aktion innerhalb des Joomla-Systems ausführen. Wenn Sie Aufgaben an ein Teammitglied delegieren, das weniger Berechtigungen erfordert, weisen Sie dem Konto des Mitglieds die minimal notwendigen Zugriffsrechte zu.

## 3. Verwendung der Joomla Multi-Faktor-Authentifizierung

Es wird dringend empfohlen, die Joomla Multi-Faktor-Authentifizierung zu aktivieren, da sie eine zusätzliche Sicherheitsebene für Ihre Joomla-Website bietet. Traditionell müssen Sie, wenn Sie sich auf Ihrer Website anmelden möchten, Ihren Benutzernamen und Ihr Passwort eingeben, um sich im System zu identifizieren. Das größte Problem bei diesem Ansatz besteht darin, dass Ihr Benutzername und Passwort gestohlen oder erraten werden können. Deshalb können die Joomla Multi-Faktor-Authentifizierungs-Plugins Ihre Website vor Hackern schützen, indem sie eine zweite Sicherheitsebene hinzufügen. Es gibt fünf verschiedene Methoden, aus denen Sie wählen können, nachdem Sie Ihren Benutzernamen eingegeben haben.

## 4. Zugang zum Joomla-Admin-Backend einschränken

Es ist sinnvoll, den Zugang zum Joomla-Admin-Backend mithilfe von IP-Filterung zu beschränken, da es sich um eine sensible Ressource handelt. Dies kann auch für andere sensible Ordner von Joomla durchgeführt werden, indem Sie die unten genannten Schritte befolgen:

Schritt 1: Erstellen Sie zunächst eine .htaccess-Datei, falls diese nicht bereits im zu schützenden Verzeichnis vorhanden ist.

Schritt 2: Fügen Sie der .htaccess-Datei den folgenden Code hinzu:
   ```
   Order Deny, Allow
   Deny from all
   Allow from xx.xx.xx.xx
   ```

Schritt 3: Geben Sie die spezielle IP-Adresse ein, von der aus Sie den Zugang erlauben möchten, anstelle von xx.xx.xx.xx.

Weitere Informationen zur Einschränkung des Verzeichniszugangs nach IP-Adresse mithilfe von htaccess finden Sie in diesem Joomla! Dokumentationsbeitrag. Sie können auch Sicherheits-Erweiterungen verwenden, die den Zugang zum Joomla-Admin-Backend mithilfe der IP-Filterungsfunktion einschränken können und viele weitere Funktionen enthalten, die die Sicherheit Ihrer Joomla-Website stärken.

## 5. Sichere FTP-Verbindungen verwenden

Stellen Sie sicher, dass die Verbindungen, die zum Zugriff auf Ihre Joomla-Websitedateien verwendet werden, abgesichert sind. Sie sollten SFTP-Verschlüsselung verwenden, wenn Ihr Hosting-Anbieter dies unterstützt, oder SSH. Wenn Sie einen FTP-Client nutzen, ist der Standardport für SFTP normalerweise 22.

Einige FTP-Clients speichern Passwörter im Klartext oder verschlüsselt auf Ihrem Computer. Selbst einige verschlüsselte Passwörter können in das Original zurückverwandelt werden. Wir empfehlen dringend, FTP-Passwörter nicht im Client zu speichern, um Hacks zu vermeiden.

## 6. Regelmäßige Backups machen

Sparen Sie Zeit, indem Sie sich auf das schlimmste Szenario vorbereiten, falls Ihre Website angegriffen wird. Daher wird empfohlen, ein vollständiges funktionierendes Backup Ihrer Joomla-Website zu erstellen. Ein funktionales Backup kann Ihre Website innerhalb von Minuten nach einem Cyberangriff wiederherstellen.

Die beiden Hauptkomponenten eines Backups sind:

- Joomla-Kern und andere wichtige Dateien
- Die Datenbank

Darüber hinaus können die Methoden zur Erstellung von Backups flexibel sein. Es gibt zwei Möglichkeiten, ein Backup zu erstellen – manuell und automatisiert, wie unten beschrieben:

### Manueller Prozess

Das manuelle Backup der Joomla-Site erfordert zwei Komponenten: Dateien und die Datenbank. Um Ihre Joomla-Dateien und -Ordner zu sichern, verwenden Sie ein FTP-Programm oder den Dateimanager, falls Sie einen Drittanbieter-Hostingdienst verwenden.

Mit FTP-Clients können Sie alle Dateien nacheinander auf Ihren lokalen Rechner herunterladen. Dieser Prozess kann jedoch langsam sein. Sobald die Dateien heruntergeladen sind, komprimieren Sie den Ordner in eine einzige Zip-Datei und schützen Sie diese mit einem Passwort.

Die Datenbank kann gesichert werden, indem Sie eine Kopie der Datenbank auf Ihren Computer exportieren. Melden Sie sich bei der Datenbank an, die Sie exportieren möchten, indem Sie phpMyAdmin verwenden. Klicken Sie auf den Datenbanknamen auf der linken Seite der Seite. Sobald Sie auf Ihre Joomla-Datenbank geklickt haben, sollten Sie zu einem Bildschirm kommen, der einen Tab mit der Bezeichnung „Exportieren“ hat. Wählen Sie den Reiter Exportieren und klicken Sie dann auf die Schaltfläche „Los“. Speichern Sie sie dann an einem sicheren Ort.

### Automatisierter Prozess

Für ein automatisiertes Backup kann eine Joomla-Erweiterung wie Akeeba Backup hilfreich sein. Installieren Sie die Akeeba Backup-Erweiterung auf Ihrer Joomla-Website, nachdem Sie sie von der offiziellen Seite des Entwicklers heruntergeladen haben. Nachdem die Installation abgeschlossen ist, greifen Sie auf das Erweiterungs-Dashboard zu und sichern Sie Ihre Website. Wenn das Backup abgeschlossen ist, werden Sie auf eine Seite weitergeleitet. Klicken Sie hier auf „Backups verwalten“. Dies öffnet eine Seite, die alle Backups enthält. Sie können das Backup von hier herunterladen und lokal speichern.

## 7. Halten Sie Ihre Joomla-Website aktuell

Das Aktualisieren Ihrer Joomla-Website kann der Seite Sicherheit und Stabilität bieten. Außerdem sind nicht alle Aktualisierungen vollständige Versions-Updates der Website; einige Updates können geringfügig sein und lediglich Fehlerbehebungen darstellen, während andere Versions-Updates sind.

Joomla verfügt über ein dediziertes Sicherheitsteam, das dafür bekannt ist, schnell Patches bereitzustellen. Wird Ihre Joomla-Website nicht gepatcht, kann sie anfällig für Hackerangriffe werden.

Um Ihre Seite auf Updates zu überprüfen, können Sie Folgendes tun:

Schritt 1: Melden Sie sich als Administrator bei Ihrer Joomla-Website an.

Schritt 2: Navigieren Sie anschließend zu Komponenten>Joomla-Update.

Schritt 3: Joomla überprüft nun, ob ein neues Update verfügbar ist. Wenn es ein neues Update anzeigt, klicken Sie einfach auf die Option „Update installieren“.

Bevor Sie auf eine neuere Version von Joomla aktualisieren, sollten bestimmte Dinge überprüft werden:

- Vorlagen-Update: Prüfen Sie, ob Ihre Joomla-Vorlagen mit der neueren Joomla-Version kompatibel sind. Wenn nicht, bitten Sie den Vorlagenautor, diese zu aktualisieren, oder verwenden Sie eine Alternative.
- Erweiterungen-Update: Überprüfen Sie und stellen Sie sicher, dass alle Joomla-Erweiterungen mit der neueren Joomla-Version kompatibel sind. Entfernen Sie alle, die nicht kompatibel sind. Um die Erweiterungen zu aktualisieren, navigieren Sie zu Erweiterungen>Verwalten und klicken Sie auf Aktualisieren.
- Cache leeren: Nachdem Sie auf eine neuere Version von Joomla aktualisiert haben, leeren Sie den Cache Ihrer Joomla-Seite. Dies kann mit der integrierten Funktionalität von Joomla erfolgen.

## 8. Verwenden Sie vertrauenswürdige Drittanbieter-Erweiterungen und Vorlagen:

Es wird empfohlen, eine minimale Anzahl von Erweiterungen auf Ihrer Website zu verwenden, um ein optimales Joomla-Sicherheitsniveau zu erreichen. Die Verwendung nicht vertrauenswürdiger Drittanbieter-Erweiterungen oder Vorlagen kann Schwachstellen darstellen und die Leistung Ihrer Joomla-Website beeinträchtigen. Nicht alle Drittanbieter-Erweiterungen sind problemlos; wenn Sie die Möglichkeit haben, auf eine Drittanbieter-Erweiterung zu verzichten, tun Sie dies! Wählen und verwenden Sie professionelle Erweiterungen und Vorlagen von renommierten Unternehmen und halten Sie sie auf dem neuesten Stand, um Ihre Website zu schützen.

## 9. PHP-Version Ihrer Joomla-Website aktualisieren

Schützen Sie Ihre Website vor verschiedenen Hackerangriffen und stärken Sie die Sicherheit Ihrer Joomla-Seite, indem Sie die PHP-Version Ihrer Website auf die neueste stabile Version aktualisieren. Achten Sie darauf, eine PHP-Version auszuwählen, die mit Ihren Joomla-Vorlagen und Erweiterungen kompatibel ist, um Probleme mit Ihrer Website zu vermeiden. Es gibt verschiedene Möglichkeiten, Ihre PHP-Version zu aktualisieren. Die wichtigsten werden in einem Beitrag der Ausgabe vom September 2020 des Joomla Community Magazins behandelt: Wie aktualisiere ich meine PHP-Version?.

## 10. HTTP-Sicherheitsheader verstärken

Es wird dringend empfohlen, HTTP-Sicherheitsheader zu implementieren oder zu aktualisieren, da sie eine zusätzliche Sicherheitsschicht für Ihre Joomla-Seite bieten, indem sie helfen, Angriffe und Sicherheitslücken zu mindern. In der Regel erfordern sie nur eine kleine Konfigurationsänderung auf Ihrem Webserver. Diese Header weisen Ihren Browser an, wie er beim Umgang mit den Inhalten Ihrer Seite zu verfahren hat. Nachfolgend sind sechs gängige HTTP-Sicherheitsheader aufgeführt, die überprüft werden sollten:

- Content-Security-Policy
- X-XSS-Protection
- Strict-Transport-Security
- X-Frame-Options
- Public-Key-Pins
- X-Content-Type

## 11. Verwenden Sie eine Joomla-Sicherheitserweiterung

Es ist notwendig, die Anmeldeversuche im Joomla-Admin-Backend zu begrenzen, um Brute-Force-Angriffe auf Ihre Joomla-Website zu vermeiden. Dies kann durch verschiedene Joomla-Sicherheitserweiterungen implementiert werden, die das Administrator-Backend Ihrer Website vor Hacking-Versuchen schützen. Solche Erweiterungen finden Sie in der Kategorie "Sicherheit" der Joomla-Erweiterungen.

## 12. Wählen Sie einen sicheren Hosting-Anbieter

Stellen Sie sicher, dass der von Ihnen gewählte Hosting-Anbieter Joomla-Sicherheitsvorkehrungen umsetzt. Wenn Sie sich für ein Shared Hosting entscheiden, achten Sie darauf, dass Subnetting unter Berücksichtigung der Joomla-Sicherheit implementiert wird. Der Kauf eines günstigen Shared-Hosting-Anbieters könnte kein idealer Startpunkt sein, da Ihre Website langsamer wird, anfällig für Spam durch eine „schlechte Nachbarschaft“ von Websites mit niedrigem Ruf ist und kompromittiert werden könnte, wenn andere Websites gehackt werden. Außerdem sollten Sie bei der Auswahl eines Hosting-Plans verschiedene Parameter wie Anpassung, Support, Bewertungen usw. prüfen.

## 13. Verwenden Sie SSL, um die Joomla-Sicherheit zu verbessern

Es wird dringend empfohlen, ein SSL-Zertifikat (Secure Socket Layer) auf Ihrer Webseite zu installieren, da es die Kommunikation zwischen Ihrer Joomla-Seite und den Browsern Ihrer Besucher verschlüsselt. Besorgen Sie sich ein SSL-Zertifikat von einer verifizierten Zertifizierungsstelle und stellen Sie sicher, dass der gesamte HTTP-Verkehr zu HTTPS umgeleitet wird. Fügen Sie dazu den folgenden Code in Ihre .htaccess-Datei ein:

```
# Weiterleitung von HTTP zu HTTPS
RewriteEngine On RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

## 14. Häufige Joomla-Sicherheitsüberprüfung

Es ist äußerst wichtig, Schwachstellen aufzudecken, bevor ein Hacker dies tut, um Ihre Joomla-Website sicher und geschützt zu halten. Dies kann durch die Wahl eines professionellen Sicherheitsüberprüfungstools erreicht werden, das Ihnen viel Zeit bei der Verwaltung Ihrer Websites sparen kann. Sorgfältige Sicherheitsüberprüfungen sind eine großartige Möglichkeit, die Sicherheit von Joomla zu verbessern. Viele Dienste tun dies, indem sie Aufgaben automatisieren, wie zum Beispiel das Erstellen von Website-Backups, das Scannen nach Anzeichen von Eindringlingen und das Mass-Updaten der von Ihnen vertrauten Erweiterungen. Es kann auch Ihre Website auf die Anwendung von Sicherheits-Best-Practices überprüfen und einen Tiefenscan durchführen, um potenzielle Sicherheitsbedrohungen zu identifizieren. Diese Dienste verwenden eine optimierte Mischung aus manuellen und automatisierten Mechanismen, um Schwachstellen auf Ihrer Joomla-Seite zu entdecken.

## 15. Überprüfen Sie die Nachrichten nach der Installation

Es wird dringend empfohlen, alle Nachrichten nach der Installation zu lesen, da das Joomla-Team Ihnen wichtige Informationen zur Verfügung stellt, die nach einem Upgrade oder nach der ersten Installation von Joomla Ihre Aufmerksamkeit erfordern. Diese Nachrichten enthalten meist Joomla-Sicherheitskonfigurationen oder Dateiänderungen, die manuell vorgenommen werden sollten und die ein Upgrade nicht ändern kann.

## 16. Lernen Sie die gefährdeten Erweiterungen kennen

Überprüfen Sie regelmäßig die Website der Liste gefährdeter Erweiterungen und deren Social-Media-Seiten, um sich über die neuesten Sicherheitsrisiken und möglichen Patches zu informieren. Es wird empfohlen, jede Erweiterung zu deinstallieren, die in der Liste gefährdeter Erweiterungen aufgeführt ist und für die kein Patch bekannt ist. Stellen Sie sicher, dass Sie Ihre gefährdete Erweiterung aktualisieren, sobald ein Patch verfügbar ist. Wenn Ihre Website eine gefährdete Version einer Erweiterung verwendet, für die es kein Patch-Update gibt, wird empfohlen, sie zu ersetzen.

## Schlussfolgerung

Da es immer ein Risiko geben wird, bleibt die Joomla-Sicherheit ein kontinuierlicher Prozess, der eine häufige Bewertung möglicher Angriffsträger erfordert. Website-Besitzer und Administratoren sollten stets die Sicherheit ihrer Website verbessern, um das Risiko eines Kompromisses zu verringern.  

*Übersetzt von openai.com*  

