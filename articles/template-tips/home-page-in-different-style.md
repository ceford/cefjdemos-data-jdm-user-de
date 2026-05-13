<!--
{
  "source": "https://docs.joomla.org/J4.x:Home_Page_in_Different_Style",
  "title": "Startseite in unterschiedlichem Stil  ",
  "description": "", 
  "author": ""
}
-->

## Startseite der Website

Eine Startseite der Website kann aus jedem Menüeintragstyp ausgewählt werden, indem man ein graues Symbol in der Spalte "Home" einer Liste von Menüpunkten auswählt. Probieren Sie doch mal eine Änderung aus! Sehen Sie sich die Änderung in einem separaten Browser-Tab oder Fenster auf Ihrer Website an. Sie können leicht wieder zurückwechseln. Wenn Sie eine charakteristische Startseite möchten, könnten Sie einen Menüeintragstyp wie „Einzelner Beitrag“, „Kategorie-Blog“, „Hervorgehobene Beiträge“ oder etwas anderes wählen.

Angenommen, Sie möchten Ihrer Startseite ein unverwechselbares Erscheinungsbild geben, das sich ein wenig von allen anderen Seiten Ihrer Website unterscheidet. Es gibt viele verschiedene Methoden, um das Erscheinungsbild einer Startseite anzupassen:

- Über Module, die nur der Startseite zugewiesen sind.
- Über benutzerdefinierte Stile.
- Über eine Vorlagen-Override oder ein Layout.
- Über eine separate Vorlage oder eine Kindvorlage, die nur für den Startseiten-Menüpunkt verwendet wird.
- Mehr...?

## Beispiel: Cassiopeia-Beispieldaten

Die Cassiopeia-Beispieldaten erstellen eine Startseite mit einem Menüpunkt des Typs **Hervorgehobene Beiträge**. Sie ist mit dem Aussehen im unten stehenden Screenshot gestaltet (einige kleinere Änderungen wurden an einzelnen Beiträgen vorgenommen, um hier einen besseren Screenshot zu erhalten).

![Startseite mit Cassiopeia und Beispieldaten](../../../en/images/template-tips/home-page-in-different-style/01-templates-home-page-style-cassiopeia-sample-data.png)

So wird das Layout erreicht:

### Bildmodul

Das große Bild unter der Menüleiste befindet sich in einem benutzerdefinierten Modul namens Bild, das der Banner-Position im Cassiopeia-Template zugewiesen ist.

![benutzerdefiniertes Modul verwendet im Stil der Beispieldaten](../../../en/images/template-tips/home-page-in-different-style/02-templates-home-page-style-custom-module-image.png)

Im Menüzuweisung-Tab wird das Modul nur der Startseite zugewiesen:

![Benutzerdefiniertes Modul Menüzuweisung Tab](../../../en/images/template-tips/home-page-in-different-style/03-templates-home-page-style-custom-module-menu-assignment.png)

Das Hintergrundbild wird im Optionen-Tab des Module: Benutzerdefiniert Bearbeitungsformulars ausgewählt.

Im Erweitert-Tab / Layout-Feld wird das Banner-Element ausgewählt. Das Banner-Layout ist ein Template-Layout:

### Template-Layout

Das Standardmodul-Layout in `siteroot/modules/mod_custom/tmpl/default.php` zeigt das Modul nicht wie gewünscht an. Es gibt ein alternatives Layout in `siteroot/template-tips/cassiopeia/html/mod_custom/banner.php`. Da `banner.php` nicht im benutzerdefinierten Modulcode vorhanden ist, funktioniert es als ein Layout, das man auswählen kann, anstatt als ein Override, das immer verwendet wird. Im Bildmodul kann man das Standardlayout auswählen, speichern und die Seite erneut laden, um den Unterschied zu sehen. Wechseln Sie zurück zum Banner-Layout und speichern Sie erneut, um das normale Verhalten wiederherzustellen.

Es gibt separate Beiträge zu Overrides und Layouts.

### Newsflash-Modul

Unter dem großen Bild befinden sich drei kleine Kästchen, jeweils mit einem Bild und Text darunter. Sie werden mit einem Beiträge - Newsflash-Modul in der Template-Position top-a erstellt. Das Modul ist so eingestellt, dass es 3 Elemente anzeigt. Seine Menüzuweisung ist nur auf der Startseite. Der Erweitert-Tab hat das Layout auf horizontal und den Modulstil auf noCard gesetzt.

![Newsflash-Modul](../../../en/images/template-tips/home-page-in-different-style/04-templates-home-page-style-newsflash-module-image.png)

Damit endet die Erklärung, wie die Cassiopeia-Beispieldaten Startseite erstellt wurde.  

## Weitere Optionen

Möglicherweise möchten Sie noch mehr tun. Ein anderes Farbschema für die Startseite, ein Wasserzeichen oder ein benutzerdefiniertes Layout. Hier sind ein paar Ideen:

### Seitenanzeige

Im Menü: Bearbeitungsformular für den Startmenüpunkt wählen Sie die Registerkarte Seitenanzeige. Das Feld Seitenklasse ist normalerweise leer. Alles, was hier eingegeben wird, wird zu einer zusätzlichen Klasse im `<body>`-Element der Seite. Wenn Sie beispielsweise `fancyhome` eingeben, ergibt dies Folgendes in der Startseitenausgabe für diese eine Seite:
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Sie können dann eine user.css-Datei über **System → Seitenvorlagen → Cassiopeia Details und Dateien** erstellen. Wählen Sie die Schaltfläche `Neue Datei` und erstellen Sie user.css im css-Ordner. Geben Sie dann Stile im user.css-Bearbeitungsformular ein. Beispiel:
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Dies verleiht der Startseite einen blassgrünen Hintergrund. Verwenden Sie \#f8f8ff; für einen blassblauen Hintergrund oder \#ffffee für blassgelb. Sie können mit Ihrem fancyhome-Stil viele andere Dinge tun, aber Sie benötigen gute Kenntnisse in CSS.

### Alternative Startseiten-Vorlagen

Sie können alternative Seitenvorlagen installieren, die von Drittanbietern bezogen werden. Und Sie können Kindvorlagen erstellen, die sich ähnlich verhalten. In beiden Fällen können Sie auswählen, welche Vorlage für alle Seiten als Standard festgelegt und welche nur für die Startseite verwendet werden soll.

- Wählen Sie **System → Webseitenvorlagenstile** im Administratormenü.
- Wählen Sie die Vorlage, die Sie für die Startseite verwenden möchten. Sie muss eine derjenigen sein, die nicht als Standardvorlage ausgewählt sind.
- Im Tab Menüzuweisung wählen Sie nur den Startmenüpunkt. Alles, was hier nicht ausgewählt ist, wird weiterhin Ihre Standardvorlage verwenden.
- Sie könnten einige Optionen im Tab Erweitert auswählen, aber sie variieren je nach Vorlage und werden hier nicht behandelt.

Es gibt weitere Beiträge zur Anpassung von Cassiopeia.

*Übersetzt von openai.com*

