<!--
{
  "source": "https://docs.joomla.org/J4.x:Apache_PHP_Handler",
  "title": "Apache PHP Handler ",
  "description": "", 
  "author": ""
}
-->

## Notizen

Um zu bestimmen, welche Methode Ihr Webserver zur Handhabung von PHP-Dateien verwendet, verwenden Sie die Links **Administrator / System / Systeminformationen** und wählen Sie den Reiter PHP-Informationen. Durchsuchen Sie die Seite nach **Server-API**. Zu den gängigen Methoden, wie ein Apache-Webserver PHP-Dateien verarbeitet, gehören die folgenden:

### DSO (mod_php)

- **Vorteil:** einer der schnellsten verfügbaren Handler.
- **Nachteil:** funktioniert nur mit einer einzigen PHP-Version; von PHP-Skripten gespeicherte Dateien gehören dem Apache-Benutzer, **außer** wenn sie zusammen mit mod_ruid2 verwendet werden.
- **Zu erkennen:** Server-API - Apache 2.0 Handler

### CGI/FastCGI

- **Vorteil:** Skripte werden als Domain- oder Subdomain-Benutzer ausgeführt, sehr schneller Handler.
- **Nachteil:** langsamer als mod_php, PHP-Konfigurationsänderungen können nicht in einer .htaccess-Datei vorgenommen werden.
- **Zu erkennen:** Server-API - CGI/FastCGI

### FPM/FastCGI

- **Vorteil:** sehr schnell, zusätzliche Flexibilität.
- **Nachteil:** verbraucht mehr Speicher als die meisten anderen, PHP-Konfigurationsänderungen können nicht in einer .htaccess-Datei vorgenommen werden.
- **Zu erkennen:** Server-API - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Vorteile:**
   - Bietet Unterstützung für Caching.
   - Ist der leistungsfähigste Handler mit geringem Speicherverbrauch.
   - Keine Konfiguration erforderlich.
   - Kann mit mehreren PHP-Versionen in einer einzigen Einrichtung arbeiten.
   - Unterstützt PHP-Konfigurationsanweisungen durch .htaccess-Dateien.
   - Sicher, da Skripte als Domain-Besitzer ausgeführt werden.
- **Nachteile:**
   - Macht nicht alle LSAPI-Funktionen verfügbar.
- **Zu erkennen:** Server-API - ?

Auf einem lokalen Laptop oder Desktop-Computer können Sie mod_php verwenden, aber möglicherweise müssen Sie den Apache-Benutzer auf Ihren eigenen Benutzernamen setzen und das Dokument-Root auf einen Ort in Ihrem eigenen Dateiraum verweisen. Andernfalls haben Sie Probleme mit Datei- und Ordnerberechtigungen.

Bei einem Hosting-Service müssen Sie eine der FastCGI-Alternativen oder LSAPI verwenden. Hosting-Dienste können Ihnen eine Auswahl bieten.

*Übersetzt von openai.com*  

