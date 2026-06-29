<!--
{
  "source": "https://docs.joomla.org/J4.x:Adding_a_New_Menu",
  "title": "Ein neues Menü hinzufügen",
  "description": "", 
  "author": ""
}
-->

## Einführung

Damit Inhalte auf Ihrer Joomla!-Website zugänglich sind, müssen Elemente einem Menü zugewiesen werden. Eine Standardinstallation von Joomla! erstellt ein **Hauptmenü** für Sie. In vielen Fällen werden Sie nur ein Menü verwenden, aber Sie können mehr als eines haben. Dies ermöglicht es Ihnen, Menüs für verschiedene Arten von Inhalten, versteckte Inhalte, benutzerspezifische Inhalte und mehr zu erstellen.

Es gibt drei Schritte zur Erstellung eines verwendbaren Menüs:

1. Erstellen Sie das Menü. Dies ist ein Container für Menüpunkte.
2. Erstellen Sie ein Menümodul. Dies ermöglicht die Platzierung des Menüs auf einer Seite.
3. Erstellen Sie Menüeinträge. Dies sind die vom Benutzer auswählbaren Elemente, die zu bestimmten Seiten führen.

Dieser Screenshot zeigt die Menüs, die in einer mehrsprachigen Website verfügbar sind. In einer anfänglichen Joomla-Installation gibt es ein einzelnes *Hauptmenü*.

![Menüliste](../../../en/images/menus/adding-a-new-menu/01-menus-manage.png)

Die Liste ermöglicht es Ihnen, auf beliebige grüne oder rote Buttons zu klicken, um direkt zur Liste der Menüpunkte in diesem Menü und Zustand zu gelangen.

Dieses Tutorial behandelt die Schritte, die bei der Erstellung eines Menüs auf einer Joomla!-Website erforderlich sind.

## Ein neues Menü erstellen

Verwenden Sie eine der folgenden Schritte, um ein neues Menü zu erstellen:

- Wählen Sie im Administrator-Menü das *Menu-Dashboard-Symbol* aus, um zum Menu-Dashboard zu gelangen, und wählen Sie dann **Verwalten**. Oder...
- Erweitern Sie im Administrator-Menü den Abschnitt *Menüs* und wählen Sie dann **Verwalten**.
- Wählen Sie die **+ Neu** Schaltfläche in der Werkzeugleiste.
- Füllen Sie im Menü-Dateneingabeformular die folgenden Felder aus:
  - **Titel**: Ein geeigneter Titel für das Menü. Dieser wird verwendet, um das Menü im Menu-Manager zu identifizieren.
  - **Einzigartiger Name**: Dies sollte ein einzigartiger Identifikationsname sein, der von Joomla! verwendet wird, um dieses Menü zu identifizieren. Leerzeichen sind nicht erlaubt, aber Sie können das Zeichen '-' verwenden, wie z. B. ressourcen-menu.
  - **Beschreibung**: Obwohl nicht erforderlich, ist dies oft nützlich auf einer Webseite mit vielen Menüs. Es erscheint unterhalb des *Titels* in der Menüliste, wie oben dargestellt.<br>
    ![Neues Menü](../../../en/images/menus/adding-a-new-menu/02-menus-new.png)
- **Speichern & Schließen**

In der Liste der Menüs hat das neu erstellte Menü eine Schaltfläche mit der Beschriftung **Ein Modul für dieses Menü hinzufügen**, was der nächste Schritt in der Menükreation ist. Sie könnten beginnen, Menüpunkte hinzuzufügen und später zurückkommen, um das Menümodul zu erstellen.

## Erstellen Sie ein Modul für das Menü

In der Liste der Menüs ermöglicht die Spalte *Verknüpfte Module* die Auswahl eines bestehenden Menümoduls zu Bearbeitungszwecken. Sie können es sich ansehen und dann *Schließen*, ohne Änderungen vorzunehmen. Für Ihr neues Menü wählen Sie die Schaltfläche **Modul für dieses Menü hinzufügen**, um ein modales Fenster mit dem Dateneingabeformular für das Menümodul zu öffnen.

![Dateneingabeformular für das Menümodul](../../../en/images/menus/adding-a-new-menu/03-menus-module.png)

