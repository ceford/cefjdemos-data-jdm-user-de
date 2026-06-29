<!--
{
  "source": "https://docs.joomla.org/J4.x:Articles_and_categories",
  "title": "Grundkonzepte",
  "description": "", 
  "author": ""
}
-->

## Einführung

Um mit Joomla zu beginnen, müssen Sie sich einiger grundlegender Bausteine bewusst sein: Beiträge, Kategorien, Menüeinträge, Menüs und Module. Sie werden hier kurz beschrieben, falls Sie den Sprung wagen und einige Inhalte erstellen möchten.

## Beiträge

In Joomla! ist ein Beitrag eine in sich geschlossene Einheit von schriftlichen Informationen, die auf einer Website angezeigt werden sollen. Er enthält normalerweise etwas Text und kann Bilder und andere Arten von Inhalten enthalten. Für viele Joomla! Websites bilden Beiträge den Großteil der präsentierten Informationen.

Es ist wichtig zu verstehen, dass der Inhalt der Website völlig getrennt von der Formatierung der Website ist, also der Art und Weise, wie sie auf der Seite aussieht. Daher ist es am besten, Beiträge als reinen Inhalt unabhängig von der Präsentation zu betrachten. Derselbe Beitrag könnte mit verschiedenen Schriftarten, Farben, Überschriften und Hintergründen angezeigt werden und könnte an unterschiedlichen Stellen auf der Seite erscheinen, wobei alles von anderen Einstellungen im Joomla! CMS abhängt.

## Kategorien

Stellen Sie sich eine Bibliothek ohne Klassifizierungssystem vor: Bücher werden einfach in der Reihenfolge, in der sie eingehen, in die Regale gestellt. Das ist nicht sehr hilfreich, wenn die Bibliothek Millionen von Büchern hat und Sie nach etwas über Geschichte, Gartenarbeit oder Wissenschaft suchen. Das gleiche Argument gilt für Beiträge. Wenn Sie Dutzende, Hunderte oder Tausende von Beiträgen haben, brauchen Sie wirklich eine Methode, um sie zu klassifizieren, damit Sie leicht finden können, was Sie brauchen. Dafür sind Kategorien da.

Eine Joomla!-Kategorie kann sowohl Beiträge als auch Kategorien in einer baumähnlichen Struktur enthalten. Wenn sich eine Kategorie in einer anderen Kategorie befindet, wird sie als Unterkategorie dieser Kategorie bezeichnet. Unterkategorien können ebenfalls weitere Unterkategorien haben, obwohl es unwahrscheinlich ist, dass Sie über eine Tiefe von drei oder vier hinausgehen möchten.

Zum Beispiel, wenn Ihre Beiträge über die Natur sind, könnten Sie sie wie folgt klassifizieren:

- Tiere
  - Vögel
    - Falken
    - Finken
    - Möwen
  - Säugetiere
    - Menschenaffen
    - Affen
    - Nagetiere
- Pflanzen
  - Blumen
    - Gänseblümchen
    - Rosen
  - Bäume
    - Eichen
    - Ulmen

In diesem Beispiel könnte die Kategorie Tiere Beiträge über Tiere im Allgemeinen sowie Unterkategorien für Beiträge über verschiedene Tierarten enthalten.

Kategorien ermöglichen es Ihnen auch, auszuwählen, welche Beiträge Sie auf jeder Seite der Website anzeigen möchten. Daher möchten Sie möglicherweise alle Beiträge, die auf derselben Seite sein sollen, in derselben Kategorie haben.

Ein Beitrag kann nur in einer Kategorie im Kategoriebereich sein. Zum Beispiel könnten Sie eine Kategorie namens Pflanzen haben und in dieser Kategorie eine Unterkategorie namens Bäume und eine andere namens Blumen. Beiträge über Blumen würden der Kategorie Blumen zugewiesen werden und diejenigen über Bäume der Kategorie Bäume. Sie können nicht einen Beitrag haben, der in beiden Kategorien Blumen und Bäume ist. Wenn Sie einen Beitrag haben, der über beides handelt, würden Sie ihn in die Kategorie Pflanzen einordnen. In einigen Fällen benötigen Sie möglicherweise eine flexiblere Methode, um Ihre Beiträge zu klassifizieren. Hier kommen Tags nützlich ins Spiel. Sie werden an anderer Stelle behandelt.

Kategorien werden auch von anderen Komponenten verwendet, einschließlich Banner, Kontakte und News-Feeds. Diese Kategorien sind vollständig von Beitragskategorien getrennt und werden auf verschiedenen Joomla! Administrator-Seiten eingerichtet. Wenn Sie also etwas über Kategorien sehen, kann es sich auf Beitragskategorien beziehen oder auf Kategorien dieser anderen Komponenten.

## Menüelemente

Neue Beiträge sind möglicherweise nicht auf der Website sichtbar. Sie benötigen Menüpunkte, um ihre Anzeige zu steuern. Menüpunkte sind die grundlegenden Navigationseinheiten einer Joomla!-Seite. Nach dem Aufrufen einer Seite der Website führen die meisten Menüpunkte zu anderen Seiten der Site.

Es gibt viele Arten von Menüeinträgen. Der einfachste ist der Einzelbeitrag-Menüeintrag, der zu einer Seite mit nur einem Beitrag verlinkt. Eine andere Art von Menüeintrag ist der Kategorie-Blog. Dieser führt zu einer Seite, die alle Beiträge einer Kategorie anzeigt. In beiden Fällen wird die URL der Zielseite durch den Menüeintrag festgelegt. Das Layout (d.h. wie der Inhalt auf der Seite organisiert ist) der Zielseite wird ebenfalls durch den Menüeintrag bestimmt. Zum Beispiel kann im Fall des Kategorie-Blogs eine Einführung zu jedem Beitrag angezeigt werden. Diese Einführungen werden Vorschauen genannt. Und diese Vorschauen können in einer oder mehreren Spalten dargestellt werden. Ihre Reihenfolge kann ebenfalls angepasst werden. Beiträge können chronologisch beginnend mit dem neuesten erscheinen. In diesem Fall, wenn Sie einen neuen Beitrag der ausgewählten Kategorie zuweisen, wird er automatisch als erster Beitrag auf der Seite angezeigt.

Eine Startseite einer Website ist oft ein Menüpunkt vom Typ Kategorie-Blog oder ein Menüpunkt vom Typ Beiträge.

## Menüs

Ein Menü ist ein Container für Menüpunkte. Eine Standardinstallation von Joomla! erstellt ein Hauptmenü für Sie mit einem einzelnen Menüpunkt namens Startseite. In vielen Fällen werden Sie nur ein Menü verwenden, aber Sie können mehr als eines haben. Menüs können eine Baumstruktur haben, wobei einige Elemente übergeordnete Elemente für andere sind.

## Module

Module sind kleine Erweiterungen, die für besondere Zwecke verwendet werden. Um ein Menü auf der Website anzuzeigen, müssen Sie es einem Menümodul zuweisen. Dann können Sie den Ort des Menüs auf der Seite angeben (oberhalb, unterhalb oder neben dem Hauptseiteninhalt). Ein Anmeldeformular ist eine andere Art von Modul, das oft rechts vom Hauptinhalt einer Seite angezeigt wird.

*Übersetzt von openai.com*


