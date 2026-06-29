<!--
{
  "source": "https://docs.joomla.org/Smart_Search_on_large_sites",
  "title": "Intelligente Suche auf großen Seiten",
  "description": "", 
  "author": ""
}
-->

## Website-Indexierung

Smart Search funktioniert, indem ein unabhängiger Index von Suchbegriffen in einer Reihe von Datenbanktabellen erstellt und verwaltet wird. Das Problem bei großen Websites besteht darin, dass der Indexierungsprozess in Bezug auf CPU, Speicher und Festplattennutzung recht ressourcenintensiv sein kann. Selbst nach der anfänglichen Erstellung des Index können inkrementelle Aktualisierungen ebenfalls ressourcenintensiv sein. Die gute Nachricht ist, dass das Abfragen des Indexes eine relativ schnelle und ressourcenschonende Operation ist.

Smart Search ist für die Mehrheit der Joomla-Seiten geeignet. Allerdings stellt die Suche besondere Herausforderungen für große Seiten dar. Es sollte daran erinnert werden, dass Smart Search eine reine PHP-Implementierung einer Suchmaschine ist und besonders große Seiten möglicherweise besser mit einer eigenständigen Suchmaschine wie Solr bedient werden.

Um die Smart Search auf einer großen Website zu verwenden, müssen Sie wahrscheinlich einige der Konfigurationseinstellungen anpassen. Im Folgenden finden Sie einige allgemeine Ratschläge, worauf Sie achten sollten und was Sie ausprobieren sollten zu optimieren.

## Verwenden Sie immer den CLI-Indexer

Da der anfängliche Indexierungsprozess lange dauern kann, ist es am besten, den Indexer über die Befehlszeile auszuführen, um Probleme durch ablaufende Browsersitzungen zu vermeiden. Der CLI-Indexer wird nicht ablaufen, unabhängig davon, wie lange er zur Fertigstellung benötigt, und er kann leicht abgebrochen werden, wenn Probleme auftreten. Darüber hinaus sind Fehlermeldungen mit dem CLI-Indexer sichtbar, während sie beim Ausführen aus der Administratoransicht möglicherweise verborgen sind.

Um die CLI zu verwenden, öffnen Sie ein Terminal, wechseln Sie in den cli-Ordner im Stammverzeichnis Ihrer Website und geben Sie den folgenden Befehl ein:

```
php joomla.php finder:index
```

## Stapelverarbeitung

Der Indexer teilt den Indexierungsauftrag in Batches von Inhaltselementen auf. Standardmäßig ist die Batch-Größe auf 50 festgelegt, was bedeutet, dass pro Batch bis zu 50 Inhaltselemente indexiert werden. Eine Erhöhung der Batch-Größe kann den Indexierungsprozess potenziell beschleunigen, aber es wird mehr Speicher und möglicherweise mehr temporärer Festplattenspeicher verwendet.

## Probleme mit nicht genügend Speicher

Wenn dem Indexer der Speicher ausgeht, versuchen Sie, die folgenden Anpassungen nacheinander vorzunehmen, bis das Problem behoben ist.

1. Verringern Sie die Batchgröße. Wenn Sie besonders große Inhalte haben, kann der Indexer selbst bei einem einzigen Inhaltselement keinen Speicherplatz mehr haben. Versuchen Sie, sie zunächst auf 5 zu reduzieren, und wenn Sie weiterhin Speicherplatzprobleme haben, reduzieren Sie sie auf 1.
2. Wenn Sie in der Lage sind, dem Indexer mehr Speicher zuzuweisen, tun Sie dies. Sie können den dem Kommandozeilen-Indexer zugewiesenen Speicher mit einem zusätzlichen Parameter in der Kommandozeile erhöhen. Um beispielsweise das Speicherlimit auf 256 MB zu erhöhen, verwenden Sie den folgenden Befehl, wobei Sie die *256M* durch so viel Speicher ersetzen, wie Sie sicher einem Prozess auf Ihrem System zuweisen können.<br>
    ```php
    php -d memory_limit=256M joomla.php finder:index
    ```
3. Versuchen Sie zu identifizieren, welche Inhaltselemente dazu führen, dass der Indexer keinen Speicherplatz mehr hat. Wenn es nicht offensichtlich ist, könnten Sie versuchen, alle Smart Search-Plugins außer einem zu deaktivieren. Das Ausführen des Indexers mit jeweils nur einem aktivierten Plugin sollte aufzeigen, welche Inhaltsart(en) das Problem verursachen. Als letzten Ausweg sollten Sie in Erwägung ziehen, ein paar außergewöhnlich große Inhaltselemente in separate Elemente aufzuteilen. Wenn das Problem bei einem benutzerdefinierten Inhaltstyp liegt, schauen Sie sich den Plugin-Code an und überlegen Sie, ob Sie weniger von den verfügbaren Inhalten pro Element indizieren.

## Probleme mit unzureichendem Speicherplatz

Die Smart Search-Indextabellen können schnell wachsen! Die Tabelle *__finder_links_termsX* enthält eine Zeile pro Begriff/Phrase pro Inhaltselement, und ein einzelner Joomla-Beitrag mit 1000 Wörtern wird typischerweise dazu führen, dass ungefähr 3000 Zeilen diesen Tabellen hinzugefügt werden. Ein zweiter Beitrag ähnlicher Größe wird eine ähnliche Anzahl von Zeilen hinzufügen, selbst wenn beide Beiträge dieselben Wörter enthalten. Eine Website mit Zehntausenden von Beiträgen, von denen einige Tausende von Wörtern enthalten könnten, wird wahrscheinlich mit dieser Zuordnungstabelle enden, die Millionen von Zeilen enthält. Es ist nicht ungewöhnlich, dass die Indextabellen unter solchen Umständen mehrere Gigabyte an Speicherplatz belegen.

Der Index hat eine Option, um zwischen Suchpräzision und Indexgröße zu entscheiden. Wenn Sie "Nach Phrasen suchen" in den globalen Optionen der Komponente aktiviert haben, wird Ihr Index größer, aber er ermöglicht auch präzisere Suchergebnisse. Wenn diese Option deaktiviert ist, bedeutet dies einen deutlich kleineren Index, aber auch keine Möglichkeit, nach ganzen Phrasen zu suchen.

## Notizen

1. Derzeit gibt es keine Gleichzeitigkeitssperre, die verhindert, dass mehr als ein Prozess den Indexer gleichzeitig ausführt. Dies wird fast sicher zu einem beschädigten Index führen. Sogar das Speichern von Änderungen an einem Inhaltsobjekt, während ein vollständiger Index durchgeführt wird, könnte potenziell den Index beschädigen.

*Übersetzt von openai.com*

