<!--
{
  "source": "https://docs.joomla.org/J4.x:Hosting_Setup",
  "title": "Hosting-Einrichtung ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Diese Seite bietet einige Anleitungen für alle, die völlig neu in der Hosting-Technologie sind. Sie können eine Website auf Ihrem eigenen Laptop oder Desktop-Computer einrichten. Dies wird als lokales Hosting bezeichnet und ist eine gute Möglichkeit, mit neuen Funktionen zu experimentieren. Es ist völlig kostenlos. Um Ihre Website-Inhalte für den Rest der Welt verfügbar zu machen, benötigen Sie ein Konto bei einem Hosting-Dienst und dafür müssen Sie bezahlen.

## Unterstützung für Software

Joomla! ist eine Anwendung, die auf drei unterstützende Softwarekomponenten angewiesen ist: die PHP-Skriptsprache, eine Datenbank (eine von MySQL, MariaDB oder PostgreSQL) und einen Webserver (einen von Apache, Nginx, Microsoft IIS oder ...). Die minimalen Versionsnummern sind in den folgenden Tabellen angegeben:

### Anforderungen für Joomla! 5.x

| Software           | Empfohlen       | Minimum     |
|--------------------|-----------------|-------------|
| PHP                | 8.3             | 8.1.0       |
| **Datenbanken**    |                 |             |
| MySQL              | 8.1             | 8.0.13      |
| MariaDB            | 11.1.0          | 10.4.0      |
| PostgreSQL         | 16.0            | 12.0        |
| **Webserver**      |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.25            | 1.21        |
| Microsoft IIS      | 10              | 10          |

### Anforderungen für Joomla! 4.x

| Software           | Empfohlen       | Minimum     |
|--------------------|-----------------|-------------|
| PHP                | 8.2             | 7.2.5       |
| **Datenbanken**    |                 |             |
| MySQL              | 8.0             | 5.6         |
| PostgreSQL         | 11.0            | 11.0        |
| **Webserver**      |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.18            | 1.10        |
| Microsoft IIS      | 10              | 8           |

## Hosting-Dienste

Kommerzielle Hosting-Dienste bieten alles, was Sie zur Unterstützung einer Website benötigen. Einige bieten auch die Ein-Klick-Installation beliebter Anwendungen wie Content-Management-Systeme, Foren, Wikis usw. an. Aber bitte beachten Sie: Die Experten im Joomla-Forum empfehlen nicht, die Ein-Klick-Installation von Joomla zu verwenden.

Jeder Hosting-Dienst bietet verschiedene Pläne zu unterschiedlichen Preisniveaus an. Je mehr Sie bezahlen, desto mehr Speicherplatz und Bandbreite erhalten Sie, zusammen mit mehr E-Mail-Adressen, Datenbanken usw. Einige bieten auch einen kostenlosen Domainnamen an. Meistens müssen Sie jedoch für einen Domainnamen und eine kleine jährliche Registrierungsgebühr bezahlen.

## Kostenloses Hosting

Es gibt kein wirklich kostenloses Hosting! Ein Joomla-Partner-Hostingdienst bietet jedoch eine kostenlose Joomla-Website in der Domain joomla.com an. Das gibt Ihnen die Möglichkeit, Ihre eigene voll funktionsfähige Joomla-Website völlig kostenlos auszuprobieren. Es ist vergleichbar mit einem Shared-Hosting-Plan, jedoch mit Einschränkungen und häufigen Bitten, auf einen kostenpflichtigen Plan zu upgraden. Der kostenlose Plan muss alle 30 Tage erneuert werden, sonst wird er beendet. Der folgende Beitrag zeigt die erforderlichen Schritte zur Einrichtung einer kostenlosen Joomla-Site.

* [Kostenloses Joomla Hosting](jdocmanual?article=user/hosting/free-hosting)

Wenn Sie feststellen, dass Ihnen Joomla gefällt, können Sie auf einen kostenpflichtigen Plan aktualisieren oder andernorts nach einem Hostingdienst suchen, der Ihren Bedürfnissen und Ihrem Budget entspricht.

## Shared Hosting

Sie können einen minimalen Hosting-Plan für etwa £/$/e50 pro Jahr erhalten. Dieses Plan-Level wird oft als Shared Hosting bezeichnet und ist für alles geeignet, was keine sensiblen Daten betrifft. Unternehmen sollten sich von Spezialisten bezüglich geeigneter Hosting-Pläne beraten lassen. Die Wahl eines Hosting-Dienstes ist nicht ohne Probleme. Die billigsten Anbieter könnten unnötig restriktive *php.ini*-Einstellungen haben, die in ihrer Werbung nicht erscheinen. Manche könnten einen schlechten Ruf in Bezug auf Unterstützung haben.

Wenn Sie sich für einen Shared Hosting-Plan entscheiden, überprüfen Sie Folgendes:

- Unterstützung für PHP-Anwendungen wie Joomla, WordPress und Mediawiki.
- Speicherplatz: 500 MB ist ein absolutes Minimum. 1 GB oder mehr wäre besser, wenn Sie planen, viele Bilder zu verwenden.
- Anzahl der Datenbanken: Joomla verwendet eine, aber Sie werden bald feststellen, dass Sie 5 oder 10 oder mehr benötigen. Einige Pläne bieten eine unbegrenzte Anzahl innerhalb der gesamten Speicherplatzzuweisung.
- Datenbankgröße: mit Smart Search kann die Datenbank sehr schnell wachsen. Wenn Shared Hosting eine Einschränkung bei der Größe der Datenbank hat, wird es wichtig sein, herauszufinden, was dies ist. Es kann dazu führen, dass eine Website nicht funktioniert.
- Anzahl der E-Mail-Adressen: viele!
- Anzahl der HTTP- und DB-Verbindungen zum Server, die einige Shared Hosts begrenzen
- Backups: wie werden diese durchgeführt und gibt es ein Dokument zu den Nutzungsbedingungen (TOS), das festlegt, wer für die Backups verantwortlich ist.

Überprüfen Sie auch das angebotene Kontrollpanel und die Plattform. Den Forenbeiträgen nach zu urteilen, verwenden die meisten cPanel auf Linux. Der Hosting-Dienst sollte alle grundlegenden Website-Unterstützungssoftwares bereitstellen:

- Apache Webserver 2.4+ - *Verzeichnisindizes* sollten deaktiviert sein. Ebenfalls unterstützt:
  - Nginx 1.18+ (weniger Nutzer, daher weniger Forumsunterstützung)
  - Microsoft IIS\[6\] (weniger Nutzer, daher weniger Forumsunterstützung)
- MySQLi-Datenbank 8.1+ oder MariaDB-Klon mit InnoDB-Unterstützung. Ebenfalls unterstützt:
  - PostgreSQL 11.0+ (weniger Nutzer, daher weniger Forumsunterstützung).
- PHP 8+ wird empfohlen.
- phpMyAdmin-Datenbankverwaltungswerkzeug.

Vor dem Kauf überprüfen Sie die folgenden minimalen PHP-Anforderungen für Joomla:

- *memory_limit* - Minimum: 256M
- *upload_max_filesize* - Minimum: 64M
- *post_max_size* - Minimum: 64M
- *max_execution_time* - Empfohlen: 30
- *allow_url_fopen* - true

Viele dieser Parameter können vom Benutzer in cPanel festgelegt werden. Fragen Sie, ob das möglich ist.

Wenn Sie einen Domainnamen erworben haben, wird Ihr Hosting-Dienst ihn für Sie konfigurieren. Sie sollten Ihnen auch eine IP-Adresse zur Verfügung stellen, die Sie verwenden können, bis Ihre Domainregistrierung auf die Domain Name Server (DNS) propagiert, normalerweise ein paar Stunden.

Der folgende Beitrag zeigt, was Sie erwarten können, wenn Sie einen Hosting-Plan mit einer cPanel-Benutzeroberfläche erwerben.

* [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting)

## VPS-Hosting

Ein Virtual Private Server (VPS)-Hosting-Plan bietet vollen Zugriff auf einen Server, der Hardware teilt. Er verhält sich wie ein dedizierter Computer. Sie können den Server stoppen und starten, ihn neu starten und Ihre eigene Software installieren, genau wie Sie es auf einem Desktop-Computer tun würden. Sie können Konten für einzelne Benutzer erstellen, genau wie beim Shared Hosting. Typischerweise können Sie einige Funktionen erlauben, die normalerweise in Shared-Hosting-Konten nicht erlaubt sind.

Dedizierte und Cloud-Hosting-Pläne sind im Prinzip ähnlich, bieten jedoch entweder dedizierte Ressourcen oder an Ihre Bedürfnisse angepasste Ressourcen.

Diese fortgeschrittenen Pläne werden hier nicht behandelt.

## Lokales Hosting

Die meisten Personen, die Websites entwickeln, halten lokale Kopien auf einem Laptop oder Desktop-Computer bereit, um Updates oder neue Erweiterungen zu testen oder um neue Designs auszuprobieren. Das Einrichten einer lokalen Entwicklungsseite erfordert zwar einige technische Kenntnisse, ist aber relativ einfach, wenn man einfachen Anweisungen folgt.

Die folgenden Beiträge beschreiben, wie man lokales Hosting auf verschiedenen Arten von Desktop- oder Laptop-Computern einrichtet:

* [Lokales Hosting auf Windows](jdocmanual?article=user/hosting/local-hosting-on-windows) nur für Windows
* [Lokales Hosting mit XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp) für Linux, Mac und Windows.
* [Lokales Hosting auf Linux](jdocmanual?article=user/hosting/local-hosting-on-linux)

*Übersetzt von openai.com*

