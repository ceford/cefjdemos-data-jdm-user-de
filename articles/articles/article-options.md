<!--
{
  "source": "https://docs.joomla.org/J6.x:_Article_Options",
  "title": "Beitrag: Bearbeiten - Optionen",
  "description": "", 
  "author": ""
}
-->

## Einführung

Das Wort *Optionen* ist in Joomla! mehrdeutig. Es wird manchmal synonym mit *Parameter* verwendet, und die meisten Komponentenlistenansichten haben eine *Optionen*-Schaltfläche in der Toolbar. Diese führt zu einer Optionsseite, auf der Parameter für die gesamte Komponente festgelegt werden. Darüber hinaus verfügen viele Bearbeitungsformulare für Komponentenobjekte über einen Tab mit der Bezeichnung *Optionen*, um Parameter für dieses einzelne Element festzulegen.

Dieser Beitrag handelt von dem *Optionen*-Tab im Formular *Beitrag: Bearbeiten*. Hier werden Parameter festgelegt, die das gesamte Erscheinungsbild des bearbeiteten Beitrags beeinflussen. Die Optionen für Beiträge im Allgemeinen werden in einem separaten Beitrag behandelt.

## Screenshot

Der *Optionen*-Tab des Formulars *Beitrag: Bearbeiten* enthält eine Reihe von Panels, meistens mit der Auswahl *Global verwenden (Ausblenden oder Anzeigen)*, *Ausblenden* oder *Anzeigen*. Der folgende Teilausschnitt zeigt das allgemeine Layout.

![Beitrag Bearbeitungsoptionen Tab](../../../en/images/articles/article-options/01-articles-edit-options-tab.png)

## Layout-Panel

Ein Beitrag oder ein Teil davon kann als einzelne Seite oder in einem Kategoriebereich-Layout erscheinen, das durch einen Menüpunkt gesteuert wird. In einem Blog-Menüpunkt haben die meisten Layout-Felder die Optionen *Global verwenden*, *Ja/Nein* oder *Anzeigen/Verbergen* und *Beitragseinstellungen verwenden*. Die Optionen in diesem Panel haben keine Wirkung in Blog-Layouts, es sei denn, die Option *Beitragseinstellungen verwenden* ist im Menüpunkt ausgewählt.

Andernfalls beeinflussen diese Optionen das Erscheinungsbild des Einzelbeitrags des zu bearbeitenden Beitrags.

- **Layout** In einer Standardinstallation werden die ersten beiden Optionen angeboten:
  - **---Aus den globalen Optionen--- / Global verwenden** Dies bezieht sich auf die *Beiträge: Optionen*-Einstellung, die über die Schaltfläche *Optionen* in der Symbolleiste der *Beiträge*-Listenansicht verfügbar ist. Der Wert *Layout wählen* ist auf *Standard* eingestellt.
  - **---Aus der Komponente--- / Standard** Dies bezieht sich auf die Einstellung in den *Beiträge: Optionen* Einstellungen. In einer Standardinstallation entspricht dies effektiv der Option *Global verwenden*. Wenn jedoch eine Überschreibung existiert, die als default.php benannt ist, wird diese Überschreibung für das Layout verwendet.
  - **---Aus der Cassiopeia-Vorlage--- / überschreibungsname** Wenn eine Vorlagenüberschreibung mit einem anderen Namen als *Standard* erstellt wurde, erscheint sie hier und kann als alternatives Layout ausgewählt werden.
- **Titel** Es ist üblich, den Titel eines Beitrags anzuzeigen, aber es kann Umstände geben, unter denen dies nicht angebracht ist. Wählen Sie *Verbergen*, um den Beitragstitel nicht auf der Seitenanzeige zu zeigen.
- **Verlinkte Titel** Das Standardverhalten ist, einen Beitragstitel zu einem Link zum Beitrag zu machen, wo er in Blog- oder Listenlayouts erscheint. Diese Einstellung wird durch den Menüpunkt gesteuert. Sie kann auf *Global verwenden (Ja)*, *Beitragseinstellungen verwenden*, *Nein* oder *Ja* gesetzt werden. Wenn der Menüpunkt auf *Beitragseinstellungen verwenden* gesetzt ist, wird der Wert *Verlinkte Titel* im Beitrag verwendet. Andernfalls hat diese Einstellung keine Wirkung. Wenn der Titel nicht verlinkt ist, können Sie einen *Weiterlesen*-Link verwenden, um auf den Beitrag von einem Blog- oder Listenlayout zuzugreifen.
- **Tags** Zeigen oder verbergen Sie Tags auf der Einzelbeitragsseite.
- **Intro-Text** Zeigen oder verbergen Sie den Intro-Text auf der Einzelbeitragsseite. Es gibt einige Umstände, in denen Sie möglicherweise völlig unterschiedlichen Intro-Text für Blog-Layouts wünschen, der im vollständigen Beitragstext weggelassen wird.
- **Position der Beitragsinfo** Dies bezieht sich auf den Informationsblock über einen Beitrag, der mit *Details* überschrieben ist und Informationen wie *Autor*, *Kategorie*, *Veröffentlicht* und *Aufrufe* enthält. Der Standard ist, dies oberhalb des Beitragstextes zu haben. Stellen Sie auf Unten, um dies unter den Beitragstext in einer Einzelbeitragsansicht zu verschieben. Wenn auf *Teilen* eingestellt, wird der *Aufrufe*-Punkt unter den Beitragstext verschoben.
- **Beitragsinfo-Titel** Zeige oder verberge das Wort *Details* über der Liste der Beitragsinformationen in der Einzelbeitragsansicht.

