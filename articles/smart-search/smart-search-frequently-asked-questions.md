<!--
{
  "source": "https://docs.joomla.org/Smart_Search_Frequently_Asked_Questions",
  "title": "Häufig gestellte Fragen zur intelligenten Suche   ",
  "description": "", 
  "author": ""
}
-->

## Warum sollte ich Smart Search verwenden?

Die Suchtechnologie hat sich seit der Einführung von Joomla erheblich verbessert, und dennoch hat sich die standardmäßige, einfache Suchkomponente in dieser Zeit kaum verändert. Sie ist immer noch sehr rudimentär und es fehlen ihr die Arten von Suchfunktionen, die Webnutzer mittlerweile erwarten, insbesondere angesichts der weit verbreiteten Nutzung fortschrittlicher Suchmaschinen wie Google. Smart Search ermöglicht es Ihnen, einige dieser fortschrittlicheren Suchfunktionen in Ihre Website zu integrieren.

## Warum ein Smart Search Plugin erstellen?

Im Allgemeinen, wenn Sie eine Art von Inhalt haben, die nicht von den Kernkomponenten von Joomla verarbeitet wird und Sie Ihren Website-Besuchern die Möglichkeit geben möchten, diese Inhalte zu durchsuchen, müssen Sie ein Smart Search Plugin schreiben, um dies zu unterstützen. Angenommen, Sie haben eine Komponente, die Informationen über verschiedene Tierarten speichert. Die Komponente verwaltet eine Datenbanktabelle, die Felder wie wissenschaftlicher Name, gebräuchlicher Name, Klassifikation und eine Beschreibung enthält. Dann müssen Sie ein Plugin erstellen, das dem Smart Search Indexer mitteilt, wie die Daten in dieser Tabelle indiziert werden sollen. Zusätzlich zur Indexierung einzelner Wörter und Ausdrücke können Sie das Plugin auch so konfigurieren, dass jeder Eintrag zu einer Inhaltskarte hinzugefügt wird, die in diesem Fall die
<a href="https://en.wikipedia.org/wiki/Taxonomy_(biology)"
rel="nofollow noreferrer noopener">biologischen Klassifikationen wie Reich, Stamm, Klasse, Ordnung und Familie</a> enthalten könnte. Inhaltskarten können dann verwendet werden, um Suchergebnisse zu filtern.

## Können mehrere Knoten aus den Filter-Dropdowns ausgewählt werden?

Ja, dies wird von Smart Search vollständig unterstützt. Tatsächlich können Sie jede beliebige Benutzeroberfläche für die Filter entwickeln, die Sie möchten. Werfen Sie einfach einen Blick auf den Code im Standard-Frontend-Modul und der Komponente, und Sie werden sehen, wie es gemacht werden muss.

## Ich habe eine große Webseite. Kann ich Smart Search verwenden?

Große Webseiten sind möglicherweise besser mit einer eigenständigen Suchmaschine, wie Solr, anstelle der reinen PHP-Implementierung, die in Smart Search verwendet wird, beraten. In dieser ersten Iteration der erweiterten Suche in Joomla ist es wahrscheinlich, dass Probleme im Zusammenhang mit Skalierung und Leistung auftreten werden. Es besteht auch die Möglichkeit von Race Conditions, wenn der Index bei häufigen Inhaltsänderungen aktualisiert wird. Es wird erwartet, dass diese Probleme in einer zukünftigen Version von Joomla umfassender angegangen werden.

## Warum hat die Smartsuche so viele Tabellen?

Die Smartsuche fügt einer Joomla-Installation einige neue Tabellen hinzu, darunter 16 "Zuordnungstabellen". Diese Zuordnungstabellen lösen die Viele-zu-Viele-Beziehung zwischen Suchbegriffen und den Inhaltelementen, die sie enthalten. Theoretisch könnten diese 16 Tabellen in einer einzigen Tabelle zusammengefasst werden, was bei kleinen Websites kaum Auswirkungen hätte. Bei größeren Websites hätte dies jedoch erhebliche Auswirkungen auf die Leistung, da die Zuordnungstabelle eine sehr große Anzahl von Einträgen enthalten würde und die Aktualisierung einer so großen Tabelle zeitaufwendig sein kann.

