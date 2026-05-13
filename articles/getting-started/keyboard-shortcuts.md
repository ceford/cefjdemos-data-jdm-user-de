<!--
{
  "source": "https://docs.joomla.org/Keyboard_Shortcuts",
  "title": "Tastenkombinationen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die Tastatur kann in der Administratoroberfläche verwendet werden, um einige der Aktionen auszuführen, die normalerweise mit einer Maus oder einem Pad durchgeführt werden. Zum Beispiel gibt es Tastenkombinationen, um die aktuelle Seite zu speichern, zum *Start-Dashboard* zu gelangen oder ein *Optionen*-Formular zu öffnen.

Es gibt eine Übersicht über alle Tastenkürzel, die durch die sequentielle Tastatureingabe von **J** und **X** (nicht gleichzeitig und ohne die normalerweise zur Großschreibung verwendete Umschalttaste) geöffnet werden kann. Sofern Sie die Plug-in-Einstellungen nicht ändern, müssen Sie die Tasten innerhalb von 2 Sekunden drücken.

Diese Funktion ist standardmäßig aktiviert. Sie kann deaktiviert oder konfiguriert werden unter **Administrator → System → Plugins → System - Tastaturkürzel**. Derzeit ist die einzige Konfiguration das Timeout: wie lange das System auf Ihre nächste Tastenbetätigung wartet. Standardmäßig beträgt diese Wartezeit 2000 Millisekunden (2 Sekunden).

## Standardtastenkombinationen in Joomla

- J + A - Speichert den aktuellen Inhalt
- J + S - Für Speichern & Schließen
- J + Q - Bricht die aktuelle Seite ab
- J + N - Drückt den *Neu* Button
- J + F - Setzt den Fokus auf das Suchfeld
- J + O - Geht zu Optionen
- J + H - Öffnet das Hilfefenster (kann eine Browser-Pop-up-Warnung auslösen)
- J + M - Schaltet die Menüleiste um
- J + X - Zeigt eine Liste der verfügbaren Tastenkombinationen an
- J + D - Geht direkt zum Home-Dashboard

## Drittanbieter-Abkürzungen - Informationen für Entwickler

Andere Entwickler können ebenfalls ihre Abkürzungen hinzufügen. Das Joomla-Plugin ruft das *onLoadShortcuts*-Ereignis auf, das auch von anderen Plugins genutzt werden kann. Das Ereignis muss der Liste der *getSubscribedEvents* innerhalb des Plugins hinzugefügt werden. Die zugeordnete Funktion könnte folgendermaßen aussehen:

```php
    public function onLoadShortcuts(EventInterface $event): void {
       $shortcuts = $event->getArgument('shortcuts');
       $exampleShortcuts = array('example' => (object)['shortcut' => 'E', 'title' => 'Tolles Beispiel', 'selector' => '#menu-collapse']);
       $event->setArgument('shortcuts',  array_merge($shortcuts, $exampleShortcuts));
    }
```
Achten Sie genau auf den array_merge-Teil: Wenn die bereits existierenden Abkürzungen nicht mit den neuen zusammengeführt werden, werden die alten überschrieben.

Entwickler können ein Array mit Abkürzungsobjekten bereitstellen:

    { shortcut: string, selector: string, title: string }

- Die *Abkürzung* muss eine Tastatureingabe sein, getrennt durch ein Plus, z.B. `Y` oder `ALT + Z + 7` (aktuell gibt es keine wirkliche Filterung). Beachten Sie, dass jede Abkürzungssequenz mit **J** beginnt.
- *Selektoren* sind CSS-Selektoren oder URLs, um das Ziel zu spezifizieren. Wenn es sich um ein Eingabeelement handelt, gibt die Abkürzung den Fokus, wie es im Fall des Suchfeldes ist. Andernfalls wird das Element angeklickt oder die URL aufgerufen.
- Der *Titel* wird in der Übersicht angezeigt. Es könnte zum Beispiel der Name des Ziels sein.

## Gründe für die Verwendung von J + X

Einige könnten sich über die Entscheidung wundern, sequenzielle Tastenkombinationen oder das **J** als Start zu verwenden, anstatt Strg oder etwas anderes. Die Hauptgründe sind die Zugänglichkeit und die Vermeidung von Unterbrechungen durch andere Software. Zum Beispiel wäre *Strg + S* schön zum Speichern eines Beitrags, wird aber bereits von Browsern verwendet. Dasselbe kann für Bildschirmlesegeräte oder Passwortmanager passieren. Die sicherere Option war also, etwas Joomla-spezifisches wie das **J** am Anfang zu verwenden.

Ein weiteres Problem ist, dass es nicht immer möglich ist, mehr als eine Taste gleichzeitig zu drücken. Windows hat dafür den Sticky-Key-Modus, aber dieser funktioniert nur für Modifikatortasten wie Shift, Strg und Alt. Daher nutzt das Plugin von Anfang an die sequenzielle Eingabe, wodurch es von mehr Menschen sogar ohne die Hilfe von Betriebssystemmodi genutzt werden kann.

*Übersetzt von openai.com*

