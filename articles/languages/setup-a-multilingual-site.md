<!--
{
  "source": "https://docs.joomla.org/J4.x:Setup_a_Multilingual_Site",
  "title": "Einrichtung einer mehrsprachigen Website",
  "description": "", 
  "author": ""
}
-->

## Beispieldaten

Joomla wird mit zwei Sätzen von Beispieldaten geliefert: Blog und Mehrsprachig. Es gibt einen dritten Testsatz, der jedoch nur für Benutzer der Joomla-Entwicklungsversion verfügbar ist. Wenn Sie eine vorhandene Website mit Beiträgen, Menüs und Modulen haben, wird sie im Prinzip einer Website mit installierten Blog-Beispieldaten ähneln.

Im Haupt-Dashboard weisen die Mehrsprachigen Beispieldaten darauf hin: **Stellen Sie vor dem Start sicher, dass Sie mindestens 2 installierte Sprachen mit ihren Inhalts-Sprachen haben und dass keine Beispieldaten installiert wurden**. Dies wird Sie wahrscheinlich dazu führen, eine mehrsprachige Website zu erstellen, indem Sie die erforderlichen Schritte manuell nacheinander ausführen. Das ist ein fehleranfälliger Prozess, bei dem Sie wahrscheinlich einen Fehler machen, besonders wenn Sie mehrere Sprachen verwenden. Fehler können zwar behoben werden, aber der gesamte Prozess ist etwas mühsam und kann verwirrend sein.

Sie können diesen Rat ignorieren und die Mehrsprachigen Beispieldaten verwenden, um eine mehrsprachige Website einzurichten, wenn Sie verstehen, wie Sie später einige Korrekturen an den ursprünglichen Menüs und Modulen vornehmen können.

## Anfangsseite

Eine neu installierte Joomla-Website hat ein **Hauptmenü** in der rechten Seitenleiste.
Es enthält einen einzelnen Menüpunkt namens **Home** vom Typ Hervorgehobene Beiträge.
Es gibt auch ein **Login-Formular** in der rechten Seitenleiste.

Anfänglich gibt es keine hervorgehobenen Beiträge, sodass der Hauptteil der Seite
leer ist.

## Blog-Beispieldaten

Wenn Sie Ihre eigenen Inhalte für die Website erstellt haben, sollten Sie die Blog-Beispieldaten **nicht** installieren. Dennoch ist es sinnvoll, sich diesen Abschnitt anzusehen, um einen Vergleich zu haben. Andernfalls:

- Wählen Sie **Installieren** im Abschnitt "Mehrsprachige Beispieldaten" des Home-Dashboards. Die Installationsphasen werden kurz angezeigt und dann verschwinden.
- Sie sollten bemerken, dass mehrere neue Menüs installiert werden (laden Sie die Administrationsseite neu und erweitern Sie das Menü Menüs):
  - Hauptmenü Blog.
  - Unteres Menü, das Anmelden/Abmelden-Menüpunkte enthält.
  - Spezielles Menü, das nach dem Anmelden angezeigt wird.
- Wählen Sie das **Frontend öffnen**-Symbol aus der oberen Statusleiste oder laden Sie die Seite neu, wenn sie bereits in einem separaten Tab geöffnet ist.

Sie sollten ein Layout mit Informationen zu hervorgehobenen Beiträgen erwarten:

- Oben befindet sich das neue **Hauptmenü Blog** für verschiedene Blog-Layouts und Beiträge.
- In der rechten Seitenleiste befinden sich Module für ein Anmeldeformular, ein Hauptmenü und einen Meine Blog RSS-Feed.
- Nach der Anmeldung enthält die rechte Seitenleiste ein spezielles Menü für Administratoraktionen.
- Der Menüpunkt **Startseite** im Hauptmenü führt zum Layout für hervorgehobene Beiträge.
- Der obere Menüpunkt **Blog** führt zu einem Kategorieblog-Layout, das sich etwas vom Layout der hervorgehobenen Beiträge unterscheidet.

Nehmen Sie sich ein paar Minuten Zeit, um die Menüeinträge und die Arten von Informationen, zu denen sie führen, zu erkunden.

## Installieren und Veröffentlichen von Inhalts­sprachen

