<!--
{
  "source": "https://docs.joomla.org/J3.x:Plugin_Joomla_Update_Notification",
  "title": "Joomla! Update-Benachrichtigung  ",
  "description": "", 
  "author": ""
}
-->

## Symbol und Aufgabe

Es gibt zwei Plugins mit ähnlichen Namen:

* **Schnell-Symbol - Joomla! Update-Benachrichtigung**
* **Aufgabe - Joomla! Update-Benachrichtigung**

Das erste Plugin prüft auf Joomla-Updates und benachrichtigt Sie, wenn Sie die Start-Dashboard-Seite besuchen. Es hat einen Parameter: die Gruppe dieses Plugins (dieser Wert wird mit dem Gruppenwert in Schnell-Symbolmodulen verglichen, um Symbole einzufügen).

Das zweite Plugin überprüft regelmäßig die Verfügbarkeit neuer Joomla!-Versionen. Wenn eine gefunden wird, löst es eine Aufgabe aus, um eine Update-Erinnerung an Super-User per E-Mail zu senden. Die E-Mail kann über *System → Mail-Templates* angepasst werden.

Die von den Joomla! Update-Benachrichtigungssystem-Plugins gesendeten E-Mails sollen helfen, die Software auf dem neuesten Stand zu halten, was zur Sicherheit der Website beiträgt. Updates sollten so schnell wie möglich nach ihrer Veröffentlichung installiert werden.

## Plugin-Status

Die beiden separaten Plugins können jeweils Aktiviert oder Deaktiviert sein.

- Bei **Schnelles Symbol ... Deaktiviert** bleibt das Home-Dashboard *Joomla überprüfen ...* Symbol inaktiv, obwohl Sie es auswählen können, um zur Joomla-Update-Seite zu gelangen.
- Bei **Aufgabe ... Deaktiviert:** wird die Aufgabe zum Senden einer E-Mail nicht ausgelöst.

## Aufgabenparameter

Gehen Sie vom Administrator-Menü zu **System / Geplante Aufgaben** und wählen Sie den Punkt **Update-Benachrichtigung** aus der Liste der *Geplanten Aufgaben* aus. Dort gibt es mehrere Registerkarten mit Parametern und Informationen, die Sie bei Bedarf anzeigen und ändern können.

### Häufigkeit der Benachrichtigungs-E-Mails

Die Häufigkeit der Aufgabenausführung ist standardmäßig auf 24 Stunden eingestellt. Das bedeutet, dass die Joomla-Website alle 24 Stunden auf Updates für den Kern und alle Erweiterungen, Plugins, Module und Templates überprüft. Ein Wert von 0 würde bei jedem Zugriff auf die Seite eine Update-E-Mail senden. 0 ist nur für Tests vorgesehen!

Beachten Sie, dass die Aufgabe durch Aktivitäten auf der Website ausgelöst wird. Wenn Sie der einzige Benutzer sind, wird sie bei Ihrem nächsten Besuch ausgelöst, wenn seit dem letzten Besuch mehr als 24 Stunden vergangen sind.

### Super-User-E-Mails

Die Benachrichtigungs-E-Mail wird nur an Benutzer gesendet, die das Super-User-Privileg haben. Dieses Feld ermöglicht es Ihnen, auszuwählen, welche Super-User die E-Mail-Benachrichtigungen erhalten sollen.

- Wenn dieses Feld leer bleibt, erhalten alle Super-User der Seite die Update-Benachrichtigungs-E-Mail.
- Um einzuschränken, welche Super-User die Update-Benachrichtigung erhalten, geben Sie hier die E-Mail-Adressen der Super-User ein. Wenn es mehrere Super-User-E-Mail-Adressen gibt, verwenden Sie ein Komma, um sie zu trennen.

### E-Mail-Sprache

Die Benachrichtigung kann in jeder Sprache gesendet werden, die Sie auf Ihrer Website verwenden.

- **Auto (Standard)** sendet die Update-Benachrichtigungs-E-Mail in der Standardsprache der Website.
- Die Auswahl einer anderen Sprache als Auto (Standard) führt dazu, dass die Update-Benachrichtigungs-E-Mails in dieser bestimmten Sprache gesendet werden.

## Tipps

- Um die Update-E-Mail-Benachrichtigungen von Joomla! zu deaktivieren, schalten Sie einfach das Plugin aus.
- Der Betreff und der Text der E-Mail können über die Liste **System / E-Mail-Vorlagen** bearbeitet werden. Wählen Sie den Eintrag **Joomla: Update-Benachrichtigung** aus. Auf einer mehrsprachigen Website wird dieser in der aktuell ausgewählten Sprache angezeigt.
  - **Betreff** Beachten Sie, dass die Platzhalter {SITENAME} – {URL} beim Senden der Nachricht ersetzt werden.
  - **Text** Auch dort gibt es weitere Platzhalter!

*Übersetzt von openai.com*