Auszufüllende Felder:

* Das **Titel**-Feld ist erforderlich, daher erstellen Sie einen beschreibenden Titel.
* Die **Titel anzeigen** Schaltfläche auf der rechten Seite wird verwendet, um den Modultitel zu *zeigen* oder *auszublenden*, eine gängige Funktion aller Module.
* Das **Menü auswählen**-Feld sollte den Namen des Menüs anzeigen, das Sie gerade erstellt haben.
* Das **Position**-Feld dient zur Auswahl einer Position in Ihrer Vorlage, an der Ihr Menü erscheinen soll.
* Wählen Sie **Speichern & Schließen**, sobald die wesentlichen Informationen hinzugefügt wurden.

Es gibt viele Optionen zur Auswahl im Formular *Moduleinstellungen bearbeiten*. Diese werden im Hilfebildschirm erwähnt, der im Formular *Modul: Bearbeiten* verfügbar ist. Dies ist dasselbe Formular, jedoch auf einer normalen Seite statt in einem modalen Fenster. Greifen Sie über das Administrator-Menü, Route Inhalt / Seitenmodule zur Liste der Seitenmodule darauf zu.

Hinweis: Wie das Menü aussehen wird, hängt von der Gestaltung Ihrer Vorlage ab.

## Elemente zum Menü hinzufügen

Um die Links in Ihrem Menü zu erstellen, müssen Sie **Menüeinträge** hinzufügen. In Joomla gibt es viele *Menüeintragstypen* und Drittanbieter-Komponenten können weitere Typen hinzufügen. Für dieses Tutorial wird ein Link zu einem einzelnen Beitrag hinzugefügt.

Sie können einen Beitrag im Voraus erstellen oder während des Menüerstellungsprozesses anlegen. In jedem Fall muss der Beitrag existieren, bevor ein Menüeintrag dafür erstellt werden kann. In diesem Beispiel wird der Beitrag ebenfalls *Ressourcen* genannt. Er soll eine Liste von Links zu PDF-Dateien enthalten.

In der **Menüs**-Liste wählen Sie in der Spalte **Menüeinträge** das Symbol für das neu erstellte Menü, in diesem Beispiel *Ressourcen*. Anfangs gibt es keine Menüeinträge, daher zeigt die Liste lediglich *Keine passenden Ergebnisse* an.

- Wählen Sie die **Neu**-Taste in der Symbolleiste, um einen neuen Menüeintrag zu erstellen.
- Im **Titel**-Feld fügen Sie den Titel hinzu, der im Menü erscheinen soll.
- Im Feld **Menüeintragstyp** wählen Sie die **Auswählen**-Taste, um einen modalen Dialog zu öffnen, der eine Liste von Komponenten enthält. Jede hat eine Dropdown-Liste, die verfügbare Menüeintragstypen anzeigt.
  - Wählen Sie **Beiträge** und dann **Einzelner Beitrag**.
- Im Feld **Beitrag auswählen**: **Entweder:**
  - Verwenden Sie den **Auswählen**-Button, um einen bestehenden Beitrag auszuwählen. Dies öffnet eine Liste von Beiträgen zur Auswahl. **Oder:**
  - Verwenden Sie den **Erstellen**-Button, um einen neuen Beitrag zu erstellen. Alles, was Sie eingeben müssen, ist der Beitragstitel. Es ist wahrscheinlich am besten, detaillierte Inhalte für später aufzubewahren.
- Vergewissern Sie sich, dass das **Menü**-Feld auf das neue Menü eingestellt ist.
- Das **Status**-Feld sollte auf **Veröffentlicht** gesetzt sein.
- Wählen Sie **Speichern & Schließen**.

![Datenformular für Menüeinträge](../../../en/images/menus/adding-a-new-menu/04-menus-single-article.png)

Fügen Sie bei Bedarf weitere Menüeinträge zum neuen Menü hinzu.

Sobald Elemente zum Menü hinzugefügt wurden, überprüfen Sie, ob das Menü an der richtigen Position auf der Website angezeigt wird.

![Menüanzeige](../../../en/images/menus/adding-a-new-menu/05-menus-display.png)

*Übersetzt von openai.com*
