<!--
{
  "source": "https://docs.joomla.org/Smart_Search_content_change_test_plan",
  "title": "Smart Search Testplan ",
  "description": "", 
  "author": ""
}
-->

Das Folgende ist ein grober Testplan, der (hauptsächlich) die Aktualisierung des Smart Search-Index abdeckt, wenn verschiedene Arten von Inhaltsaktualisierungen auftreten.

Smart Search muss für jeden der unterstützten Kerninhaltstypen getestet werden. Diese sind:

- Beiträge
- Kategorien
- Kontakte
- Newsfeeds
- Weblinks

Für jeden der oben genannten Inhaltstypen müssen wir Folgendes testen:

## Textänderungen

Das Ändern verschiedener Textfelder innerhalb eines Inhaltsobjekts sollte die Suchbegriffe im Index ändern (mit einer bemerkenswerten Ausnahme, die unten beschrieben wird). Es ist nicht nötig, alle Textfelder für einen bestimmten Inhaltstyp zu testen, da es, wenn es für eins funktioniert, für alle funktioniert. Wählen Sie also einfach eins für jeden Inhaltstyp aus. Die folgenden Textfelder werden für die Kernkomponenten indiziert:

- Beiträge
  - Titel
  - Alias
  - Beitragstext
  - Metadatenbeschreibung
  - Metadatenschlüsselwörter
  - Metadatenautor
  - Autor
  - Erstellt von Alias
- Kategorien
  - Titel
  - Alias
  - Beschreibung
  - Link ??? (nicht sicher, ob es so ein Feld gibt)
  - Metadatenbeschreibung
  - Metadatenschlüsselwörter
  - Metadatenautor
  - Autor
- Kontakte
  - Name
  - Alias
  - Verknüpfter Benutzername
  - Weitere Informationen
  - Position (wenn in den Optionen aktiviert)
  - Adresse (wenn in den Optionen aktiviert)
  - Stadt (wenn in den Optionen aktiviert)
  - Region (wenn in den Optionen aktiviert)
  - Land (wenn in den Optionen aktiviert)
  - PLZ (wenn in den Optionen aktiviert)
  - Telefon (wenn in den Optionen aktiviert)
  - Fax (wenn in den Optionen aktiviert)
  - E-Mail (wenn in den Optionen aktiviert)
  - Mobil (wenn in den Optionen aktiviert)
  - Webseite (wenn in den Optionen aktiviert)
- Newsfeeds
  - Titel
  - Alias
  - Link
  - Metadatenbeschreibung
  - Metadatenschlüsselwörter
  - Metadatenautor
  - Autor
  - Erstellt von Alias
- Weblinks
  - Titel
  - Alias
  - URL
  - Beschreibung
  - Metadatenbeschreibung
  - Metadatenschlüsselwörter
  - Metadatenautor
  - Autor
  - Erstellt von Alias

Zum Testen fügen Sie einfach eine zufällige Zeichenfolge, wie z. B. "xyz", in einen Haufen regulärer Text ein, und zwar möglichst am Anfang, und versuchen Sie dann, diesen Begriff im Frontend zu suchen.

- Ihre zufällige Zeichenfolge sollte während der Eingabe in der Autovervollständigungsliste erscheinen.
- Ihre zufällige Zeichenfolge sollte 3-mal in der Autovervollständigungsliste erscheinen.
  - Allein
  - Zusammen mit dem nächsten Wort danach
  - Zusammen mit den nächsten 2 Wörtern danach
- Das Inhaltsobjekt, das Ihre zufällige Zeichenfolge enthält, sollte in der Liste der Suchergebnisse erscheinen.
- Ihre zufällige Zeichenfolge sollte in den Suchergebnissen hervorgehoben sein, vorausgesetzt, Sie haben sie nahe dem Anfang des Textes eingegeben (da der Text in den Suchergebnissen abgeschnitten ist).

Entfernen Sie Ihre zufällige Zeichenfolge aus dem Text: Dies sollte die 3 Suchbegriffe/-phrasen aus dem Index entfernen. Die Suche nach einem der 3 Suchbegriffe sollte keine Suchergebnisse liefern.

