<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=performance&filename=page-analysis.md",
  "title": "Seitenanalyse ",
  "description": "", 
  "author": ""
}
-->

## Lighthouse

> Lighthouse ist ein Open-Source, automatisiertes Tool zur Verbesserung der Qualität von Webseiten. Sie können es auf jede Webseite anwenden, sei es eine öffentliche oder eine, die Authentifizierung erfordert. Es führt Audits in den Bereichen Leistung, Zugänglichkeit, Progressive Web Apps, SEO und mehr durch.

Es ist als Add-On-Tool für Google Chrome und Firefox verfügbar und kann über die Befehlszeile ausgeführt werden. Dies ist nützlich für Tests in einer lokalen Entwicklungsumgebung.

Mehr Informationen finden Sie auf der Chrome für Entwickler: Lighthouse Webseite.

Sie können das Tool online über PageSpeed Insights auf dieser Seite nutzen.

Der folgende Screenshot zeigt den ersten Teil des PageSpeed Insights-Berichts:

![PageSpeed Insights-Bericht](../../../en/images/performance/page-analysis/01-performance-pagespeed-insights.png)

## Leistungsverbesserungen

Der zweite Teil des Berichts schlägt Methoden zur Verbesserung der Leistung vor:

* **Render-blockierende Ressourcen eliminieren** - Potenzielle Einsparung von 540 ms.
Ehrlich gesagt, ist das zu viel Arbeit für zu wenig Belohnung.
* **Textkomprimierung aktivieren** - Potenzielle Einsparung von 11 KiB. In der globalen
Konfiguration im Server-Panel die GZip-Seitenkomprimierung auf *Ja* setzen. Das lässt
kleine JavaScript- und CSS-Dateien übrig, die noch minimiert und komprimiert werden müssen.
* **Unbenutztes CSS reduzieren** - Potenzielle Einsparung von 62 KiB. Die Übeltäter sind
template.min.css und joomla-fontawesome.min.css, aber das würde bedeuten, dass das CSS für jede Seite
auf der Website maßgeschneidert werden muss, was zu fehleranfällig ist und zu wenig Belohnung bietet.
* **Statische Assets mit einer effizienten Cache-Richtlinie bereitstellen** - 21 Ressourcen gefunden.
Referenzen sind bereitgestellt, einschließlich Joomla-spezifischer Referenzen.

Die allgemeine Botschaft ist, dass einige Vorschläge es wert sind, behoben zu werden, und andere nicht.

## Bericht über mobile vs. Desktop-Nutzung

Der Desktop-Bericht unterscheidet sich normalerweise vom Mobile-Bericht. In diesem Fall wurden einige zusätzliche Probleme identifiziert:

* **Bilder richtig dimensionieren** - Potenzielles Einsparpotenzial von 48 KiB. Das Bild-Tag ist tatsächlich mit webp-Bildern bei 768 und 1200 Pixeln Breite optimiert. Es scheint, dass etwas dazwischen erforderlich ist.

## Zugänglichkeit

* **Links haben keinen erkennbaren Namen** Dies bezieht sich auf die Pfeile nach links und rechts am unteren Rand der Seite, die vorwärts oder rückwärts navigieren. Der Text wurde ausgelassen, um Übersetzungsprobleme zu vermeiden. Noch einmal darüber nachdenken!
* **Touch-Ziele haben nicht ausreichend Größe oder Abstand** Dies bezieht sich auf die Größe der Menüpunkte in den linken und rechten Spalten. Sie benötigen mehr vertikalen Raum – eine CSS-Anpassung ist erforderlich.

## Beste Praktiken und SEO

Obwohl sowohl für mobile als auch für Desktop-Versionen 100 Punkte erzielt wurden, müssen sie nach jeder Designänderung erneut überprüft werden.

## Zusammenfassung

Alle Probleme auf dieser Website sind behoben, mit Ausnahme der Zerstückelung der CSS-Dateien und der Minimierung der kleinen Komponenten-Javascript- und CSS-Dateien.
*Übersetzt von openai.com*

