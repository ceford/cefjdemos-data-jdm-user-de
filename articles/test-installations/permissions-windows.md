<!--
{
  "source": "https://docs.joomla.org/How_do_Windows_file_permissions_work?",
  "title": "Dateiberechtigungen: Windows ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Für diejenigen unter Ihnen, die ihre Joomla!-Websites entweder entwickeln oder bereitstellen und dabei eine Windows-Umgebung verwenden, ist es manchmal schwierig, relevante Informationen zu Berechtigungen zu erhalten. Leider ist es eine Tatsache, dass die meisten Web-Services unter Unix angeboten werden und dass Unix in diesem Umfeld ziemlich gut dokumentiert ist. Hoffentlich werden die folgenden Informationen dazu beitragen, etwas Verwirrung zu klären und ein wenig Orientierung zu bieten. 

## Übersicht über Windows-Webserver

Zunächst wollen wir die Unterschiede zwischen den Servern besprechen. Im Allgemeinen scheinen die meisten Windows-Nutzer entweder Apache (Win32) oder Microsoft IIS zu verwenden. Diese beiden Webserver funktionieren sehr unterschiedlich und nutzen leicht unterschiedliche Bereitstellungsmodelle. Apache (Win32) läuft in der Regel auf dem Host-Computer als der Benutzer, unter dem es installiert wurde, während IIS unter einem bestimmten Benutzer installiert wird, aber unter einem neu eingerichteten Benutzer *IUSR_* läuft.

## Berechtigungs-Standards

Standardmäßig neigt Unix dazu, nur dem *besitzenden* Benutzer vollen Zugriff auf Dateien und Verzeichnisse zu gewähren. Im Gegensatz dazu weist Windows standardmäßig auch der Gruppe *Jeder* volle Berechtigungen zu. Das Erste, was ein guter Windows-Administrator tut, ist, die Rechte der Gruppe *Jeder* zu entfernen, um die Sicherheit zu verbessern. Für lokale PC-Tests ist dies wahrscheinlich nicht erforderlich, erklärt jedoch, warum Sie, wenn *Jeder* nicht entfernt wird und Sie irgendeine Form von Berechtigungsskript oder den Joomla! Vorinstallations-Check ausführen, volle *Lese-, Schreib- und Ausführungs*-Berechtigungen haben. Sie übernehmen die Rechte der Gruppe *Jeder*.

## Microsoft Internet Information Server (IIS)

IIS gibt es in zwei Hauptvarianten: PWS (Personal WebServer) und IIS (Internet Information Server). Im Wesentlichen handelt es sich um dieselbe Anwendung. PWS ist lediglich eine abgespeckte Version von IIS, die für Desktop-Umgebungen entwickelt wurde, während IIS für Server-Umgebungen konzipiert ist. PWS beschränkt Sie auf eine einzige Hauptwebsite, sodass Ihre Anwendungsinstallationen in der Regel in Unterverzeichnissen der Hauptwebsite erfolgen. IIS hingegen bietet die Funktionalität für virtuelle Hosts, die aus diesen Verzeichnissen betrieben werden, und ermöglicht so die Verwaltung mehrerer Websites.

Aufgrund der unterschiedlichen Funktionsbeschränkungen verfügt PWS nicht über den *Permissions Wizard* (Berechtigungsassistent), da er als nicht notwendig erachtet wird. Nur ein Benutzer wird den PWS-Server verwenden. In IIS werden viele Benutzer den Server nutzen, weshalb unterschiedliche Berechtigungszuweisungen erforderlich sind.

Sobald das *Everyone*-Konto entfernt wurde, bleibt in Windows IIS nur noch das *IUSR_**-Konto mit Top-Level-Rechten für die Web-Server-Verzeichnisse übrig. Eine Berechtigungsprüfung sollte nun unterschiedliche Ergebnisse liefern. Nur das *IUSR_**-Konto hat volle Berechtigungen, und andere Benutzer sollten entweder nur Lesezugriff oder keine Rechte haben. Die Rechte werden durch die anderen Benutzer bestimmt, denen manuell Rechte in den IIS-Verzeichnissen zugewiesen wurden.

### Zuweisen von Berechtigungen

Das Zuweisen von Berechtigungen in Windows ist im Grunde recht einfach, aber manchmal ein wenig verwirrend. Klicken Sie mit der rechten Maustaste auf den betreffenden Ordner oder die Datei. Wenn Sie *Eigenschaften* oder *Freigabe und Sicherheit* auswählen, gelangen Sie in das Windows-Sicherheitsverwaltungsfenster. Wenn Sie einen in der Liste aufgeführten Benutzernamen einmal anklicken, werden die Rechte dieses Benutzers im unteren Bereich des Fensters angezeigt. Einige Rechte könnten ausgegraut sein. Diese sind entweder deshalb nicht verfügbar, weil der aktuelle Benutzer (unter dem Sie angemeldet sind) nicht über ausreichend hohe Berechtigungen verfügt, um sie zu ändern, oder sie von dem übergeordneten Verzeichnis geerbt wurden und so eingestellt sind, dass sie die Berechtigungen dieses höherstufigen Verzeichnisses verwenden. (Dies ist im Allgemeinen der Standardmechanismus.)

Wie Sie sehen, verwendet Windows das folgende Berechtigungs-/Rechteschema:

| # | Kontrolle | Erlaubt # |
| :---: | :---- | :--- |
| 1. | Volle Kontrolle | Erlaubt: 1, 2, 3, 4, 5, 6, 7 |
| 2. | Ändern | Erlaubt: 2, 3, 4, 5, 6 | - |
| 3. | Lesen & Ausführen | Erlaubt: 3, 4 | - |
| 4. | Ordnerinhalt auflisten | Erlaubt: 4 (aber kann keine Programme ausführen) | - |
| 5. | Lesen | Erlaubt: 5 (Impliziert: 4) | - |
| 6. | Schreiben | Erlaubt: 6 (Impliziert: 4) | - |
| 7. | Besondere Berechtigungen | Erlaubt: Kombinationen |

### Windows-Dateiberechtigungseigenschaften

Windows-Dateiberechtigungen können als ähnlich wie UNIX- oder Linux-Datei (Moden) Berechtigungen betrachtet werden. Sie werden nur anders dargestellt. Wenn Sie beispielsweise hauptsächlich Unix/Linux verwenden, sind Sie es wahrscheinlich gewohnt, dass Berechtigungen als 644/666 755/777 dargestellt werden, anstatt in den obigen Begriffen. Wenn Sie also 644 verwenden, bedeutet dies:

- Der Besitzer dieser Datei kann sie lesen und schreiben.
- Die Gruppe des Besitzers kann die Datei lesen.
- Jeder andere kann die Datei lesen.

**Hinweis:** Windows- und Unix-Berechtigungen (Zugriffskontrolllisten) sind nicht genau gleichzusetzen; Windows verwendet den *Gruppen*-Mechanismus nicht in derselben Weise. Für diese Diskussion und im Hinblick auf die Web-Hosting-Umgebung können sie jedoch gleichgesetzt werden. Ah, aber in Windows werden *Gruppen* nicht verwendet und *Everyone* sollte entfernt worden sein. Hier weichen Windows und Unix etwas voneinander ab, aber was getan werden kann, ist, gleichwertige Bedeutungen *anzupassen* oder *zu korrelieren*.

Diese Übersicht wird Ihnen wirklich keinen Windows- oder NTFS-spezifischen Berechtigungsleitfaden zur Verfügung stellen, sondern mehr ein Verständnis dafür, wie die häufig genannten nummerierten UNIX/Linux-Style Berechtigungen auf einem Computer mit einem NTFS-Dateisystem korrelieren. Die Dateien, die im `www`- oder `public_html`-Stammverzeichnis abgelegt werden, oder welches Verzeichnis auch immer Ihre Site (`www.domain.com` oder `localhost`) auf Ihrer Festplatte anzeigt, sollten Ihrem Benutzerkonto gehören, aber nur, wenn dieser Benutzer nicht als privilegierter Benutzer wie *Administrator* unter Windows oder *root* unter UNIX/Linux angesehen wird. Diese Konten erlauben viel zu viel Zugriff und sollten niemals für den täglichen Gebrauch verwendet werden.

### Best Practices

Häufig verwendete Sicherheitspraktiken schlagen vor, dass alle **Dateien** die folgenden Berechtigungen haben sollten.

- **Besitzer** Lesen & Schreiben
- **Gruppe** Nur Lesen
- **Andere** Nur Lesen

Alle **Verzeichnisse/Ordner** sollten die folgenden Berechtigungen haben.

- **Besitzer** Lesen, Schreiben & Ausführen
- **Gruppe** Lesen & Ausführen
- **Andere** Lesen & Ausführen

Dies ist argumentativ nicht unbedingt die *optimale* Sicherheit, aber ein Gleichgewicht zwischen Sicherheit, Funktionalität und Wartbarkeit muss gefunden werden.

Windows, anders als Unix, pflegt keine einzelne ACL für *Ausführen*, sondern bietet einfach *Lesen & Ausführen* kombiniert an, was nicht *Schreiben* impliziert. Die *Lesen & Ausführen* ACL impliziert jedoch *Verzeichnisinhalte auflisten*. Deshalb, wenn Sie nur *Lesen und Schreiben* Berechtigungen für ein Verzeichnis haben, aber kein *Ausführen*, werden Sie nicht in der Lage sein, den Inhalt des Verzeichnisses zu sehen und möglicherweise Probleme haben, wenn Sie versuchen, die Datei über einen Webbrowser zu laden. Ein gewisses Verständnis von UNIX/Linux-Berechtigungen ist erforderlich, um sie vollständig mit Windows-Berechtigungen gleichzusetzen/zu korrelieren. Die folgende Tabelle sollte dabei helfen:

| Unix Modus | Windows ACL | Kommentare |
|:-----------:| :---- | :--- |
| 7 | Ändern | Lesen, Schreiben & Ausführen, Sie sollten der Besitzer dieser Datei sein |
| 6 | Lesen & Schreiben | |
| 5 | Lesen & Ausführen | wird für die meisten Anwendungen verwendet |
| 4 | Nur Lesen | Sicherheit durch Verschleierung ist keine gute Praxis |
| 3 | Schreiben & Ausführen | nicht verfügbar in Windows, es sei denn *Besondere* Berechtigungen werden verwendet, nicht häufig verwendet |
| 2 | Nur Schreiben | nicht verfügbar in Windows, es sei denn *Besondere* Berechtigungen werden verwendet, nicht häufig verwendet |
| 1 | Nur Ausführen | (nicht verfügbar in Windows, es sei denn *Besondere* Berechtigungen werden verwendet, nicht häufig verwendet) |

Im Vergleich zu Unix-Moden, wenn Sie so etwas wie 644 sehen, zerbrechen Sie dies in drei Elemente:

Die erste Zahl repräsentiert die Besitzerberechtigungen, die zweite repräsentiert die Gruppenberechtigungen und die dritte, die Anderen-Berechtigungen. Das Windows-Äquivalent wäre:

- **Besitzer** (6) Lesen & Schreiben
- **Gruppe** (4) Nur Lesen
- **Andere** (4) Nur Lesen

Hoffentlich bietet dieses Beispiel einige Einblicke darin, wie man Unix-Moden/Berechtigungen in Windows-Berechtigungen/ACLs korreliert. Dieses Dokument beinhaltet nicht komplexere Themen wie *Effektive*, *Geerbte* oder *Besondere* Berechtigungen. Trotz der Benutzerfreundlichkeit von Windows sind die Berechtigungs- und ACL-Mechanismen von Microsoft tatsächlich ziemlich komplex und sehr umfangreich, aber dies könnte Ihnen einen schnellen Verweis geben, um einige der Verwirrungen rund um die Übersetzungen von Unix- und Windows-Berechtigungen zu lindern.

*Übersetzt von openai.com*

