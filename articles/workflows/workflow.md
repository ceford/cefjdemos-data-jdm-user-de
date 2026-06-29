<!--
{
  "source": "https://docs.joomla.org/J4.x:Workflow",
  "title": "Veröffentlichungs-Workflow",
  "description": "", 
  "author": ""
}
-->

## Einführung

In Joomla ist ein Workflow eine Abfolge von Schritten im Lebenszyklus eines Beitrags von der Erstellung bis zur Löschung. Die Schritte werden normalerweise von verschiedenen Personen mit unterschiedlichen Verantwortlichkeiten durchgeführt. Zum Beispiel übernimmt in der Zeitungswelt ein Unterredakteur einen Bericht von einem Reporter und überprüft die Genauigkeit, Grammatik, Leserfreundlichkeit und Länge des Textes, und möglicherweise mehr. Der Unterredakteur gibt dann die Geschichte an den Redakteur weiter, der sie akzeptieren oder ablehnen, entscheiden kann, wo sie in der Zeitung platziert wird, und so weiter.

Die Workflow-Komponente wird verwendet, um **Phasen** zu Beiträgen hinzuzufügen, um die statischen Zustände (unveröffentlicht, veröffentlicht, gelöscht und archiviert) mit **Übergängen** zu verbessern. Die statischen Zustände und Übergänge werden separat aufgezeichnet, damit Workflows aktiviert oder deaktiviert werden können, ohne den Zustand der Inhalte zu beeinflussen. Workflows werden im *Beiträge: Optionen* Bereich unter dem Reiter *Integration* aktiviert oder deaktiviert.

Es gibt eine Tutorial-Seite, die Schritte zur Erstellung eines Beispiel-Workflows enthält: [Workflow-Szenarien](jdocmanual?article=user/workflows/workflow-scenarios).

## Begriffe & Definitionen

- *Workflow:* Ein Workflow ist eine vollständige Abfolge von Schritten. Es können mehrere verschiedene Workflows für unterschiedliche Zwecke erstellt werden. Die Workflow-Komponente enthält einen *Basis-Workflow* und die Blog-Beispieldaten haben einen komplexeren *Blog-Workflow*.
- *Stufe:* Eine Stufe ist ein Ort innerhalb eines Workflows. Zum Beispiel kann ein unveröffentlichter Beitrag in Stufe 1: In Vorbereitung oder Stufe 2: Bereit zur Überprüfung sein, und so weiter. Es ist die Stufe des Elements, die in der Datenbank aufgezeichnet wird.
- *Übergang:* Ein Übergang ist eine Änderung von einer Stufe zur nächsten, oft zur nächsten im Workflow, kann aber auch zur vorherigen oder anfänglichen Stufe führen.
- *Status:* Der Status eines Beitrags kann unveröffentlicht, veröffentlicht, gelöscht oder archiviert sein. Ein Status kann durch die Ausführung eines Workflow-Übergangs geändert werden, vorausgesetzt, der Benutzer hat die Berechtigung, den Status zu ändern.
- *Kategorie:* Wenn Workflows verwendet werden, kann ein spezifischer Workflow für eine Kategorie im *Beitrag: Kategorie bearbeiten* Formular im *Workflow* Tab ausgewählt werden.

## Die Workflow-Liste

Wenn Workflows aktiviert sind, kann die Liste der verfügbaren Workflows durch die Auswahl von **Content → Workflows** im Administrator-Menü angezeigt werden.

![Workflow-Liste](../../../en/images/workflows/workflow/01-workflows-list.png)

- Der **Status** eines Workflows kann Aktiviert, Deaktiviert oder Gelöscht sein.
- Der **Name** ist ein Link zum Bearbeitungsformular des Workflows.
- Der **Standard**-Eintrag wird für neue Beiträge verwendet, die keiner Kategorie zugewiesen sind, die einen definierten Workflow hat.
- Der **Stufen**-Eintrag ist eine Schaltfläche, die die Anzahl der Stufen anzeigt und einen Link zur Liste der Stufen für den Workflow bietet.
- Der **Übergänge**-Eintrag ist eine Schaltfläche, die die Anzahl der Übergänge anzeigt und einen Link zur Liste der Übergänge für den Workflow bietet.
- Die **ID** ist der numerische Wert des Workflows, der intern verwendet wird.  

## Phasen

Die Phasen sind über die *Workflows*-Liste zugänglich. Wählen Sie den gelben Knopf, der die Anzahl der Phasen anzeigt.

![Liste der Workflow-Phasen](../../../en/images/workflows/workflow/02-workflow-stages-list.png)

Wählen Sie den Namen einer Phase aus, um sie zu bearbeiten.

![Bearbeitungsformular der Workflow-Phase](../../../en/images/workflows/workflow/03-workflow-stage-edit.png)

## Übergänge

In Workflows wechseln Beiträge von einer Phase zur nächsten. Die Übergänge werden
über die *Übergänge* Liste verwaltet.

![Die Übergänge Liste](../../../en/images/workflows/workflow/04-workflow-transitions-list.png)

- Die *Aktuelle Phase* definiert, wo dieser Übergang beginnt.
- Die *Zielphase* definiert, wo dieser Übergang endet.

### Übergangsphasen

Die *Aktuelle* und *Zielphasen* werden im *Übergang Bearbeiten* Formular festgelegt:

![Übergang Bearbeiten Formular](../../../en/images/workflows/workflow/05-workflow-transition-edit.png)

Der Tab *Übergangsaktionen* wird verwendet, um den *Status* des Elements zu definieren,
nachdem der Übergang abgeschlossen ist.

![Übergang Bearbeiten Formular Aktionen Tab](../../../en/images/workflows/workflow/06-workflow-transition-edit-actions-tab.png)

- **Hervorhebungsstatus** Ob das Element *Hervorgehoben* wird oder nicht.
- **Veröffentlichungsstatus** Wählen Sie aus der Liste den Zielstatus.

Der Tab *Übergangsbenachrichtigungen* wird verwendet, um zu definieren, ob eine 
Benachrichtigung für diesen Status gesendet wird. Zum Beispiel, wenn ein Beitrag 
geschrieben wurde, aber noch lektoriert werden muss, könnte eine E-Mail an den 
Editor gesendet werden.

![Übergang Bearbeiten Formular Benachrichtigungen Tab](../../../en/images/workflows/workflow/07-workflow-transition-edit-notifications-tab.png)

- **Benachrichtigung senden** Wenn auf *Ja* gesetzt, erscheinen zusätzliche Felder.
- **Zusätzlicher Nachrichtentext** Fügen Sie zusätzlichen Nachrichtentext hinzu oder 
  verwenden Sie einen Sprach-String, um den Nachrichtentext übersetzbar zu machen.
- **Benutzergruppen** Wählen Sie, wer die Benachrichtigung erhält, z.B. alle Benutzer
  in der Benutzergruppe *Editor*.
- **Benutzer** Wählen Sie einzelne Benutzer, die diese Benachrichtigung erhalten sollen.

### Berechtigungen

Der Berechtigungen-Tab steuert den Zugriff auf diesen Übergang durch ausgewählte Benutzergruppen.
Normalerweise werden die Berechtigungen von den Berechtigungen in den 
*Beiträge: Optionen* Berechtigungseinstellungen geerbt.

### Workflow-Übergangs-Plugins

Die Workflow-Plugins werden für Aktionen eingesetzt, die durch Übergänge aufgerufen werden. Gehen Sie zu 
**System → Plugins** und ändern Sie den Filter *- Typ auswählen -* in *workflow*.
Jedes dieser Plugins kann deaktiviert werden, wenn es nicht benötigt wird.

![Workflow Plugins Liste](../../../en/images/workflows/workflow/08-workflow-plugins.png)

- **Workflow Hervorhebung** Diese Aktion implementiert die Änderung des 
  *Hervorgehobenen* Status eines Beitrags von *Ja* zu *Nein*.
- **Workflow-Benachrichtigung** Diese Aktion implementiert die Benachrichtigung eines Benutzers,
  dass ein Phasenwechsel Aufmerksamkeit erfordert.
- **Workflow Veröffentlichung** Diese Aktion implementiert eine Statusänderung eines
  Beitrags von einem zum anderen der folgenden: *Veröffentlicht*, *Unveröffentlicht*, 
  *Papierkorb* oder *Archiviert*. Wenn der Benutzer keine Berechtigung zur Änderung des 
  Status hat, schlägt der Übergang mit einer erklärenden Nachricht fehl. Der Übergang, 
  der die Statusänderung angefordert hat, wird dennoch erfolgreich sein!

## Kategorien

Beiträge können Kategorien zugewiesen werden. Sie entsprechen einem bestimmten Workflow und können auf verschiedene Weise angepasst werden. Sie können einen Status, eine übergeordnete Kategorie festlegen und auch den Zugriff sowie die Berechtigungen einschränken. Diese Option befindet sich nicht im Workflow-Bildschirm. Für diese Option müssen Sie zu **Inhalt → Kategorien** gehen. Öffnen Sie dort eine beliebige Kategorie und Sie sehen einen *Workflows*-Reiter.

![Beiträge Kategorie Workflow bearbeiten](../../../en/images/workflows/workflow/09-workflow-categories-blog.png)

### Beispiel

Bestimmte Beiträge müssen nur für Administratoren oder Benutzer mit höherem Rang verfügbar sein.

- Erstellen Sie eine Kategorie mit dem Namen *Restricted*.
- Setzen Sie alle Berechtigungen auf *Erlaubt* für Administratoren oder höhere Ränge. 
- Verschieben Sie die betreffenden Beiträge in die *Restricted*-Kategorie.

Dies spart das Setzen von Berechtigungen auf einzelne Beiträge.

## Versionierung

Wenn der Workflow aktiviert ist, werden Felder, die vom Workflow verwaltet werden, von der Versionierung ausgeschlossen (wie „Status“ und „hervorgehoben“), um Berechtigungskonflikte zu vermeiden.

## Beispiele

Einige spezifische Beispiele stehen zur Verfügung, um zu veranschaulichen, wie man Workflows für verschiedene Benutzergruppen verwendet:

- [Beispiel 1](jdocmanual?article=user/workflows/workflow-example-1) nutzt die standardmäßigen Benutzergruppen Autor, Redakteur und Verleger, um Beiträge für einen Newsletter vorzubereiten.
- [Beispiel 2](jdocmanual?article=user/workflows/workflow-example-2) nutzt benutzerdefinierte Benutzergruppen, um Beiträge für Ausschusssitzungen vorzubereiten.

*Übersetzt von openai.com*

