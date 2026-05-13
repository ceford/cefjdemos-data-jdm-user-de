<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Mehrsprachige Websites ",
  "description": "", 
  "author": ""
}
-->

Let me know if you need further assistance!
## Einführung

Wenn Sie eine mehrsprachige Website haben, können Sie die Bezeichnungen und Beschreibungen von Feldern und Feldgruppen in der Sprache des Benutzers anzeigen. Dazu:

1. Definieren Sie den Titel und die Beschreibung Ihrer Feldgruppe als Sprachkonstanten.
2. Definieren Sie die Bezeichnung und die Beschreibung Ihres Feldes als Sprachkonstanten.
3. Richten Sie diese Sprachkonstanten als Overrides für jede Ihrer Sprachen ein.

Im folgenden Beispiel werden eine Kontaktfeldgruppe und ein Feld für die persönlichen Vorlieben eines Kontakts erstellt. Die Feldgruppe heißt Favoriten und das Beispiel-Feld heißt Auto. Natürlich können weitere Felder für andere Lieblingsdinge, wie Essen oder Filme, hinzugefügt werden.

Um diesem Beispiel zu folgen, wird angenommen, dass Sie eine mehrsprachige Website eingerichtet haben, wie im [Mehrsprachige Websites](jdocmanual?article=user/languages/setup-a-multilingual-site) Tutorial beschrieben.

## Sprachkonstanten

Sprachkonstanten sind Platzhalter, die durch Sprachwerte ersetzt werden, wenn eine Seite dargestellt wird. Die Konstanten und ihre Werte werden in Sprachdateien wie JPATH_SITE/languages/en-GB/com_contact.ini und JPATH_SITE/administrator/languages/en-GB/com_contact.ini für das Frontend bzw. Backend gespeichert. Üblicherweise beginnen die meisten Sprachkonstanten mit dem Namen der Erweiterung, komplett in Großbuchstaben, zum Beispiel COM_CONTACT_...

Sprachübersteuerungen sind benutzerdefinierte Ersetzungen für bestehende Sprachkonstanten und -werte oder komplett neue Konstanten und Werte, wie in diesem Beispiel. Sie werden alle in einzelnen Dateien gespeichert, eine für die Site-Seiten und eine andere für die Administrator-Seiten:
```
SITE_ROOT/language/overrides/en-GB.override.ini
SITE_ROOT/administrator/language/overrides/en-GB.override.ini
```
Es ist wichtig, dass neue benutzerdefinierte Sprachkonstanten eindeutig sind, um zu vermeiden, dass bestehende Konstanten überschrieben werden. Zum Beispiel:

COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES="Favoriten"
COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION="Lieblingsauto, -film, etc."
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR="Lieblingsauto"
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION="Wird manchmal als Sicherheitsfrage verwendet"

Wenn es ein Problem mit der Syntax einer Sprachdatei gibt, wird sie nicht geladen und alle darin enthaltenen Konstanten könnten auf den Ausgabeseiten erscheinen. Beachten Sie außerdem, dass eine Datei in alphabetischer Reihenfolge sortiert wird.

## Definieren der Überschreibungen

Es ist wichtig, englische (GB) Überschreibungen zu erstellen. Joomla lädt zuerst die en-GB-Übersetzungsdateien und überschreibt dann die Werte mit einer ausgewählten Sprachdatei. Dies stellt sicher, dass Benutzer niemals eine Textkonstante sehen sollten. Wenn ein übersetzter Wert fehlt, wird Englisch in der Ausgabe erscheinen. Das sieht zwar seltsam aus, ist aber besser, als eine recht lange Konstante zu sehen, die normalerweise Layouts stört.

Vom Administratormenü:

