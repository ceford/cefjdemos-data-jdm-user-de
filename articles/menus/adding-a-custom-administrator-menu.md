<!--
{
  "source": "https://docs.joomla.org/J4.x:Adding_a_Custom_Administrator_Menu",
  "title": "Benutzerdefiniertes Administrator-Menü",
  "description": "", 
  "author": ""
}
-->

## Einführung

Angenommen, Sie haben einen Benutzer, dem Sie erlauben möchten, auf Ihrer Website nur eine einzige Aufgabe auszuführen. Nehmen wir den Fall einer Organisation, die weltweit Niederlassungen hat und bei der jede Niederlassung nur die Aufgabe hat, Standorte auf einer Karte zu platzieren, um sie auf der Seite anzuzeigen. Die Komponente für diese Aufgabe ist Ffmap, jedoch werden hier nur die im Administrator-Menü relevanten Punkte behandelt.

Um diese Aufgabe zu erfüllen, müssen Sie eine benutzerdefinierte Benutzergruppe erstellen, einen Benutzer dieser Gruppe zuweisen und ein benutzerdefiniertes Menü erstellen, das dieser Benutzer verwenden kann.

## Erstellen Sie eine Benutzergruppe

- Wählen Sie im Administratormenü **Benutzer → Benutzer → Gruppen** aus.
- Wählen Sie die Schaltfläche **Neu** in der Toolbar.
  - Geben Sie einen **Titel für die Gruppe** ein, in diesem Fall *Branch*.
  - Wählen Sie **Öffentlich** als übergeordnete Gruppe aus. Dies ist wichtig, da Sie keine Berechtigungen von einer anderen Gruppe erben möchten.
- Wählen Sie **Speichern und Schließen** in der Toolbar.

## Globale Berechtigungen für die Gruppe festlegen

- Wähle **Globale Konfiguration** vom Start-Dashboard aus.
- Wähle die Registerkarte **Berechtigungen** aus.
- Wähle das Element **Zweig** aus.
- Setze **Administrator-Anmeldung** auf **Erlaubt**.
- Wähle **Speichern und Schließen** aus der Symbolleiste.

An diesem Punkt kann sich jeder Benutzer, der der Benutzergruppe Zweig zugewiesen ist, in die Administratoroberfläche einloggen und das Start-Dashboard sehen. Es könnten Dashboard-Module sichtbar sein, weil ihr Zugriffslevel auf Öffentlich gesetzt wurde, zum Beispiel: Angemeldete Benutzer, Beliebte Beiträge und Kürzlich hinzugefügte Beiträge. Am besten stellst du den Zugriff auf diese Module auf Speziell ein. Es werden keine Menüelemente für den Benutzer sichtbar sein.

## Komponentenberechtigung für die Gruppe festlegen

Entweder:

- Wählen Sie die **Ffmap**-Komponente im Administrator-Menü aus.
- Wählen Sie die **Optionen**-Schaltfläche von FFmap in der Symbolleiste, um den
  Konfigurationsbildschirm zu öffnen.

Oder:

- Wählen Sie **Globale Konfiguration** vom Home-Dashboard aus.
- Wählen Sie Ffmap aus der Liste der Komponenten.

Dann:

- Wählen Sie die Registerkarte **Berechtigungen** und dann den **Zweig**-Punkt aus.
- Setzen Sie Zugriff auf das Administrationsinterface, Erstellen, Löschen, Bearbeiten, Status bearbeiten,
  Eigenes bearbeiten und Wert für benutzerdefiniertes Feld bearbeiten auf **Erlaubt**.
- Wählen Sie **Speichern und Schließen** aus der Symbolleiste.

## Ein neues Administrator-Menü erstellen

- Wählen Sie **Menü → Verwalten** aus dem Administrator-Menü.
- Wählen Sie **Administrator** aus der Site/Administrator-Dropdown-Liste.
- Wählen Sie die **Neu**-Schaltfläche aus der Werkzeugleiste.
- Geben Sie einen Titel für das Menü ein, zum Beispiel **Filialmenü**, und eine eindeutige ID, zum Beispiel **filial-menü**.
- Wählen Sie **Speichern und Schließen** aus der Werkzeugleiste.

## Erstellen Sie ein Modul für das Menü

In der Menü-Liste wählen Sie die Schaltfläche **Verknüpfte Module** im Eintrag des Filialmenüs aus.

- Geben Sie einen Titel für das Modul ein, zum Beispiel **Filialmenü**.
- Wählen Sie Menü anzuzeigen: **Filialmenü**.
- Setzen Sie Menü überprüfen auf **Nein**, da ansonsten Warnmeldungen über fehlende Administratorfunktionen erscheinen.
- Wählen Sie die Position: **menü**.

## Erstellen Sie einen Komponenten-Menücontainer

- Wählen Sie in der Menüliste das Symbol "Menüeinträge" für das Zweigmenü (Branch Menu) aus. Dies öffnet die Liste der Einträge, die zu diesem Zeitpunkt leer ist.
- Wählen Sie die Schaltfläche **Neu** aus der Werkzeugleiste.
- Geben Sie einen Titel für den Menüeintrag ein: **Zweigkomponenten**.
- Wählen Sie den Menüeintragstyp **Schaltfläche auswählen**.
  - Scrollen Sie im Modaldialog nach unten zum Punkt **System-Links** und erweitern Sie das Fenster.
  - Wählen Sie den Elementtyp **Komponenten-Menücontainer** aus.
- Gehen Sie zurück zum Menükonfigurationsformular und wählen Sie **Keine anzeigen**, um alle Komponenten-Menüeinträge auszublenden (rot).
- Scrollen Sie zu den Ffmap-Elementen und klicken Sie die Ausblenden-Schaltflächen, um sie auf Anzeigen (grün) zu setzen.
- Wählen Sie **Speichern und schließen** aus der Werkzeugleiste.

## Bildschirmfoto

![Benutzerdefiniertes Administrator-Menükomponenten-Auswahl](../../../en/images/menus/adding-a-custom-administrator-menu/01-menus-custom-administrator-menu.png)

## Ergebnis

Erstellen Sie einen Benutzer in der Zweiggruppe, um selbst zu testen. Melden Sie sich als dieser Benutzer in der Administratoroberfläche an, um das Ergebnis zu sehen:

![benutzerdefiniertes Administrator-Menü Ergebnis](../../../en/images/menus/adding-a-custom-administrator-menu/02-menus-custom-administrator-menu-result.png)

## Notizen

Wenn Sie später eine weitere Komponente hinzufügen, wird diese zum Komponentenmenü-Container hinzugefügt und standardmäßig sichtbar sein. Sie müssen zum Administratormenüpunkt zurückkehren und den neuen Inhalt auf Ausblenden setzen.

Wenn die Komponente so eingerichtet ist, dass sie Menüeinträge in jeder der Administrator-Listenansichten durch Einbeziehung von default.xml-Dateien enthält, können Sie Menüeinträge direkt zum benutzerdefinierten Menü hinzufügen und die Verwendung des Komponentenmenü-Containers vermeiden.

Das Branch-Komponentenmenü bleibt Teil des Administratormenüs - unvermeidbare Duplizierung!

*Übersetzt von openai.com*

