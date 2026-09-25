<!--
{
    "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
    "title": "Anmeldung mit Passkey",
    "description": " ",
    "author": ""
}
-->

## Einführung

Die Anmeldung mit Passkey, früher als Web Authentication oder kurz WebAuthn
bekannt, ermöglicht es einem Benutzer, sich sicher bei einer Website
anzumelden, ohne ein Passwort zu verwenden, obwohl weiterhin ein
Benutzername erforderlich ist. Sie verwendet starke Kryptografie auf eine
Art und Weise, die äußerst widerstandsfähig gegen die häufigsten Probleme
von Passwörtern ist:

* jemand hat es erraten (Brute-Force-Angriff)
* jemand hat es abgefangen (Man-in-the-Middle-Angriff)
* jemand hat Sie dazu gebracht, es preiszugeben (Phishing-Angriff)
* jemand hat es geknackt, nachdem er eine Kopie Ihrer Datenbankdaten erhalten hatte
  (SQL-Injection-Angriffe)
* jemand hat es gestohlen.

Die Anmeldung mit Passkey ist nicht nur sehr sicher, sondern auch äußerst
benutzerfreundlich! Sie müssen sich keine langen Passwörter mehr merken
oder einen Passwortmanager verwenden. Alles, was Sie benötigen, ist ein
*Authentifikator*, der manchmal auch *Passkey* genannt wird.

Ein Authentifikator kann viele Formen haben, physisch oder virtuell. Es kann
sich um einen separaten Hardwareschlüssel handeln, der über USB, Bluetooth
oder NFC mit Ihrem Gerät verbunden wird. Es kann auch Ihr Gerät selbst sein,
das seinen integrierten Authentifikator mit einer PIN, einem
Fingerabdruckleser, einem Gesichtsscan oder einer ähnlichen biometrischen
Prüfung entsperrt.

Diese Funktion funktioniert bereits auf Android- und iOS-/iPadOS-Geräten,
und wir arbeiten daran, sie auch unter Windows zu aktivieren. Es kann sogar
Ihr Telefon sein – derzeit ist dies mit Android-Telefonen möglich, aber diese
Funktion kommt auch auf iOS-/iPadOS-Geräte.

Die Anmeldung mit Passkey funktioniert nur über HTTPS und nur, wenn Ihre
Website ein gültiges, vertrauenswürdiges Zertifikat dafür verwendet. Keine
Sorge, Sie müssen kein zusätzliches Geld ausgeben; kostenlose Dienste wie
Let's Encrypt sind normalerweise in die Bedienfelder von Webhosting-Anbietern
integriert und funktionieren problemlos mit der Anmeldung per Passkey.

Die Anmeldung mit Passkey verwendet Kryptografie mit öffentlichen Schlüsseln,
dieselbe bewährte Technologie, die Ihre Websites mit HTTPS schützt, Ihre
Bankdaten sicher hält und vieles mehr. Der private Schlüssel verlässt den
Authentifikator niemals. Ihre Website speichert nur einen öffentlichen
Schlüssel. Selbst wenn Sie Opfer eines Datenlecks werden, bleibt dem
Angreifer ein praktisch nutzloser öffentlicher Schlüssel; es würde Tausende
bis Millionen CPU-Jahre dauern, ihn zu knacken, im Gegensatz zu den wenigen
Minuten oder Stunden, die zum Knacken des Hashes eines festen Passworts
benötigt werden, das Sie sich merken können.

Die Anmeldung mit Passkey ist die Zukunft der Authentifizierung. Einfach,
sicher und problemlos. Alles, was feste Passwörter nicht sind.

Das folgende Bild zeigt ein Hardwaregerät, das in den USB-Anschluss eines
Laptops eingesteckt ist. Es kostete im Februar 2022 15 £.

![Foto eines Hardwaregeräts](../../../en/images/users/passkey-login/01-hardware-device.jpg)

Die Anmeldung mit Passkey verwendet ein System-Plugin, das standardmäßig
aktiviert ist. Eine Schaltfläche **Mit Passkey anmelden** wird in den
standardmäßigen Anmeldebildschirmen von Joomla 4 und höher angezeigt, wie
im Anmeldebildschirm des Administrators dargestellt:

![Sicheres Administrator-Anmeldeformular](../../../en/images/users/passkey-login/02-login-form.png)

## Benutzerkonfiguration