Installieren Sie zuerst alle Sprachen, die Sie verwenden möchten. Wenn Sie später eine zusätzliche Sprache installieren müssen, müssen Sie die Konfigurationsschritte für diese Sprache manuell nacheinander abschließen. Das wird an anderer Stelle behandelt. Für dieses Tutorial wurden während der Joomla-Installation Französisch, Deutsch und Walisisch zur Standard­sprache Englisch der Website hinzugefügt. Um nach der Installation Sprachen hinzuzufügen:

- Wählen Sie **System **→** Sprachen installieren** aus dem Administrator-Menü.
- Wählen Sie die **Installieren**-Schaltfläche für jede Sprache, die Sie verwenden möchten.

Installierte Sprachen müssen **veröffentlicht** werden, um sie verfügbar zu machen. Aus dem Administrator-Menü:

* Wählen Sie **System / Verwaltungspanel / Inhaltssprachen**
* Veröffentlichen Sie in der Statusspalte jede der Sprachen, die Sie verwenden möchten.  

## Mehrsprachige Beispieldaten

Die Installation der mehrsprachigen Beispieldaten hat Auswirkungen, mit denen Sie später umgehen müssen:

- Menüs in der rechten Seitenleiste werden nicht veröffentlicht. Das bedeutet, dass das Hauptmenü-Modul nicht veröffentlicht wird und es keinen Link zum Layout der hervorgehobenen Beiträge geben wird. Wenn Sie andere Links im Hauptmenü hatten, werden diese ebenfalls nicht verfügbar sein.
- Das Spezialmenü wird nicht veröffentlicht. Es bot einen Link zur Erstellung eines neuen Beitrags.

Die mehrsprachigen Beispieldaten bieten die folgenden zusätzlichen Funktionen:

- Eine Beitragskategorie für jede Sprache.
- Ein Beitrag für jede Sprache konfiguriert, obwohl in Lorem ipsum Pseudo-Text.
- Ein separates Menü für jede Sprache. Dies sehen Sie in der **Administrator**→**Menüs**-Liste.
- Ein **Hauptmenü xx-YY** Menümodul in der rechten Seitenleiste der Site, wobei xx-YY ein Sprachcode wie en-GB ist.
- Der **Haupt** Menüpunkt führt jetzt zu einem Kategorie-Blog-Layout für Beiträge in der ausgewählten Sprache. Es enthält nur einen Beitrag.
- Es gibt ein **Sprachwechsler**-Modul in der rechten Seitenleiste. Es ist unbetitelt, um die Notwendigkeit eines separaten Moduls für jede Sprache mit übersetzten Titeln zu vermeiden. Die Auswahl erfolgt nach Sprachflagge. Probieren Sie es aus.

Etwas, das Sie beachten sollten: Wörter, die von Joomla bereitgestellt werden, werden übersetzt, zum Beispiel in den Breadcrumbs und im Anmeldeformular. Wörter, die von Benutzern getippt werden, müssen manuell übersetzt werden, zum Beispiel Anmeldeformular und Hauptmenü. Mehr dazu später.

## Behebung von anfänglichen Problemen

### Sprachreihenfolge

Es kann sein, dass der Sprachumschalter Sprachen in umgekehrter alphabetischer Reihenfolge anzeigt. Um die Reihenfolge zu ändern:

- Wählen Sie **System → Inhalts-Sprachen** aus dem Administrator-Menü.
- Verwenden Sie die vertikalen Ellipsensymbole, um die Sprachen in die gewünschte Reihenfolge zu ziehen.
- Laden Sie die Seite neu und sehen Sie, dass der Sprachumschalter die Sprachen jetzt in Ihrer bevorzugten Reihenfolge hat.

### Modulreihenfolge in der rechten Seitenleiste

Die Modulreihenfolge in der rechten Seitenleiste ist eine Frage des persönlichen Geschmacks. Um die Reihenfolge zu ändern:

- Wählen Sie **Inhalt → Seitenmodule** aus dem Administrator-Menü.
- Filtern Sie nach **Position → sidebar-right**.
- Wählen Sie das Bestellsymbol der Spalte aus, um die Ziehgriffe für die Anordnung (vertikale Ellipsensymbole) zu aktivieren. Das Spaltensymbol sollte ein nach oben zeigendes Chevron sein.
- Ziehen Sie die Elemente in die gewünschte Reihenfolge:
  - Sprachumschalter
  - Hauptmenü (alle Varianten - die Reihenfolge ist egal).
  - Spezialmenü
  - Anmeldeformular
  - Archivierte Beiträge
  - Syndikation

### Hervorgehobene Beiträge

