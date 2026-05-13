<!--
{
  "source": "https://docs.joomla.org/J4.x:Administrator_Modules",
  "title": "Administrator-Module ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Das Atum Administrator-Template wird mit einem vollständigen Satz von Administrator-Modulen geliefert, die für den täglichen Gebrauch installiert und konfiguriert sind. Die folgende Abbildung zeigt die Positionen des Home-Dashboards, um darzustellen, wo sich die Module befinden.

![Atum Home-Dashboard-Positionen](../../../en/images/modules/administrator-modules/01-atum-template-positions.png)

In der obigen Abbildung sind die Panels Instanzen des Quick-Icon-Moduls, die mit Quickicon-Plugins verknüpft sind.

### Hinweise zu einigen Modulpositionen

- **Custom Top** befindet sich über dem Banner und ist nützlich, wenn Sie ein benutzerdefiniertes Menü oder ein benutzerdefiniertes Modul mit einer wichtigen Nachricht veröffentlichen möchten. Beispielsweise, um Administratoren zu warnen, dass die Website bald für Systemwartungen geschlossen wird.
- **Status** ist für die rechts im Banner ausgerichteten Symbole.
- **Menü** befindet sich in der linken Seitenleiste des Atum-Bildschirms.
- **Toolbar** befindet sich über dem Hauptinhaltsbereich auf Listen- und Bearbeitungsbildschirmen, ist jedoch nicht in Dashboard-Bildschirmen vorhanden.
- **Top** befindet sich unterhalb der Toolbar, aber über jeder Systemnachricht und dem Komponenteninhalt.
- **Bottom** befindet sich unterhalb des Komponenteninhalts.
- **Debug** befindet sich unter allem.

Atum-Template-Positionen nach Namen

```xml
  <positions>
    <!-- direkt im Template verwendet -->
    <position>bottom</position>
    <position>cpanel</position>
    <position>customtop</position>
    <position>debug</position>
    <position>icon</position>
    <position>login</position>
    <position>menu</position>
    <position>sidebar</position>
    <position>status</position>
    <position>title</position>
    <position>toolbar</position>
    <position>top</position>
  </positions>
```

## Ein benutzerdefiniertes Modul hinzufügen

Möglicherweise möchten Sie ein benutzerdefiniertes Modul hinzufügen, um Administratoren auf ein Systemproblem hinzuweisen. Wählen Sie **Inhalt → Administrator-Module** aus dem Administrator-Menü. Die Liste der installierten Module ist recht lang:

![Liste der Administrator-Module von atum](../../../en/images/modules/administrator-modules/02-atum-admin-modules-list.png)

Wählen Sie die Schaltfläche Neu und dann das benutzerdefinierte Modul. Im Bearbeitungsformular des Moduls: Benutzerdefiniert geben Sie einen Titel, eine benutzerdefinierte Nachricht ein und wählen eine Position für das Modul aus. Im unten stehenden Beispiel wurde die Position Oben ausgewählt. Zusätzlich wurden im Register Erweitert im Feld Modul-Klasse einige Stile eingegeben, um den Text zu zentrieren und einen Rand zu erzeugen: **alert alert-warning text-center**. Speichern Sie, um das Ergebnis zu sehen. Schließen Sie, um das Ergebnis auf der Modullistenseite zu sehen.

![atum benutzerdefiniertes Modul Bearbeitung Systemnachricht](../../../en/images/modules/administrator-modules/03-atum-admin-module-system-message.png)

Wenn Sie mit der Nachricht fertig sind, können Sie einfach die Status-Schaltfläche in der Modulliste auswählen, um das Modul zu deaktivieren.

## Liste der Administrator-Module

- **Aktionsprotokolle - Neueste** Dieses Modul zeigt eine Liste der
  neuesten Aktionen.
- **Administrator-Dashboard-Menü** Dieses Modul zeigt ein Submenü-Modul
  für Administratoren an.
- **Administrator-Menü** Dieses Modul zeigt ein Menü-Modul für
  Administratoren an.
- **Beiträge - Neueste** Dieses Modul zeigt eine Liste der zuletzt
  erstellten Beiträge.
- **Benutzerdefiniert** Dieses Modul ermöglicht es Ihnen, Ihr eigenes
  Modul mithilfe eines WYSIWYG-Editors zu erstellen.
- **Feed-Anzeige** Dieses Modul ermöglicht die Anzeige eines
  syndizierten Feeds.
- **Frontend-Link** Dieses Modul zeigt einen Link zum Frontend an und
  soll in der 'Status'-Position angezeigt werden.
- **Joomla! Versionsinformationen** Dieses Modul zeigt die Joomla!
  Version an und soll in der 'Status'-Position angezeigt werden.
- **Angemeldete Benutzer** Dieses Modul zeigt eine Liste der
  angemeldeten Benutzer an.
- **Anmeldeformular** Dieses Modul zeigt ein Anmeldeformular für
  Benutzername und Passwort an. Es sollte nicht deaktiviert werden.
- **Login-Support-Informationen** Dieses Modul zeigt einige nützliche
  Links zu Joomla-Support-Seiten auf dem Anmeldebildschirm an.
- **Nachrichten** Dieses Modul zeigt die Anzahl der privaten Nachrichten
  an und soll in der 'Status'-Position angezeigt werden. Es wird nur
  angezeigt, wenn Nachrichten zu lesen sind.
- **Mehrsprachiger Status** Dieses Modul zeigt den Status der
  mehrsprachigen Parameter an und soll in der 'Status'-Position
  angezeigt werden.
- **Beliebte Beiträge** Dieses Modul zeigt eine Liste der am meisten
  verbreiteten veröffentlichten Beiträge, die noch aktuell sind. Einige
  der gezeigten Beiträge können abgelaufen sein, auch wenn sie die
  neuesten sind.
- **Nachinstallationsnachrichten** Dieses Modul zeigt einen Zähler und
  einen Link zu den neuesten Nachinstallationsnachrichten an. Es wird
  nur angezeigt, wenn Nachrichten zu lesen sind.
- **Datenschutz-Dashboard** Das Datenschutz-Dashboard-Modul zeigt
  Informationen zu Datenschutzanfragen an.
- **Datenschutzstatus-Check** Das Datenschutzstatus-Check-Modul zeigt
  Informationen zum Datenschutzstatus Ihrer Website an.
- **Schnellsymbole** Dieses Modul zeigt Schnellsymbole, die auf dem
  Home-Dashboard (Administratorbereich-Startseite) sichtbar sind.
- **Beispieldaten** Dieses Modul lässt Sie Beispieldaten installieren.
- **Statistiken** Das Statistik-Modul zeigt Informationen über Ihre
  Serverinstallation zusammen mit Statistiken über die Website-Benutzer
  und die Anzahl der Beiträge in Ihrer Datenbank an.
- **Titel** Dieses Modul zeigt den Titel der Toolbar-Komponente an.
- **Toolbar** Dieses Modul zeigt die Toolbar-Symbole, die zur Steuerung
  von Aktionen im gesamten Administratorbereich verwendet werden.
- **Benutzermenü** Dieses Modul zeigt das Benutzermenü an und soll in
  der 'Status'-Position angezeigt werden.