Der Benutzer muss sich zunächst mit einem normalen Benutzernamen und Passwort
registrieren. Nach der Anmeldung wechseln Sie zum Formular „Benutzerprofil“.
Für einen Administrator:

- Wählen Sie **Benutzermenü → Konto bearbeiten → Passkey-Anmeldung**, um das
  Formular anzuzeigen, in dem zunächst keine Authentifikatoren registriert
  sind.
- Wählen Sie **Neuen Passkey hinzufügen**

Die genaue Darstellung des nächsten Schritts hängt von Ihrem Browser ab.
Normalerweise sehen Sie eine Warnung, Nachricht oder ein Fenster, in dem Sie
aufgefordert werden, einen Authentifikatortyp auszuwählen, oder, wenn Sie
einen mit Ihrem Gerät verbundenen Hardware-Authentifikator verwenden, daran
erinnert werden, die Taste am Hardware-Authentifikator zu drücken. Aus
Sicherheitsgründen und praktischen Erwägungen steht zum Aktivieren des
Authentifikators nur ein relativ kurzes Zeitintervall zur Verfügung:
60 Sekunden.

![Sichere Aufforderung zur Hardware-Authentifizierung bei der Administrator-Anmeldung](../../../en/images/users/passkey-login/03-hardware-prompt.png)

Sobald Sie Ihren Authentifikator entsperren – durch Drücken einer Taste,
Scannen Ihres Fingerabdrucks oder Gesichts, Eingeben einer PIN oder einer
Kombination daraus, je nach Ihrem Authentifikator – verschwindet die
Nachricht, der Authentifikator wird registriert und der Bildschirm sieht wie
folgt aus:

![Sichere Administrator-Anmeldung mit registriertem Authentifikator](../../../en/images/users/passkey-login/04-registered-authenticator.png)

Es ist sehr wichtig zu beachten, dass Sie Authentifikatoren nur für Ihr
eigenes Benutzerkonto registrieren oder entfernen können. Aus
Sicherheitsgründen ist es selbst einem Super User nicht gestattet,
Authentifikatoren für andere Benutzerkonten zu registrieren, zu bearbeiten
oder hinzuzufügen.

### Authentifikatoren

Sie können jeden FIDO-U2F- oder FIDO2-Authentifikator verwenden. FIDO U2F ist ein älterer
Standard, der eine begrenztere und weniger sichere Auswahl an
kryptografischen Methoden unterstützt. FIDO2 ist der neuere Standard, der wesentlich
sicherere kryptografische Methoden unterstützt, einschließlich der Kryptografie
mit elliptischen Kurven – einer kryptografischen Methode, von der man annimmt,
dass sie sogar gegen Quantencomputer resistent ist (falls und sobald diese
praktische Realität werden). Außerdem können FIDO2-Authentifikatoren so eingerichtet
werden, dass sie über zusätzliche Schutzmaßnahmen wie eine
PIN oder eine biometrische Kontrolle (z. B. Fingerabdruckscan) verfügen. Das bedeutet, dass selbst
wenn Sie den physischen Besitz des Authentifikators verlieren, die Person, die ihn
findet, sich nicht bei Ihren Websites anmelden kann.

Wenn Sie einen Hardware-Authentifikator kaufen möchten, können Sie auf
Ihrem bevorzugten Marktplatz, beispielsweise Amazon, nach
„FIDO2“ suchen. Es gibt eine große Auswahl.

Sie können auch einen Software-FIDO-Schlüssel wie Krypton als Ihren
Authentifikator verwenden.

Viele Geräte verfügen über eine integrierte FIDO2-konforme Authentifizierung:

- Windows 10 und 11 verfügen über Windows Hello mit einer PIN, einem Fingerabdruckscanner,
  einer Kamera zur Gesichtserkennung oder einer Kombination aus Hardwareschlüssel und PIN.
- macOS verfügt auf allen Laptops mit dem T2-Chipsatz oder auf Geräten mit
  Apple Silicon über TouchID mithilfe des integrierten TouchID-Sensors sowie auf allen
  Desktops mit Apple Silicon über die neue Apple-Aluminiumtastatur mit
  Fingerabdruckscanner.
- iOS / iPadOS verfügt auf allen Geräten mit Fingerabdruckscanner über TouchID und
  auf allen neueren Geräten mit einer Infrarotkamera zur Punktprojektion für FaceID
  über FaceID.