Das ursprüngliche Hauptmenü ist unveröffentlicht, aber das darin enthaltene Startseiten-Menüelement kann an anderer Stelle reproduziert werden. Der praktischste Ort ist das obere Menü.

- Wählen Sie **Menüs → Hauptmenü-Blog** aus dem Administrator-Menü.
- Wählen Sie die **Neu**-Schaltfläche aus der Werkzeugleiste.
- Geben Sie einen **Titel** im Formular **Menüs: Neues Element** ein, zum Beispiel **Hervorgehoben**.
- Verwenden Sie die **Auswählen**-Schaltfläche im Feld **Menüeintragstyp**.
- Wählen Sie **Beiträge → Hervorgehobene Beiträge** aus der Liste **Menüeintragstyp**.
- Wählen Sie **Speichern** aus der Werkzeugleiste.
- Im Feld **Reihenfolge** wählen Sie **- Erste -**.
- Im Tab **Blog-Layout** stellen Sie **Einleitungsbeiträge** auf 3.
- Wählen Sie **Speichern & Schließen** aus der Werkzeugleiste.

### Zuweisung von Seitenmodulen

Das ursprüngliche Layout der hervorgehobenen Beiträge auf der Startseite wurde durch die Zuweisung ausgewählter Module, die nur auf dieser einen Seite erscheinen sollen, erstellt. Die neue hervorgehobene Seite muss für jedes dieser Module hinzugefügt werden.

- Wählen Sie **Inhalt → Seitenmodule** im Administrator-Menü.
- Finden und wählen Sie den **Bild**-Eintrag aus.
- Im Reiter **Menüzuweisung** finden und markieren Sie den **Hervorgehoben**-Eintrag im Abschnitt **Hauptmenü-Blog**.
- Wählen Sie **Speichern & Schließen** aus der Werkzeugleiste.
- Finden und wählen Sie den **Letzte Beiträge**-Eintrag aus.
- Im Reiter **Menüzuweisung** finden und markieren Sie den **Hervorgehoben**-Eintrag im Abschnitt **Hauptmenü-Blog**.
- Wählen Sie **Speichern & Schließen** aus der Werkzeugleiste.

## Seite neu laden

Wenn Sie die Seite neu laden, wird das erste Element im oberen Menü der Link „Empfohlen“ sein, der zum Layout der empfohlenen Beiträge führt. Das angrenzende Blog-Element ist ein kompakteres Kategorie-Blog-Layout. Probieren Sie den Sprachumschalter aus. Der von Joomla bereitgestellte Text, in den Breadcrumbs und im Login-Formular, ändert sich entsprechend. Außerdem enthalten die empfohlenen Beiträge jetzt einen Beitrag aus den mehrsprachigen Beispieldaten in der ausgewählten Sprache. Möglicherweise befindet er sich auf der letzten Seite.

### Hybride oder reine mehrsprachige Seite

In diesem Stadium haben Sie eine hybride Seite: Einige Inhalte sind in allen Sprachen verfügbar und einige Inhalte sind in einer bestimmten Sprache verfügbar. Wenn Sie eine reine mehrsprachige Seite wünschen, müssen Sie das Modul für das obere Hauptmenü-Blog und möglicherweise andere deaktivieren. In einigen Fällen möchten Sie möglicherweise sprachspezifische Module erstellen, zum Beispiel könnte das Login-Formular Versionen mit Titeln wie Formulaire de connexion, Login Formular und Ffurflen Mewngofnodi haben.

Was Sie als nächstes tun, liegt ganz bei Ihnen!

## Originales Hauptmenü

Ihr ursprüngliches Hauptmenü-Modul, das jetzt nicht veröffentlicht ist, könnte zusätzliche Menüpunkte enthalten haben. Sie könnten es veröffentlichen. Der Haken dabei ist, dass der Home-Punkt auf denselben Ort verweist wie jede der sprachspezifischen Menü-Startseiten, aber nur in Englisch. Dies können Sie folgendermaßen umgehen:

- Wählen Sie **Menüs** → **Hauptmenü** aus dem Administrator-Menü.
- Wählen Sie den Menüpunkt **Home**.
- Wählen Sie die Registerkarte **Verknüpfungstyp**.
- Setzen Sie **In Menü anzeigen** auf **Nein**.
- Wählen Sie **Speichern & Schließen** in der Werkzeugleiste.
- Wählen Sie **Inhalt** → **Seitenmodule** aus dem Administrator-Menü.
- Finden Sie das **Hauptmenü** und veröffentlichen Sie es, indem Sie das graue Kreuz in einen grünen Haken ändern.

