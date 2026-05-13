<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=news&filename=news-display.md",
  "title": "Nachrichtenanzeige ",
  "description": "", 
  "author": ""
}
-->

## Das Feed Display Modul

Es gibt ein Kernmodul *Feed Display*, das verfügbar ist, um Nachrichten von anderen Seiten anzuzeigen. Der folgende Screenshot zeigt das Dateneingabeformular mit der URL des Joomla-Ankündigungen-News-Feeds. Beachten Sie, dass die Wortanzahl auf 100 festgelegt ist. Andernfalls kann die Länge einer Ankündigung für ein Seitenleistenmodul übermäßig sein.

![Feed Display Modul Dateneingabe](../../../en/images/news-feeds/news-display/01-news-joomla-news-form.png)

Das Ergebnis kann unschön sein, kann aber mit einigen benutzerdefinierten Stilen in user.css verbessert werden:

![Feed Display Modul Dateneingabe](../../../en/images/news-feeds/news-display/02-news-joomla-news-display.png)

## Feed-Anzeigeseiten

Als Alternative zur Darstellung von Nachrichten in einem Modul können Sie ein Menüelement erstellen, um einen Nachrichten-Feed auf einer Webseite anzuzeigen. Vom Administrator-Menü aus:

* Wählen Sie **Komponenten / NewsFeeds / Feeds**. Sie könnten zuerst eine Kategorie für Nachrichten erstellen.
* Wählen Sie die **Neu**-Schaltfläche in der *Werkzeugleiste*.
* Füllen Sie das Formular **News Feeds: Bearbeiten** aus:
    - Der **Link** ist der RSS-Link, der von einer externen Quelle kopiert wurde.
    - Die **Beschreibung** ist optional.
    - Der Tab **Optionen** enthält Elemente zur Steuerung der Feed-*Anzeige*.
* **Speichern & Schließen**

![NewsFeed-Komponentendateneingabe](../../../en/images/news-feeds/news-display/03-news-feed-data-entry.png)

Erstellen Sie ein Menüelement ausgehend vom Administrator-Menü:

* Wählen Sie **Menüs / Hauptmenü** oder ein anderes Menü für dieses Element.
* Wählen Sie **Neu** aus der *Menüs: Artikel* Werkzeugleiste.
* Verwenden Sie im **Menüelementtyp** die **Auswählen**-Schaltfläche, um *News Feeds / Einzelner News Feed* zu finden und auszuwählen.
* Füllen Sie den Rest des Formulars entsprechend aus.
* **Speichern & Schließen**

![NewsFeed-Menüelement-Dateneingabe](../../../en/images/news-feeds/news-display/04-news-feed-menu-form.png)

Testen Sie es: Gehen Sie zum Seitennmenü und wählen Sie das Feed-Menüelement aus.

![NewsFeed-Anzeige](../../../en/images/news-feeds/news-display/05-news-feed-display.png)

Jeder Beitrag im Feed ist ein `<li>` innerhalb eines `<ul>`-Tags, daher erscheint er standardmäßig mit einem Aufzählungspunkt markiert. Dies ist nicht so offensichtlich, wenn die Beiträge lang sind. Sie können Ihre eigenen Stile in *user.css* anwenden. Folgendes sorgt dafür, dass jeder Beitrag in einem eigenen Kasten erscheint:

```
ul.com-newsfeeds-newsfeed__items {
  list-style-type: none;
  padding-left: 0;
}

ul.com-newsfeeds-newsfeed__items > li {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 2px solid navy;
}
```

Was so aussieht:

![Benutzerdefinierte NewsFeed-Anzeige](../../../en/images/news-feeds/news-display/06-news-feed-custom-display.png)

## Nachrichten-Feeds in einer Kategorie auflisten

Die Seite *Joomla! RSS-Nachrichten-Feeds* listet acht separate News-Feeds auf. Sie könnten einen Feed für einige oder alle davon erstellen und sie einer Kategorie zuweisen, zum Beispiel *Joomla Nachrichten*. Dann können Sie einen Menüpunkt erstellen, bei dem der *Menüpunkt-Typ* auf *Nachrichten-Feeds in einer Kategorie auflisten* gesetzt ist und die Kategorie auf *Joomla Nachrichten* gesetzt wird.

![Nachrichten-Feed nach Kategoriemenü-Formular](../../../en/images/news-feeds/news-display/07-news-feed-menu-category-form.png)

Probieren Sie es aus, um das Ergebnis zu sehen!
*Übersetzt von openai.com*

