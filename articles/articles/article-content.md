<!--
{
  "source": "https://docs.joomla.org/J4.x:Adding_a_New_Article",
  "title": "Beitrag: Bearbeiten - Inhalt ",
  "description": "", 
  "author": ""
}
-->

## Einführung

*Einen Beitrag hinzufügen* wurde in einem *Erste Schritte*-Beitrag behandelt. Dies ist der erste einer Reihe von Beiträgen, die mehr Details zum *Beitrag: Bearbeiten*-Formular bieten. Es behandelt die *Inhalt*-Registerkarte und einige Aspekte des TinyMCE-Editors, des standardmäßigen Editors, der mit Joomla bereitgestellt wird.

Der folgende Screenshot zeigt das Bearbeitungsformular mit einem Beitrag, der bereits gespeichert wurde.

![Das Inhaltsbearbeitungsformular](../../../en/images/articles/article-content/01-articles-edit-content.png)

## Dateneingabe

Das Bearbeitungsformular für Beiträge hat Registerkarten. Bei einem neuen Beitrag ist die **Inhalt**-Registerkarte standardmäßig ausgewählt. Andernfalls ist die zuletzt geöffnete Registerkarte ausgewählt.

### Das Titel-Feld

Das **Titel**-Feld ist *erforderlich* und wird überall dort verwendet, wo der Beitragstitel angezeigt wird. Dies ist das einzige Feld, das Text enthalten muss, um ein Bearbeitungsformular zu speichern.

Titel sollten kurz, aber beschreibend für den Beitrag-Inhalt sein, da sie in Listen und Menüeinträgen erscheinen, wo der Platz begrenzt ist.

Titel müssen nicht einzigartig sein, obwohl es am besten wäre, wenn sie es sind. Wenn Sie zum Beispiel *Als Kopie speichern* aus der Dropdown-Liste *Speichern & Schließen* auswählen, wird der aktuelle Beitrag gespeichert und ein neuer mit einer an den Titel und Alias angehängten Nummer erstellt. Sie können die Nummer aus dem Titel entfernen, aber nicht aus dem Alias und die Kopie *Speichern*. Das ergibt zwei Beiträge mit demselben Anzeigetitel.

### Das Alias-Feld

Das *Alias*-Feld bleibt normalerweise leer. Wenn der Beitrag gespeichert wird, wird der Alias aus dem Titel generiert, indem alles in Kleinbuchstaben umgewandelt und nicht alphanumerische Zeichen durch Bindestriche ersetzt werden.

Wenn Sie den Beitragstitel ändern, können Sie den Alias löschen und es wird ein neuer generiert. Wenn der Alias verwendet wurde, um sich in internen und externen Links auf den Beitrag zu beziehen, werden diese Links gebrochen. Daher ist es am besten, den Alias eines alten Beitrags nicht zu ändern.

### Die Inhalt-Registerkarte - Beitragstext

Der obige Screenshot zeigt den Beitragstext in einem WYSIWYG-Editor, der eher wie eine Textverarbeitung aussieht. Sie sollten jedoch wissen, dass der Beitragstext als HTML gespeichert wird und das Dateneingabefeld in Wirklichkeit ein Textbereichsfeld ist, das dieses HTML enthält. Sie können es selbst sehen, indem Sie die Schaltfläche *Editor umschalten* unter dem Bearbeitungsbereich auswählen. Der Editor ist in der Tat eine JavaScript-Anwendung, die das HTML neu darstellt, um es leichter lesbar und manipulierbar zu machen.

#### Nicht erlaubte HTML-Tags und -Attribute

Sowohl Joomla als auch der TinyMCE-Editor haben Einstellungen, die bestimmte HTML-Tags und -Attribute nicht zulassen. Zum Beispiel steht auf der standardmäßigen Joomla-Verbotsliste *iframe*, sodass, wenn Sie versuchen, dieses Tag in einen Beitrag einzufügen, es stillschweigend beim Speichern entfernt wird. Textfilter werden in der *Globalen Konfiguration* festgelegt. Das TinyMCE-Plugin hat eine Option, *Joomla-Textfilter verwenden*. Wenn auf *Aus* gestellt, listet es *script,applet,iframe* als *Verbotene Elemente* auf.

#### Editor-Symbolleisten

Über dem Textbereich befinden sich Reihen von Symbolleisten. Zwei sind standardmäßig angezeigt. Die anderen können durch Auswahl des Ellipsis-Symbols (...) am Ende der zweiten Symbolleiste ein- oder ausgeschaltet werden. Die Symbolleisten können so konfiguriert werden, dass sie verschiedenen Benutzergruppen unterschiedliche Leisten und Leisteninhalte anzeigen.

Es gibt zu viele Werkzeuge, um jedes hier zu beschreiben. Das würde Ihnen einen Heuhaufen schaffen, in dem Sie die Nadel suchen müssten. Erkunden Sie einfach!