## Warum benötigt die intelligente Suche so viel Speicherplatz?

Die Verwaltung eines Suchbegriff-Indexes erfordert eine beträchtliche Menge an Speicherplatz, die umso größer wird, je mehr Begriffe die Inhalte enthalten. Da auch Phrasen indiziert werden, erfordert es umso mehr Speicherplatz, je länger die Phrasen sind. Für die intelligente Suche in Joomla 2.5 wurde die maximale Länge einer Phrase auf 3 Begriffe festgelegt, um einen vernünftigen Kompromiss zwischen Suchbenutzerfreundlichkeit und Speicherplatznutzung zu erreichen. Es ist wahrscheinlich, dass dies in einer zukünftigen Version der intelligenten Suche ein Parameter sein wird, der angepasst werden kann.

## Warum sind die Einträge in den Zuordnungstabellen nicht gleichmäßig verteilt?

Es ist vielleicht überraschend, dass die Anzahl der Einträge in jeder der Zuordnungstabellen nicht einmal annähernd gleich ist. Sicherlich würde die Leistung mit einer gleichmäßigen Verteilung verbessert werden? Tatsächlich jedoch nicht, es gibt einen Kompromiss zwischen Einfügeleistung und Suchleistung, wobei eine gleichmäßige Verteilung für erstere gut, aber für letztere schlecht ist. Dies ist ein Bereich fortlaufender Forschung, wobei die Anzahl der Tabellen und der Verteilungsalgorithmus im Lichte der Erfahrungen verändert werden können.

## Warum gibt es ein separates Smart Search Content-Plugin?

Dies ist lediglich eine Annehmlichkeit, die es einfacher macht, alle Smart Search Plugins mit einem einzigen Vorgang zu aktivieren oder zu deaktivieren. Dies wurde als wünschenswert erachtet, da Smart Search in Joomla 2.5 standardmäßig nicht aktiviert ist.

## Warum verwenden intelligente Such-Plugins separate Ereignisse wie *onFinderContentAfterSave*?

Intelligente Suche verwendet eigene Ereignisse, wie zum Beispiel onFinderContentAfterSave, anstelle des generischen Äquivalents onContentAfterSave, rein aus dem Grund, die Aktivierung oder Deaktivierung der Indexierung der intelligenten Suche zu erleichtern, indem man einfach ein einzelnes Plugin aktiviert oder deaktiviert.

## Warum ist Smart Search in Joomla 2.5 und Joomla 3.x nicht standardmäßig aktiviert?

Da Joomla 2.5 das letzte in der 1.x/2.x-Serie ist, muss es eine hohe
Rückwärtskompatibilität mit der vorherigen Veröffentlichung der Serie
beibehalten. Da Smart Search etwas völlig Neues ist und keine
Ähnlichkeit mit der regulären Suchkomponente dieser oder früherer
Versionen aufweist, wurde es als wichtig erachtet, dass Benutzer, die
von diesen früheren Versionen upgraden, nicht gezwungen werden, die
Art und Weise, wie die Suche auf ihren Seiten funktioniert, zu ändern.
Tatsächlich sollte die Aktivierung von Smart Search auf eine gut
überlegte Weise erfolgen.

## Warum gibt es keine Such-API?

