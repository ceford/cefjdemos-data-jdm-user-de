<!--
{
  "source": "https://docs.joomla.org/J4.x:Read_More_Links",
  "title": "Beitrag: Bearbeiten - Mehr lesen ",
  "description": "", 
  "author": ""
}
-->

## Blog- und hervorgehobene Beitragslayouts

Diese Layouts zeigen normalerweise den Beitragstitel und einen Textausschnitt als Kostprobe für den vollständigen Beitrag. Der Benutzer kann wählen, den kompletten Beitrag entweder durch Auswahl eines Titellinks oder durch Auswahl einer "Weiterlesen"-Schaltfläche zu sehen. Jedes dieser Elemente kann im Formular "Beiträge: Optionen" deaktiviert oder aktiviert werden.

## Beiträge: Optionen

Um die entsprechenden Beitragsoptionen festzulegen:

- Wählen Sie **Inhalt → Beiträge** aus dem Administratormenü.
- Wählen Sie die **Optionen**-Schaltfläche in der Symbolleiste.
- Setzen Sie **Verlinkte Titel** auf **Ja**, um Titel als Links zu verwenden. Oder setzen Sie es auf **Nein**, um sich nur auf die "Weiterlesen"-Schaltfläche zu verlassen.
- Stellen Sie den **"Weiterlesen"-Link** auf **Anzeigen**, um eine "Weiterlesen"-Schaltfläche zu verwenden. Oder auf **Ausblenden**, um sich nur auf den Titellink zu verlassen.
- Setzen Sie **"Weiterlesen" mit Titel** auf **Anzeigen**. Oder setzen Sie auf **Ausblenden**, um "Weiterlesen" ohne Titel anzuzeigen.
- Stellen Sie **Weiterlesen-Limit (Zeichen)** auf eine geeignete Zahl ein (der Standardwert ist 100). Dies ist die Anzahl der Zeichen, die in der „Weiterlesen“-Schaltfläche nach den Worten `Weiterlesen:` angezeigt werden.
- Speichern Sie und prüfen Sie das Ergebnis in der Seitenansicht.

Sie können mit diesen Einstellungen experimentieren, um eine geeignete Kombination zu finden.

## Beiträge: Bearbeiten

Für einzelne Beiträge können Sie den Text für Weiterlesen: ändern. Zum Beispiel könnten Sie ihn auf `Weiterlesen:` oder `Mehr:` verkürzen:

- Wählen Sie **Inhalt → Beiträge** im Administrator-Menü.
- Wählen Sie den Beitrag aus, den Sie bearbeiten möchten.
- Wählen Sie die **Optionen**-Registerkarte.
- Scrollen Sie zum Feld **Weiterlesen-Text** und geben Sie Ihren neuen Text ein.
- Speichern Sie und überprüfen Sie das Ergebnis in Ihrer Seitenansicht.

## Sprachüberschreibung

Wenn Sie die standardmäßige Formulierung der Schaltfläche Weiterlesen ändern möchten, gehen Sie wie folgt vor:

- Wählen Sie **System → Verwaltungspanel → Sprachüberschreibungen**.
- Wählen Sie **Englisch (Vereinigtes Königreich) - Webseite** für die Liste `Sprache und Client auswählen`.
- Wählen Sie die Schaltfläche **Neu**.
- Geben Sie im Formular Sprachen: Überschreibung bearbeiten **Read more** im Suchtextfeld und den Wert im Suche-nach-Feld ein.
- Wählen Sie **Suchen**
- Oh je! Es stellt sich heraus, dass **Read more** an vielen verschiedenen Stellen mit geringfügigen Unterschieden verwendet wird.
- Wählen Sie den Eintrag, der JGLOBAL_READ_MORE_TITLE mit Read more: %s als Wert angibt. Er wird in den Abschnitt Neue Überschreibung erstellen des Formulars kopiert.
- Ändern Sie die Formulierung des Textes, aber **achten Sie darauf, den %s-Teil beizubehalten**, da dies der Platzhalter für den Titel ist.
- Speichern Sie und überprüfen Sie Ihre Seitenansicht. Alle Weiterlesen-Schaltflächen sollten die überschriebene Formulierung haben, **außer** bei Beiträgen, wo die Formulierung im Beitrag selbst festgelegt wurde.

Einige der anderen Stellen, an denen Weiterlesen verwendet wird, befinden sich in Modulen und Newsfeeds. Möglicherweise möchten Sie einige oder alle von ihnen ändern!

*Übersetzt von openai.com*

