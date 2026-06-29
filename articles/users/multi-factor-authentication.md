<!--
{
  "source": "https://docs.joomla.org/J4.x:Multi-factor_Authentication",
  "title": "Multifaktor-Authentifizierung ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Das Joomla! Multi-Faktor-Authentifizierungssystem basiert auf Akeeba Loginguard und ein Großteil dieser Dokumentation wurde mit Genehmigung von Akeeba übernommen.

## Was macht es?

Es fügt mehrere, optionale Zwei-Schritt-Verifizierungsmethoden für den Joomla!-Login hinzu. Nach dem Einloggen mit nur Ihrem Benutzernamen und Passwort werden Sie aufgefordert, Ihre zweite Schritt-Verifizierung einzugeben, zum Beispiel einen Code, der von Google Authenticator generiert wird. Solange Sie keine korrekte zweite Schritt-Verifizierung bereitstellen, können Sie keine Seiten auf der Website aufrufen. Sie werden immer zur "Captive Login"-Seite weitergeleitet. Das ist ähnlich wie bei Google, wenn Sie versuchen, sich bei GMail anzumelden.

Dies unterscheidet sich von der ursprünglichen Joomla! Zwei-Faktor-Authentifizierungsmethode, die den zweiten Authentifizierungsfaktor (z.B. den von Google Authenticator generierten Code) erforderte, um zusammen mit dem Benutzernamen und Passwort eingegeben zu werden.

Die Vorteile der Zwei-Schritt-Verifizierung sind:

- Sie ist weniger verwirrend für den Benutzer. Es gibt kein "Geheimschlüssel"-Feld mehr, das Benutzer verunsichert.
- Sie kann mit nicht-passwortbasierten Login-Methoden wie Social Login (z.B. Facebook), sicheren Hardware-Token, SSO (Single Sign-On) etc. funktionieren. 
  Klarstellung: Die Zwei-Schritt-Verifizierung kann so konfiguriert werden, dass sie angefordert wird, nachdem ein Benutzer sich mit einer nicht-passwortbasierten Login-Methode angemeldet hat. Sie implementiert keine nicht-passwortbasierten Login-Methoden.
- Sie bietet eine bessere Zugriffskontrolle. Sie können Benutzeroptionen festlegen, um Multi-Faktor-Authentifizierung nach Benutzergruppe zu verlangen oder zu deaktivieren.
- Sie ermöglicht alternative Authentifizierungsmethoden in einem einzigen Konto. Sie können mehrere Authentifizierungsmethoden in Ihrem Konto haben. Zum Beispiel können Sie eine Google Authenticator-App und einen YubiKey einrichten.
- Sie unterstützt Methoden, die kein Eingeben eines Codes erfordern. Zum Beispiel FIDO2-Dongles, biometrische Verifizierung etc. Diese müssen mit dem Browser und/oder Betriebssystem über native HTML5-APIs interagieren.
- Sie unterstützt Methoden, die Benutzerinteraktion erfordern. Zum Beispiel das Senden eines Codes per Push-Nachricht, SMS oder E-Mail. Diese Methoden setzen voraus, zu wissen, welcher Benutzer authentifiziert wird, bevor der Authentifizierungscode an den Benutzer gesendet wird.
- Sie ist kostenlos. Im Gegensatz zu Drittanbietern, die Multi-Faktor-Authentifizierung anbieten, müssen Sie keine Vorauszahlungsgebühren oder monatliche/jährliche Wartungsgebühren für jede Seite oder jeden Benutzer, der die Zwei-Schritt-Verifizierung nutzt, bezahlen. Die Software ist kostenlos.

## Wie funktioniert es

Sie melden sich wie gewohnt auf Ihrer Website an, beispielsweise durch Eingabe eines Benutzernamens und Passworts. Es ist wichtig zu beachten, dass Sie in diesem Stadium keine Anmeldedaten für die Zwei-Faktor-Authentifizierung eingeben müssen.

Das System erkennt, dass Sie nun angemeldet sind, die Zwei-Faktor-Authentifizierung jedoch nicht durchgeführt haben. Es speichert die URL, die Sie sehen sollten, und leitet Sie sofort zur Captive-Anmeldeseite um. Jeder Versuch, zu einer anderen Seite zu navigieren, führt dazu, dass die Captive-Seite erscheint.

Beiträge auf Ihrer Website können vertrauliche Informationen enthalten. Um die Vertraulichkeit zu gewährleisten, werden Beiträge während der Renderzeit zwangsweise deaktiviert. Das bedeutet, dass keine Beitragsposition auf der Seite gerendert wird. Denken Sie daran, falls Sie bemerken, dass die Kopfzeile oder andere wichtige Designelemente Ihrer Website auf der Captive-Anmeldeseite fehlen.

Beachten Sie, dass Plug-ins hingegen NICHT deaktiviert werden. Dies liegt sowohl daran, dass Joomla es extrem schwierig macht, spezifische Plug-ins zu entfernen, sobald sie geladen sind, als auch daran, dass die meisten Plug-ins auf Ihrer Website kritische Funktionen erfüllen.

Nachdem Sie Ihre Zwei-Faktor-Authentifizierung durchgeführt haben, wird eine Markierung in der Benutzersitzung gesetzt, die anzeigt, dass Sie vollständig autorisiert sind, die Website zu nutzen. Zudem werden Sie zur URL weitergeleitet, die es unmittelbar nach Ihrer anfänglichen Anmeldung gespeichert hat.

## Zwei-Faktor-Authentifizierung versus WebAuthn-Anmeldungen

Die Anmeldung mit WebAuthn ist die sicherste Option. Sie geben nur einen Benutzernamen an, der als öffentliche, nicht privilegierte Information betrachtet werden sollte. Die Website erstellt eine kryptografische Herausforderung, die vom Browser mit sicherer Hardware signiert wird — einem externen sicheren Hardware-Token oder dem Trusted Platform Module / Secure Enclave Ihres Geräts — und an den Server zurückgesendet wird. Der Server validiert die Signatur. Diese Validierung verwendet eine Public-Key-Kryptografie, wobei die Website nur den öffentlichen Schlüssel speichert. Dies macht die Anmeldung nahezu nicht phishbar und äußerst sicher. Wenn Sie dies verwenden, benötigen Sie keinen zweiten Authentifizierungsfaktor — aber wenn Sie wirklich möchten, können Sie auch WebAuthn dafür verwenden.

Abgesehen von der Verwendung von föderierten Anmeldemethoden (wie z.B. Anmeldung mit Ihrem Social Media-Konto, einem Single Sign-On-Dienst, einem LDAP-Server usw.) ist eine herkömmliche Benutzername + Passwort-Anmeldung bei weitem nicht so sicher wie eine WebAuthn-Anmeldung. Die Eingabe eines Benutzernamens und eines Passworts kann abgefangen, gestohlen oder erraten werden. Dies macht es sehr problematisch, nur Benutzernamen und Passwort zu vertrauen.

Bei der Multi-Faktor-Authentifizierung geben Sie nur Ihren Benutzernamen und Ihr Passwort an. Ein erfolgreicher Phishing-Angriff würde nur diesen ersten Authentifizierungsfaktor erfassen, aber nicht Ihren zweiten Authentifizierungsfaktor. Nach erfolgreicher Anmeldung wird Ihnen eine gebundene Seite präsentiert. Sie können auf der Website nichts anderes tun, bis Sie Ihren zweiten Faktor angegeben haben. Da die Eingabe des zweiten Faktors auf einer eigenen Seite erfolgt, kann sie interaktiv (z.B. WebAuthn), asynchron (z.B. Erhalt eines OTP per E-Mail, SMS oder Push-Benachrichtigung) oder vom Benutzer initiiert (z.B. ein TOTP oder ein Yubikey OTP) sein. Noch besser ist, dass ein Benutzer mehrere Methoden für den zweiten Faktor auf seinem Konto aktiviert haben kann, um unbeabsichtigte Aussperrungen von der Website zu vermeiden. Zum Beispiel können Sie WebAuthn mit einem externen sicheren Hardware-Dongle als primären, sichersten zweiten Faktor verwenden. Sie könnten auch ein reguläres TOTP einrichten, falls Sie den Dongle verlieren oder vergessen, ihn mitzunehmen. Einige Methoden für den zweiten Faktor ermöglichen mehrere Instanzen, zum Beispiel können Sie mehrere WebAuthn-Authentifikatoren haben, sodass Sie den integrierten Authentifikator auf Ihrem Windows-Computer, Ihrem iPhone und Ihrem Android-Tablet verwenden können, ohne jedes Mal, wenn Sie Ihren Schreibtisch verlassen, daran denken zu müssen, einen Hardware-Dongle und Adapter einzupacken.

Fassen wir zusammen. Von am sichersten bis am wenigsten sicher sind Ihre Optionen:

- WebAuthn als Ihre primäre Anmeldemethode mit sekundärer Multi-Faktor-Authentifizierung.
- WebAuthn als Ihre einzige Anmeldemethode.
- Benutzername und Passwort als Ihre primäre Anmeldemethode mit sekundärer Multi-Faktor-Authentifizierung.
- Nur Benutzername und Passwort als Ihre einzige Anmeldemethode.

## Plugins

Jeder der Faktoren in der Multi-Faktor-Authentifizierung wird über Plugins implementiert. Diese können je nach Bedarf aktiviert oder deaktiviert werden. Neue Plugins können hinzugefügt werden, wenn neue Methoden verfügbar werden. Die mit dem Joomla-Kern gelieferten Plugins umfassen:

- **Bestätigungscode**: Sechsstellige Bestätigungscodes, die von einer Authenticator-App (Google Authenticator, Authy, LastPass Authenticator usw.), einem Passwort-Manager (1Password, BitWarden, Keeper, KeePassXC, Strongbox usw.) oder, in manchen Fällen, dem Browser generiert werden.
- **YubiKey**: Ermöglicht Benutzern auf Ihrer Seite die Verwendung von Multi-Faktor-Authentifizierung mit einem YubiKey sicherem Hardware-Token. Benutzer benötigen ihren eigenen YubiKey, der unter www.yubico.com erhältlich ist.
- **Web-Authentifizierung**: Unterstützt von allen modernen Browsern. Die meisten Browser bieten gerätespezifische Authentifizierung, die durch ein Passwort und/oder biometrische Verfahren (Fingerabdrucksensor, Gesichtserkennung, ...) geschützt ist.
- **Authentifizierungscode per E-Mail**: Verwendung von zeitlich begrenzten, sechsstelligen Sicherheitscodes, die Ihnen per E-Mail zugesandt werden. Die Standardeinstellung beträgt 2 Minuten.
- **Fester Code**: Dieser ist für Tests und Illustrationen gedacht und standardmäßig deaktiviert. Er sollte nicht auf einer Produktionsseite aktiviert werden.

Beachten Sie, dass es ein separates Plugin **System - WebAuthn Passwortloser Login** gibt, um die Anmeldung über die Schaltfläche "Web-Authentifizierung" im Anmeldeformular zu verwalten.

## Benutzeroptionen

Das Formular Benutzer: Optionen enthält ein Formular für die Multi-Faktor-Authentifizierung, um zu konfigurieren, wie die Multi-Faktor-Authentifizierung in Joomla funktioniert. Wählen Sie die Schaltfläche Inline-Hilfe umschalten, um Informationen zu jeder Option zu erhalten.

![benutzeroptionen multifaktor-authentifizierungsformular](../../../en/images/users/multi-factor-authentication/01-users-configuration-mfa.png)

## Benutzerprofil

Das Formular Administrator / Benutzer: Profil bearbeiten hat separate Tabs für WebAuthn-Login und Multi-Faktor-Authentifizierung, aber letzterer ist nur für den Kontoinhaber sichtbar. Selbst Superbenutzer sehen diesen Tab nicht für andere Benutzer.

Das Formular Webseite / Dein Profil bearbeiten hat die Backend-Formular-Tabs übereinander angeordnet, was verwirrend sein kann, da die Web-Authentifizierung zweimal erscheint: zuerst für passwortlosen Login und dann für die Multi-Faktor-Authentifizierung. Die folgende Abbildung zeigt den Abschnitt zur Multi-Faktor-Authentifizierung des Formulars, nachdem eine Methode erstellt wurde. Dies setzt die Funktion automatisch auf aktiviert und zeigt die Option zur Erstellung von Backup-Codes an.

![Ansicht des Formulars zur Multi-Faktor-Authentifizierung eines Benutzers auf der Webseite](../../../en/images/users/multi-factor-authentication/02-multi-factor-authentication-site-profile.jpg)

Wie oben erwähnt, können Sie jede ausprobieren, indem Sie die + Hinzufügen ... Schaltfläche auswählen, aber wählen Sie Abbrechen im nachfolgenden Formular, wenn Sie sich entscheiden, nicht fortzufahren.

*Übersetzt von openai.com*

