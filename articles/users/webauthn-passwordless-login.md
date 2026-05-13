<!--
{
  "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
  "title": "WebAuthn Anmeldung  ",
  "description": "", 
  "author": ""
}
-->

## WebAuthn Passworlose Anmeldung

Web-Authentifizierung, oder kurz WebAuthn, ermöglicht einem Benutzer, sich sicher bei einer Website anzumelden, ohne ein Passwort zu verwenden – obwohl ein Benutzername weiterhin erforderlich ist. Es verwendet starke Kryptographie auf eine Weise, die extrem resistent gegenüber den häufigsten Problemen von Passwörtern ist:
* jemand hat es erraten (Brute-Force-Angriff)
* jemand hat es abgefangen (Man-in-the-Middle-Angriff)
* jemand hat Sie ausgetrickst, es preiszugeben (Phishing-Angriff)
* jemand hat es geknackt, nachdem er eine Kopie Ihrer Datenbank-Daten erhalten hat (SQL-Injection-Angriffe)
* jemand hat es gestohlen.

WebAuthn ist nicht nur sehr sicher, sondern auch sehr benutzerfreundlich! Sie müssen sich keine langen Passwörter mehr merken oder einen Passwort-Manager verwenden. Alles, was Sie brauchen, ist ein *Authentifikator*, manchmal auch *Passkey* genannt.

Ein Authentifikator kann viele Formen haben, physisch oder virtuell. Er kann ein separates Hardware-Schlüssel sein, der sich über USB, Bluetooth oder NFC mit Ihrem Gerät verbindet. Er kann Ihr Gerät selbst sein, das seinen integrierten Authentifikator mit einer PIN, Fingerabdruckleser, Gesichtserkennung oder ähnlichem biometrischen Check freigibt.

Diese Funktion funktioniert bereits auf Android- und iOS/iPadOS-Geräten, und wir arbeiten daran, sie auch unter Windows zu ermöglichen. Es kann sogar Ihr Telefon sein – derzeit ist dies mit Android-Telefonen möglich, aber diese Funktion kommt auch auf iOS/iPadOS-Geräte.

WebAuthn funktioniert nur über HTTPS und nur, wenn Ihre Website ein gültiges, vertrauenswürdiges Zertifikat dafür verwendet. Keine Sorge, Sie müssen kein zusätzliches Geld ausgeben; kostenlose Dienste wie Let's Encrypt sind in der Regel in Webhosting-Bedienfelder integriert und funktionieren einwandfrei mit WebAuthn.

WebAuthn verwendet asymmetrische Kryptographie, dieselbe bewährte Technologie, die Ihre Websites mit HTTPS sicher hält, Ihre Bankinformationen schützt und so weiter. Der private Schlüssel verlässt den Authentifikator nie. Ihre Website speichert nur einen öffentlichen Schlüssel. Selbst wenn Sie einen Datenverstoß erleiden, bleibt dem Angreifer ein praktisch nutzloser öffentlicher Schlüssel; es würde Tausende bis Millionen von CPU-Jahren dauern, ihn zu knacken, im Gegensatz zu den wenigen Minuten oder Stunden, die erforderlich sind, um den Hash eines festen Passworts zu knacken, das Sie sich merken können.

WebAuthn ist die Zukunft der Authentifizierung. Einfach, sicher und problemlos. Alles, was feste Passwörter nicht sind.

Das folgende Bild zeigt ein Hardware-Gerät, das in den USB-Anschluss eines Laptop-Computers eingesetzt wurde. Es kostete im Februar 2022 £15.

![Fotografie des Hardware-Geräts](../../../en/images/users/webauthn-passwordless-login/01-passwordless-login-hardware-device.jpg)

WebAuthn nutzt ein System-Plugin, das standardmäßig aktiviert ist. Ein **Web-Authentifizierung**-Button wird in den Standardanmeldebildschirmen von Joomla 4 und später vorhanden sein, wie im Administrator-Anmeldebildschirm veranschaulicht:

![Sicheres Administrator-Anmeldeformular](../../../en/images/users/webauthn-passwordless-login/02-passwordless-login-login-form.jpg)

## Benutzerkonfiguration