- Einige Android-Geräte verfügen über einen Fingerabdruckscanner oder eine Kamera
  zur Gesichtserkennung. Diese können ebenfalls als FIDO2-Authentifikatoren
  funktionieren, unter Android 9 oder höher bei Verwendung von mindestens Google Chrome.
- Möglicherweise sind auch andere Geräte verfügbar. Zum Beispiel Android-Telefone mit
  [caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Mit der Passkey-Anmeldung kompatible Browser

Praktisch gesehen sollten Sie keine Probleme haben, wenn Ihr Betriebssystem und Ihr Browser
nach Mitte 2020 veröffentlicht wurden. Nur einige sehr ungewöhnliche
Browser unterstützen die Passkey-Anmeldung noch nicht.

## Authentifizierung

Für die Anmeldung müssen Sie Ihren Benutzernamen in das Feld „Benutzername“ des Anmeldeformulars eingeben.
Sie müssen Ihr Passwort nicht eingeben. Wenn Ihr Browser es jedoch für
Sie eingibt, lassen Sie es einfach stehen. Das Passwort wird NICHT an den Server
gesendet, wenn das Formular über die Schaltfläche „Web-Authentifizierung“ übermittelt wird.

Daraus folgt, dass Sie sich entweder mit Ihrem Benutzernamen und Passwort oder
mit Ihrem Benutzernamen und der Passkey-Anmeldung anmelden können.

## So deaktivieren Sie das Plugin

Wenn Sie die Passkey-Anmeldung nicht zulassen möchten, rufen Sie einfach die Liste der Plugins auf und
suchen Sie in der Gruppe „System“ nach dem Plugin **System – Passkey (Passwortlose Anmeldung)**
und deaktivieren Sie es. Es müssen keine Parameter festgelegt werden.

## Serveranforderungen

Damit die Passkey-Anmeldung funktioniert, müssen die folgenden Voraussetzungen erfüllt sein:

- HTTPS mit einem gültigen, signierten Zertifikat. Bei den meisten Hostern können Sie kostenlos
  von Let's Encrypt ausgestellte Zertifikate verwenden. Diese funktionieren
  mit der Passkey-Anmeldung einwandfrei.
- Die OpenSSL-Erweiterung für PHP muss installiert und aktiviert sein.
- Die PHP-Erweiterung GMP oder die PHP-Erweiterung BCmath muss installiert
  und aktiviert sein (eine von beiden genügt).
- Die Sodium-Bibliothek sollte idealerweise aktiviert sein; sie ermöglicht die Verwendung der
  Kryptografie mit elliptischen Kurven auf kompatiblen FIDO2-Authentifikatoren,
  die, wie bereits erwähnt, die sicherste kryptografische Methode ist.

## Häufig gestellte Fragen und Fehlerbehebung

### Die Schaltfläche *Mit Passkey anmelden* wird nicht angezeigt

Sie greifen nicht über HTTPS auf Ihre Website zu. Die Passkey-Anmeldung ist nur für
HTTPS-Websites mit einem gültigen Zertifikat verfügbar. Dies ist eine Sicherheitsmaßnahme,
die im Standard für die Passkey-Anmeldung verankert ist. Das Plugin prüft tatsächlich,
ob über HTTPS auf die Website zugegriffen wird, und verwendet dazu die Uri-Klasse von Joomla.
In seltenen Fällen, in denen der Server ein falsches Protokoll meldet, wird die Schaltfläche
möglicherweise nicht angezeigt, obwohl Ihre Website (angeblich) HTTPS verwendet. Dasselbe gilt,
wenn Sie Ihre Datei configuration.php bearbeitet und den optionalen Konfigurationsparameter
\$live_site mit dem Protokollpräfix http:// statt https:// eingerichtet haben.

Beachten Sie außerdem, dass Login-Module und -Komponenten von Drittanbietern, die
ihr eigenes Anmeldeformular implementieren, diese Schaltflächen möglicherweise noch nicht
anzeigen. Wir haben eine neue Infrastruktur hinzugefügt, um sie zu unterstützen – ähnlich wie bei
den erforderlichen Anpassungen in Joomla! 3.2 zur Unterstützung der Zwei-Faktor-Authentifizierung.

### Ich muss noch einen Benutzernamen angeben. Sollte die Passkey-Anmeldung Benutzernamen nicht überflüssig machen?

Nicht wirklich. Die aktuelle Spezifikation der Passkey-Anmeldung bietet keine
Identitätsverwaltung. Webbrowser verlangen, dass wir ihnen während der
Anmeldephase eine Liste akzeptabler öffentlicher Schlüssel für die
Passkey-Anmeldung senden. Das bedeutet, dass wir deinen Benutzernamen benötigen,
um diese abzurufen.

Allerdings macht die Verwendung der Passkey-Anmeldung endlich deutlich, dass
Benutzernamen *nicht als Geheimnisse betrachtet werden sollen*. Sie gelten als
öffentliche Informationen, die genau wie die öffentlichen Schlüssel in der
Datenbank der Website frei an einen Angreifer übermittelt werden können. Das
einzige Geheimnis wird im Authentifikator selbst gespeichert und verlässt den
Authentifikator niemals!

### Ich habe einen Authentifikator registriert, aber beim Anmeldeversuch wird mir mitgeteilt, dass ich keinen registriert habe. Ist das ein Fehler?

Es handelt sich um einen Fehler, aber nicht im Passkey-Anmeldungs-Plugin selbst.

Ein oder mehrere Plugins auf deiner Website erzeugen PHP-Hinweise, -Warnungen
oder -Fehler und beschädigen dadurch die von deinem Server gesendete Antwort.
Infolgedessen kann das JavaScript auf der Seite die Serverantwort nicht
analysieren und weiß nicht sicher, ob der Benutzer Authentifikatoren
registriert hat.

Gehe im Backend deiner Website zu System, Globale Konfiguration und setze die
Fehlerberichterstattung auf Keine. In den meisten Fällen fehlerhafter Core- und
Drittanbieter-Plugins reicht dies aus. Untersuche andernfalls die Ausgabe der
Anfrage mithilfe der Entwicklertools deines Browsers, um festzustellen, wodurch
die Anfrage beschädigt wird.

### In Safari wird keine Aufforderung angezeigt, meinen Authentifikator zu verwenden

Dies sollte mit iOS 13, iPadOS 13 und macOS
Catalina oder einer späteren Version nicht mehr vorkommen.

Dies ist ein Safari-Fehler in älteren Safari-Versionen. Ältere Versionen von
Safari unterstützten die Passkey-Anmeldung nur als experimentelle Funktion und
diese war noch nicht vollständig fertiggestellt.

### Ich kann keinen biometrischen Sensor verwenden (TouchID, Fingerabdruck, Windows Hello)

Einige ältere Chromium-basierte Browser (mit Ausnahme von Google Chrome selbst)
unterstützten integrierte Authentifikatoren nicht vollständig. Bei dem Versuch,
einen solchen zu verwenden, stürzten sie ab oder hängten sich auf. Diese
Probleme wurden in diesen Browsern etwa Mitte 2020 behoben.

Wenn du Windows verwendest, beachte bitte, dass dein Gerät unbedingt über einen
Trusted Platform Module-(TPM-)Chip verfügen muss und dieser im BIOS aktiviert
sein muss. Ein mit Windows Hello kompatibler biometrischer Sensor allein reicht
nicht aus. Dies ist eine Sicherheitsvorkehrung des Passkey-Anmeldestandards
selbst: Die Informationen des Authentifikators müssen mithilfe sicherer,
manipulationsgeschützter Hardware verarbeitet werden, um eine Unterwanderung
des Schlüssels zu verhindern (beispielsweise kann auf dem Computer ausgeführte
Schadsoftware den zur Authentifizierung verwendeten Schlüssel nicht stehlen).

Beachte schließlich, dass die Unterstützung für Windows Hello noch in Arbeit
ist und mit Joomla 4.2 veröffentlicht wird.

### Wenn ich einen Software-Authentifikator verwenden kann, warum sollte ich dann einen Hardware-Token verwenden?

Der entscheidende Punkt der Passkey-Anmeldung ist die absolute Geheimhaltung
des privaten Schlüssels. Er ist ausschließlich dem Authentifikator bekannt und
sollte nicht in der Lage sein, mit der Außenwelt zu kommunizieren.

Bei einem Hardware-Authentifikator, unabhängig davon, ob es sich um ein
eigenständiges Hardwaregerät oder um ein in dein Gerät integriertes TPM bzw.
eine Secure Enclave handelt, ist dies bereits durch die Beschaffenheit dieser
Hardware gewährleistet.

Ein Software-Authentifikator erzeugt einen geheimen Schlüssel und speichert ihn
im Dateisystem. Dennoch handelt es sich weiterhin um eine gewöhnliche
Softwareanwendung, die innerhalb deines normalen Betriebssystems ausgeführt
wird, unabhängig davon, ob es das deines Smartphones oder deines Computers
ist. Dadurch ist sie anfällig für verschiedene Angriffskategorien, mit denen
Informationen heimlich gestohlen werden können (Sicherheitsprobleme in der
Software selbst, Schadsoftware, die Spectre-ähnliche Schwachstellen in modernen
CPUs ausnutzt usw.).

Ein Software-Authentifikator ist also wesentlich bequemer und sicherer als ein
gewöhnliches Passwort, aber ein Hardware-Authentifikator bietet die beste
Sicherheit. Wähle deinen Authentifikator entsprechend deinem Budget und deinen
Sicherheitsanforderungen aus.

Da der Preis eines FIDO-Schlüssels (der mit der Passkey-Anmeldung kompatibel
ist) bei Amazon unter 20 € liegt, kannst du in den meisten praktischen
Anwendungsfällen einen Hardware-Authentifikator verwenden.

### Warum werden die Anmeldedaten in der Datenbank verschlüsselt? Ist das nicht übertrieben?

Das Einzige, was in der Datenbank gespeichert wird, ist der öffentliche Schlüssel, den der Authentifikator zurückgibt, wenn wir die Beglaubigungszeremonie durchführen (so lautet der Fachbegriff für die Registrierung eines Authentifikators gemäß der Passkey-Anmeldespezifikation). Da es sich um einen öffentlichen Schlüssel handelt, muss er nicht vor dem Auslesen geschützt werden. Selbst wenn ein nicht autorisierter Benutzer diese Informationen auslesen könnte, wäre er nicht in der Lage, den Authentifikator zu imitieren, beispielsweise durch Klonen.

Wenn ein böswilliger Benutzer jedoch nur Schreibzugriff auf die Datenbanktabelle `#__webauthn_credentials` hätte, ohne Lesezugriff auf das Dateisystem und ohne Schreibzugriff auf irgendeine andere Tabelle, könnte er theoretisch **seinen eigenen** Authentifikator hinzufügen und dadurch den anvisierten Benutzer im System imitieren. Dies ist ein sehr theoretischer Angriff, da der Angreifer außerdem die Benutzerkennung des angegriffenen Benutzers kennen müsste, die sich ohne gewisse interne Kenntnisse über die Website selbst nur schwer ermitteln lässt. Außerdem ist es äußerst unwahrscheinlich, dass jemand nur auf diese Tabelle und nicht auf die gesamte Datenbank Schreibzugriff hat (in diesem Fall könnte er einen neuen Super User erstellen). Trotzdem verschlüsseln wir die Anmeldedaten, um auch diesen rein theoretischen Angriff unmöglich zu machen.

Uns ist völlig bewusst, dass ein Benutzer mit Lesezugriff auf das Serverdateisystem Zugriff auf den Verschlüsselungsschlüssel und die Datenbankverbindungsinformationen hat, die allesamt in der configuration.php gespeichert sind. In diesem Fall wurden Sie jedoch bereits gehackt: Der Angreifer kann die configuration.php lesen und weiß daher, wie er eine Verbindung zu Ihrer Datenbank herstellen kann. In diesem Fall kann er mit Ihrer Website tun, was er möchte, einschließlich des Löschens aller vorhandenen Super User und des Erstellens eines eigenen Super-User-Kontos. Daher gibt es keinen Grund, diese Situation zu behandeln; Ihre Website wäre vollständig kompromittiert (gehackt). Das Einzige, was Sie noch retten könnte, sind regelmäßige, getestete Backups außerhalb der Website.

### Ich habe die Zwei-Faktor-Authentifizierung eingerichtet, aber ich bin angemeldet, ohne meinen geheimen Schlüssel anzugeben. Ist das nicht unsicher?

Nein, das ist beabsichtigt und entspricht dem Design.

Als wir die Zwei-Faktor-Authentifizierung (TFA) in Joomla! 3.2 eingeführt haben, konnten Sie sich nur mit einem Benutzernamen und einem Passwort auf Ihrer Website anmelden. Passwörter können gestohlen oder erraten werden. Daher war TFA die einzige Möglichkeit, ein Mindestmaß an Sicherheit für Ziele mit hohem Risiko und hohem Wert zu bieten. Das war im Jahr 2013.

Die Passkey-Anmeldung ist eine völlig andere Authentifizierungslösung, bei der keines der Probleme feststehender Passwörter auftritt. Sie verwendet starke Kryptografie und sichere Hardware, um es praktisch unmöglich zu machen, die kryptografischen Authentifizierungsschlüssel zu kompromittieren. Außerdem ist sie nicht durch Phishing angreifbar, d. h. Sie können nicht dazu verleitet werden, sie auf einer imitierenden Website zu verwenden, da die Anmeldedaten für die Passkey-Anmeldung an den exakten Domainnamen gebunden sind, für den sie ausgestellt wurden (ja, wenn Sie mehrere Domains für Ihre Website verwenden oder Ihre Website auf eine andere Domain übertragen, müssen Sie alle Ihre Authentifikatoren für die Passkey-Anmeldung erneut registrieren – genau!). Daher ist die Authentifizierung mit der Passkey-Anmeldung unglaublich sicher und macht die Gründe für die TFA überflüssig. Das bedeutet, dass der geheime TFA-Schlüssel überhaupt nicht überprüft werden muss – und daher auch nicht überprüft wird –, wenn Sie sich erfolgreich mit der Passkey-Anmeldung authentifizieren.

In einer idealen Welt könnten Sie sich nur mit der Passkey-Anmeldung auf Ihrer Website anmelden. An dieser Funktion arbeiten wir, und möglicherweise möchten Sie sie nicht aktivieren; schließlich wären Sie von Ihrer Website ausgesperrt, wenn sich Ihr Domainname ändert oder Sie den Zugriff auf alle Ihre Authentifikatoren für die Passkey-Anmeldung verlieren oder sie zurücksetzen. Daher sollten Sie TFA weiterhin für Ihr Benutzerkonto aktivieren, da die Anmeldung per Passwort weiterhin als Ausweichmöglichkeit für die Anmeldung auf Ihrer Website verwendet werden kann und vor bekannten Angriffen auf feststehende Passwörter geschützt werden muss.

### Reicht TFA nicht aus? Warum benötigen wir die Passkey-Anmeldung?

TFA allein ist in den meisten Fällen ausreichend, hat aber zwei Nachteile.

Erstens ist die Benutzererfahrung eher umständlich. Sie müssen Ihren
sich ständig ändernden geheimen Schlüssel zusammen mit Ihrem Benutzernamen
und Passwort angeben. Die meisten Menschen verwenden TOTP (die sechsstellige
PIN, die sich alle 30 Sekunden ändert), was die Anmeldung verlangsamt
und Benutzer leicht frustriert. Die Verwendung eines YubiKeys ist deutlich
schneller, aber auch teurer und bei mehr als nur einigen Benutzern auf der
Website komplizierter bereitzustellen. Ein YubiKey hat bei der Generierung
von Einmalpasswörtern zudem eine erwartete Lebensdauer von etwa zwei Jahren
bei täglicher Nutzung (der einmal beschreibbare Speicher, den er verwendet,
um den Überblick über die ausgestellten Signaturen zu behalten, ist dann
aufgebraucht).

Zweitens sind Sie bei der Verwendung von TOTP weiterhin Sicherheitsrisiken
wie Keyloggern, Phishing und der Möglichkeit ausgesetzt, dass der für die
Generierung des TOTP verwendete geheime Schlüssel gestohlen wird. Darüber
hinaus ist es bei einer Million Möglichkeiten und dreißig Sekunden, um sie
auszuprobieren, denkbar, dass ein Angreifer Glück hat, da Joomla Ihr Konto
nicht sperrt und auch keine anderweitige Ratenbegrenzung für fehlgeschlagene
Anmeldeversuche verwendet. Diese Schutzmaßnahmen könnten zwar implementiert
werden, die Implementierung selbst könnte jedoch missbraucht werden, um eine
Denial-of-Service-Situation zu erzeugen, die einen legitimen Benutzer von
seiner Website aussperrt, während der Angreifer damit beschäftigt ist, in
sie einzudringen. Es ist ein Fall, in dem das Heilmittel schlimmer als die
Krankheit ist.

Die Passkey-Anmeldung verbessert die Benutzererfahrung erheblich. Große
Browser haben die Passkey-Anmeldung übernommen und bieten eine überzeugende
Benutzererfahrung, indem sie Benutzer erfolgreich zur Verwendung von
Authentifikatoren anleiten. Die Anmeldung mit einer Passkey ist sogar
bequemer als die Verwendung der automatischen Ausfüllfunktion eines
Passwortmanagers. Bei aktuellen Versionen mobiler Betriebssysteme wird
selbst diese früher etwas verwirrende Erfahrung rasch einfacher, als es
Passwörter und TFA jemals waren.

Ihre wahre Stärke zeigt die Passkey-Anmeldung jedoch bei der Sicherheit.
Durch die Verwendung sicherer Hardware und die starke Validierung des
Domainnamens der Website ist sie praktisch immun gegen Keylogger, Phishing
und die Manipulation von Schlüsseln. Sie verfügt sogar über einen integrierten
Schutz gegen das Klonen von Schlüsseln. Ja, Sie können Ihre Hardware weiterhin
verlieren – FIDO2-Authentifikatoren, ob externe Geräte oder integriert,
können jedoch mit einer PIN oder biometrischen Daten gesperrt werden.
Insgesamt ist die Verwendung der Passkey-Anmeldung mit FIDO2-Authentifikatoren
besser gegen Diebstahl und Verlust geschützt als Ihre Haus- oder
Autoschlüssel.

## Hinweise für Entwickler

### Zusätzliche Anmeldeschaltflächen

Das Plugin-Modul und com_users verwenden nun das Ereignis
onUserLoginButtons, das in
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` definiert und
aufgerufen wird, um die Definitionen zusätzlicher Schaltflächen abzurufen,
die nach der regulären Anmeldeschaltfläche platziert werden müssen.

Alle Entwickler, die ein Anmeldemodul oder allgemeiner ein Anmeldeformular
implementieren, sollten ebenfalls die öffentliche statische Methode
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` verwenden, um
diese Definitionen abzurufen und die Schaltflächen zu rendern, damit ihre
Software vollständig mit Joomla 4 kompatibel ist.

Entwickler, die benutzerdefinierte Schaltflächen implementieren möchten,
sollten sich ansehen, wie das System-Plugin für die Passkey-Anmeldung diese
Funktionalität implementiert. Solche Schaltflächen können zur Implementierung
von Single-Sign-on-Diensten von Drittanbietern oder sogar zur Anmeldung über
Identitätsdienste von Drittanbietern verwendet werden, wie sie von beliebten
sozialen Medien angeboten werden (Facebook, Google, Twitter, GitHub usw.).

Diese Änderung beeinträchtigt die Abwärtskompatibilität nicht. Anmeldemodule
und Anmeldeformulare von Drittanbietern funktionieren weiterhin normal, auch
wenn sie die Funktion für zusätzliche Anmeldeschaltflächen nicht
implementieren. Es fehlt dann lediglich die durch diese Funktion ermöglichte
Integration, beispielsweise Web Authentication selbst. Das heißt, sie
funktionieren weiterhin (was ein b/c-Bruch wäre), sind aber nicht
vollständig mit allen Funktionen ausgestattet.

### com_ajax auf der Backend-Anmeldeseite zulassen

Die Anmeldeseite des Administrators setzt com_ajax in
AdministratorApplication auf die Whitelist, damit es zur Verarbeitung von
Anfragen durch Gastbenutzer verwendet werden kann.

Diese Änderung verursacht keine Probleme mit der Abwärtskompatibilität,
solange Entwickler sinnvolle Praktiken anwenden und nicht davon ausgehen,
dass der Aufruf durch com_ajax im Backend beweist, dass der Benutzer im
Backend angemeldet ist. Das wäre eine schlechte Sicherheitspraxis. Die
sinnvolle Vorgehensweise besteht darin, das Joomla-User-Objekt zu verwenden,
um zu erkennen, ob es sich um einen Gastbenutzer handelt, und falls nicht,
ob der Benutzer über die erforderliche Berechtigung verfügt, um die über
com_ajax angeforderte Aktion auszuführen. Das heißt: Wenn diese Änderung
Ihren Code beschädigt hat, war Ihr Code bereits fehlerhaft und musste
ohnehin überarbeitet werden.

## Weitere Informationen

Die ursprüngliche Dokumentation dieser Funktion befindet sich im Pull
Request unter
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Übersetzt von openai.com*