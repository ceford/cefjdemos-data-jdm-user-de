<!--
{
  "source": "https://docs.joomla.org/J4.x:Submenus",
  "title": "Untermenüs ",
  "description": "", 
  "author": ""
}
-->

## Menügrundlagen

In Joomla tragen drei Elemente zur Anzeige eines Menüs für den Benutzer bei:

- Ein Menü ist ein Container für Menüelemente.
- Ein Menüelement ist ein Link zu einer Seite der Website oder einer externen Seite.
- Ein Menümodul bietet eine Methode, das Menü auf einer bestimmten Position auf der Seite zu platzieren und Aspekte des Erscheinungsbildes oder des Verhaltens des Menüs oder der Seite zu steuern.

Einfache Menüs bestehen aus Listen von Links. Manchmal haben Mitglieder einer Liste Eltern-Kind-Beziehungen, die als eingerückte Kinder oder Dropdown-Listen angezeigt werden. Eltern-Kind-Beziehungen können beliebig tief verschachtelt werden. Allerdings kann eine Verschachtelung über zwei Ebenen hinaus Listen unattraktiv und schwer nutzbar machen.

Es gibt Gelegenheiten, bei denen Sie die Kinder eines übergeordneten Menüs als separates Untermenü anzeigen möchten. Ein häufiges Einsatzszenario ist es, ein Untermenü links von einer Seite, den Seiteninhalt in der Mitte und ein Inhaltsverzeichnis der Seite rechts anzuzeigen. Dieses Tutorial erklärt, wie dies zu bewerkstelligen ist.

### Beispiel Daten

Angenommen, Sie haben eine Reihe von Beiträgen über Tiere. Es könnten Familienhaustiere, ein Informationsblatt für Tierärzte oder ein Zoo sein. Das folgende ist eine kurze Beispielstruktur zu Demonstrationszwecken:

    Tiere
        Katzen
            Burmesen
            Russisch Blau
        Hunde
            Collies
            Pomeranians

Die Listen könnten ziemlich lang sein, sodass Sie möglicherweise nur eine Liste von Katzenrassen auf Seiten über Katzen und nur eine Liste von Hunderassen auf Seiten über Hunde anzeigen möchten. Der folgende Screenshot zeigt das Ziellayout, das der Benutzer erreichen möchte:

![untermenüs ziele tiere katzen](../../../en/images/menus/submenus/01-submenus-objectives-animals-cats.png)

In diesem Beispiel wird beim Auswählen des Menüelements "Tiere" die Seite "Tiere" geladen und das Katzen-Menümodul verschwindet (und auch kein Hunde-Modul). Wählen Sie das Menüelement "Katzen" aus, erscheint das Katzen-Menümodul neben der Katzen-Seite. Wählen Sie das Menüelement "Burmesen" aus, erscheint die Burmesen-Seite. Wählen Sie das Menüelement "Hunde" aus, wird das Katzen-Menümodul durch ein Hunde-Menümodul neben der Hunde-Seite ersetzt.

Um dieses Tutorial selbst auszuprobieren, müssen Sie einige Beiträge, ein Menü mit Menüelementen und drei Menümodule erstellen.

## Beiträge erstellen

Wenn Sie super effizient sind, können Sie einen Beitrag erstellen und dann ein Menüelement aus diesem Beitrag erstellen. Dafür müssten Sie zuerst ein neues Menü erstellen und einige zusätzliche Schritte während der Beitragserstellung unternehmen. Daher sollten Sie es zunächst einfach halten und mit Ihren neuen Beiträgen beginnen:

- Wählen Sie **Inhalt** → **Beiträge** → **+** aus dem Administrator-Menü. Oder wählen Sie die Schaltfläche `Neu` aus der Beitragsliste.
- Füllen Sie das Formular wie bei jedem anderen Beitrag aus.
- Wählen Sie die Schaltfläche `Speichern & Neu` anstelle von `Speichern & Schließen`, um mit dem nächsten neuen Beitrag fortzufahren.

Die oben gezeigten Beispieldaten erfordern sieben Beiträge.

## Ein neues Menü erstellen

Aus dem Administrator-Menü:

