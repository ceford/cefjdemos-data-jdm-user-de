<!--
{
  "source": "https://docs.joomla.org/Get_locally_hosted_Joomla!_website_e-mail_functions_to_work",
  "title": "Lokaler Host-E-Mail",
  "description": "", 
  "author": ""
}
-->

## Lokales Hosting

Die meisten ISPs blockieren Port 25, sodass Sie keine E-Mails von Ihrem eigenen SMTP-Server auf Ihrem Computer senden können. Dies dient dazu, Spammer zu blockieren. Wenn Sie nicht beabsichtigen zu spammen, können Sie den Mailserver Ihres ISPs nutzen.

Um die E-Mail-Funktion des SMTP-Servers Ihres ISPs zu nutzen, selbst wenn Sie Ihre eigene Joomla-Website auf Ihrem eigenen Computer hosten, melden Sie sich als Super User auf Ihrer Joomla-Website an und navigieren Sie zum **Server**-Tab auf der Seite **Globale Konfiguration**. Im Abschnitt **Mail** sollten Ihre Daten folgendermaßen aussehen:

    Von E-Mail: jemand@example.com (normalerweise Sie)
    Von Name: EinName

    Mailer: SMTP
    SMTP Host: smtp.charter.net (Was auch immer Ihr ISP Ihnen für deren SMTP-Server angibt)
    Sendmail-Pfad: /usr/sbin/sendmail
    SMTP-Port: 25
    SMTP-Sicherheit: STARTTLS
    SMTP-Authentifizierung: Ja (oder Nein)
    SMTP-Benutzername: johndoe (Benutzername eines Ihrer E-Mail-Konten bei Ihrem ISP)
    SMTP-Passwort: trr33459 (Passwort eines Ihrer E-Mail-Konten bei Ihrem ISP)
Senden Sie eine Testnachricht, um zu überprüfen, ob es funktioniert.

Der SMTP-Benutzername, das Passwort und der Host sind die gleichen Felder, die Sie eingeben, wenn Sie ein Outlook Express Konto oder Eudora oder einen anderen E-Mail-Client einrichten, den Sie auf Ihrem Computer verwenden.

Möglicherweise stoßen Sie auf Probleme mit Erweiterungen, die die *Von*-Adresse in den ausgehenden E-Mails ändern. Zum Beispiel sendet die ProjectFork-Erweiterung manchmal E-Mails, als ob sie von der für das Projekt verantwortlichen Person kommen. Dies kann zu einem Problem führen, da einige ISP-SMTP-Server keine "Von"-Adressen zulassen, die nicht mit dem Benutzernamen übereinstimmen (z.B. Rogers in Kanada). Sie erhalten eine Nachricht wie diese: "PHPMAILER_FROM_FAILEDname@whatever.com." Ein Workaround besteht darin, sicherzustellen, dass Sie immer eine gültige E-Mail-Adresse von Ihrem ISP für Ihre Benutzer verwenden.

*Übersetzt von openai.com*

