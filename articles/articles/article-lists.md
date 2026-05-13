<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Lists",
  "title": "Beitrag: Bearbeiten - Listen ",
  "description": "", 
  "author": ""
}
-->

## Listentypen

HTML hat drei Typen von Listen:

- Ungeordnete Listen werden oft mit einer Einrückung und einem Aufzählungszeichen dargestellt, wie diese Liste.
- Geordnete Listen sind ähnlich, werden jedoch mit Zahlen markiert.
- Definitionslisten bestehen aus Titeln und Definitionen.

Die Aufzählungszeichen und Zahlen werden vom Browser aus einer Auswahl von Stilen angewendet. Der Benutzer darf keine Aufzählungs- oder Zahlentexte eingeben, da diese als Teil der Liste behandelt werden. Der TinyMCE-Editor verfügt über Symbole, um gebräuchliche Aufzählungsstile und Zahlentypen anzuwenden. Definitionslisten sind komplizierter und müssen manuell erstellt werden.

Listen können andere Listen in jeder beliebigen Ebene enthalten, obwohl stark eingerückte Listen schwer lesbar werden, daher ist es am besten, sich auf ein oder zwei Ebenen zu beschränken.

## Screenshot

Der folgende Screenshot zeigt eine ungeordnete Liste mit zwei Ebenen der Einrückung.
Er zeigt auch das vollständige Werkzeugsatz, der durch Auswählen der Ellipsenschaltfläche (...)
am Ende der ersten Reihe der Werkzeugsymbole geöffnet wird.

![Verschachtelte ungeordnete Listen](../../../en/images/articles/article-lists/01-articles-edit-lists.png)

Dieser Screenshot wird verwendet, um zu erklären, wie die Aufzählungsliste mit den
Werkzeugen *Aufzählungsliste* und *Einrückung erhöhen* oder *Einrückung verringern* erstellt wurde:

## Liststile

### Aufzählungslisten

Es gibt drei Stile:

- Ein gefüllter Kreis ist der Standard.
- Ein offener Kreis.
- Ein gefülltes Quadrat.

Der Chevron nach unten rechts vom Aufzählungslisten-Symbol öffnet ein kleines Panel,
das die Auswahl des bevorzugten Stils für ein ausgewähltes Listenelement ermöglicht:

![Werkzeuge zur Manipulation von Aufzählungslisten](../../../en/images/articles/article-lists/02-articles-edit-list-bullets.png)

Das Listensymbol funktioniert wie ein Umschalter. Befindet sich der Cursor in einem Absatz und wird eine Aufzählung ausgewählt, wird der Absatz zu einem Listenelement. Wenn die Aufzählung erneut ausgewählt wird, wird das Listenelement wieder zu einem Absatz.

Wenn zwei oder mehr Absätze ausgewählt werden und ein Listensymbol ausgewählt wird, wird jeder der Absätze zu einem Listenelement. Um eine eingerückte Liste zu erstellen, wähle das Werkzeug *Einzug erhöhen* rechts von den Listen-Werkzeugen. Standardmäßig übernimmt das eingerückte Listenelement den nächsten Listenstil.

So erstellt man die eingerückten Listen im Screenshot:

- Gib jeden der Begriffe als ein Wort-Absatz ein.
- Wähle alle Absätze aus, die in eine Aufzählungsliste umgewandelt werden sollen.
- Wähle das Symbol *Aufzählung*.
- Wähle die erste Gruppe von Begriffen aus, die eingerückt werden sollen.
- Wähle das Symbol *Einzug erhöhen*.
- Wähle die zweite Gruppe von Begriffen aus, die eingerückt werden sollen.
- Wähle das Symbol *Einzug erhöhen*.

### Nummerierte Listen

Es gibt sechs Stile:

- Zahlen: 1, 2, 3 ...
- Buchstaben: a, b, c ...
- Griechische Zeichen: &alpha;, &beta;, &gamma; ...
- Kleine römische Ziffern: i, ii, iii ...
- Große Buchstaben: A, B, C ...
- Große römische Ziffern: I, II, III ...

![Werkzeuge zur Manipulation von nummerierten Listen](../../../en/images/articles/article-lists/03-articles-edit-list-numbers.png)

Nummerierte Listen funktionieren etwas anders. Wenn ein Listenelement eingerückt wird, übernimmt es den ersten Zahlenwert und die Zahlen auf dem Rest der Liste steigen auf, sodass die Liste immer in der richtigen numerischen Reihenfolge ist.

### Gemischte Listen

Das Nummerierungssystem kann in jeder Ebene geändert werden. Du könntest zum Beispiel die erste Ebene auf numerische Werte setzen und die zweite Ebene auf Aufzählungen, griechische Zeichen oder etwas anderes.

Es ist wahrscheinlich am besten, mit Listen zu experimentieren, um zu sehen, wie sie manipuliert werden können.

## Definitionslisten

Definitionslisten bestehen aus einem *Definitions-Titel* und einer oder mehreren *Definitions-Beschreibungen*, gefolgt vom nächsten *Definitions-Titel* und seiner *Beschreibung*. Sie wären gut für ein *Glossar* oder jede Art von Satz aus Schlüssel/Wert-Paaren geeignet. Um eine Definitionsliste zu erstellen:

- Wählen Sie die Schaltfläche *Editor umschalten*, um die HTML-Beiträge-Markierung zu sehen.
- Geben Sie die Definitionslisten-Markierung ein. Hier ist ein Beispiel:
```html
<dl>
<dt>Amphibie</dt>
<dd>Wechselwarmes Wirbeltier, das Eier im Wasser legt und ein aquatisches Larvenstadium hat.</dd>
<dt>Reptil</dt>
<dd>Wechselwarmes Wirbeltier, das Eier an Land legt.</dd>
</dl>
```
Speichern Sie und sehen Sie das Ergebnis in der Vorschau an.

*Übersetzt von openai.com*

