<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Links",
  "title": "Beitrag: Bearbeiten - Links  ",
  "description": "", 
  "author": ""
}
-->

## Zugängliche Links

Wählen Sie einen Link in einem Dokument aus, und Ihr Browser öffnet das verknüpfte Dokument entweder im selben Fenster, in einem neuen Fenster oder in einem neuen Tab. Eine Person, die einen Screenreader verwendet, navigiert möglicherweise nur über Links, daher muss der Linktext aussagekräftig sein.

Das folgende Beispiel zeigt eine **gute Praxis**, da es angibt, wohin der Link führt:

- Um mehr zu erfahren, lesen Sie unser [Manifest](#)

Das folgende Beispiel zeigt eine **schlechte Praxis**, da es keinen Hinweis auf die Art des Ziels gibt und es möglicherweise einer von mehreren ähnlichen Links auf derselben Seite ist:

- Um mehr zu erfahren, klicken Sie [hier](#)

Um mehr über zugängliche Links zu erfahren, lesen Sie diesen Beitrag über 
[Erstellen von gültigen und zugänglichen Links](https://www.a11yproject.com/posts/creating-valid-and-accessible-links/).

## Eingebettete Links

Dieser Beitrag handelt von Links, die im Inhalt eines Beitrags eingebettet sind. Es gibt einen separaten Beitrag zur Nutzung des Tabs [Bilder und Links](jdocmanual?article=user/articles/article-images-and-links), um mit einem Beitrag verknüpfte Links einzufügen.

Links, die in einen Beitrag eingebettet sind, können auf andere Seiten innerhalb der Website (interne Links) oder auf andere Websites (externe Links) verweisen. Das Verfahren zum Einfügen der beiden Linktypen unterscheidet sich. Sie werden jeweils unten beschrieben.

## Einfügen eines internen Links

Der Prozess zum Einfügen eines Links zu einem Beitrag auf derselben Website ist einfach:
- Geben Sie den Satz mit dem Linktext ein. Zum Beispiel:

  *Für weitere Informationen siehe bitte die Seite über Frösche.*
- Wählen Sie den Linktext: *Frösche*

Der Link kann zu einem einzelnen Beitrag oder zu einem Menüpunkt für einen Kategoriebereich, eine Kategorieliste oder empfohlene Beiträge führen.

### Ein Link zu einem einzelnen Beitrag

- Wählen Sie *Beitrag* aus der *CMS-Inhalt* Dropdown-Liste.
- Wählen Sie den gewünschten Beitragstitel aus dem Beitrags-Dialog.
- Speichern Sie den Beitrag und probieren Sie ihn mit der Vorschau-Schaltfläche in der Toolbar aus.

### Ein Menüpunkt-Link

- Wählen Sie *Menü* aus der *CMS-Inhalt* Dropdown-Liste.
- Wählen Sie den gewünschten Menüpunkt aus dem Menü-Dialog.
- Speichern Sie den Beitrag und probieren Sie ihn mit der Vorschau-Schaltfläche in der Toolbar aus.

## Einen externen Link einfügen

Für einen externen Link ist es am besten, den Link aus der URL-Leiste des Browsers zu kopieren. Dafür ist es hilfreich, separate Fenster oder Tabs für das *Beiträge: Bearbeiten*-Formular Ihrer Website und die externe Seite, zu der Sie einen Link erstellen, geöffnet zu haben.
Vorgehensweise:

- Finden oder erstellen Sie einen Satz, der den Text enthält, der als Linktext verwendet werden soll.
  Zum Beispiel:

  *Für weitere Informationen siehe den Wikipedia-Beitrag über Grüne Laubfrösche.*
- Wählen Sie das Wort oder die Wörter aus, die verlinkt werden sollen, in diesem Fall *Grüne Laubfrösche*.
- Verwenden Sie dann eine der folgenden Methoden:
  - Wählen Sie **Einfügen → Link** aus dem Menü Beitragstext (die erste Symbolleiste
    oben im Tab Inhalt).
  - Doppelklicken Sie auf den ausgewählten Text, um ein kleines Popup-Menü zu öffnen,
    das ein Link-Symbol zum Auswählen enthält.

Beide Methoden öffnen ein Dialogfeld *Link einfügen/bearbeiten*, das wie folgt ausgefüllt wird:

- Im Feld *URL* fügen Sie den aus der Ziel-URL-Leiste kopierten Link ein.
- Das Feld *Anzuzeigender Text* sollte den Text enthalten, den Sie vor dem Öffnen des Dialogs ausgewählt haben. Falls nicht, wird jeder hier eingegebene Text in den Beitrag eingefügt, daher sollte er sinnvoll im Kontext sein. Hinweis: Vermeiden Sie *Hier klicken* oder *Mehr lesen*.
- Das Feld *Titel* erstellt ein Link-Attribut Titel, dessen Verwendung durch Browser jedoch inkonsistent und kontrovers für Barrierefreiheitszwecke ist. Im Zweifelsfall leer lassen.
- Das Feld *Rel* bietet eine Reihe von Optionen. Bei Unsicherheit lassen Sie es auf *Keine* eingestellt. Eine Liste der Optionen finden Sie im *mdn web docs* Beitrag zu [HTML-Attribut: rel](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel).
- Das Feld *Link öffnen in...* bietet eine einfache Wahl zwischen *Aktuelles Fenster* und *Neues Fenster*. Die Browsereinstellungen steuern, ob dies in einem neuen separaten Fenster oder in einem neuen Tab resultiert.
- Speichern Sie den Beitrag und probieren Sie ihn mit der Vorschau-Schaltfläche in der Symbolleiste aus.

## Link-Überprüfung

In der Seitenansicht der Seite überprüfen, ob der Link gut aussieht und ordnungsgemäß funktioniert. 
Probieren Sie es auch mit einem Screenreader aus!

## Einen Link entfernen

Es gibt mehrere Möglichkeiten, einen Link zu entfernen. Methode 1:
- Klicken Sie auf den Link.
- Wählen Sie das Auslassungszeichen-Symbol (...) um das erweiterte Menü des Editors zu öffnen.
- Wählen Sie das *Link entfernen*-Symbol.
- Speichern. Der Text bleibt, aber der Link ist verschwunden.

Methode 2:
- Doppelklicken Sie auf den Link.
- Wählen Sie das Link-Symbol im kleinen Popup-Fenster.
- Löschen Sie im Dialogfenster "Link einfügen/bearbeiten" den Inhalt des URL-Feldes.
- Speichern. Der Text bleibt, aber der Link ist verschwunden.

Methode 3:
- Löschen Sie den Text, der den Link enthält. Der Link und der Text sind beide verschwunden.

Methode 4:
- Wählen Sie den Link aus.
- Wählen Sie die TinyMCE Bearbeiten / Link-Schaltfläche.
- Löschen Sie im Dialogfenster "Link einfügen/bearbeiten" den Inhalt des URL-Feldes.
- Speichern. Der Text bleibt, aber der Link ist verschwunden.

## Einen Link ändern

Verwenden Sie eine der oben beschriebenen Methoden, um den Dialog "Link einfügen/bearbeiten" zu öffnen, und fügen Sie eine neue Link-URL ein. Denken Sie daran: Es ist immer am besten, die URL aus der Adressleiste eines Browserfensters oder -tabs zu kopieren, das die Zielseite anzeigt, und diese in das URL-Feld des Formulars "Link einfügen/bearbeiten" einzufügen.

*Übersetzt von openai.com*