Löschen Sie das Inhaltsobjekt: Dadurch werden alle im Inhaltsobjekt verwendeten Suchbegriffe/-phrasen aus dem Index entfernt, außer wenn diese Suchbegriffe/-phrasen noch in anderen Inhaltsobjekten verwendet werden.<sup>[\[1\]](#cite_note-1)</sup>

Das gelöschte Inhaltsobjekt sollte in keiner Suchergebnisliste erscheinen.

## Statusänderungen von Content-Beiträgen

Finde einen Content-Beitrag des erforderlichen Typs mit der Smart-Suche. Führe dann diese Tests durch:

- Lege den Beitrag in den Papierkorb und wiederhole die Suche. Der Beitrag sollte nicht mehr in den Suchergebnissen erscheinen.
- Veröffentliche den Beitrag erneut und wiederhole die Suche. Der Beitrag sollte wieder in den Suchergebnissen erscheinen.
- Widerrufe die Veröffentlichung des Beitrags und wiederhole die Suche. Der Beitrag sollte nicht mehr in den Suchergebnissen erscheinen.
- Archiviere den Beitrag und wiederhole die Suche. Der Beitrag sollte wieder in den Suchergebnissen erscheinen.

## Änderungen der Inhaltskarte (Taxonomie)

Obwohl Änderungen an der Kategorie ein Sonderfall von Änderungen der Inhaltskarte sind, müssen wir auch Änderungen an nicht-kategorischen Inhaltszweigen testen, da Kategorieänderungen einige unterschiedliche Codebereiche betreffen. Dies sind die nicht-kategorischen Felder, die in den Kernkomponenten Inhaltskarten unterliegen:

- Beiträge
  - Autor
  - Kategorie
  - Sprache
- Kontakte
  - Kategorie
  - Land
  - Sprache
  - Region
- Nachrichten-Feeds
  - Kategorie
  - Sprache
- Weblinks
  - Kategorie
  - Sprache

Wählen Sie also einen der oben genannten Punkte aus (wenn einer funktioniert, funktionieren alle für diesen Inhaltstyp), der für den Inhaltstyp geeignet ist, und überprüfen Sie folgendes:

- Eine Änderung des Feldes führt dazu, dass das Element in einer Suche mit dem relevanten Dropdown-Menü (in der erweiterten Suche) für das geänderte Feld erscheint. <sup>[\[2\]](#cite_note-2)</sup>
- Das Inhaltselement erscheint nicht mehr in einer Suche, wenn Sie den alten Wert des Feldes verwenden.

Löschen Sie das Inhaltselement und überprüfen Sie, dass es nicht mehr in den Suchergebnissen mit dem relevanten Dropdown-Filter erscheint. Beachten Sie, dass **nicht** erwartet wird, dass ein ungenutzter Knoten aus dem relevanten Filter-Dropdown entfernt wird. <sup>[\[3\]](#cite_note-3)</sup>

## Kategorie Statusänderungen

Das Ändern des Status der Kategorie, zu der ein Element gehört, sollte den Index für dieses Element aktualisieren. Darüber hinaus sollte das Ändern des Status einer übergeordneten Kategorie der Kategorie, zu der ein Element gehört, ebenfalls den Index für dieses Element aktualisieren. Um dies zu testen, finden oder erstellen Sie ein Element mit der folgenden Struktur:

    Kategorie A enthält Kategorie A.1, die ein Inhaltselement enthält

Ändern Sie den Status von Kategorie A.1 und testen Sie wie folgt:

- Verschieben Sie Kategorie A.1 in den Papierkorb und wiederholen Sie die Suche. Das Element sollte nicht mehr in den Suchergebnissen erscheinen.
- Veröffentlichen Sie Kategorie A.1 erneut und wiederholen Sie die Suche. Das Element sollte wieder in den Suchergebnissen erscheinen.
- Entfernen Sie die Veröffentlichung von Kategorie A.1 und wiederholen Sie die Suche. Das Element sollte nicht mehr in den Suchergebnissen erscheinen.
- Archivieren Sie Kategorie A.1 und wiederholen Sie die Suche. Das Element sollte wieder in den Suchergebnissen erscheinen.

Stellen Sie Kategorie A.1 wieder her und ändern Sie dann den Status von Kategorie A und testen Sie wie folgt:

- Verschieben Sie Kategorie A in den Papierkorb und wiederholen Sie die Suche. Das Element sollte nicht mehr in den Suchergebnissen erscheinen.
- Veröffentlichen Sie Kategorie A erneut und wiederholen Sie die Suche. Das Element sollte wieder in den Suchergebnissen erscheinen.
- Entfernen Sie die Veröffentlichung von Kategorie A und wiederholen Sie die Suche. Das Element sollte nicht mehr in den Suchergebnissen erscheinen.
- Archivieren Sie Kategorie A und wiederholen Sie die Suche. Das Element sollte wieder in den Suchergebnissen erscheinen.

## Änderungen des Zugriffslevels von Inhalten

Ändern Sie das Zugriffslevel eines Inhaltsbeitrags auf ein Level, das ein Frontend-Benutzer nicht sehen können sollte.

- Überprüfen Sie, dass der Beitrags nicht in Suchergebnislisten erscheint.

Stellen Sie das Zugriffslevel auf ein Level zurück, das ein Frontend-Benutzer sehen können sollte.

- Überprüfen Sie, dass der Beitrags jetzt in Suchergebnislisten erscheint.

Beachten Sie, dass Suchbegriffe innerhalb des Inhaltsbeitrags weiterhin in der Autovervollständigungsliste erscheinen, selbst wenn der Benutzer keinen Zugriff auf den Beitrags selbst hat. Dies ist das erwartete Verhalten, obwohl es etwas ist, das wir möglicherweise untersuchen sollten. <sup>[\[4\]](#cite_note-4)</sup>

## Änderungen der Zugriffsberechtigungen von Kategorien

Änderungen der Zugriffsberechtigung der Kategorie, zu der ein Beitrag gehört, sollten den Index für diesen Beitrag aktualisieren. Darüber hinaus sollten Änderungen der Zugriffsberechtigung einer übergeordneten Kategorie der Kategorie, zu der ein Beitrag gehört, ebenfalls den Index für diesen Beitrag aktualisieren. Um dies zu testen, finden oder erstellen Sie einen Beitrag mit der folgenden Struktur:

    Kategorie A, die Kategorie A.1 enthält, die einen Inhaltsbeitrag enthält

Führen Sie die folgenden Tests durch:

- Ändern Sie die Zugriffsberechtigung von Kategorie A.1 so, dass ein Front-End-Benutzer sie nicht sehen kann.
  Überprüfen Sie, dass der Inhaltsbeitrag nicht in den Suchergebnislisten erscheint.
- Ändern Sie die Zugriffsberechtigung von Kategorie A.1 zurück zu etwas, das ein Front-End-Benutzer sehen können sollte.
  Überprüfen Sie, dass der Inhaltsbeitrag jetzt in den Suchergebnislisten erscheint.
- Ändern Sie die Zugriffsberechtigung von Kategorie A so, dass ein Front-End-Benutzer sie nicht sehen kann.
  Überprüfen Sie, dass der Inhaltsbeitrag nicht in den Suchergebnislisten erscheint.
- Ändern Sie die Zugriffsberechtigung von Kategorie A zurück zu etwas, das ein Front-End-Benutzer sehen können sollte.
  Überprüfen Sie, dass der Inhaltsbeitrag jetzt in den Suchergebnislisten erscheint.

## Änderungen des Zustands der Smart Search

Im Bildschirm Administrator → Komponenten → Smart Search → Inhaltskarten ist es möglich, den Veröffentlichungs-/Unveröffentlichungszustand von Inhaltskartenästen und -knoten zu ändern. Die folgenden Tests sollten durchgeführt werden:

- Einen Inhaltskartenast (z. B. Autor) unveröffentlichen.
  Überprüfen Sie, dass das Filter-Dropdown für diesen Ast in der erweiterten Suche nicht mehr sichtbar ist.
- Einen Inhaltskartenknoten (innerhalb eines veröffentlichten Astes) unveröffentlichen. Zum Beispiel "Tiere" innerhalb des "Kategorie"-Astes.
  Überprüfen Sie, dass der Knoten im Filter-Dropdown für den Ast in der erweiterten Suche nicht aufgeführt ist.

Im Bildschirm Administrator → Komponenten → Smart Search → Indexierte Inhalte führen Sie den folgenden Test durch:

- Einen Inhaltselement unveröffentlichen.
  Überprüfen Sie, dass das Inhaltselement nicht mehr in den Suchergebnissen erscheint.

Im Bildschirm Administrator → Erweiterungen → Plug-in-Manager führen Sie den folgenden Test durch:

- Setzen Sie den Filter „Typ auswählen“ auf „finder“ oder „smart search“.
- Wählen Sie eines der Inhaltsarten-Plug-ins aus und veröffentlichen Sie es nicht.
  Alle Daten für diesen Inhaltstyp sollten aus dem Index entfernt werden.

Hinweis: Wenn Sie das Plug-in erneut veröffentlichen, wird es die Daten nicht zurück in den Index hinzufügen. Dies ist das erwartete Verhalten. Sie müssen den Indexierer erneut ausführen, um die Daten zurückzubekommen.

*Übersetzt von openai.com*