Der Benutzer muss sich zunächst mit einem normalen Benutzernamen und Passwort registrieren. Nach dem Einloggen gehen Sie zum Benutzerprofil-Formular. Für einen Administrator:

- Wählen Sie **Benutzermenü → Konto bearbeiten → W3C Web Authentication (WebAuthn) Login**, um das Formular anzuzeigen, das anfänglich keine registrierten Authentifikatoren hat.
- Wählen Sie **Neuen Authentifikator hinzufügen**

Die genaue Darstellung des nächsten Schritts hängt von Ihrem Browser ab. Typischerweise sehen Sie eine Benachrichtigung oder ein Fenster, das Sie auffordert, einen Authentifikatortyp auszuwählen oder, falls Sie einen an Ihr Gerät angeschlossenen Hardware-Authentifikator verwenden, Sie daran erinnert, den Knopf am Hardware-Authentifikator zu drücken. Aus Sicherheits- und praktischen Gründen ist die Zeitspanne für die Aktivierung des Authentifikators relativ kurz: 60 Sekunden.

![sicherer Administratoranmeldung Hardware-Aufforderung](../../../en/images/users/webauthn-passwordless-login/03-passwordless-login-hardware-propmpt.png)

Sobald Sie Ihren Authentifikator entsperren — durch Antippen eines Knopfes, Scannen Ihres Fingerabdrucks/Gesichts, Eingabe einer PIN oder einer Kombination der oben genannten, je nach Ihrem Authentifikator — verschwindet die Nachricht, der Authentifikator wird registriert und der Bildschirm erscheint wie folgt:

![sicherer Administratoranmeldung registrierter Authentifikator](../../../en/images/users/webauthn-passwordless-login/04-passwordless-login-registered-authenticator.png)

Es ist sehr wichtig zu beachten, dass Sie Authentifikatoren nur auf Ihrem eigenen Benutzerkonto registrieren oder entfernen können. Aus Sicherheitsgründen ist es selbst einem Super-User untersagt, Authentifikatoren auf anderen Benutzerkonten zu registrieren, zu bearbeiten oder hinzuzufügen.

### Authentifikatoren

Sie können jeden FIDO U2F oder FIDO2 Authentifikator verwenden. FIDO U2F ist ein älterer Standard, der eine begrenztere, weniger sichere Auswahl an kryptografischen Methoden unterstützt. FIDO2 ist der neuere Standard, der viel sicherere kryptografische Methoden unterstützt, einschließlich Elliptische Kurvenkryptographie, einer kryptografischen Methode, von der angenommen wird, dass sie selbst gegen Quantencomputer resistent ist (falls und wenn sie eine praktische Realität werden). Darüber hinaus können FIDO2 Authentifikatoren mit zusätzlichen Schutzmaßnahmen eingerichtet werden, wie einer PIN oder einer biometrischen Kontrolle (z.B. Fingerabdruckscan), was bedeutet, dass selbst wenn Sie den physischen Besitz des Authentifikators verlieren, die Person, die ihn findet, sich nicht in Ihre Websites einloggen kann.

Wenn Sie einen Hardware-Authentifikator kaufen möchten, können Sie in Ihrem bevorzugten Marktplatz, wie Amazon, nach "FIDO2" suchen. Es gibt eine breite Auswahl zur Auswahl.

Sie können auch einen Software-FIDO-Schlüssel wie Krypton als Ihren Authentifikator verwenden.

Viele Geräte haben integrierte FIDO2-kompatible Authentifikationen:

- Windows 10 und 11 verfügen über Windows Hello mit einer PIN, einem Fingerabdruckscanner, einer Gesichtserkennungskamera oder einer Kombination aus Hardware-Schlüssel und PIN. Unterstützung für Windows Hello wird dem Plugin mit dem Release-Ziel von Joomla 4.2.0 hinzugefügt.
- macOS verfügt über TouchID auf allen Laptops mit dem T2-Chipsatz oder jenen, die auf Apple Silicon basieren und den integrierten TouchID-Sensor verwenden, sowie alle auf Apple Silicon basierenden Desktops, die die neue Apple Aluminium-Tastatur mit einem Fingerabdruckscanner verwenden.
- iOS / iPadOS verfügt über TouchID auf allen Geräten mit einem Fingerabdruckscanner und FaceID auf allen neueren Geräten mit einer FaceID-Infrarotpunktprojektionskamera.
- Einige Android-Geräte haben einen Fingerabdruckscanner oder eine Gesichtserkennungskamera. Diese können auch als FIDO2-Authentifikatoren funktionieren, ab Android 9 oder neuer mit mindestens Google Chrome.
- Weitere Geräte können auch verfügbar sein. Zum Beispiel Android-Handys, die ![caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1) verwenden