- Wählen Sie **Menüs** → **Verwalten**.
- Klicken Sie auf der Menü-Liste-Seite auf den `Neu`-Button, um ein neues Menü zu erstellen.
- Geben Sie im Formular "Menüs: Hinzufügen" dem Menü einen Titel: Tiere und einen eindeutigen Namen: tiere.
- In einigen Fällen müssen Sie sich vielleicht erinnern, wofür dieses Menü gedacht ist. Füllen Sie daher das Beschreibungsfeld aus.
- Speichern oder Speichern & Schließen.

![untermenüs neues menü](../../../en/images/menus/submenus/02-submenus-new-menu.png)

## Menüeinträge erstellen

Es gibt sieben Menüeinträge zu erstellen.

### Menüeintrag Tiere

Die neuen Menüeinträge werden im Menü Tiere zu finden sein.

- Wählen Sie **Menüs **→** Tiere **→** +** aus dem Administrator-Menü.
- Füllen Sie das Formular "Menü: Eintrag bearbeiten" aus.
  - Titel: Tiere
  - Menüeintragstyp: Einzelner Beitrag
  - Beitrag auswählen: Tiere - dies ist der übergeordnete Beitrag, der die Reihe über Tiere einleitet
  - Menü: Tiere
  - Übergeordnet: - Kein übergeordnetes Element - dies ist die Menüwurzel
- Wählen Sie **Speichern & Neu** aus der `Speichern & Schließen`-Dropdown-Liste.

### Menüeintrag Katzen

Dies ist eine Wiederholung des Menüeintrags Tiere. Ausnahme:

- Der Titel sollte Katzen sein.
- Der im Feld Beitrag auswählen ausgewählte Beitrag sollte `Katzen` sein.
- Das übergeordnete Element sollte auf `Tiere` gesetzt werden.

### Menüeintrag Burma-Katzen

Wiederholen Sie erneut. Ausnahme:

- Der Titel sollte Burma-Katzen sein.
- Der im Feld Beitrag auswählen ausgewählte Beitrag sollte `Burma-Katzen` sein.
- Das übergeordnete Element sollte auf `Katzen` gesetzt werden.

### Weitere Menüeinträge

Fahren Sie fort, bis Sie sieben Menüeinträge haben, einen für jeden Beitrag.  

## Menüpunktliste

Nachdem Sie alle Ihre Menüpunkte erstellt haben, überprüfen Sie, ob sie die korrekten Eltern-Kind-Beziehungen haben und in der richtigen Reihenfolge sind. Sie können nach der Spalte Reihenfolge (die zweite Spalte) sortieren und die Haltegriffe (vertikale Ellipse) verwenden, um Elemente in die richtige Reihenfolge zu ziehen. Wenn ein Element einen falschen Elternpunkt hat, wählen Sie einfach den Titel des Elements aus und ändern den Elternpunkt im Formular Menüs: Beitrag bearbeiten.

![Untermenüs Menüpunkte Liste](../../../en/images/menus/submenus/03-submenus-menu-items-list.png)

## Menümodule

In diesem Stadium haben Sie ein Menü, aber es gibt kein Modul, das einer Position auf der Seite zugewiesen werden kann. Sie könnten das gesamte Menü als Standard- oder Dropdown-Menü verwenden. Der Zweck dieser Anleitung ist es jedoch, zu zeigen, wie man Untermenüs erstellt. Dafür benötigen Sie drei verschiedene Module:

- Ein Modul "Tiere" für ein Untermenü mit Menüeinträgen zu Tieren, Katzen und Hunden.
- Ein Modul "Katzen" für ein Untermenü mit Menüeinträgen zu Katzenrassen.
- Ein Modul "Hunde" für ein Untermenü mit Menüeinträgen zu Hunderassen.

## Modul für das Untermenü Tiere

Im Administrator-Menü:

- Wählen Sie **Inhalt** → **Website-Module** → **+** oder wählen Sie `Neu` aus der Modul-Liste (Website).
- Wählen Sie das **Menü**-Modul aus.
- Geben Sie im Bearbeitungsformular Module: Menü die folgenden Daten ein:
  - Titel: Tiere
  - Menü auswählen: Tiere
  - Basiselement: Tiere (dies ist der übergeordnete Menüpunkt)
  - Startebene: 1
  - Endebene: 2 (dies beschränkt die Elemente auf die Menüpunkte Katzen und Hunde)
  - Position: sidebar-left (oder wo immer es passt)