* Wählen Sie **System / Verwaltungspanel / Sprachüberschreibungen**
* Wählen Sie **Englisch (Vereinigtes Königreich) - Site** aus der Liste *Sprache & Client auswählen*
* Wählen Sie die **Neu** Schaltfläche aus der Werkzeugleiste.
* Geben Sie im Feld **Sprachkonstante** *COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES* ein
* Geben Sie im Feld **Text** den Wert *Favourites* ein
* Aktivieren Sie das Kontrollkästchen **Für beide Standorte**. Dies wird Überschreibungen sowohl für die Site- als auch die Administrator-Seiten erstellen.
* Wählen Sie **Speichern & Neu** aus der Liste *Speichern * Schließen*.
* Wiederholen Sie dies für jede der anderen erforderlichen Konstanten.
* Wählen Sie **Schließen** nachdem der letzte Eintrag gespeichert wurde.
* Wiederholen Sie dies für jede der installierten Sprachen.

Der folgende Screenshot zeigt ein Beispiel für die Erstellung einer Überschreibung für eine deutsche Sprachkonstante.

![Erstellung von Überschreibungen in Deutsch](../../../en/images/fields/adding-custom-fields-multilingual-sites/01-fields-overrides-creation-de.png)

## Definieren der Feldgruppe

Vom Administrator-Menü:

* Wählen Sie den Menüpunkt **Komponenten / Kontakte / Feldgruppen** aus.
* Klicken Sie auf die **Neu**-Schaltfläche in der Werkzeugleiste.
* Geben Sie im Titel-Feld den konstanten Wert COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES ein.
* Geben Sie im Beschreibungsfeld den konstanten Wert COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION ein.
* Wählen Sie **Speichern & Schließen** aus der Werkzeugleiste.

## Das Feld definieren

Um ein Lieblingsauto auszuwählen, könnten Sie eine Dropdown-Liste von Autos bereitstellen, die Sie definieren, oder eine Dropdown-Liste von Autos, die aus einer Datenbanktabelle gewonnen wurden, oder eine Liste von Optionsfeldern mit von Ihnen definierten Labels. In diesem Fall ermöglicht ein einfaches Texteingabefeld die Eingabe jeder beliebigen Marke und jedes Modells eines Autos aus der gesamten Geschichte der Automobilindustrie.

Vom Administrator-Menü aus:

* Wählen Sie den Menüpunkt **Komponenten / Kontakte / Felder** aus.
* Wählen Sie die Schaltfläche **Neu** aus der Werkzeugleiste.
* Geben Sie im Titelfeld die Konstante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR ein.
* Wählen Sie im Typ-Feld **Text (text)** aus, falls es nicht bereits ausgewählt ist.
* Geben Sie im Beschreibungsfeld die Konstante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION ein.
* Wählen Sie im Feld **Feldgruppe** (rechts) die von Ihnen erstellte Feldgruppe aus.
* Wählen Sie **Speichern & Schließen** aus der Werkzeugleiste.

## Einen Kontakt bearbeiten

Wenn Englisch ausgewählt ist, bevor Sie sich als Administrator anmelden, sollte das Kontakteingabeformular einen Tab mit dem englischen Namen Ihrer Feldgruppe und Felder in dieser Gruppe ebenfalls mit englischen Werten enthalten.

![Dateneingabe auf Englisch](../../../en/images/fields/adding-custom-fields-multilingual-sites/02-fields-overrides-entry.png)

Wenn Deutsch ausgewählt wird, bevor Sie sich als Administrator anmelden, sollten Sie die deutschen Übersetzungen Ihrer Sprachkonstanten sehen:

![Dateneingabe auf Deutsch](../../../en/images/fields/adding-custom-fields-multilingual-sites/03-fields-overrides-entry-de.png)

Hinweis: Übersetzung durch translate.google.co.uk!

## Einen Kontakt anzeigen

Auf Englisch:

![Datenanzeige auf Englisch](../../../en/images/fields/adding-custom-fields-multilingual-sites/04-fields-overrides-display.png)

Und auf Deutsch:

![Datenanzeige auf Deutsch](../../../en/images/fields/adding-custom-fields-multilingual-sites/05-fields-overrides-display-de.png)

*Übersetzt von openai.com*