### WebAuthn-kompatible Browser

Chromium- und Firefox-basierte Browser unterstützen WebAuthn seit Anfang 2019.

Safari und alle iOS/iPadOS Browser (die im Grunde genommen Safari mit einer anderen Benutzeroberfläche sind) unterstützen WebAuthn vollständig seit iOS/iPadOS 13, das Ende 2019 veröffentlicht wurde.

Praktisch gesehen sollten Sie keine Probleme haben, wenn Ihr Betriebssystem und Browser nach Mitte 2020 veröffentlicht wurden. Nur einige sehr seltene Browser unterstützen WebAuthn noch nicht.

## Authentifizierung

Um sich anzumelden, müssen Sie Ihren Benutzernamen in das entsprechende Feld des Anmeldeformulars eingeben. Sie brauchen Ihr Passwort nicht einzugeben, aber wenn Ihr Browser es automatisch ausfüllt, lassen Sie es einfach so. Das Passwort wird NICHT an den Server gesendet, wenn das Formular über die Schaltfläche Web-Authentifizierung übermittelt wird.

Daraus folgt, dass Sie sich entweder mit Ihrem Benutzernamen und Passwort oder mit Benutzernamen und Web-Authentifizierung anmelden können.

## So deaktivieren Sie das Plugin

Wenn Sie WebAuthn nicht zulassen möchten, gehen Sie einfach zur Liste der Plugins, suchen Sie System - WebAuthn Passwortloses Login in der Systemgruppe und deaktivieren Sie es. Es gibt keine Parameter, die eingestellt werden müssen.  

## Serveranforderungen

Damit WebAuthn funktioniert, müssen die folgenden Voraussetzungen erfüllt sein:

- HTTPS mit einem gültigen, signierten Zertifikat. Die meisten Hosts erlauben die Nutzung kostenloser Zertifikate von Let's Encrypt. Diese funktionieren einwandfrei mit WebAuthn.
- Die OpenSSL-Erweiterung für PHP muss installiert und aktiviert sein.
- Die PHP-Erweiterung GMP oder die PHP-Erweiterung BCmath muss installiert und aktiviert sein (eine von beiden reicht aus).
- Die Sodium-Bibliothek sollte idealerweise aktiviert sein; sie ermöglicht die Nutzung der Elliptischen-Kurven-Kryptografie auf kompatiblen FIDO2-Authentifikatoren, was, wie bereits erwähnt, die sicherste kryptografische Methode ist.

## Häufig gestellte Fragen und Fehlerbehebung

### Ich kann den „Web-Authentifizierung“-Login-Button nicht sehen

Sie greifen nicht über HTTPS auf Ihre Website zu. WebAuthn ist nur für HTTPS-Seiten mit einem gültigen Zertifikat verfügbar. Dies ist eine Sicherheitsmaßnahme, die im WebAuthn-Standard integriert ist. Das Plugin überprüft tatsächlich, ob auf die Seite über HTTPS zugegriffen wird, indem es die Uri-Klasse von Joomla verwendet. In seltenen Fällen, in denen der Server über das Protokoll lügt, sehen Sie möglicherweise den Button nicht, obwohl Ihre Seite (angeblich) HTTPS ist. Gleiches gilt, wenn Sie Ihre `configuration.php`-Datei bearbeitet und den optionalen \$live_site-Konfigurationsparameter mit einem http://-Protokoll-Präfix anstelle von https:// eingerichtet haben.

Bitte beachten Sie auch, dass Module und Komponenten von Drittanbietern, die ihr eigenes Anmeldeformular implementieren, diese Buttons möglicherweise noch nicht anzeigen. Wir haben neue Infrastruktur hinzugefügt, um sie zu unterstützen, ähnlich wie wir es in Joomla! 3.2 für die Unterstützung der Zwei-Faktor-Authentifizierung tun mussten.

