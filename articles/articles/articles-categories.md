<!--
{
  "source": "https://docs.joomla.org/J4.x:Create_and_Manage_Article_Categories",
  "title": "Beiträge: Kategorien",
  "description": "", 
  "author": ""
}
-->

## Einführung

Stellen Sie sich eine Bibliothek ohne Klassifikationssystem vor: Bücher werden einfach in der Reihenfolge, in der sie eingehen, in die Regale gestellt. Das ist nicht sehr hilfreich, wenn die Bibliothek Millionen von Büchern hat und Sie nach etwas über Geschichte, Gartenarbeit oder Wissenschaft suchen. Dasselbe Argument gilt für Beiträge. Wenn Sie dutzende, hunderte oder tausende von Beiträgen haben, benötigen Sie wirklich eine Methode, um sie zu klassifizieren, damit Sie leicht finden können, was Sie brauchen. Dafür sind Kategorien da.

Eine Joomla!-Kategorie kann sowohl Beiträge als auch Unterkategorien in einer baumartigen Struktur enthalten, die in beliebige Tiefe geschachtelt ist, obwohl es unwahrscheinlich ist, dass Sie tiefer als drei oder vier Ebenen gehen möchten. Zum Beispiel, wenn Ihre Beiträge über die Natur sind, könnten Sie sie folgendermaßen klassifizieren:

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

In diesem Beispiel könnte die *Tiere*-Kategorie Beiträge über Tiere im Allgemeinen sowie Unterkategorien für Beiträge über verschiedene Tierarten enthalten.

Joomla bietet eine einzelne Standardkategorie mit dem Namen Unkategorisiert. Jeder Beitrag, der keiner von Ihnen erstellten spezifischen Kategorie zugewiesen ist, wird Mitglied der Kategorie Unkategorisiert. Sie erstellen Kategorien nach Bedarf, um der Natur Ihrer Beiträge zu entsprechen.

Ein Beitrag kann nur in einer Kategorie sein. In manchen Fällen reicht das nicht ganz aus. Angenommen, Sie möchten nach Büchern aller Art suchen, die in einer bestimmten Sprache geschrieben wurden, oder nach allen Pflanzen, die giftig sind, oder nach allen Tieren, die gefährlich sind. Genau hier werden Tags nützlich. Sie werden an anderer Stelle behandelt.

### Verwendung von Kategorien

Auf der Administratorseite *Beiträge* verfügt das Formular *Filteroptionen* über eine **- Kategorie auswählen -** Dropdown-Liste, die einen Kategoriebereich anzeigt, mit dem Sie nach Beiträgen in einer ausgewählten Kategorie filtern können. Sie können auch Menüelementtypen *Kategorien-Blog* und *Kategorien-Liste* erstellen, um Beiträge aus einer ausgewählten Kategorie für die Besucher der Seite anzuzeigen.

## Hinzufügen von Kategorien und Unterkategorien

Es gibt mehrere Wege zur Seite *Beiträge: Neue Kategorie*:

- Über das **Home Dashboard** Wählen Sie das **Plus (+) Symbol** rechts neben dem 
  *Beiträge Kategorien* Link. Letzterer führt zur *Beiträge: Kategorien* 
  Listen-Seite.
- Über das **Administrator-Menü** Wählen Sie den Menüpunkt *Inhalt* aus, um die Liste zu erweitern, und wählen Sie dann das **Plus (+) Symbol** rechts neben dem *Kategorien* Link.
- Über das **Inhalt Dashboard** Wählen Sie das Dashboard-Symbol rechts neben dem *Inhalt* Link im Administrator-Menü und wählen Sie dann im Dashboard-Panel *Inhalt* das **Plus (+) Symbol** rechts neben dem *Kategorien* Link.
- Über **Beiträge: Kategorien** Folgen Sie einem der Wege zur Listen-Seite und wählen Sie die **Neue** Schaltfläche in der Toolbar.

