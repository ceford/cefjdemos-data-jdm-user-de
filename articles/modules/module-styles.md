<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=modules&filename=module-styles.md",
  "title": "Modulstile",
  "description": "", 
  "author": ""
}
-->

## Stilkonzepte

Ein Moduldatenformular verfügt über einen **Erweitert**-Tab. Die Felder variieren je nach Modultyp, und Sie können dies selbst sehen, indem Sie ein Menümodul auswählen und es mit einem Anmeldemodul oder einem Breadcrumbs-Modul vergleichen. Sie werden die folgenden drei Formularfelder im Zusammenhang mit dem Styling sehen:

* **Modulklasse** ist ein Textfeld, das es Ihnen erlaubt, eine eigene CSS-Klasse zum Modulcontainer-Tag hinzuzufügen, normalerweise ein `<div>`.
* **Headerklasse** ist ein Textfeld, das es Ihnen erlaubt, eine eigene CSS-Klasse zum Header-Tag hinzuzufügen, standardmäßig ein `<h3>`-Tag.
* **Modulstil** ist eine Liste, die es Ihnen erlaubt, einen aus einer Reihe von Standardstilen auszuwählen. Die Liste enthält keinen, html5, Umriss, Tabelle, Karte und keineKarte. Die Standardeinstellung ist Karte aus den Cassiopeia-Template-Stilen.

Sie können die *Modulstil*-Optionen ausprobieren, indem Sie ein Modul bearbeiten und den Wert ändern, um zu sehen, was es für die Darstellung der Website bewirkt.

* **html5** ergibt `<div class="moduletable ">`
* **keiner** entfernt das äußere `<div>` vollständig sowie das Modul-`<h3>`-Tag.
* **Umriss** ergibt `<div class="mod_preview_info">`, wobei Positions- und Stilinformationen das Modul-`<h3>`-Tag ersetzen.
* **Tabelle** ergibt ein Tabellenlayout beginnend mit `<table class="moduletable ">`, wobei das frühere h3-Tag jetzt ein `<th>`-Tag ist.
* **Karte** ergibt `<div class="sidebar-right card ">`, die Standardeinstellung.
* **keineKarte** ergibt `<div class="sidebar-right no-card ">`

## Die Modulklasse

An diesem Punkt sollten Sie ein wenig über Cascading Style Sheets oder CSS wissen. Wenn Sie ein einzelnes Wort in das Modulklassenfeld eingeben, zum Beispiel **green** (da CSS-Klassen konventionell alle in Kleinbuchstaben gehalten sind) und der Modulstil auf **inherited** eingestellt ist, enthält die Ausgabe `<div class="sidebar-right card green">`.

Es gibt keine sichtbare Änderung im Erscheinungsbild der Website, da die Klasse green nicht definiert ist. Um sie zu definieren, machen Sie einen Eintrag in der Datei user.css des Templates.

Vom Administrator-Menü aus:
* Wählen Sie **System / Site Templates / Cassiopeia Templates und Dateien**.
* Wählen Sie **Neue Datei** aus der *Werkzeugleiste*.
* Wählen Sie **css** in der linken Spalte, als Ziel für die neue Datei.
* Geben Sie **user** im Dateinamensfeld ein.
* Wählen Sie **css** aus der Dateitypliste.
* Wählen Sie die Schaltfläche **Erstellen**.

Sie können jetzt den css-Ordner öffnen, um die Datei user.css zu finden und zum Bearbeiten zu öffnen. Geben Sie diese Stil-Anweisungen ein und beachten Sie die US-amerikanische Schreibweise von *color*:
```
.sidebar-right.card.green {
    background-color: #ddffdd;
}
.sidebar-right.card.green .card-body {
    background-color: #eeffee;
}
```
Der Stil hätte nur `.green` verwenden können, aber das hätte andere Tags mit diesem Stil auf anderen Seiten beeinflussen können.

## Die Header-Klasse

Gehen Sie zurück zum Modul-Bearbeitungsformular und fügen Sie **blau** im Feld für die Header-Klasse hinzu. Das Modul weist auf der Seite keine sichtbare Änderung auf, aber die Überschrift wird nun als `<h3 class="card-header blue">` angezeigt. Bearbeiten Sie die Datei user.css, um einen Eintrag für den Überschriftenstil hinzuzufügen:
```css
.card-header.blue {
    color: navy;
}
```
Die Modulüberschrift ist nun dunkelblau. Es gibt verschiedene Möglichkeiten, Farben in CSS anzugeben. Die gebräuchlichsten sind Hexadezimal- und Standardfarbnamen. Lesen Sie mehr darüber woanders!  

## CSS-Herausforderung

* Ändere die Modulrahmenfarbe zu Marineblau!
* Ändere auch die untere Rahmenlinie der Überschrift.
* Wende diesen Stil auf mehrere Beiträge gleichzeitig an, anstatt sie einzeln zu bearbeiten.

![Archivierte Beiträge Modul Beispiel](../../../en/images/modules/module-styles/01-modules-archived-articles.png)

*Übersetzt von openai.com*  