### Ich muss immer noch einen Benutzernamen angeben. Soll WebAuthn nicht Benutzernamen überflüssig machen?

Nicht wirklich. Die aktuelle Spezifikation von WebAuthn bietet kein Identitätsmanagement. Webbrowser erfordern, dass wir ihnen während der Anmeldephase eine Liste akzeptabler WebAuthn-Öffentlichkeiten senden. Das bedeutet, dass wir Ihren Benutzernamen benötigen, um sie abzurufen.

Das gesagt, macht die Verwendung von WebAuthn endlich deutlich, dass Benutzernamen *nicht als Geheimnisse gelten dürfen*. Sie werden als öffentliche Informationen betrachtet, die einem Gegner frei übermittelt werden können, ähnlich wie die in der Datenbank der Website gespeicherten öffentlichen Schlüssel. Das einzige Geheimnis wird im Authentifikator selbst gespeichert und verlässt diesen nie!

### Ich habe einen Authentifikator registriert, aber beim Einloggen wird mir mitgeteilt, dass ich keinen habe. Ist das ein Fehler?

Es ist ein Fehler, aber nicht im WebAuthn-Plugin selbst.

Ein oder mehrere Plugins auf Ihrer Website werfen PHP-Hinweise, Warnungen oder Fehler und beschädigen so die von Ihrem Server gesendete Antwort. Infolgedessen kann das JavaScript auf der Seite die Serverantwort nicht analysieren und ist unsicher, ob authentifizierte Benutzer registriert sind.

Gehen Sie zum Backend Ihrer Webseite, System, Globale Konfiguration und setzen Sie die Fehlerberichterstattung auf Keine. In den meisten Fällen von fehlerhaften Kern- und 3PD-Plugins reicht dies aus. Ansonsten überprüfen Sie bitte die Ausgabe der Anfrage mit den Entwicklertools Ihres Browsers, um zu sehen, was die Anfrage korrumpiert.

### Es gibt keine Aufforderung in Safari, meinen Authentifikator zu verwenden

Das sollte mit iOS 13, iPadOS 13 und macOS Catalina oder einer neueren Version nicht mehr passieren.

Dies ist ein Safari-Fehler in älteren Versionen. Ältere Safari-Versionen haben WebAuthn nur als experimentelle Funktion und nicht ganz fertig implementiert.

### Ich kann keinen biometrischen Sensor (TouchID, Fingerabdruck, Windows Hello) verwenden

Einige ältere Browser auf Grundlage von Chromium (außer Google Chrome selbst) hatten keine vollständige Unterstützung für eingebaute Authentifikatoren. Sie stürzten ab oder hängten sich auf, wenn Sie versuchten, einen zu verwenden. Diese Probleme wurden etwa Mitte 2020 in diesen Browsern behoben.

Wenn Sie Windows verwenden, beachten Sie, dass Ihr Gerät einen Trusted Platform Module (TPM)-Chip haben MUSS und dieser im BIOS aktiviert sein muss. Nur ein Windows Hello-kompatibler biometrischer Sensor reicht nicht aus. Dies ist eine Sicherheitsmaßnahme im WebAuthn-Standard selbst: Die Authentifikator-Informationen müssen mit sicherer, manipulationssicherer Hardware verarbeitet werden, um Schlüsselunterwanderung zu verhindern (z. B. kann Malware auf dem Computer den Schlüssel nicht stehlen, der zur Authentifizierung verwendet wird).

Denken Sie schließlich daran, dass die Unterstützung von Windows Hello noch in Arbeit ist und mit Joomla 4.2 veröffentlicht wird.

### Warum sollte ich mir die Mühe machen, einen Hardware-Token zu verwenden, wenn ich einen Software-Authentifikator verwenden kann?

Der Dreh- und Angelpunkt von WebAuthn ist das absolute Geheimhalten des privaten Schlüssels. Er ist nur dem Authentifikator bekannt und sollte unmöglich nach außen kommuniziert werden können.

