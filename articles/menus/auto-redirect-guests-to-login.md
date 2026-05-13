<!--
{
  "source": "https://docs.joomla.org/Auto_redirect_guests_to_login",
  "title": "Gäste automatisch zur Anmeldung weiterleiten ",
  "description": "", 
  "author": ""
}
-->

## Gewünschte Funktionalität

Angenommen, Sie haben einige Menüoptionen, die erfordern, dass ein Benutzer eingeloggt ist,
wie z. B. *Einen Beitrag einreichen*. Sie möchten, dass alle Benutzer den
eingeschränkten Menüpunkt sehen können, unabhängig davon, ob sie eingeloggt sind oder nicht. Das gewünschte Verhalten ist wie folgt.

* Wenn der Benutzer eingeloggt ist, gelangt er direkt zum eingeschränkten Menüpunkt.
* Wenn der Benutzer nicht eingeloggt ist, wird ihm das Anmeldeformular präsentiert und nach
erfolgreicher Anmeldung wird er zur eingeschränkten Seite weitergeleitet.
* Wenn der Benutzer nicht registriert ist, hat er die Möglichkeit, sich zu registrieren oder auf eine andere Seite zu navigieren.

## Lösung

So machen Sie es in Joomla!.

1. Erstellen Sie ein neues Menü aus der **Menüs**-Liste, nennen Sie es zum Beispiel **Verstecktes Menü**.
2. Fügen Sie Menüeinträge hinzu, die nur für registrierte Benutzer zugänglich sind (zum Beispiel *Beitrag einreichen*). Setzen Sie die erforderlichen Zugriffsebenen dieser Menüeinträge auf **Registriert**.
3. Erstellen Sie kein Modul für das *Versteckte Menü*. Es wird auf keiner Seite angezeigt, daher benötigt es kein Modul.
4. Erstellen Sie Ihr *richtiges* Menü, nennen Sie es zum Beispiel **Seitenmenü**, und den Menüpunkt, der für alle Benutzer angezeigt wird, zum Beispiel *Beitrag einreichen*.
    - Der Menüpunkt hat einen Menüpunkt-Typ von **Menüpunkt-Alias**, der im Menüpunkt-Typ **System-Links** zu finden ist.
    - Sein *Menüpunkt*-Parameter wird der Menüpunkt *Beitrag einreichen* im *Versteckten Menü* sein.
    - Die Zugriffsebene für diesen Menüpunkt wird **Öffentlich** sein, da jeder ihn sehen und benutzen können muss.
5. Erstellen Sie ein Modul für das *Seitenmenü*, genau wie Sie es für jedes Menü tun.
6. Wenn Sie Untermenüs wünschen, stellen Sie sicher, dass Sie die Untermenüpunkte im **Seitenmenü** und nicht im **Versteckten Menü** hinzugefügt haben.

Wenn nun ein Gast (nicht eingeloggter Benutzer) die Menüoption *Beitrag einreichen* aufruft, wird er zur Login-Seite weitergeleitet. Wenn der Login erfolgreich ist, wird der Benutzer zur eingeschränkten **Beitrag einreichen**-Seite weitergeleitet. Wenn er bereits eingeloggt ist, erfolgt die Weiterleitung sofort.

## Beispiel

Für die folgenden Menüeinträge:

1.  Startseite
2.  Blog
3.  Wiki
4.  Verzeichnis
5.  Kleinanzeigen
6.  FAQs
7.  Shop
8.  Kontakt

Sollten alle Menüeinträge im Frontend für jeden sichtbar sein, aber die Einträge 3, 4, 5, 6 und 7 sollten nur für **registrierte** Benutzer zugänglich sein.

In diesem Fall befinden sich die Menüeinträge 3 bis 7 im *versteckten* Menü mit ihrem **Zugriffs**parameter auf **registriert** gesetzt. Die Einträge 3 bis 7 haben im *realen* Menü *Alias*-Menüeinträge, bei denen die **Zugriffs**parameter auf **Öffentlich** gesetzt sind.

*Übersetzt von openai.com*

