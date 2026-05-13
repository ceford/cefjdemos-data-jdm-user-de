<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md",
  "title": "Barrierefreiheit Prüfer ",
  "description": "", 
  "author": ""
}
-->

## System - Joomla Accessibility Checker

Dies ist ein Kern-Plugin, das verwendet werden kann, um die Barrierefreiheit beim Erstellen von Beitragsinhalten zu überprüfen. Der folgende Screenshot zeigt einige Plugin-Einstellungen:

![Plugin-Formulareinstellungen](../../../en/images/performance/accessibility-checker/01-performance-jooa11y-plugin-form.png)

Mit der Option **Immer anzeigen** auf *Ein* erscheint das Berichtssymbol auf jeder Seite der Website. Das ist nützlich für die Entwicklung, sollte jedoch niemals auf einer Live-Website aktiviert bleiben. Stellen Sie es auf **Aus**!

Wenn die Option *Immer anzeigen* auf *Ein* gesetzt ist, hat jede Seite der Website unten rechts ein Symbol mit einer Zählung der Anzahl der Probleme. Der folgende Screenshot zeigt das Symbol, das ausgewählt ist, um ein Informationsfeld anzuzeigen. Es enthält eine Seitenübersicht, Lesbarkeitshinweise und Warnungen, die nacheinander ausgewählt werden können. Das erste Problem wurde ausgewählt.

![Barrierefreiheitsprüfung der Website](../../../en/images/performance/accessibility-checker/02-performance-jooa11y-site-display.png)

Das Formular *Beiträge: Bearbeiten* hat eine **Barrierefreiheitsprüfung**-Schaltfläche in der Symbolleiste. Es zeigt die Prüfung für einen einzelnen Beitrag in einem Popup-Fenster:

![Barrierefreiheitsprüfung im Editor](../../../en/images/performance/accessibility-checker/03-performance-jooa11y-admin-display.png)

## Problemlösungen

Der Accessibility Checker ist ein Tool zur Identifizierung von Problemen. Er behebt jedoch keine Probleme – das müssen Sie selbst tun. Der Prüfer verfügt über einige Einstellungen, die Sie je nach Bedarf ein- oder ausschalten können. Dazu gehören Kontrast, Formularbeschriftungen, Links (Erweitert) AAA, Lesbarkeit AAA, Dunkelmodus und Farbfilter mit Simulation von vier Typen fehlerhafter Farbwahrnehmung.

Weitere Informationen finden Sie in der Sa11y-Übersicht.

Zum Beispiel heißt es zur Lesbarkeit:

> Sa11y kann den Lesbarkeitsindex aus allen Absätzen und Listeninhalten schätzen. Ein guter Lesbarkeitsindex ist ein Hinweis darauf, dass Ihr Text verständlich und leicht verdaulich ist. Er basiert auf der durchschnittlichen Länge von Sätzen und Wörtern auf Ihrer Seite und verwendet eine Formel, die als Flesch-Reading-Ease-Test bekannt ist (Wikipedia). Ein "guter" Lesbarkeitswert liegt zwischen 60 und 100. Manchmal kann es schwierig sein, einen guten Lesbarkeitswert zu erreichen. Die meisten Ihrer Seiten mögen als „schwierig“ bezeichnet werden. Denken Sie daran, dass diese Funktion nur verwendet wird, um die Lesbarkeit Ihrer Inhalte zu schätzen. Sie sollte nur als Referenz und nicht als Hinweis auf Konformität verwendet werden. Sa11y berechnet die Lesbarkeit basierend auf allen Absatz- (`<p>`-Tags) und Listeninhalten (`<li>`-Tags). Ein niedriger Wert wirkt sich nicht auf den Erfolgs- oder Fehlzustand von Sa11y aus.

*Übersetzt von openai.com*

