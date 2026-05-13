<!--
{
  "source": "https://docs.joomla.org/Monitoring_Server_Health",
  "title": "Überwachung der Servergesundheit ",
  "description": "", 
  "author": ""
}
-->

Selbst wenn Sie eine fantastisch optimierte Website haben, wird sie nicht gut geladen, wenn der Server, auf dem sie gehostet wird, nicht gut funktioniert. Daher wird empfohlen, auch wenn Sie Shared Hosting nutzen, eines der vielen Systeme zu verwenden, die es Ihnen ermöglichen, die Betriebszeit und Reaktionszeit zu überwachen und Sie im Idealfall im Falle von Problemen zu benachrichtigen. [Pingdom](https://www.pingdom.com/) bietet einen kostenlosen Test an, der dies für eine Website erledigt – ideal, um Ihre Website im Auge zu behalten.

## Überwachung der Servergesundheit in Google Analytics

Sie können auch die Serverantwortzeit in Google Analytics anzeigen und im Laufe der Zeit verfolgen. In diesem Fall können wir einige signifikante Erhöhungen der Antwortzeit sehen (was bedeuten würde, dass die Seiten auf dem Server langsam laden) und auch einige signifikante Verbesserungen, die zu einer besseren Ladezeit führen würden. Wenn Sie sich das Diagramm über die Zeit ansehen, sollten Sie einige der Schwankungen mit Ereignissen in Verbindung bringen können – wie in diesem Fall den Umzug in eine schnellere Hosting-Umgebung, das Erleben eines Denial-of-Service-Angriffs, hohe Auslastung aufgrund eines Prominenten, der eine auf dem Server gehostete Seite teilt, und die Reduzierung der Auslastung, da hochfrequentierte Kunden auf ihre eigenen Hosting-Server ausgelagert werden.

![Seitengeschwindigkeit - Seitentimings](../../../en/images/performance/monitoring-server-health/01-monitoring-site-speed.png)

Es ist auch möglich, diese Daten mit einer Kartenüberlagerung anzuzeigen – die Ihnen zeigt, welche Länder Probleme mit den Ladezeiten der Seiten haben.

![Seitengeschwindigkeit - Seitentimings](../../../en/images/performance/monitoring-server-health/02-monitoring-site-speed-by-country.png)

Diese Art von Einblick kann hilfreich bei der Identifizierung von sich entwickelnden Problemen sein. Sie sollten jedoch einen Serveradministrator hinzuziehen, wenn Sie Ihre eigenen Server verwalten, der dies mit einem speziell entwickelten System wie dem Open-Source-Paket [Nagios](https://www.nagios.org/) verwalten kann.

## Dashboard zur Website-Performance

Wie bei den anderen Metriken gibt es auch ein vorgefertigtes Dashboard zur Website-Performance, das Sie in Ihr Analytics-Konto einfügen können, um alle wichtigen Informationen zu erhalten. Sie können diesen Dashboards auch Widgets hinzufügen und sie so anpassen, dass sie in dem von Ihnen bevorzugten Format angezeigt werden. Sie sind nicht in Stein gemeißelt.

![Dashboard zur Website-Performance](../../../en/images/performance/monitoring-server-health/03-performance-dashboard.png)

*Übersetzt von openai.com*

