<!--
{
  "source": "https://docs.joomla.org/Changing_user_groups",
  "title": "Ändern der Benutzergruppen ",
  "description": "", 
  "author": ""
}
-->

## Gruppenvererbung

Gruppenlisten verwenden ein Vererbungsmuster. Zum Beispiel erbt ein Benutzer in der Autoren-Gruppe alle Privilegien der Registrierten-Gruppe und erhält einige zusätzliche Privilegien. Ebenso erbt ein Benutzer in der Redakteurs-Gruppe alle Privilegien der Autoren-Gruppe und erhält noch einige weitere zusätzliche Privilegien. Die Backend-Gruppen erben das höchste Privilegienniveau im Frontend.

Aus diesem Grund müssen Sie nur eine Gruppe für einen einzelnen Benutzer auswählen - die Gruppe mit den meisten Privilegien.

## Schritte

Sie können die Gruppe eines Benutzers ändern, indem Sie diese Schritte befolgen. Sie müssen sich als Administrator oder Super User anmelden, um die Gruppen eines Benutzers ändern zu können. Außerdem kann ein Administrator sich selbst oder andere nicht zu einem Super User machen.

1. Wählen Sie im *Home Dashboard* den Punkt **Benutzer** aus. Oder...
2. Wählen Sie im Menüpunkt *Benutzer* die Option **Benutzer** und dann **Verwalten**.
3. Finden Sie den gewünschten Benutzer in der Liste der Benutzer. Sie können nach Name, Benutzername, E-Mail oder ID: Präfix suchen.
4. Wählen Sie den Namen des Benutzers zur Bearbeitung aus.
5. Wählen Sie den Tab *Zugeordnete Benutzergruppen*.
6. Wählen Sie die Gruppe, zu der der Benutzer gehören soll.
7. Wählen Sie *Speichern*.

## Zugriffskontrollliste (ACL) für Joomla

Im Folgenden sind die Zugriffskontrollliste (ACL) für Joomla aufgeführt. Die Benutzergruppe wird aufgelistet, und die Aufzählungspunkte unten beschreiben die Berechtigungen, die mit dieser Gruppe verknüpft sind.

### Frontend-Gruppen

#### Gast

- Öffentliche Seite und öffentliche Beiträge ansehen

#### Registriert

- Gastgruppen-Privilegien
- Registrierte Beiträge ansehen
- Kein Zugriff auf Elemente, die nur für die Gastgruppe eingeschränkt sind

#### Autor

- Registrierten Gruppenprivilegien
- Neue Beiträge erstellen
- Beiträge bearbeiten, die sie besitzen
- Spezielle Inhalte ansehen

#### Editor

- Autoren-Gruppenprivilegien
- Alle Beiträge bearbeiten, einschließlich unveröffentlichter

#### Publisher

- Editor-Gruppenprivilegien
- Beiträge veröffentlichen

### Backend-Gruppen

Diese Gruppen ermöglichen es Ihnen, sich über die URL */administrator* beim Administrator anzumelden.

#### Manager

- Publisher-Gruppenprivilegien
- Zugriff auf das Administrator-Backend

#### Administrator

- Manager-Gruppenprivilegien
- Neue Benutzer erstellen
- Erweiterungen installieren

#### Super User

- Administratoren-Privilegien
- Site-Template ändern
- Globale Konfiguration ändern

*Übersetzt von openai.com*

