<!--
{
  "source": "https://docs.joomla.org/Managing_404_Errors",
  "title": "Umgang mit 404-Fehlern ",
  "description": "", 
  "author": ""
}
-->

## Warum 404 Nicht Gefunden Wichtig Ist

Das häufigste Problem von Websites, die Schwierigkeiten in den Suchmaschinenplatzierungen haben, ist die Anzahl der „Nicht Gefunden“-Fehler – allgemein als *404*-Fehler bezeichnet, da dies der Statuscode ist, der zurückgegeben wird, wenn die Seite nicht gefunden werden kann.

Zunächst gibt es legitime Gründe für das Vorhandensein von 404-Fehlern – beispielsweise wenn Sie eine Seite für ein Ereignis haben, das bereits vorbei ist, oder einen Dienst, den Sie nicht mehr anbieten. In diesen Fällen wird die Seite schließlich aus dem Index der Suchmaschinen entfernt und nicht mehr mit Ihrer Website in Verbindung gebracht.

Das Problem tritt auf, wenn Sie viele 404-Fehler haben – zum Beispiel, wenn Sie eine Kategorie offline schalten, die Hunderte von Beiträgen enthielt. Aus Sicht der Suchmaschine ist dies keine großartige Erfahrung für ihre Besucher, da sie auf Ihrer Seite landen und die Informationen, die die Suchmaschine ihnen mitteilte, nicht vorhanden sind. Aus diesem Grund ist es keine gute Idee, zu viele 404-Fehler auf Ihrer Website zu haben.

## Google Search Central

Der erste Schritt besteht darin, herauszufinden, wie viele es gibt – was mit Googles [Search Central](https://developers.google.com/search) gemacht werden kann. Dies ist eine kostenlose Sammlung von Tools, die es Ihnen ermöglicht, Ihre Website zu analysieren und Probleme, Fehler und Schwierigkeiten schnell zu erkennen. Es wird empfohlen, dass Sie jede von Ihnen verwaltete Website bei Search Central registrieren, um im Falle von Problemen benachrichtigt zu werden.

Wenn Sie Search Central besuchen, gibt es einen Abschnitt, der Ihnen URL-Fehler in der Suchauflistung zeigt – hier wird Ihnen eine Liste der 404-Fehler angezeigt, die Google auf Ihrer Seite gefunden hat, sowie ein Diagramm, das Ihnen zeigt, wie sich dies im Laufe der Zeit verändert hat. Wenn das Diagramm anfängt zu steigen, sollten Sie nachforschen, warum Seiten, die sich zuvor auf Ihrer Website befanden, jetzt nicht mehr gefunden werden können.

Wenn es ein temporäres Problem auf Ihrer Website gab, können Sie Fehler als behoben markieren.

![webmaster tools](../../../en/images/performance/managing-404-errors/01-404-discovery.png)

## Probleme beheben

Die Entdeckung ist nur ein Teil des Prozesses. Sobald Sie die problematischen URLs entdeckt haben, unternehmen Sie etwas dagegen (falls es behoben werden muss!), indem Sie entweder die Seite zu einer anderen auf der Website umleiten, die ursprüngliche Seite wiederherstellen oder untersuchen, was den 404-Fehler verursacht hat.

Wenn Sie eine Seite umleiten müssen, können Sie das System - Redirect-Plugin verwenden, um fehlende Seiten zu sammeln, und die System / Redirects-Komponente, um fehlende Seiten auf bestehende Seiten umzuleiten.

## Überwachung von Problemen

Wenn du deinen 404-Traffic überwachen möchtest, ist der beste Weg, dies in Analytics zu tun, indem du beobachtest, was passiert, wenn ein 404-Fehler auftritt. In den meisten Fällen ändert sich der Seitentitel auf 404 – also können wir ein benutzerdefiniertes Segment erstellen, das den Traffic mit einem Titel von 404 filtert und dir mitteilt, was die Einstiegsseite ist. Dies sollte es dir ermöglichen, deine 404-Fehler zu überwachen und proaktiv zu verwalten, um sicherzustellen, dass deine Website-Besucher nicht auf toten Links landen.

![Analytics warnt 404-Traffic](../../../en/images/performance/managing-404-errors/02-404-analytics-alerts.png)

![Analytics warnt vor Publikumsübersicht](../../../en/images/performance/managing-404-errors/03-404-analytics-alerts-2.png)

Google bietet in Analytics auch die Möglichkeit, Warnungen einzurichten. Warnungen ermöglichen es dir, per E-Mail benachrichtigt zu werden, wenn bestimmte Ereignisse eintreten. In diesem Fall können wir eine Warnung einrichten, um benachrichtigt zu werden, wenn es in einer Woche zu einem Anstieg von mehr als 5% bei der Anzahl der 404-Fehler kommt – was bedeuten könnte, dass wir ein Problem mit der Webseite haben, das untersucht werden muss.

Dies ist eine großartige Möglichkeit, die Dinge im Auge zu behalten, auch wenn du dich nicht in dein Dashboard eingeloggt hast!

![Email-Benachrichtigung von Analytics](../../../en/images/performance/managing-404-errors/04-404-analytics-alerts-email.png)

## Überwachung von Fehlern mit einem Dashboard

Es gibt auch ein Dashboard, das Sie installieren können, das *Datenintegritäts-Dashboard* genannt wird. Es zeigt Ihnen Informationen über 404-Fehler sowie einige andere Metriken, die für Sie von Interesse sein könnten. Suchen Sie einfach in der Google Analytics Gallery nach *Datenintegritäts-Dashboard* und wählen Sie das Profil aus, unter dem Sie es installieren möchten.

![Datenintegrität](../../../en/images/performance/managing-404-errors/05-404-data-integrity.png)

*Übersetzt von openai.com*