Im Fall eines Hardware-Authentifikators, sei es ein separates Hardwaregerät oder ein in Ihr Gerät integrierter TPM / Secure Enclave, ist dies aufgrund der Art dieser Hardware gegeben.

Ein Software-Authentifikator erzeugt einen geheimen Schlüssel und speichert ihn im Dateisystem. Es ist jedoch immer noch eine reguläre Softwareanwendung, die in Ihrem regulären Betriebssystem läuft, sei es auf Ihrem Telefon oder Ihrem Computer. Daher ist sie anfällig für mehrere Arten von Angriffen, durch die Informationen unbemerkt gestohlen werden können (Sicherheitsprobleme in der Software selbst, Malware, die Spectre-artige Schwachstellen in modernen CPUs nutzt, usw.).

Ein Software-Authentifikator ist also weitaus bequemer und sicherer als ein reguläres Passwort, aber ein Hardware-Authentifikator bietet die beste Sicherheit. Wählen Sie Ihren Authentifikator je nach Budget und Sicherheitsbedarf.

Da der Preis für einen FIDO-Schlüssel – der mit WebAuthn kompatibel ist – auf Amazon unter 10 € liegt, können Sie in den meisten praktischen Anwendungsfällen einen Hardware-Authentifikator verwenden.

### Warum sind die Anmeldedaten in der Datenbank verschlüsselt? Ist das nicht übertrieben?

Das Einzige, was in der Datenbank gespeichert ist, ist der öffentliche Schlüssel, den der Authentifikator bei der Bestätigungszeremonie (das ist die formale Bezeichnung für die Registrierung eines Authentikators nach der WebAuthn-Spezifikation) zurückgibt. Als öffentlicher Schlüssel muss er nicht vor dem Lesen geschützt werden. Selbst wenn ein unbefugter Benutzer in der Lage wäre, diese Informationen zu lesen, könnte er den Authentifikator z. B. nicht durch Klonen nachahmen.

Wenn ein böswilliger Benutzer jedoch Schreibzugriff auf die `#__webauthn_credentials`-Datenbanktabelle hätte, ohne Lesezugriff auf das Dateisystem und ohne Schreibzugriff auf eine andere Tabelle, könnte er theoretisch **seinen eigenen** Authentifikator hinzufügen und somit den Zielnutzer im System nachahmen. Dies ist ein sehr theoretischer Angriff, da sie auch wissen müssten, welches Benutzerhandle der angegriffene Benutzer hat, was ohne Insiderwissen über die Seite selbst schwer abzuleiten ist. Außerdem ist es äußerst unwahrscheinlich, dass jemand nur Schreibzugriff auf diese Tabelle und nicht auf die gesamte Datenbank hat (in diesem Fall könnten sie einen neuen Super-Benutzer erstellen). Trotzdem verschlüsseln wir die Anmeldedaten, um es unmöglich zu machen, dass dieser völlig theoretische Angriff erfolgreich ist.

Wir sind uns voll bewusst, dass wenn ein Benutzer Lesezugriff auf das Server-Dateisystem hat, er Zugriff auf den Verschlüsselungsschlüssel und die Datenbankverbindungsinformationen hat, die alle in `configuration.php` gespeichert sind. In diesem Fall sind Sie jedoch bereits gehackt: Der Angreifer kann `configuration.php` lesen, daher weiß er, wie er sich mit Ihrer Datenbank verbinden kann. In diesem Fall kann er mit Ihrer Seite tun, was er will, einschließlich Löschen aller Super-Benutzer und Erstellen eines eigenen Super-Benutzeraccounts. Es gibt daher keinen Grund, diese Situation anzugehen; Sie wären vollständig kompromittiert (gehackt). Das Einzige, was ein Rettungsanker sein könnte, sind regelmäßige, getestete, dezentrale Backups.

### Ich habe die Zwei-Faktor-Authentifizierung eingerichtet, aber ich bin eingeloggt, ohne meinen Geheimschlüssel anzugeben. Ist das nicht unsicher?

Nein, es ist beabsichtigt und bewusst so gestaltet.