Der Schwerpunkt der aktuellen Version von Smart Search lag darauf, den Code von der alten JXtended Finder-Komponente in die neueste Version von Joomla zu übertragen. Da dieser Code bereits als stabil angesehen wurde und nur ein kurzes Zeitfenster für die Portierung bestand, wurde entschieden, dass eine umfassende Neuentwicklung von Finder nicht im Rahmen der Joomla 2.5-Version möglich wäre. Folglich verwendet der Code Plugins, um Änderungen am Kern-CMS-Code zu vermeiden, anstatt eine ordnungsgemäße Such-API zu entwickeln. Für eine zukünftige Iteration von Joomla planen wir die Erstellung einer solchen API.

## Kann Smart Search Facettensuche durchführen?

Ja. Die erweiterte Suche, die auf der Suchergebnisseite verfügbar ist, und das Smart Search-Modul bieten ein Beispiel dafür, wie Sie Suchergebnisse filtern können, um eine Facettensuche zu erzeugen. Es gibt nichts, was Sie daran hindert, Ihre eigenen Varianten dieser grundlegenden Ideen zu entwickeln. Zum Beispiel könnten Sie die einfachen Dropdown-Menüs so ändern, dass sie Mehrfachauswahlen akzeptieren, oder Sie könnten die Dropdown-Menüs durch eine Reihe von Kontrollkästchen ersetzen.

## Warum werden Platzhaltersuchen nicht unterstützt?

Die alte Joomla-Suche verwendete eine sehr primitive Suchmethode, die sich auf die von der Datenbank bereitgestellte FULLTEXT-Suche stützte. Dies war sehr ineffizient, bot jedoch eine einfache Möglichkeit, mit Suchanfragen mit Platzhaltern umzugehen. Smart Search bietet eine Autovervollständigungsfunktion, die effektiv eine Platzhaltersuche von Begriffen im Index ist. Eine vollständige Platzhaltersuche wird jedoch nicht unterstützt, da das Risiko besteht, den Server zu überlasten, wenn diese Funktion missbraucht wird. In den meisten Fällen wird die Platzhaltersuche verwendet, um Variationen eines Suchbegriffs zu erfassen. Zum Beispiel, wenn man nach *jonglier\** sucht, um Verweise auf *jonglieren* sowie *Jongleur* zu erfassen. Smart Search versucht, die Notwendigkeit für Platzhaltersuchen zu vermeiden, indem stattdessen Wortstamm-Unterstützung geboten wird, bei der Wörter mit dem gleichen Stamm als gleichwertig betrachtet werden, sodass die Suche nach *Jongleur* auch Vorkommen von *jonglieren* ohne die Verwendung von Platzhaltern findet.

## Kann die intelligente Suche auf mehrsprachigen Websites verwendet werden?

Ja, aber es gibt noch einige Probleme zu lösen, insbesondere was die Unterstützung asiatischer Sprachen betrifft.

- Damit die Inhalte korrekt indiziert werden, müssen Sie sicherstellen, dass alle Inhalte gültiges UTF-8 sind.
- Die *Meinten Sie?*-Funktion verwendet die Soundex-Funktion, um phonetisch ähnliche Suchbegriffe zu finden. Allerdings funktioniert Soundex nicht gut für nicht-englische Sprachen und für viele Sprachen funktioniert es gar nicht. Wir untersuchen derzeit alternative Methoden, um diese Funktion bereitzustellen.

Wenn Sie die intelligente Suche auf einer mehrsprachigen Website verwenden und auf Probleme stoßen, melden Sie diese bitte im Tracker, damit wir die Probleme, die gelöst werden müssen, besser verstehen können.

## Werden *jXTended* Finder-Plugins mit der Smart-Suche funktionieren?

Nein. Sie müssen die Finder-Plugins aktualisieren, damit sie mit der Smart-Suche funktionieren. Die Änderungen sollten jedoch nicht schwer umzusetzen sein und führen in den meisten Fällen zu deutlich weniger Code. Wenn Sie sich die aktuellen Smart-Suche-Plugins ansehen, sollten Sie feststellen, dass das Aktualisieren eines Finder-Plugins ziemlich einfach ist.

*Übersetzt von openai.com*

