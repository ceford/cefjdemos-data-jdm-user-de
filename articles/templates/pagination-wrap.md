<!--
{
    "source": "https://jdocmanual.org/jdocmanual?article=user/templates/pagination-wrap",
    "title": "Umbruch der Seitennavigation",
    "description": "Lernen Sie eine einfache Methode kennen, um die Seitennavigationsliste auf schmalen Bildschirmen umzubrechen.",
    "author": ""
}
-->

In Joomla können Listen von Beiträgen, Benutzern und anderen Elementen sehr lang sein, daher werden sie standardmäßig in Gruppen von jeweils 20 Elementen angezeigt. 

## Die normale Seitennavigationsleiste

Um zwischen den Gruppen zu navigieren, befindet sich unterhalb der Liste der Elemente eine Seitennavigationsleiste, über die der Benutzer die nächste Gruppe von Elementen auswählen kann, wie in dieser Abbildung dargestellt:

![die normale Seitennavigationsleiste für Listen](../../../en/images/templates/pagination-wrap/01-pagination-wide-screen.png)

## Paginierung auf schmalen Bildschirmen

Die Paginierungsleiste funktioniert auf breiten Bildschirmen gut. Auf schmalen Bildschirmen kann die Paginierungsleiste jedoch breiter als der Bildschirm sein. Dadurch entsteht die Notwendigkeit, nach rechts zu scrollen, um andere Elemente auf der Seite zu finden, beispielsweise Menü-Hamburger.

![die Paginierungsleiste auf einem schmalen Bildschirm](../../../en/images/templates/pagination-wrap/02-pagination-narrow-screen.png)

In der obigen Abbildung sind alle Elemente im grauen Bereich rechts zunächst *außerhalb des Bildschirms* und werden wahrscheinlich übersehen. Der Benutzer muss nach rechts scrollen, um sie zu sehen. In diesem Fall sind die außerhalb des Bildschirms liegenden Elemente das Toolbar-Symbol oben rechts und das Menü-Symbol unten rechts.## Fehlerbehebung mit einer Template-Überschreibung

Diese Fehlerbehebung fügt dem Code, der die Paginierungsleiste generiert, eine *flex-wrap*-Klasse hinzu.

- Gehen Sie im Backend zu System > Administrator-Templates > Atum-Details und Dateien
- Wählen Sie optional html > layouts aus, um zu sehen, was dort vorhanden ist
- Wählen Sie den Tab **Überschreibungen erstellen**
- Wählen Sie im Feld „Layouts“ **joomla** und anschließend **pagination** aus
- Wählen Sie im Tab „Editor“ html > layouts > joomla > pagination > **links.php** aus
- Suchen Sie nach Zeile 70 mit `<ul class="pagination ms-auto me-0">`
- Fügen Sie `flex-wrap` zur Liste der Klassen hinzu: `<ul class="pagination ms-auto me-0 flex-wrap">`
- **Speichern & Schließen**
- Optional: Sie können /html/layouts/joomla/pagination/link.php und /html/layouts/joomla/pagination/links.php löschen

Sehen Sie sich das Ergebnis sowohl auf breiten als auch auf schmalen Bildschirmen an. Auf dem schmalen Bildschirm werden das Toolbar-Symbol und das Menüsymbol nun innerhalb der normalen Bildschirmbreite angezeigt:

![die geänderte Paginierungsleiste auf einem schmalen Bildschirm](../../../en/images/templates/pagination-wrap/02-modified-pagination-narrow-screen.png)

Für das Website-Template befolgen Sie diese Anweisungen, erstellen Sie jedoch eine Überschreibung im Cassiopeia-Template.

*Übersetzt von openai.com*