Die sichtbaren Beiträge im ursprünglichen Hauptmenü sollten nun normal funktionieren. Wenn das Hauptmenü keine sichtbaren Beiträge hat, wird es nicht angezeigt.

## Eine zusätzliche Sprache hinzufügen

Nach der ersten Einrichtung einer mehrsprachigen Website, wenn Sie eine zusätzliche Sprache hinzufügen möchten, müssen Sie die Schritte manuell einzeln durchgehen:

### Schritt 1: Sprache installieren

- Wählen Sie **System** → **Installieren** → **Sprachen** aus dem Administrator-Menü.
- Suchen Sie die benötigte Sprache in der Liste **Erweiterungen: Sprachen**.
- Wählen Sie die Schaltfläche **Installieren**.
- Es wird eine Nachricht angezeigt: **Installation des Sprachpakets war erfolgreich.**

In dieser Beispielsequenz ist die zusätzliche Sprache Spanisch.

### Schritt 2: Veröffentlichen und Anordnen

- Wählen Sie **System** → **Verwalten** → **Inhaltssprachen** aus dem Administrator-Menü.
- Aktivieren Sie die neu installierte Sprache: Wählen Sie die Status-Schaltfläche, um das graue Kreuz in ein grünes Häkchen zu verwandeln.
- Verwenden Sie die vertikalen Ellipsen-Symbole, um die Sprachen in die gewünschte Reihenfolge zu ziehen.

### Schritt 3: Ein Menü erstellen

- Wählen Sie **Menüs** → **Verwalten** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche **Neu** in der Symbolleiste.
- Geben Sie einen passenden Menü-Titel und einen eindeutigen Namen ein, Beispiele: Hauptmenü (es-ES) und hauptmenü-es-es.
- Geben Sie eine Beschreibung ein, Beispiel: Das Hauptmenü der Website in der Sprache Spanisch (es-ES).

### Schritt 4: Menümodul hinzufügen

- Wählen Sie **Menüs** → **Verwalten** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche **Modul für dieses Menü hinzufügen** für das neu erstellte Menü.
- Geben Sie einen passenden Titel ein, Beispiel: Hauptmenü es-ES
- Wählen Sie eine Position: Sidebar-right
- Wählen Sie eine Sprache: Spanisch (es-ES)
- Wählen Sie **Speichern**.
- Ordnen Sie das Modul: Wählen Sie aus der Bestellliste das Element aus, nach dem dieses neue Element erscheinen soll.
- Wählen Sie **Speichern & Schließen**.

### Schritt 5: Eine Kategorie hinzufügen

- Wählen Sie **Inhalt** → **Kategorien** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche **Neu** in der Symbolleiste.
- Geben Sie einen passenden Titel ein, Beispiel: Categoría (es-es)
- Wählen Sie die richtige Sprache: Spanisch (es-ES)
- Wählen Sie die Registerkarte **Verknüpfungen**.
- Wählen Sie für jede Sprache eine Kategorie aus. Es gibt in jedem Fall nur eine Auswahlmöglichkeit.
- Wählen Sie **Speichern & Schließen**.

### Schritt 6: Ein Menüelement hinzufügen

- Wählen Sie **Menüs** → **Hauptmenü (es-ES)**, das neu erstellte Menü.
- Wählen Sie die Schaltfläche **Neu** in der Symbolleiste.
- Geben Sie einen passenden Titel ein, Beispiel: Página de inicio
- Verwenden Sie die Schaltfläche Auswählen am Ende des Feldes **Menüelementtyp**, um einen Elementtyp auszuwählen.
- Wählen Sie aus der Popup-Liste **Beiträge** → **Kategorieblog**.
- Verwenden Sie im Feld Kategorie auswählen die Schaltfläche Auswählen.
- Wählen Sie aus der Popup-Kategorieliste die Kategorie Categoría (es-es) aus.
- Setzen Sie das Feld **Standardseite** auf **Ja**.
- Wählen Sie im Dropdown-Menü **Sprache** die Option **Spanisch (es-ES)** aus.
- **Speichern & Schließen**

### Schritt 7: Einen Beitrag hinzufügen

Der einfache Weg, einen Beitrag für die neue Sprache hinzuzufügen, besteht darin, einen vorhandenen Beitrag zu kopieren.

