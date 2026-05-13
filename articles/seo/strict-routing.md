<!--
{
  "source": "https://docs.joomla.org/J5.x:Improving_SEO_with_Strict_Routing_and_SEF_URLs",
  "title": "SEO Strikte Weiterleitung ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die Option "Striktes Routing", die in Joomla 5.2 eingeführt wurde, verbessert die SEO-Leistung der Plattform, indem sie strengere Routing-Regeln mithilfe eines Schalters im *System - SEF* Plugin ermöglicht. Sie hilft, doppelte Inhalte zu eliminieren, indem sie konsistentere URLs erzwingt und Duplikate mit einer 301-Weiterleitung zur korrekten URL umleitet.

![system sef plugin settings](../../../en/images/seo/strict-routing/01-seo-system-sef-plugin.png)

### Erzwingen von Suffixen

Zurzeit erlaubt Joomla den Zugriff auf URLs mit oder ohne Suffix, wenn diese Option in den *Global Configuration*-Einstellungen aktiviert ist.

Die **Erzwinge ein Suffix durch Umleitung**-Option im *System - SEF*-Plugin erzwingt ein konsistentes Suffix-Verhalten. Wenn sie aktiviert ist, leitet sie GET-Anfragen zu einer URL mit einem Suffix um, falls dieses fehlt. Sie wird auch URLs mit einem Abfrageformat-Parameter zur saubereren URL umleiten, indem sie das Suffix durch den Format-Parameter ersetzt, wo nötig.

Diese Funktion soll in Joomla 6.0 zum Standardverhalten werden, wobei die Option zum Aktivieren oder Deaktivieren entfernt wird und diese Funktionalität in das Kern-Routingsystem integriert wird. Im Moment ermöglicht diese Option den Benutzern, das Verhalten auf Live-Systemen zu testen und es zu deaktivieren, falls während der Übergangsphase von Joomla 5.1 zu 6.0 unvorhergesehene Probleme auftreten.

## So greifen Sie darauf zu

Um striktes Routing für SEO zu aktivieren:

1. Wählen Sie den **Plugins**-Eintrag im *Home Dashboard*.
2. Suchen und öffnen Sie das **System - SEF** Plugin.
3. Stellen Sie **Strict Routing** auf *Ja* ein, um eine strengere URL-Verarbeitung zu aktivieren.
4. Stellen Sie **Erzwingen eines Suffixes durch Weiterleitung** je nach Ihrer Präferenz für das Erzwingen von URL-Suffixen auf Ja oder Nein ein.

Sobald aktiviert, leitet Joomla automatisch doppelte URLs mit einem 301-Redirect zur korrekten weiter, was die SEO verbessert, indem Inhalte unter einer einzigen, maßgeblichen URL konsolidiert werden.

## Zusätzliche Anmerkungen

Diese Funktion ist als vorbereitender Schritt für weitere SEO-Verbesserungen konzipiert und wird automatisch für neue Joomla 5.2-Installationen aktiviert. Sie legt den Grundstein für zukünftige Verbesserungen des Joomla-Routingsystems.  
*Übersetzt von openai.com*