Der folgende Screenshot zeigt den *Beitragskategorien* Link im Home Dashboard zur Liste der Kategorien und das danebenliegende *Plus-Symbol*, das zum Formular *Beiträge: Neue Kategorie* führt.

![Das Symbol zum Hinzufügen einer Kategorie im Home-Dashboard hervorgehoben](../../../en/images/articles/articles-categories/01-category-add-via-home-dashboard.png)

## Die Beiträge: Neues Kategorieformular

![Das neue Kategoriebearbeitungsformular der Beiträge](../../../en/images/articles/articles-categories/02-article-category-edit.png)

Der obige Screenshot zeigt das ausgefüllte Formular. Es gibt nur zwei Felder, die einige Inhalte benötigen. Alles andere hat Standard- oder Nullwerte, die Sie momentan belassen und später bei Bedarf ausfüllen können.

- **Titel** Dies ist das einzige Pflichtfeld. Es sollte kurz, aber beschreibend für die Kategorie sein.

### Der Kategorie-Tab

- **Beschreibung** Obwohl nicht zwingend erforderlich, kann dieses Feld in den Kategorielisten-Seiten der Website angezeigt werden, die durch Menüeinträge gesteuert werden. Möglicherweise müssen Sie später die Beschreibung aktualisieren.
- **Übergeordnet** Wenn auf *- Kein Übergeordneter -* gesetzt, ist dieses neue Element eine potenzielle übergeordnete Kategorie für andere Kategorien. Wenn eine andere Kategorie als übergeordnet ausgewählt wird, ist dieses neue Element eine Unterkategorie.
- **Status** Standardmäßig ist eine neue Kategorie auf *Veröffentlicht* gesetzt. Sie können den Status einer Kategorie zu *Veröffentlicht*, *Nicht veröffentlicht*, *Archiviert* oder *Papierkorb* ändern.
  [ToDo] Erklären, was passiert, wenn eine Kategorie nicht veröffentlicht wird...
- **Zugriff** Standardmäßig ist der Zugriff auf *Öffentlich* gesetzt. Weitere Optionen zur Einschränkung des Zugriffs sind *Gast*, *Registriert*, *Speziell* und *Super Benutzer*.
  [ToDo] Erklären, wie der Zugriff auf eine Kategorie verwendet werden könnte...
- **Sprache** In mehrsprachigen Seiten wird durch Setzen auf *Alle* die neue Kategorie unabhängig von der Site-Sprache. Wenn auf eine bestimmte Sprache eingestellt, ist sie nur auf Seiten in dieser Sprache verfügbar.
- **Tags** Wenn Sie sie verwenden, können Sie der Kategorie ein oder mehrere Tags hinzufügen. Das Setzen von Tags auf Kategorieebene ist eine gute Möglichkeit, um Konsistenz zu wahren. Für dieses Tutorial wurde ein *Natur*-Tag erstellt und verwendet, um Listen zu filtern, damit nur Elemente angezeigt werden, die mit den Tutorials zusammenhängen.
- **Hinweis** und **Versionshinweis** Verwenden Sie diese, um relevante Notizen hinzuzufügen, falls erforderlich.

### Der Optionen-Tab

Einstellungen in diesem Tab beeinflussen das Erscheinungsbild dieser Kategorie auf den Seiten der Website.

- **Layout** Dies bezieht sich auf die Platzierung von Inhalten auf der Seite. Es kann je nach verwendetem Komponent und Template Auswahlmöglichkeiten für Layouts geben.
  [ToDo] Beispiele...
- **Bild** Möglicherweise möchten Sie ein Bild verwenden, um als Symbol zu dienen, sodass diese Kategorie in einer Liste von Kategorien sofort erkannt werden kann. Wird es zu einem solchen Zweck verwendet, ist eine *Bildbeschreibung (Alt-Text)* nicht notwendig, jedoch sollte das *Keine Beschreibung* Kontrollkästchen aktiviert werden.

### Speichern & Schließen