Es gibt jedoch einige Funktionen, die eine zusätzliche Erklärung verdienen.

#### CMS-Inhalte

Diese Schaltfläche zeigt eine Dropdown-Liste an, die das Einfügen von Elementen in einen Beitrag ermöglicht, die anderswo im CMS erhalten wurden.

- **Beitrag** Dieser Link zeigt eine Popup-Liste von Beiträgen an. Wählen Sie einen Beitrag aus, um einen Link zu diesem Beitrag im aktuellen Beitrag einzufügen.
- **Kontakt** Fügen Sie einen Link zu einem Kontakt im aktuellen Beitrag ein.
- **Feld** Fügen Sie ein Feld in den Beitrag ein. Es wird als `{field 1}` angezeigt.
- **Medien** Fügen Sie ein Bild oder eine Datei aus einem Medienkomponenten-Popup ein.
- **Menü** Fügen Sie einen Link zu einem Menüpunkt aus einem Menülisten-Popup ein.
- **Seitenumbruch** Es erfolgt eine Eingabeaufforderung für einen *Seitentitel* und einen *Inhaltsverzeichnis-Alias*. Diese Funktion wird verwendet, um lange Dokumente in mehrere Seiten aufzuteilen.
- **Weiterlesen** Ein *Weiterlesen...*-Trenner wird an der Position des Cursors eingefügt. Wählen Sie einen Absatzumbruch vor der Auswahl.

#### Externe Links

Das **Einfügen**-Element in der ersten Symbolleiste bietet Optionen zum Einfügen eines *Links...*, eines *Bildes...* oder von *Medien...*. Diese sind für externe Elemente gedacht, seien Sie also mit der URL des zu verwendenden Elements bereit.

### Die Inhalt-Registerkarte - Einstellungen

Die **Inhalt**-Registerkarte wird hauptsächlich vom TinyMCE-Editor beansprucht.

Neben dem Inhalt gibt es Felder zur Verwaltung der Veröffentlichung, wie und wo der Beitrag angezeigt wird und wer ihn sehen kann, wenn er veröffentlicht wird. In den meisten Fällen können diese Einstellungen auf ihren Standardwerten belassen werden.

1.  **Status** *Veröffentlicht*, *Unveröffentlicht*, *Archiviert* oder *Gelöscht* - der Standard ist *Veröffentlicht*.
2.  **Kategorie** Dies ist ein *erforderliches* Feld, wird aber standardmäßig auf *Nicht kategorisiert* gesetzt. Sie können eine Kategorie aus der Liste auswählen oder einige Zeichen eines Kategorienamens eingeben, um die Liste der auszuwählenden Kategorien zu verkürzen.
3.  **Hervorgehoben** Wechseln Sie zwischen *Nein* und *Ja*, um den Beitrag auf der Startseite anzuzeigen, wenn diese ein *Hervorgehobene Beiträge*-Layout verwendet.
4.  **Zugriff** Die Zugriffsberechtigung kann geändert werden, um den Beitrag auf Benutzergruppen zu beschränken, die bestimmten *Zugriffsebenen* zugewiesen sind: *Öffentlich*, *Gast*, *Registriert*, *Speziell* oder *Super Benutzer*.
5.  **Tags** Beginnen Sie, einzugeben, um vordefinierte Tags zu finden und auszuwählen, oder Sie können ein neues hinzufügen, indem Sie es eingeben und **Enter drücken**.
6.  **Notiz** Jeder Kommentar zu diesem Beitrag, der unter dem Titel auf der Beitragslistenseite sichtbar wird.
7.  **Versionsnotiz** Fügen Sie Kommentare hinzu, um anzugeben, was sich in dieser Version geändert hat. Dies wird im *Versionen*-Modaldialog angezeigt und das Feld wird nach dem Speichern wieder leer.

### Andere Registerkarten

**Möglicherweise sehen Sie nicht alle folgenden Registerkarten**, da ein Website-Administrator einige ausblenden kann, um die Konsistenz des Beitragslayouts auf der Website aufrechtzuerhalten. Sie können auch zusätzliche Registerkarten für *Benutzerdefinierte Felder* sehen, wenn diese eingerichtet wurden.

