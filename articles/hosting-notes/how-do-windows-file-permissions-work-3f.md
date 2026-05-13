<!--
{
  "source": "https://docs.joomla.org/How_do_Windows_file_permissions_work%3F",
  "title": "Windows-Dateiberechtigungen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Für diejenigen unter Ihnen, die entweder Joomla!-Websites aus einer Windows-Umgebung entwickeln oder bereitstellen, ist es manchmal schwierig, relevante Informationen zu Berechtigungen zu erhalten. Leider ist es eine Tatsache, dass die meisten Web-Server unter Unix angeboten werden und Unix in dieser Umgebung ziemlich gut dokumentiert ist. Hoffentlich wird die folgende Information dazu beitragen, einige Verwirrungen aufzuklären und ein wenig Anleitung zu bieten.

### Überblick über Windows Web-Server

Zunächst einmal lassen Sie uns die Unterschiede zwischen Servern diskutieren. Im Allgemeinen scheinen die meisten Windows-Nutzer entweder Apache(Win32) oder Microsoft IIS zu verwenden. Diese beiden Web-Server arbeiten sehr unterschiedlich und nutzen leicht unterschiedliche Bereitstellungsmodelle. Apache(Win32) läuft im Allgemeinen auf dem Host-Computer als der Benutzer, unter dem es installiert wurde, während IIS unter einem bestimmten Benutzer installiert wird, aber unter einem neu installierten Benutzer *IUSR_* läuft.

### Standardberechtigungen

Standardmäßig neigt Unix dazu, nur dem *besitzenden* Benutzer vollen Zugriff auf Dateien und Verzeichnisse zu geben, während Windows im Gegensatz dazu standardmäßig auch der Gruppe *Jeder* volle Berechtigungen zuweist. Das Erste, was ein guter Windows-Administrator tun wird, ist, die Rechte der Gruppe *Jeder* zu entfernen, um die Sicherheit zu verbessern. Für lokale PC-Tests ist dies wahrscheinlich nicht notwendig, erklärt jedoch, warum, wenn *Jeder* nicht entfernt wird und Sie eine Art von Berechtigungsprüfskript oder den Joomla! Vor-Installations-Check ausführen, Sie im Großen und Ganzen volle *Lese-, Schreib- und Ausführungsberechtigungen* haben, weil Sie die Rechte der Gruppe *Jeder* erwerben.

### Microsoft Internet Information Server (IIS)

IIS kommt in zwei Hauptvarianten, PWS (Personal WebServer) und IIS (Internet Information Server). Im Wesentlichen handelt es sich um dieselbe Anwendung. PWS ist nur eine abgespeckte Version von IIS, die für Desktop-Umgebungen konzipiert ist, während IIS für Serverumgebungen entwickelt wurde. PWS beschränkt Sie auf eine einzelne Hauptwebsite, sodass Ihre Anwendungsinstallationen im Allgemeinen in Unterverzeichnissen der Hauptwebsite stattfinden werden. IIS hingegen bietet die Funktionalität, virtuelle Hosts aus diesen Verzeichnissen heraus auszuführen, was die Möglichkeit mehrerer Websites bietet.

Aufgrund der unterschiedlichen Funktionseinschränkungen hat PWS den *Berechtigungsassistenten* nicht, da er als nicht notwendig erachtet wird. Nur ein Benutzer wird den PWS-Server verwenden. In IIS werden viele Benutzer den Server nutzen, daher sind unterschiedliche Berechtigungszuweisungen notwendig.

Sobald das Konto *Jeder* entfernt wurde, bleibt Windows IIS nun mit dem Konto *IUSR_* die obersten Rechte für die Web-Server-Verzeichnisse. Eine Berechtigungsprüfung sollte jetzt andere Ergebnisse liefern. Nur das Konto *IUSR_* hat volle Berechtigungen und andere Benutzer sollten entweder *Nur Lesezugriff* oder keine Rechte haben. Rechte werden durch die manuelle Zuweisung von Rechten zu den IIS-Verzeichnissen an andere Benutzer bestimmt.

### Zuweisen von Berechtigungen

Das Zuweisen von Berechtigungen in Windows ist relativ einfach, kann aber manchmal ein wenig verwirrend sein. Klicken Sie mit der rechten Maustaste auf den entsprechenden Ordner oder die Datei. Wenn Sie *Eigenschaften* oder *Freigabe und Sicherheit* auswählen, gelangen Sie in das Windows Sicherheit Management-Fenster. Durch einmaliges Anklicken eines aufgelisteten Benutzernamens werden die Rechte angezeigt, die dieser Benutzer in der unteren Hälfte des Fensters hat. Einige Rechte könnten ausgegraut sein. Diese sind entweder nicht verfügbar, weil der aktuelle Benutzer (also der angemeldete Benutzer) nicht über ausreichende Berechtigungen verfügt, um sie zu ändern, oder sie werden vom übergeordneten Verzeichnis geerbt und wurden auf dessen Erlaubnisse gesetzt (dies ist im Allgemeinen der Standardmechanismus).

Wie Sie sehen können, verwendet Windows das folgende Berechtigungen/Rechte-Schema:

<table data-cellpadding="2" data-cellspacing="0" data-align="center"
data-border="1" width="533">
<thead>
<tr>
<th>#</th>
<th>Berechtigungen</th>
<th>Rechte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p>1. </p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Vollständige Kontrolle</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 1, 2, 3, 4, 5, 6, 7</p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 2.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Ändern</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 2, 3, 4, 5, 6</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 3.</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p> Lesen &amp; Ausführen</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 3, 4 </p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 4.</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p> Ordnerinhalt auflisten</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 4 (aber kann keine Programme ausführen) </p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 5.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Lesen</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 5 (Impliziert: 4)</p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 6.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Schreiben</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: 6 (Impliziert:4 )</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p>7.</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p> Spezielle Berechtigungen</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Erlaubt: Kombinationen </p></td>
</tr>
</tbody>
</table>

### Windows-Dateiberechtigungseigenschaften

Windows-Dateiberechtigungen können als **ähnliche** Eigenschaften wie UNIX- oder Linux-Datei (Modi) Berechtigungen angesehen werden, sie werden nur anders dargestellt. Wenn Sie z. B. hauptsächlich ein Unix/Linux-Benutzer sind, sind Sie wahrscheinlich daran gewöhnt, Berechtigungen als 644/666 755/777 dargestellt zu sehen, anstatt in den obigen Begriffen beschrieben zu werden. Wenn Sie also aufgefordert werden, 644 zu verwenden, bedeutet das:

* Der Eigentümer dieser Datei kann sie lesen und bearbeiten.
* Die Gruppe des Eigentümers kann die Datei lesen.
* Alle anderen können die Datei lesen.

**Hinweis:** Windows- und Unix-Berechtigungen (Zugriffskontrolllisten) sind nicht exakt gleich, da Windows den *Gruppen*-Mechanismus nicht auf die gleiche Weise verwendet. In Bezug auf die Web-Hosting-Umgebung können jedoch äquivalente Bedeutungen *abgeglichen* oder *korreliert* werden. In Windows werden ***Gruppen*** nicht verwendet und ***Jeder*** sollte entfernt worden sein. Hier stimmen Windows und Unix nicht ganz überein, aber es kann versucht werden, äquivalente Bedeutungen anzupassen oder zu korrelieren.

Dieses Outline soll Ihnen keinen spezifischen Leitfaden für Windows oder NTFS-Berechtigungen geben, sondern vielmehr einem Verständnis dienen, wie die allgemein angegebenen nummerischen UNIX/Linux-Stil-Berechtigungen auf einem NTFS-Dateisystem korrelieren. Die Dateien, die in den www- oder public_html-Stammordner oder ein beliebiges Verzeichnis platziert werden, auf das Ihre Site (www.domain.com.au oder localhost) auf Ihrer Festplatte verweist, sollten mit Ihrem Benutzerkonto zugeordnet sein, jedoch nur, wenn dieser Benutzer nicht als privilegierter Benutzer wie *Administrator* auf Windows oder *root* auf UNIX/Linux betrachtet wird. Diese Konten erlauben zu viel Zugriff und sollten niemals für den täglichen Gebrauch verwendet werden.

### Beste Praktiken

Gängige Sicherheitsempfehlungen besagen, dass alle **Dateien** die folgenden Berechtigungen haben sollten.

* **Eigentümer:** Lesen & Schreiben
* **Gruppe:** Nur lesen
* **Andere:** Nur lesen

Alle **Verzeichnisse/Ordner** sollten die folgenden Berechtigungen haben:

* **Eigentümer:** Lesen, Schreiben & Ausführen
* **Gruppe:** Lesen & Ausführen
* **Andere:** Lesen & Ausführen

Dies ist jedoch nicht unbedingt eine *optimale* Sicherheit, aber ein gewisses Gleichgewicht muss zwischen Sicherheit, Funktionalität und Wartbarkeit gefunden werden. Windows, im Gegensatz zu Unix, hält keine einzelne ACL für *Ausführen* vor, sondern bietet einfach *Lesen & Ausführen*, das **nicht** *Schreiben* impliziert. Die *Lesen und Ausführen* ACL impliziert jedoch *Ordnerinhalt auflisten*. Daher können Sie, wenn Sie nur *Lesen &amp; Schreiben* Berechtigungen für ein Verzeichnis haben, aber keine *Ausführen* Berechtigungen, den Inhalt des Verzeichnisses nicht sehen und Probleme haben, wenn Sie versuchen, die Datei über einen Webbrowser auszuführen. Ein gewisses Verständnis der UNIX/Linux-Berechtigungen ist erforderlich, um sie vollständig auf Windows-Berechtigungen umsetzen und korrelieren zu können. Die folgende Tabelle sollte dabei helfen:

<table data-cellpadding="2" data-cellspacing="0" data-align="center"
data-border="1" width="659">
<thead>
<tr class="odd">
<th style="text-align: center;" data-bgcolor="#cccccc" width="7%"
data-valign="top"><p><strong>Unix Modus</strong></p></th>
<th data-bgcolor="#cccccc" width="10%" data-valign="top"><p><strong>Windows ACL </strong></p></th>
<th data-bgcolor="#cccccc" width="33%" data-valign="top"><p><strong>Anmerkungen </strong></p></th>
</tr>
</thead>
<tbody>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>7 </strong></p></td>
<td width="10%" data-valign="top"><p><strong> Ändern </strong></p></td>
<td width="33%" data-valign="top"><p><em>Lesen, Schreiben &amp; Ausführen, Sie sollten der Besitzer dieser Datei sein</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>6</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Lesen &amp; Schreiben</strong></p></td>
<td width="33%" data-valign="top"><p><em> </em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>5</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Lesen &amp; Ausführen</strong></p></td>
<td width="33%" data-valign="top"><p><em>wird für die meisten Anwendungen verwendet</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>4</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Nur lesen</strong></p></td>
<td width="33%" data-valign="top"><p><em>Sicherheit durch Verschleierung ist keine gute Praxis</em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>3</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Schreiben &amp; Ausführen</strong></p></td>
<td width="33%" data-valign="top"><p><em>nicht verfügbar in Windows, es sei denn "Spezielle" Berechtigungen werden verwendet, nicht allgemein benutzt</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>2</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Nur schreiben</strong></p></td>
<td width="33%" data-valign="top"><p><em>nicht verfügbar in Windows, es sei denn "Spezielle" Berechtigungen werden verwendet, nicht allgemein benutzt</em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>1</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Nur ausführen</strong></p></td>
<td width="33%" data-valign="top"><p><em>nicht verfügbar in Windows, es sei denn "Spezielle" Berechtigungen werden verwendet, nicht allgemein benutzt
</em></p></td>
</tr>
</tbody>
</table>

Im Vergleich zu Unix-Modi, wenn Sie etwas wie 644 sehen, würden Sie das in drei Elemente aufteilen:

**6**  :  **4**  : **4**

Die erste Zahl repräsentiert die Berechtigungen der ***Eigentümer***, die zweite die ***Gruppen*** Berechtigungen und die dritte die ***Anderen*** Berechtigungen. Das Windows-Äquivalent wäre;

* **Eigentümer** (6) : **Lesen & Schreiben**
* **Gruppe** (4) : **Nur lesen**
* **Andere** (4) : **Nur lesen**

Hoffentlich bietet dieses Beispiel Einblick in die Korrelation von Unix-Modi/Berechtigungen in Windows-Berechtigungen/ACLs. Dieses Dokument enthält nicht komplexere Themen wie *Effektive*, *Geerbte* oder *Spezielle* Berechtigungen. Trotz der Benutzerfreundlichkeit von Windows sind Microsofts Mechanismen für Berechtigungen und ACLs tatsächlich relativ komplex und sehr umfangreich, aber dies könnte Ihnen eine schnelle Referenz sein, um einige der Verwirrungen rund um Unix- und Windows-Berechtigungsübersetzungen zu lindern.

*Übersetzt von openai.com*