Als wir die Zwei-Faktor-Authentifizierung (TFA) in Joomla! 3.2 einführten, konnten Sie sich nur mit einem Benutzernamen und Passwort auf Ihrer Seite anmelden. Passwörter können gestohlen oder erraten werden. Daher war TFA die einzige Möglichkeit, bei Zielen mit hohem Risiko und hohem Wert ein gewisses Maß an Sicherheit zu bieten. Das war im Jahr 2013.

WebAuthn ist eine völlig andere Authentifizierungslösung, die keines der Probleme fester Passwörter hat. Es nutzt starke Kryptografie und sichere Hardware, um es praktisch unmöglich zu machen, die kryptografischen Authentifizierungsschlüssel zu untergraben. Es ist auch nicht phishbar, d. h. Sie können nicht dazu verleitet werden, es auf einer nachgeahmten Seite zu verwenden, da die WebAuthn-Anmeldedaten an den genauen Domainnamen gebunden sind, für den sie ausgestellt wurden (ja, wenn Sie mehrere Domains für Ihre Seite verwenden oder Ihre Seite auf eine andere Domain übertragen, müssen Sie alle Ihre WebAuthn-Authentifikatoren neu registrieren – genau richtig!). Daher ist die Authentifizierung mit WebAuthn unglaublich sicher und übertrifft die Gründe, die TFA erforderlich machten. Dies bedeutet, dass wenn Sie sich erfolgreich mit WebAuthn authentifizieren, der TFA-Geheimschlüssel nicht überprüft werden muss und daher auch nicht überprüft wird.

Ideal wäre es, wenn Sie sich nur mit WebAuthn auf Ihrer Seite anmelden könnten. Das ist eine Funktion, an der wir arbeiten und die Sie möglicherweise nicht aktivieren möchten; Schließlich, wenn sich Ihr Domainname ändert oder Sie den Zugriff auf oder alle Ihre WebAuthn-Authentikatoren verlieren oder zurücksetzen, wären Sie von Ihrer Seite ausgeschlossen. Daher sollten Sie TFA weiterhin auf Ihrem Benutzerkonto aktivieren, da Passworthlogin weiterhin als Rückfallebene für das Anmelden auf Ihrer Seite verwendet werden kann und vor bekannten Angriffen gegen feste Passwörter geschützt werden muss.

### Ist TFA nicht gut genug? Warum brauchen wir WebAuthn?

TFA allein reicht in den meisten Fällen aus, leidet jedoch an zwei Problemen.

Erstens hat er eine ziemlich umständliche Benutzererfahrung. Sie müssen Ihren sich ständig ändernden Geheimschlüssel zusammen mit Ihrem Benutzernamen und Passwort angeben. Die meisten Leute verwenden TOTP (die sechsstellige PIN, die sich alle 30 Sekunden ändert), was den Login verlangsamt und Benutzer frustriert. Die Verwendung eines YubiKey ist wesentlich schneller, jedoch auch teurer und komplizierter, wenn Sie mehr als ein paar Benutzer auf der Seite haben. Ein YubiKey hat auch eine erwartete Lebensdauer von etwa 2 Jahren im täglichen Gebrauch, wenn er Einmalpasswörter generiert (er läuft aus dem Einmalspeicher, der verwendet wird, um die von ihm ausgestellten Signaturen zu verfolgen).

Zweitens sind Sie, wenn Sie TOTP verwenden, immer noch anfällig für Sicherheitsprobleme wie Keylogger, Phishing und die Möglichkeit, dass der Geheimschlüssel, der zur Generierung des TOTPs verwendet wird, gestohlen wird. Darüber hinaus ist es bei einer Million Möglichkeiten und dreißig Sekunden, sie zu überprüfen, denkbar, dass ein Angreifer Glück hat, da Joomla Ihr Konto nicht sperrt oder anderweitig die Rate fehlgeschlagener Anmeldeversuche beschränkt. Während diese Schutzmaßnahmen implementiert werden könnten, könnte die Implementierung selbst missbraucht werden, um eine Denial-of-Service-Situation zu schaffen, die einen legitimen Benutzer ausschließt, während der Angreifer damit beschäftigt ist, es zu infiltrieren. Es ist ein Fall, in dem das Heilmittel schlimmer ist als die Krankheit.

