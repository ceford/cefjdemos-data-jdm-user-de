<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Pagination",
  "title": "Beitrag: Bearbeiten - Paginierung ",
  "description": "", 
  "author": ""
}
-->

## Lange Beiträge

Das einzige Limit für die Länge eines Beitrags in Joomla ist die Größe des Datenbankfelds, das den Beitragstext enthält. Dieses ist sehr groß! Lange Beiträge können viele Bilder enthalten und benötigen Zeit zur Verarbeitung, was sich als Unannehmlichkeit für den Leser und die Website erweisen kann. Daher gibt es einen einfachen Mechanismus, um lange Beiträge in separate Seiten mit einem Inhaltsverzeichnis zu unterteilen.

## Eine Seitenumbruch Einfügen

Um Seitenumbrüche hinzuzufügen, öffnen Sie zunächst einen Beitrag im Texteditor. TinyMCE ist der Standardeditor, und gehen Sie wie folgt vor:

- Platzieren Sie den Cursor an der Stelle, an der ein Seitenumbruch erfolgen soll.
- Wählen Sie aus der **CMS-Inhalt**-Dropdown-Liste den Eintrag *Seitenumbruch* aus.
- Geben Sie im Seitenumbruch-Dialogfeld Folgendes ein:
  - *Seitentitel* – dies wird an den vorhandenen Seitentitel angehängt.
    Beispiel: Seite 2
  - *Inhaltsverzeichnis-Alias* – dies wird als Text im Inhaltsverzeichnis verwendet. Beispiel: Kapitel 2
- Wählen Sie die Schaltfläche **Seitenumbruch einfügen** aus.

![Seitenumbruch-Dialogformular](../../../en/images/articles/article-pagination/01-articles-edit-pagination.png)

- Wiederholen Sie dies für jeden Seitenumbruch, den Sie erstellen möchten.
- Speichern Sie den Beitrag und sehen Sie sich die Vorschau oder die Website-Ansicht an.

![Beitrags-Paginierung Website-Ansicht](../../../en/images/articles/article-pagination/02-articles-site-pagination.png)

## Bearbeiten oder Verschieben eines Seitenumbruchs

Sie können einen Seitenumbruch auswählen und löschen. Sie können ihn jedoch nicht ausschneiden und einfügen, und Sie können keinen bestehenden Seitenumbruch im Seitenumbruch-Formular öffnen. Um einen Seitenumbruch zu verschieben oder zu ändern, verwenden Sie den Quelltext-Editor wie folgt:

- Wählen Sie den Menüpunkt **Werkzeuge -> Quelltext+** im Texteditor.
- Der Quelltext-Editor zeigt den Quell-HTML-Code mit Syntaxhervorhebung an.
- Scrollen Sie nach unten zu dem Seitenumbruch, den Sie bearbeiten oder verschieben möchten.
- Um einen Seitenumbruch zu verschieben:
  - Markieren und schneiden Sie die Zeile aus, die den Seitenumbruch enthält.
  - Platzieren Sie den Cursor an der neuen Position und fügen Sie die ausgeschnittene Zeile ein.
- Zum Bearbeiten:
  - Ändern Sie den Titeltext und/oder den Alternativtext nach Belieben.
- Wählen Sie **Speichern**.
- Speichern Sie den Beitrag und sehen Sie sich die Vorschau- oder Website-Ansicht an.

Der Quelltext-Editor befindet sich in einem Popup-Dialog:

![Quelltext-Editor](../../../en/images/articles/article-pagination/03-articles-edit-pagination-source-code.png)

*Übersetzt von openai.com*