- **Speichern & Schließen** Um die Bearbeitung dieser Kategorie abzuschließen. Oder im Dropdown-Menü...
  - **Speichern & Neu** Speichern Sie diese Kategorie und öffnen Sie ein neues Bearbeitungsformular für eine neue Kategorie. Zum Beispiel möchten Sie vielleicht ein Kategoriensystem starten, indem Sie eine *Affen*-Kategorie mit *Säugetiere* als übergeordnet hinzufügen.
  - **Speichern ins Menü als Liste** ...
  - **Speichern ins Menü als Blog** ...
  - **Als Kopie speichern** ...

Durch das Schließen des Bearbeitungsformulars gelangen Sie zur **Beiträge: Kategorien**-Liste.

![Eine Kategorienliste, gefiltert nach dem Tag Natur](../../../en/images/articles/articles-categories/03-categories-list.png)

### Speichern ins Menü als Liste

Die Auswahl dieses Elements aus dem Dropdown-Menü *Speichern & Schließen* wird das Kategoriebearbeitungsformular speichern und schließen und ein neues Menüeintragsformular mit allen Daten öffnen, die benötigt werden, um eine *Kategorienliste* für diese Kategorie zu erstellen. Möglicherweise möchten Sie den *Titel* ändern. Zum Beispiel könnte es *Säugetier-Beitragsliste* sein, um klarzustellen, dass es sich wahrscheinlich um eine Liste von Beiträgen handelt.

Im *Seitendarstellung*-Tab versuchen Sie, das Feld *Seitenüberschrift anzeigen* auf *Anzeigen* zu setzen. Das zeigt *Säugetier-Beitragsliste* als fettgedruckte Überschrift oben auf der Seite und verleiht ihr ein insgesamt vollständigeres Erscheinungsbild.

### Speichern ins Menü als Blog

Die Auswahl dieses Elements aus dem Dropdown-Menü *Speichern & Schließen* wird das Kategoriebearbeitungsformular speichern und schließen und ein neues Menüeintragsformular mit allen Daten öffnen, die benötigt werden, um einen *Kategorienblog* für diese Kategorie zu erstellen. Möglicherweise möchten Sie den *Titel* ändern. Zum Beispiel könnte es *Säugetier-Beitragsblog* sein, sodass die neuesten Beiträge über Säugetiere vorgestellt werden.

Im *Seitendarstellung*-Tab versuchen Sie, das Feld *Seitenüberschrift anzeigen* auf *Anzeigen* zu setzen. Das zeigt *Säugetier-Beitragsblog* als fettgedruckte Überschrift oben auf der Seite und verleiht ihr ein insgesamt vollständigeres Erscheinungsbild.

Der folgende Screenshot zeigt die Seitenansicht einer in Entwicklung befindlichen Kategorien-Blog-Seite.

![Kategorie-Blog-Seite Säugetiere](../../../en/images/articles/articles-categories/04-article-mammals-articles-blog-site-view.png)

## Tipps

- Sie können auch Beitragskategorien direkt innerhalb eines Beitrags erstellen.
- Denken Sie daran, dass Sie einen Beitrag nur einer Kategorie zuweisen können.
- Da sowohl Hauptkategorien als auch Unterkategorien weitere
  Unterkategorien haben können, planen und organisieren Sie die Kategorien sorgfältig. Eine komplizierte
  Kategorierhierarchie kann eine Herausforderung bei der Verwaltung sein.
- Eine weitere Methode zur Gruppierung von Inhalten in Joomla ist die Verwendung der **Tags**-Komponente, mit der Sie Ihren Beiträgen mehrere Tags hinzufügen können.
  Die Verwendung von Kategorien und Tags kann helfen, die Anzahl der
  Unterkategorien zu minimieren und bietet eine effiziente Möglichkeit, Website-
  Inhalte zu strukturieren und den Besuchern mehr Funktionen zur Navigation 
  der Inhalte zu bieten.