WebAuthn verbessert das Benutzererlebnis erheblich. Große Browser haben WebAuthn übernommen und bieten ein überzeugendes Benutzererlebnis und führen die Benutzer erfolgreich zur Verwendung von Authentifikatoren. Das Einloggen mit WebAuthn ist bequemer, sogar im Vergleich zur Auto-Fill-Funktion eines Passwort-Managers. Mit den neuesten Versionen mobiler Betriebssysteme wird diese Erfahrung, die einst leicht verwirrend war, schnell einfacher als Passwörter und TFA es je waren.

Wo WebAuthn wirklich überzeugt, ist im Bereich Sicherheit. Aufgrund der Verwendung von sicherer Hardware und der starken Validierung des Domainnamens der Seite ist es praktisch immun gegen Keylogger, Phishing und Schlüsselmanipulation. Es hat sogar eingebaute Schutzmechanismen gegen das Klonen von Schlüsseln. Ja, Sie können Ihre Hardware weiterhin verlieren – aber FIDO2-Authentifikatoren, sei es externe Geräte oder integrierte, können mit einem PIN oder biometrischen Merkmalen gesperrt werden. Insgesamt ist die Verwendung von WebAuthn mit FIDO2-Authentifikatoren diebstahl- und verlustresistenter als Ihre Haus- oder Autoschlüssel.

## Entwicklerhinweise

### Zusätzliche Login-Buttons

Das Plugin-Modul und com_users verwenden jetzt das onUserLoginButtons-Ereignis, das in `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` definiert und aufgerufen wird, um die Definitionen zusätzlicher Buttons abzurufen, die nach dem regulären Login-Button platziert werden müssen.

Alle Entwickler, die ein Login-Modul oder allgemeiner ein Login-Formular implementieren, sollten ebenfalls die öffentliche statische Methode `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` verwenden, um diese Definitionen abzurufen und die Buttons zu rendern, um ihre Software vollständig mit Joomla 4 kompatibel zu machen.

Entwickler, die benutzerdefinierte Buttons implementieren möchten, sollten sich ansehen, wie das WebAuthn-System-Plugin diese Funktionalität implementiert. Solche Buttons können verwendet werden, um Dienste von Drittanbietern für Single Sign-On oder sogar das Einloggen mit Identitätsdiensten von Drittanbietern, wie sie von beliebten sozialen Medien (Facebook, Google, Twitter, GitHub etc.) angeboten werden, zu implementieren.

Diese Änderung hat keine nachteiligen Auswirkungen auf die Abwärtskompatibilität. Drittanbieter-Login-Module und Login-Formulare funktionieren weiterhin normal, selbst wenn sie das Feature für zusätzliche Login-Buttons nicht implementieren, mit der bemerkenswerten Ausnahme der Integrationen, die durch diese Funktion ermöglicht werden, wie die Web-Authentifizierung selbst. Das heißt, sie werden nicht aufhören zu funktionieren (was einen Bruch der Abwärtskompatibilität bedeuten würde), jedoch werden sie nicht feature-komplett sein.

### Erlauben von com_ajax auf der Backend-Login-Seite

Die Administrator-Login-Seite setzt com_ajax auf die Whitelist in der AdministratorApplication, damit es verwendet werden kann, um Anfragen von Gastnutzern zu bearbeiten.

Diese Änderung verursacht keine Probleme mit der Abwärtskompatibilität, solange Entwickler vernünftige Praktiken anwenden und nicht davon ausgehen, dass ein Aufruf durch com_ajax im Backend ein Beweis dafür ist, dass der Benutzer im Backend eingeloggt ist. Das wäre eine schlechte Sicherheitspraktik. Die vernünftige Praxis besteht darin, Joomlas Benutzerobjekt zu verwenden, um zu erkennen, ob es sich um einen Gastbenutzer handelt und ob nicht, ob der Benutzer eine Erlaubnis hat, die erforderlich ist, um die durch com_ajax angeforderte Aktion auszuführen. Das heißt, wenn diese Änderung Ihren Code gebrochen hat, war Ihr Code bereits fehlerhaft und musste ohnehin neu überarbeitet werden.

## Weitere Informationen

Die ursprüngliche Dokumentation dieser Funktion befindet sich im Pull-Request unter [PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Übersetzt von openai.com*

