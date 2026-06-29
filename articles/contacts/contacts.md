<!--
{
  "source": "https://docs.joomla.org/contacts.md",
  "title": "Kontakte",
  "description": "", 
  "author": ""
}
-->

## Einführung

Ein Kontakt ist eine Sammlung von persönlichen Informationen über eine Person. Sie möchten solche Informationen möglicherweise auf Ihrer Website entweder für die öffentliche oder private Anzeige bereitstellen. Zum Beispiel möchten Sie vielleicht wichtige Mitglieder Ihrer Organisation oder Gemeinschaft auflisten. Die Joomla! Kontakt-Komponente ist für diesen Zweck entworfen. Sie ermöglicht es Ihnen, Personen und deren persönliche Informationen auf Ihrer Website aufzulisten, nicht notwendigerweise registrierte Benutzer. Sie können auch jedem, oder nur registrierten Benutzern, erlauben, E-Mails an diese Personen zu senden.

Ein Beispiel für die Nutzung persönlicher Daten finden Sie auf der Wikipedia-Seite über die Parlamentsausschüsse des Vereinigten Königreichs. Dort sehen Sie Listen von Ausschüssen mit Popup-Informationen zu einzelnen Vorsitzenden. Wenn Sie einem Link zu einem Ausschuss folgen, sehen Sie eine Liste von Mitgliedern mit ausgewählten Informationen zu jeder Person. Um etwas Ähnliches in Joomla zu machen, würden Sie Kategorien und Unterkategorien für jeden Ausschuss einrichten. So zum Beispiel:

```
House of Commons
- Wirtschaft
- Kultur
- ...
House of Lords
- Kommunikation
- Verfassung
- ...
```
Jedes Ausschussmitglied hat zusätzliche Informationen, die nicht in den Standarddaten enthalten sind - politische Zugehörigkeit wie Konservative, Labour oder SNP, und Wahlkreis, das Gebiet des Landes, das sie vertreten. Diese Elemente können mit benutzerdefinierten Feldern erfasst werden.

Bei der Erfassung und Anzeige persönlicher Informationen ist Vorsicht geboten. Einzelpersonen können sehr empfindlich darauf reagieren, dass Informationen online verfügbar gemacht werden.

## Kontaktdaten

Kontakte werden über die Kontaktliste erstellt. Wählen Sie die Schaltfläche `Neu` in der Werkzeugleiste, um einen neuen Eintrag hinzuzufügen. Es gibt auch ein **Benutzer - Kontakt-Ersteller**-Plugin, das automatisch einen Kontakt erstellt, wenn ein neuer Benutzer registriert wird.

Im **Kontakte: Bearbeiten**-Formular geben Sie alle verfügbaren Daten zum Kontakt ein.

![Daten-Eingabebildschirm](../../../en/images/contacts/contacts/01-contact-data-entry.png)

**Hinweise:**

Im Screenshot wurde die **Position** als *Vorsitzender* eingetragen, was im Kontext einer Kategorieliste von Ausschussmitgliedern sinnvoll war, aber im Kontext einer Liste lesenswerter Kontakte, die aus allen Vorsitzenden aller Ausschüsse besteht, keinen Sinn ergibt. Dies muss spezifischer sein: *Vorsitzender des Ausschusses für Kultur, Medien und Sport*.

In die Felder **Erstes...**, **Zweites...** und **Drittes Sortierfeld** müssen Begriffe hinzugefügt werden, um eine Sortierung nach einer vom Benutzer definierten Reihenfolge zu ermöglichen, z. B. einer konventionellen Reihenfolge Nachname-Vorname. Dies wird später in diesem Beitrag behandelt.

Der **Sonstige Informationen**-Tab enthält ein Textbearbeitungsfeld mit einer kurzen persönlichen Stellungnahme.

Der **Extra**-Tab enthält die benutzerdefinierten Felder *Partei* und *Wahlkreis*.

Der **Formular**-Tab enthält Einstellungen für das E-Mail-Kontaktformular. Wenn keine E-Mail-Adresse eingegeben wird, wird dieses Feld nicht angezeigt.

## Kontaktanzeige

Die Kontaktkomponente bietet vier Menüeinträge zum Anzeigen von Kontaktdaten:

* Einzelner Kontakt
* Hervorgehobene Kontakte
* Kontakte in einer Kategorie auflisten
* Alle Kontakte in einer Kategoriestammstruktur auflisten

Es ist eine gute Idee, jeden Menütyp auszuprobieren, um zu sehen, wie die Ausgabe aussieht. Einige Beispiele:

### Alle Kategorien in einer Kontaktkategoriestammstruktur auflisten

In diesem Fall besteht die Kategoriestammstruktur aus einer übergeordneten Kategorie und zwei Unterkategorien:
```
House of Commons
- Wirtschaftsausschuss
- Kulturausschuss
```
![alle Kategorien in einer Kategoriestammstruktur](../../../en/images/contacts/contacts/02-contact-all-committees.png)

Die zweite Zeile jeder Eintragung stammt aus der Kategoriebeschreibung.

Wenn Sie einen der Ausschuss-Links auswählen, könnte die Ausschussseite so aussehen:

![Kontakte in einer Kategorie](../../../en/images/contacts/contacts/03-contact-culture-committee.png)

Das Layout entspricht nicht ganz den Erwartungen. Es wäre gut gewesen, ein
Vorschaubild jeder Person einzufügen und die Details besser zu gestalten. Das
kann mit einer Template-Überschreibung gemacht werden (später).

### Kontakte in einer Kategorie auflisten

Für den Wirtschaftsausschuss gibt es einen Menüeintrag "Kontakte in einer Kategorie auflisten". Dadurch wird ein anderes Layout verwendet:

![Kontaktkategorieliste](../../../en/images/contacts/contacts/04-contact-category-list.png)

Besser, aber immer noch nicht ganz richtig! Eine Designanpassung war notwendig, um den
Bildstil zu reduzieren. Auch hier könnte eine Template-Überschreibung nützlich sein.

### Hervorgehobene Kontakte

Für dieses Beispiel wurden die Vorsitzenden aller Ausschüsse als hervorgehoben markiert.

![Hervorgehobene Kontakte](../../../en/images/contacts/contacts/05-contact-featured.png)

## Sortierreihenfolge

Die Reihenfolge, in der Kontakte erscheinen, kann in den Optionen der Kontaktkomponente oder in einem Menüpunkt festgelegt werden. Letzterer überschreibt den ersteren, wenn er gesetzt ist. Die verfügbaren Einstellungen sind wie folgt:
* **Name** Der Name des Kontakts. Dies ist möglicherweise nicht für die alphabetische Sortierung geeignet.
* **Sortiername** Dies sind die drei *Sortierfeld*-Felder im zuvor erwähnten Kontakt-Datenformular.
* **Reihenfolge** Dies ist die Reihenfolge, in der Kontakte in der Kontaktliste erscheinen.
* **Reihenfolge der vorgestellten Kontakte** Vorgestellte Kontakte erscheinen vor anderen Kontakten, aber ansonsten werden Kontakte in Listenreihenfolge angezeigt.