![Untermenüs Tiere Modul](../../../en/images/menus/submenus/04-submenus-animals-module.png)

### Menüzuweisung für Tiere

Untermenüs werden normalerweise nur auf Seiten angezeigt, auf denen sie relevant sind, in diesem Fall nur auf drei Seiten. Im Reiter Menüzuweisung:

- Setzen Sie das Feld Modulzuweisung auf `Nur auf den ausgewählten Seiten`. Dadurch wird eine hierarchische Liste aller Elemente in allen Menüs angezeigt.
- Markieren Sie die Kästchen neben Tiere, Katzen und Hunde.
- Markieren Sie die Kästchen neben den Rassen von Katzen und Hunden. Andernfalls verschwindet das Untermenü Tiere auf Seiten über Rassen.
- Stellen Sie sicher, dass keine anderen Kästchen markiert sind.
- Speichern & Schließen

![Untermenüs Tiere Modul Menüzuweisung](../../../en/images/menus/submenus/05-submenus-animals-module-menu-assignment.png)

## Untermodul für Katzen-Menü

Dies ist sehr ähnlich:

- Wählen Sie **Inhalt**→**Seitenmodule**→**+** oder wählen Sie `Neu` aus der Liste der
  Module (Seite).
- Wählen Sie das **Menü**-Modul.
- Geben Sie im Bearbeitungsformular für Module: Menü die folgenden Daten ein:
  - Titel: Katzen
  - Menü auswählen: Tiere
  - Basis-Element: Katzen (dies ist das übergeordnete Menüelement)
  - Start-Level: 3
  - End-Level: Alle
  - Position: sidebar-left (oder wo immer es passt)

### Zuweisung des Katzen-Menüs

Von der Menüzuteilung:

- Setzen Sie das Feld Modulanweisung auf `Nur auf den ausgewählten Seiten`. Dies
  zeigt eine hierarchische Liste aller Elemente in allen Menüs an.
- Markieren Sie die Kontrollkästchen bei Katzen, Burmesen und Russisch Blau. Stellen Sie sicher, dass keine anderen Kontrollkästchen markiert sind.
- Speichern und schließen

## Modul für das Untermenü Hunde

Mehr vom Gleichen ...

## Menüpunkt-Alias

Bis hierhin ist alles gut! Aber es gibt keinen Link zur Tierseite im Hauptmenü oder in einem der anderen Menübereiche der Website. Der einfache Weg, dies zu beheben, ist mit einem Menüpunkt-Alias. Für dieses Beispiel wird ein Eintrag im Menü oben auf der Seite, betitelt als Hauptmenü-Blog, gemacht. Aus dem Administrator-Menü:

- Wählen Sie **Menüs** → **Hauptmenü-Blog** (oder eines Ihrer bevorzugten Seitenmenüs aus).
- Wählen Sie die Schaltfläche `Neu` aus der Toolbar.
- Füllen Sie das Formular Menüs: Element bearbeiten aus
  - Titel: Tiere
  - Alias: creatures - es gibt bereits einen Menüpunkt namens Tiere, daher müssen Sie einen anderen Alias verwenden.
  - Menüpunkt-Typ: Menüpunkt-Alias
  - Menüpunkt: Tiere - aus der Liste der vorhandenen Menüpunkte ausgewählt.

![Untermenüs Tiere-Alias](../../../en/images/menus/submenus/06-submenus-animals-alias.png)

- Speichern
- Reihenfolge - nach dem Speichern kann die Reihenfolge geändert werden. In diesem Beispiel wird es als erstes platziert.

## Überprüfen Sie das Ergebnis

Sehen Sie sich die Seiten auf Ihrer Website an. In diesem Beispiel werden die meisten Seiten die Untermenüs nicht auf der linken Seite anzeigen. Der Link "Tiere" im oberen Menü öffnet die Tierseite, von der aus es möglich ist, zu den Katzen- oder Hundeseiten zu navigieren:

![submenus objectives animals dogs](../../../en/images/menus/submenus/07-submenus-objectives-animals-dogs.png)

*Übersetzt von openai.com*