- Wählen Sie **Inhalt** → **Beiträge** aus dem Administrator-Menü.
- Wählen Sie den zu kopierenden Beitrag aus, in diesem Beispiel **Beitrag (en-GB)**.
- Ändern Sie im Formular **Beiträge: Bearbeiten** den Titel in **Beitrag (es-ES)**.
- Ändern Sie die **Kategorie** in **Categoría (es-es) (es-ES)**.
- Ändern Sie die **Sprache** in Spanisch (es-ES)**.**
- Wählen Sie **Speichern als Kopie** aus dem Dropdown-Menü **Speichern & Schließen** in der Symbolleiste. **Vorsicht!**
- Wählen Sie die Registerkarte **Verknüpfungen**.
- Wählen Sie für jede Sprache einen Beitrag aus, der verknüpft werden soll – der entsprechende Beitrag in jeder Sprache.
- Wählen Sie **Speichern & Schließen** aus der Symbolleiste.
```

## Hinzufügen eines mehrsprachigen Beitrags

Angenommen, Sie möchten einen Beitrag in jeder Ihrer ausgewählten Sprachen erstellen.

- Wählen Sie **Inhalt** → **Beiträge** → **+** aus dem Administrator-Menü oder die **Neu**-Schaltfläche aus der Symbolleiste in der Beitragsliste.
- Geben Sie einen Titel für den Beitrag ein, zum Beispiel **William Shakespeare**.
- Setzen Sie das Feld **Kategorie** auf **Kategorie (en-gb) (en-GB)**.
- Setzen Sie das Feld **Sprache** auf **Englisch (en-GB)**.
- Geben Sie den **Beitragstext** ein, beispielsweise aus Wikipedia:

„William Shakespeare (getauft am 26. April 1564 – 23. April 1616) war ein englischer Dramatiker, Dichter und Schauspieler. Er wird weithin als der größte Schriftsteller der englischen Sprache und als der weltweit größte Dramatiker angesehen. Er wird oft Englands Nationaldichter und der "Barde von Avon" (oder einfach "der Barde") genannt. Seine erhaltenen Werke, einschließlich Zusammenarbeiten, bestehen aus etwa 39 Theaterstücken, 154 Sonetten, drei langen Erzählgedichten und einigen anderen Versen, von denen einige unsicherer Urheberschaft sind. Seine Stücke wurden in jede bedeutende lebende Sprache übersetzt und werden häufiger aufgeführt als die jedes anderen Dramatikers. Er bleibt wohl der einflussreichste Schriftsteller der englischen Sprache, und seine Werke werden weiterhin studiert und neu interpretiert.“

- Wählen Sie **Speichern** aus der Symbolleiste.
- Wählen Sie die Registerkarte **Verknüpfungen**.
- Für jede Sprache:
  - Wählen Sie die Schaltfläche **Erstellen**.
  - Geben Sie im Popup-Formular **Neuer Beitrag** einen übersetzten Titel ein, **William Shakespeare**.
  - Setzen Sie die Kategorie auf diejenige der gewählten Sprache.
  - Geben Sie den übersetzten Text in das Feld **Beitragstext** ein (Sie können es mit <a href="https://translate.google.com/" rel="nofollow noreferrer noopener">https://translate.google.com/</a> versuchen).
  - Wählen Sie **Speichern & Schließen**.
- Nachdem ein neuer Beitrag für jede Sprache erstellt wurde, wählen Sie **Speichern & Schließen**.

## Hauptmenü

Wenn Sie einen Link zu einem Beitrag für alle Sprachen im Hauptmenü haben und diesen Beitrag später als Basis für zugehörige Beiträge in anderen Sprachen verwenden möchten, müssen Sie den Link im Hauptmenü ändern. Andernfalls führt das Umschalten der Sprache bei ausgewähltem Beitrag zu einem Fehler "Seite nicht gefunden" in der ausgewählten Sprache.

- Wählen Sie **Menüs** → **Hauptmenü** aus dem Administrator-Menü.
- Wählen Sie das Menüpunkts aus, den Sie ändern müssen, zum Beispiel **William Shakespeare**.
- Ändern Sie das Feld **Sprache** zu **Englisch (en-GB)**.
- Wählen Sie **Speichern & Schließen** aus der Symbolleiste.

Wenn es nur diesen einen Punkt im Hauptmenü gibt, wird dieses Modul beim Umschalten auf andere Sprachen verschwinden.

*Übersetzt von openai.com*

