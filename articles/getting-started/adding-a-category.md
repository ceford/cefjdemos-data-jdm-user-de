<!--
{
  "source": "https://docs.joomla.org/J4.x:Getting_Started:_Adding_a_Category",
  "title": "Hinzufügen einer Kategorie ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Webseitenbetreiber mit mehr als einer Handvoll von Beiträgen sollten darüber nachdenken, wie sie Inhalte am besten präsentieren, um die Navigation zu erleichtern. Wenn Sie beispielsweise einen Zoo, ein Museum, eine Mineraliensammlung oder einfach einen großen Garten besitzen, haben Sie möglicherweise etwa 1000 Exemplare zu beschreiben. Ein Beitrag für jedes Exemplar, mit Fotos, benötigt eine gewisse Organisationsstruktur. Wenn die Beiträge Dateien wären, würden Sie sie wahrscheinlich in einer Dateihierarchie ablegen. In einem CMS sind Beiträge zwar keine Dateien, aber Kategorien bieten eine ähnliche baumartige Struktur. Beispiel:

| Kategorie  | Unterkategorien                         |
|------------|-----------------------------------------|
| Säugetiere | Menschenaffen, Affen, Huftiere, Hunde, Katzen |
| Reptilien  | Schlangen, Echsen, Krokodile, Schildkröten   |
| Amphibien  | Frösche, Kröten                           |
| Vögel      | Greifvögel, Enten, Möwen, Finken, Meisen   |
| Gliederfüßer| Spinnen, Schmetterlinge, Bienen, Heuschrecken |
| Fische     | Haie, Lachs, Kabeljau, Heringe, Makrelen    |

Unterkategorien können ebenfalls weitere Unterkategorien haben. Eine maximal handhabbare Tiefe scheint etwa sieben zu betragen. Für die obige Tabelle könnte ein Museum weitere übergeordnete Kategorien hinzufügen:

```text
natur -> leben -> tiere -> säugetiere...
natur -> leben -> pflanzen -> bäume...
natur -> mineralien...
geschichte -> ägypten...
wissenschaft -> astronomie...
wissenschaft -> chemie...
```

Stellen Sie sich vor, wie viele Exemplare ein nationales oder kleines Stadtmuseum besitzt!

## Menüelement-Typen

Es gibt verschiedene Menüelement-Typen, die mit Kategorien funktionieren sollen:

- **Kategorie-Blog** Dies ist ein Seitenlayout, das einen oder zwei führende
  Beitrag-Starter hat, oft über die volle Seitenbreite, dann mehrere weitere Beitrag-Starter 
  in zwei oder drei Spalten und schließlich einen Paginierungsmechanismus, um 
  mehr Beiträge in derselben Kategorie zu verlinken. Der Starter ist der Inhalt vor 
  einem Seitenumbruch, oft die ersten ein oder zwei Absätze. Eine *Startseite* der Webseite ist 
  oft ein Kategorie-Blog, das *Alle Kategorien* umfasst. Ein *Hervorgehobene Beiträge* 
  Layout ähnelt einem Kategorie-Blog und wird oft auch als Startseite verwendet.
- **Kategorieliste** Dies ist ein Listenlayout, das eine Liste von
  Beiträgen in einer Kategorie anzeigt. Es kann mit einem Suchfilter angezeigt werden, um
  das Suchen nach Beiträgen nach Titel, Autor, Zugriffen, Tags oder Veröffentlichungsmonat zu ermöglichen.
- **Alle Kategorien in einer Beitragskategorie-Struktur auflisten** Dieses Layout listet eine 
  Kategoriestruktur auf, die ab einem gewählten Elternteil beginnt. Jeder Zweig ist einklappbar und
  ist sehr nützlich für große, komplexe Kategoriestrukturstrukturen.

Menüelemente werden in einem späteren Beitrag behandelt.

## Eine Kategorie erstellen

Das folgende Beispiel verwendet eine Kategorie "Säugetiere", inspiriert von der obigen Liste, um zu demonstrieren, wie man eine neue Kategorie erstellt:

![Kategorie-Bearbeitungsformular](../../../en/images/getting-started/adding-a-category/01-article-category-edit.png)

- Wählen Sie den **Inhalt**-Punkt aus dem Administrator-Menü, um ihn zu erweitern.
- Wählen Sie das **+**-Symbol neben dem Menüpunkt *Kategorien*, um das Kategorie-Bearbeitungsformular zu öffnen.
- Das Formular **Beiträge: Neue Kategorie** enthält nur ein Pflichtfeld: den *Titel*, in diesem Fall *Säugetiere*.
- Das Feld **Beschreibung** ist optional, aber es ist ratsam, es auszufüllen, da es in einigen Listen verwendet wird. Vorschlag:<br>
  *Säugetiere sind gleichwarme Tiere, die lebende Junge zur Welt bringen.*
- Das Feld **Übergeordnet** gibt an, ob es sich um eine Hauptkategorie (-Kein Übergeordnetes-) oder eine aus der Liste der Kategorien ausgewählte Unterkategorie handelt.
- **Speichern und Schließen**, um zur Liste der **Beiträge: Kategorien** zurückzukehren.

Diese Kategorie ist nun für die Verwendung mit Beiträgen verfügbar.

*Übersetzt von openai.com*

