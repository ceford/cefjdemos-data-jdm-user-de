<!--
{
  "source": "https://docs.joomla.org/J4.x:Module_Display_by_Menu_Item",
  "title": "Modulanzeige nach Menüpunkt ",
  "description": "", 
  "author": ""
}
-->

## Einführung

In Joomla ist es häufig der Fall, dass verschiedene Module auf
verschiedenen Seiten erscheinen. Und manchmal werden unterschiedliche Module
unterschiedlichen Benutzergruppen präsentiert. Das Anzeigeverhalten von Modulen wird durch eine
Kombination aus Menüzuweisung und Zugriffsberechtigung im Modul-Editierformular gesteuert. Standardmäßig wird ein Modul auf allen Seiten und für alle Benutzergruppen angezeigt.

## Zugriff

Dieses Feld befindet sich im Reiter Modul des Modul-Datenformulars. Es befindet sich im rechten Bedienfeld und sollte nicht mit dem Reiter Berechtigungen verwechselt werden. Die verfügbaren Optionen sind:

- Öffentlich - für alle Benutzergruppen sichtbar.
- Gast - nach dem Login nicht sichtbar.
- Registriert - nur nach dem Login sichtbar.
- Spezial - nur nach dem Login in andere Benutzergruppen als 
  Registriert sichtbar.
- Super Nutzer - nur für diese Benutzergruppe sichtbar.

## Menüzuweisung

Es gibt vier Optionen für die Menüzuweisung:

- Auf allen Seiten
- Keine Seiten
- Nur auf den ausgewählten Seiten
- Auf allen Seiten außer den ausgewählten

Für die letzten zwei Optionen wird ein Menüauswahl-Panel angezeigt. Anfänglich sind die Menüs darin vollständig erweitert, aber sie können mit der **Menüunterbäume erweitern** *Keine* Schaltfläche eingeklappt werden. Danach das gewünschte Menü erweitern.
![Modul-Menüzuweisung](../../../en/images/modules/module-display-by-menu-item/01-module-display-by-menu.png)

Wählen Sie die Menüeinträge aus, um das Modul nach Wunsch anzuzeigen oder nicht anzuzeigen. 

## Beispiele

### Breadcrumbs nicht auf der Startseite

- Öffnen Sie das Breadcrumbs-Modul.
- Wählen Sie *Auf allen Seiten außer den ausgewählten*.
- Wählen Sie *Keine* nach **Menüpunkten zuweisen**.
- Finden Sie den Menüpunkt der Startseite und aktivieren Sie das Kontrollkästchen.
- Speichern
- Überprüfen Sie die Website - Breadcrumbs sollten auf allen Seiten außer der Startseite vorhanden sein.

*Übersetzt von openai.com*

