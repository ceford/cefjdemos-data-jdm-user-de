<!--
{
  "source": "https://docs.joomla.org/J4.x:Multilingual_Associations",
  "title": "Mehrsprachige Beiträge",
  "description": "", 
  "author": ""
}
-->

## Mehrsprachige Seiten

Installieren Sie zusätzliche Sprachen auf Ihrer Seite und Sie könnten denken, Sie haben eine mehrsprachige Seite. Fast, aber nicht ganz. Von Menschen eingegebene Texte müssen von Menschen übersetzt werden. Das umfasst solche Dinge wie Beitragstitel und -inhalte, Menütitel, Modul-Titel und in einigen Fällen auch Inhalte und mehr. Sie können einfach dieselben Elemente in jeder verwendeten Sprache erstellen. Das funktioniert gut, kann aber etwas mühsam sein. Da kommt die Multilingual Associations-Komponente ins Spiel. Sie ist so konzipiert, dass sie Inhalte in verschiedenen Sprachen nebeneinander anzeigt, damit Sie leicht von einer Sprache in die andere übersetzen können.

## Elemente für Assoziationen

Die folgenden Elemente können in Assoziationen einbezogen werden:

- Inhalt: Beiträge und Kategorien
- Kontakte: Kontakte und Kategorien
- Menüs: Menüelemente
- Newsfeeds: Newsfeeds und Kategorien
- Andere: Drittanbieterkomponenten können so codiert werden, dass sie Assoziationen verwenden.

Der folgende Screenshot zeigt eine Beispielauflistung von Beiträgen in Englisch mit ihren Entsprechungen in anderen Sprachen.

![Liste der mehrsprachigen Assoziationen](../../../en/images/languages/multilingual-associations/01-multilingual-associations-list.png)

Der letzte Beitrag über Berge hat noch keine entsprechenden Beiträge in anderen Sprachen. Die fehlenden Beiträge können von der Originalversion auf Englisch von dieser Seite übersetzt werden.

## Erstellen einer Übersetzung für Beiträge

Wenn Sie eine mehrsprachige Website erstellt haben, haben Sie eine Sprachkategorie für jede Sprache angelegt und möglicherweise einen Beitrag in Ihrer Standardsprache erstellt. Wenn nicht, tun Sie dies jetzt. Der Beispielbeitrag trägt den Titel "Berge". Sie können die zugehörigen Beiträge direkt aus dem Formular "Beitrag: Bearbeiten" erstellen. In diesem Beispiel wird stattdessen die Liste der mehrsprachigen Zuordnungen verwendet. Der übersetzte Text für dieses Beispiel wurde mit Google Translate erhalten.

- Wählen Sie **Komponenten** → **Mehrsprachige Zuordnungen** aus dem Administrationsmenü.
- Für den Beitrag ohne Zuordnungen wählen Sie eine der Schaltflächen in der Spalte "Nicht zugeordnet", in diesem Beispiel fr-FR.
- Geben Sie im Formular "Mehrsprachige Zuordnungen: Zuordnungen bearbeiten" einen Ziel-Titel ein: Montagne
- Geben Sie im Textfeld "Zielbeitrag" den neuen Text ein, übersetzt oder kopiert und eingefügt aus einem Übersetzungsdienst.
- Setzen Sie die Kategorie auf die Sprachkategorie, in diesem Beispiel Französisch (fr-FR) (in der Screenshot nicht angezeigt - sie befindet sich weiter unten).
- Wählen Sie **Ziel speichern** aus der Toolbar.
- Wählen Sie **Schließen**.
- Wiederholen Sie dies für die anderen Sprachen.

![mehrsprachige Zuordnungen bearbeiten](../../../en/images/languages/multilingual-associations/02-multilingual-associations-edit.png)

## Erstellung einer Menüübersetzung

Fortsetzung mit dem Berg-Beispiel:

- Wählen Sie **Menüs **→** Hauptmenü (en-GB)**, vorausgesetzt, dass dies Ihr sprachspezifisches Standardmenü ist.
- Wählen Sie die **Neu**-Schaltfläche aus der Werkzeugleiste.
- Geben Sie im Formular Menüs: Neues Element einen Titel ein: **Berge**.
- Verwenden Sie die Auswahl-Schaltfläche im Feld Menüpunkttyp.
- Wählen Sie **Beiträge**→**Einzelner Beitrag** aus dem Popup-Formular Menüpunkttyp aus.
- Verwenden Sie die Auswahl-Schaltfläche im Feld Beitrag auswählen.
- Wählen Sie **Berge** aus der Liste Beitrag wählen.
- Wählen Sie **Englisch (en-GB)** aus der Dropdown-Liste Sprache.
- Speichern.
- Wählen Sie die Registerkarte **Zuordnungen**.
- Verwenden Sie für jede Sprache die **+Erstellen**-Schaltfläche, um einen äquivalenten übersetzten Menüpunkt zu erstellen.
  - Geben Sie den übersetzten **Titel** ein.
  - Stellen Sie sicher, dass das Menü für die gewählte Sprache eingestellt ist.
  - **Speichern & Schließen**

## Seitenansicht

Öffnen oder aktualisieren Sie die Seitenansicht, um zu überprüfen, dass Ihre Menüs und Beiträge wie erwartet angezeigt werden.

![mehrsprachige Zuordnungen Seitenansicht](../../../en/images/languages/multilingual-associations/03-multilingual-associations-site.png)

*Übersetzt von openai.com*