1.  **Bilder und Links** erlaubt Ihnen, ein Einführungs- und ein hervorgehobenes Bild und/oder Links festzulegen, die an vordefinierten Positionen erscheinen. Dies kann verwendet werden, wenn Ihr Beitrag innerhalb eines Kategorieblogs angezeigt wird.
2.  **Optionen** erlauben Ihnen, das Layout des Beitrags und zugehörige Informationen wie Titel, Kategorie, Tags, Veröffentlichungsdetails usw. festzulegen. Dies wird normalerweise global festgelegt, kann aber über diese Optionen auch beitragsspezifisch sein.
3.  **Schema** ist eine Methode, um Metadaten zu einem Beitrag hinzuzufügen. Es wird von Robotern verwendet, ist aber für Menschen nicht sichtbar.
3.  **Veröffentlichung** erlaubt Ihnen, Veröffentlichungsdaten und -zeiten festzulegen, um die Veröffentlichung eines Beitrags zu planen. Standardmäßig wird ein Beitrag sofort nach dem Speichern veröffentlicht. Sie können auch die Metadaten für den Beitrag festlegen.
4.  **Bearbeitungsbildschirm konfigurieren** erlaubt es Ihnen, Parameter für den Beitrag ein- oder auszublenden.
5.  **Berechtigungen** zeigt die Berechtigungen für jede Benutzergruppe, die steuern, was getan werden kann oder nicht.

Es gibt separate Beiträge zu jedem dieser Registerkarten.

## Speichern des Beitrags

Sobald Sie die erforderlichen Informationen und Inhalte hinzugefügt haben, können Sie den Beitrag speichern. Es gibt verschiedene Möglichkeiten, dies zu tun, je nachdem, was Sie als Nächstes in Joomla machen möchten.

Um den Beitrag zu speichern, können Sie entweder *Speichern* oder *Speichern & Schließen* wählen. Letzteres hat Dropdown-Optionen wie *Speichern & Neu*, *In Menü speichern* und *Als Kopie speichern*.

- **Speichern** Speichern Sie den Beitrag und lassen Sie ihn für weitere Bearbeitungen offen. Bei längeren Beiträgen ist es eine gute Praxis, regelmäßig Ihre Arbeit zu speichern.
- **Speichern & Schließen** Speichern Sie den Beitrag und gehen Sie zur Beitragsliste. Die Schaltfläche „Speichern & Schließen“ hat weitere Dropdown-Optionen:
  - **Speichern & Neu** Speichern Sie den Beitrag und öffnen Sie dann eine Seite **Beiträge: Neuer Beitrag**. Diese Option spart Zeit beim Hinzufügen mehrerer Beiträge.
  - **In Menü speichern** Speichern Sie den Beitrag und öffnen Sie eine Seite **Menüs: Neuer Menüpunkt**.
  - **Als Kopie speichern** Speichern Sie den Beitrag, dann öffnen Sie eine **Beiträge: Bearbeiten**-Seite mit einer Zahl in Klammern, die an den Titel angehängt ist, und der gleichen Zahl nach einem Bindestrich, z.B. -2, im Alias-Feld. Sie können den Titel ändern sowie den Alias des neuen Beitrags, der bereits erstellt wurde, ändern oder löschen.

Eine Systemnachricht wird anzeigen, dass der Beitrag erfolgreich gespeichert wurde.

### Fehler beim Versuch zu speichern:

- Wenn Sie die erforderlichen Felder nicht ausgefüllt haben, erscheint eine rote Fehlermeldung, die die fehlenden Informationen angibt, die Sie hinzufügen müssen.
- Sie werden eine Fehlermeldung sehen, wenn der Beitrag einen Alias hat, der bereits existiert. Sie können dies überwinden, indem Sie das Alias-Feld ändern.

## Tipps

- Wenn Sie nicht der Super User oder Administrator sind, nehmen Sie sich die Zeit, um zu verstehen, wie die Website eingerichtet ist. Nur weil Sie einen Beitrag gespeichert haben, bedeutet das nicht, dass er auf der Website sichtbar ist. Wenn Kategorie-Blog-Seiten verwendet werden, wird der Beitrag durch die Zuweisung der richtigen Kategorie angezeigt. Andernfalls muss ein Beitrag einem Menüpunkt zugewiesen werden. Dies können Sie im Beitrag selbst oder über das Administrator-Menü **Menüs** tun.
- Versuchen Sie, die Titel von Beiträgen kurz und präzise zu halten.
- Auch wenn es möglich ist, vermeiden Sie es, neue Kategorien und Tags in Beiträgen zu erstellen, wenn mehrere Benutzer Beiträge zur Website hinzufügen. Rechtschreibfehler und Unterschiede können leicht verhindern, dass Beiträge dort angezeigt werden, wo sie vorgesehen sind. Kategorien und Tags auf ihrer jeweiligen Listenseite zu erstellen, sorgt für Konsistenz auf der gesamten Website.
- Falls erforderlich, nutzen Sie Beitragsnotizen. Sie können sehr hilfreich sein, insbesondere wenn mehrere Personen Beiträge hinzufügen.
- Wo auch immer Sie in Joomla sind, können Sie einen Beitrag hinzufügen, ohne zum Home Dashboard zu gehen – verwenden Sie das Joomla Administrator-Menü.

