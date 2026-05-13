<!--
{
  "source": "https://docs.joomla.org/J4.x:Template_Basics",
  "title": "Grundlagen der Vorlagen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

In Joomla! ist ein Template eine Sammlung von Dateien, die zusammen das Erscheinungsbild der Website definieren. Joomla 4 bietet zwei Templates: Atum ist das Administrator-Template, das für die Verwaltung der Website verwendet wird, und Cassiopeia ist das Seiten-Template, das für Besucher der Website genutzt wird. Darüber hinaus stehen viele weitere Seiten-Templates von unabhängigen Anbietern zur Verfügung, entweder kostenlos oder gegen eine geringe Gebühr. Tatsächlich gibt es eine ganze Branche, die sich auf die Bereitstellung von spezialisierten Seiten-Templates spezialisiert hat.

Ein typisches Seiten-Template enthält PHP-Dateien zur Anordnung der Inhalte und CSS-Dateien zur Gestaltung der Inhalte. Oft gibt es zusätzliche Dateien wie Bilder, die im Layout verwendet werden, und JavaScript-Dateien, die zur Interaktion mit Website-Features wie Links und Buttons genutzt werden. Der folgende Screenshot zeigt die Ordner und Dateien des Cassiopeia-Templates in einer neuen Joomla 4-Installation:

![templates customise cassiopeia page](../../../en/images/templates/template-basics/01-templates-customise-cassiopeia.png)

Beachten Sie, dass sich die PHP-Dateien im Ordner site /templates befinden und die Mediendateien im Ordner site /media.

## Vorlagenpositionen

Die Website-Vorlage legt die Positionen des Hauptinhalts fest, zum Beispiel eines einzelnen Beitrags oder eines Blog-Layouts mit hervorgehobenen Beiträgen, sowie aller Module, die über, unter, links oder rechts vom Hauptinhalt angezeigt werden sollen. Die folgende Abbildung zeigt die in Cassiopeia verfügbaren Positionen:

![Diagramm der Vorlagenpositionen](../../../en/images/templates/template-basics/02-cassiopeia-template-positions.png)

Sie können die Vorlagenpositionen in jeder Vorlage anzeigen, indem Sie in den Vorlagenoptionen die Vorschau der Modulpositionen auf "Aktiviert" einstellen und dann ?tp=1 an die URL anhängen. Wenn bereits eine Abfragezeichenfolge an die URL angehängt ist, dann stattdessen &tp=1 anhängen.  

## Benutzer-Styling

Cassiopeia bietet einige Optionen, die Sie ändern können, um das Erscheinungsbild der Website anzupassen (es gibt einen separaten Beitrag zur Cassiopeia-Anpassung). Das mag für Ihre Zwecke jedoch nicht ausreichen. Sie können das Erscheinungsbild auch mit einem user.css-Stilblatt selbst ändern. Sie müssen dieses selbst im Formular Vorlagen:Anpassen erstellen. Wählen Sie einfach Neue Datei aus und geben Sie Dateiname: user ein, wählen Sie Dateityp: .css und wählen Sie css aus der Liste der Ordner aus. Wählen Sie dann die neu erstellte user.css-Datei im Bearbeitungsformular aus und geben Sie einige Stile ein, um beispielsweise Überschriften dunkelgrün zu machen:

```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Template-Überschreibungen

Zusätzlich zum gesamten Layout, das durch das Seitentemplate definiert ist, hat jede Komponente oder jedes Modul ein Template, um sein Erscheinungsbild innerhalb des Gesamtlayouts zu definieren. Solche Templates befinden sich in einem tmpl-Ordner innerhalb der Komponente oder des Moduls. Einige Plugins haben ebenfalls Templates. Und es gibt Layouts, die von jedem Typ der Erweiterung aufgerufen werden können.

Manchmal entspricht eines dieser *Erweiterungs*-Templates nicht ganz Ihren Vorstellungen. In diesem Fall können Sie eine Template-Überschreibung erstellen. Dies ist eine Kopie des Codes, der verwendet wird, um das Erweiterungslayout zu generieren, das Sie nach Ihren eigenen Bedürfnissen anpassen können. Der folgende Screenshot zeigt das Formular "Template: Überschreibungen erstellen":

![template overrides](../../../en/images/templates/template-basics/03-cassiopeia-customisation-create-overrides.png)

Cassiopeia hat bereits einige Überschreibungen installiert. Das könnte als Problem erscheinen. Wenn Sie eine der standardmäßigen Cassiopeia-Dateien ändern, werden Ihre Änderungen beim nächsten Joomla-Update überschrieben (und gehen somit verloren). Die Lösung sind Kind-Templates.

## Alternative Layouts

Eine Vorlage oder eine Vorlage-Überschreibung definiert das Erscheinungsbild einer Erweiterung in einer bestimmten Datei, wie z. B. default.php. In einigen Fällen möchten Sie möglicherweise zwischen dem Standardlayout und einem alternativen Layout wählen. Zum Beispiel benötigt ein Menü in einer oberen Position normalerweise ein anderes Layout als dasselbe Menü in einer seitlichen Position. In einem Menümodul gibt es im Reiter "Erweitert" des Moduls-Bearbeitungsformulars einen Layout-Parameter, der es Ihnen ermöglicht, aus verfügbaren alternativen Layouts zu wählen. Es gibt ein separates Tutorial zu alternativen Layouts für Vorlagen.

## Kindvorlagen

Eine Kindvorlage verwendet die Dateien in ihrer Elternvorlage, außer für alle Dateien, die in der Kindvorlage enthalten sind. Zum Beispiel könnten Sie unterschiedliche user.css-Dateien in der Eltern- und Kindvorlage haben, sodass verschiedene Seiten unterschiedliche Farbschemata haben könnten. Oder Sie könnten die index.php-Datei von der Elternvorlage in die Kindvorlage kopieren und die Kindvorlage ändern, um ein anderes Layout als die Elternvorlage zu erzeugen. Es gibt ein separates Tutorial zu Kindvorlagen.

*Übersetzt von openai.com*