## Kategoriefeld

Das Feld in diesem Panel funktioniert wie erwartet. In Blog-Ansichten haben die Menüeintrag-Einstellungen Vorrang, es sei denn, sie sind auf *Einstellungen für Beiträge verwenden* gesetzt.

- **Kategorie** Zeigt den Kategorienamen an oder versteckt ihn.
- **Kategorie verlinken** Verlinken (Ja oder Nein) des Kategorienamens. Wenn auf *Ja* gesetzt, wird der Kategoriename mit seinem Kategorieblog verlinkt.
- **Übergeordnete Kategorie** Wenn auf Ja gesetzt, erscheint die übergeordnete Kategorie als separates Element über der Kategorie in den Beitragsinformationen *Details* im Einzelbeitragslayout.
- **Übergeordnete Kategorie verlinken** Wenn auf Ja gesetzt, wird der Name der übergeordneten Kategorie mit seiner Kategorieblog-Seite verlinkt.

## Assoziationen Panel

Dieses Panel ist nur auf mehrsprachigen Websites präsent.

- **Assoziationen** Wenn auf "Anzeigen" gesetzt, wird im Beitragsinhalt ein
  zusätzlicher Eintrag platziert, der mit *Auch verfügbar:* beginnt, gefolgt von Flaggen, die die in anderen Sprachen verfügbaren Versionen dieses Beitrags repräsentieren.
- **Bild-Flaggen verwenden** Dieser Punkt erscheint, wenn *Assoziationen* auf *Anzeigen* gesetzt ist. 
  Die Standardeinstellung *Ja* zeigt Schaltflächen als Länderflaggen an. Die Alternative 
  *Nein* zeigt Schaltflächen als Sprachcodes an, zum Beispiel *en-GB*. 

## Autorenpanel

- **Autor** Zeigt oder verbirgt den Namen des Autors bei der Einzelbeitragsansicht. Die Zeile in den Beitragsinformationen lautet *Geschrieben von: Autorenname*.
- **Verlinkung zur Kontaktseite des Autors** Ja oder nein, um den Autorenname mit der Kontaktseite des Autors zu verlinken, sofern eine existiert.

## Datumspanel

Joomla-Beiträge speichern mehrere Daten. Wenn sie angezeigt werden, erscheinen die folgenden Informationen jeweils als separate Zeilen in den Beitragsinformationen für einen einzelnen Beitrag. Denken Sie daran, dass Blog-Layouts die Einstellungen aus dem Menüpunkt verwenden, es sei denn, sie sind auf *Verwende Beitragseinstellungen* gesetzt. Das Datenformat ist der 03. November 2024, kann aber geändert werden ...[ToDo]

- **Erstellungsdatum** Standardmäßig verborgen.
- **Änderungsdatum** Standardmäßig verborgen.
- **Veröffentlichungsdatum** Standardmäßig angezeigt.

## Optionsmenü

- **Navigation** Für einen Beitrag, der Teil einer Reihe von Beiträgen in einer Kategorie ist, befinden sich unterhalb des Beitragstextes die Schaltflächen *Vorheriger* und *Nächster*, um zur vorherigen oder nächsten Seite zu navigieren. Wenn auf *Verbergen* gesetzt, werden die Navigationsschaltflächen auf einzelnen Beitragsseiten nicht angezeigt.
- **Aufrufe** Die Gesamtanzahl der Male, die der Beitrag als einzelner Beitrag angezeigt wurde, wird in der Beitragsinformationsliste angezeigt.
- **Nicht autorisierte Links** Dies betrifft Blog-Layouts, sodass der relevante Kategorieblog-Menüpunkt seinen Wert *Optionen: Nicht autorisierte Links* auf *Ja* oder *Beitragseinstellungen verwenden* setzen muss. Wenn dann der Beitrag *Zugang* auf *Registriert* gesetzt ist und die Einstellung im Beitrag nicht *Nein* lautet, wird der *Einleitungstext* des Beitrags im Blog-Layout angezeigt, aber das Label der Weiterlesen-Schaltfläche wird *Registrieren, um mehr zu lesen...* sein. Das Klicken auf den Weiterlesen-Link erfordert eine Anmeldung, um den vollständigen Beitrag zu sehen.
- **Position der Links** Dies bezieht sich auf die Positionierung der Links im Tab Bilder und Links, Links A, B und C. Die Standardposition ist oberhalb des Beitragstextes. Diese Option ermöglicht es, die Links unterhalb des Beitragstextes oder gar nicht anzuzeigen.
- **Weiterlesen-Text** Der normale Text, *Weiterlesen:* gefolgt vom Beitragstitel, wird aus den Sprachschlüssel-/Zeichenfolgenwerten übernommen. Eine benutzerdefinierte Überschreibung nur für diesen Beitrag kann hier eingegeben werden, zum Beispiel *Vollständigen Beitrag anzeigen:* gefolgt vom Beitragstitel.
- **Browser-Seitentitel** Der Seitentitel ist normalerweise der Beitragstitel. Wenn das unpraktisch ist, kann hier ein alternativer Seitentitel für die Verwendung auf der einzelnen Beitragsseite eingegeben werden. Er erscheint in der Browsertab und im `<head>...</head>` Bereich der Seite. Er wird von Suchmaschinen verwendet.

*Übersetzt von openai.com*

