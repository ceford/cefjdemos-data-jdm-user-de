<!--
{
  "source": "https://docs.joomla.org/J4.x:Module_and_Menu_Styles",
  "title": "Modul- und Menü-Stile ",
  "description": "", 
  "author": ""
}
-->

## Über Cascading Style Sheets

Eine von Joomla! ausgegebene Webseite besteht aus HTML-Tags mit Stilattributen in Form von Klassendefinitionen. Zum Beispiel könnte eine Überschrift innerhalb eines Beitrags so aussehen: `<h3 class="special-warning">Achtung!</h3>`. Diese Überschrift könnte in einer größeren Schrift angezeigt werden, mit anderen Farben für Text und Hintergrund, und möglicherweise mit einem Rahmen und einem Warnsymbol. Die Klassenstile würden in der user.css-Datei des Templates definiert, so:

```css
    h3.special-warning {
      color: #900;
      background-color: #fee;
      border: 1px solid #900;
      padding: 1rem;
      font-size: 2rem;
    }
```

Dies funktioniert, weil das user.css-Stylesheet zuletzt geladen wird und alle darin enthaltenen Stile Vorrang vor denselben Stilen in zuvor geladenen css-Dateien haben. Der `special-warning` Stil wird nicht auf andere `<h3>`-Tags angewendet, sondern nur auf diejenigen mit dieser spezifischen Klasse. Es funktioniert innerhalb eines Beitrags, weil Sie dort selbst den Klassennamen eingeben.

Aber was, wenn Sie ein Modul oder eine ganze Seite stylen möchten? Zum Beispiel könnten Sie verschiedenen Modulen oder Seiten unterschiedliche Hintergrundfarben zuweisen. Oder Sie könnten die Überschrift Ihrer Startseite anders gestalten als die Überschriften auf anderen Seiten. All dies kann erreicht werden, indem Klassennamen im Modulbearbeitungsformular oder im Menüpunktbearbeitungsformular hinzugefügt werden. Die Stilklassen werden dann in die user.css-Datei eingetragen.

## Modulstile

Dieses einfache Beispiel wendet benutzerdefinierte Stile auf das Anmeldemodul und dessen Überschrift an. Der folgende Screenshot zeigt die eingegebenen Stilenamen im Tab "Erweitert" des Moduls: Bearbeitungsformular für Login. Die Modulklasse wurde auf `make-me-light-green` und die Kopfzeilenklasse auf `make-me-dark-green` gesetzt. Beachten Sie, dass Sie in Klassennamen Minuszeichen oder Unterstriche einschließen können, aber Leerzeichen trennen verschiedene Klassennamen.

![Bearbeitungsformular für das Anmeldemodul im Tab "Erweitert" mit benutzerdefinierter Klasse](../../../en/images/template-tips/module-and-menu-styles/01-templates-edit-module-style.png)

Die folgenden Stildefinitionen werden in der user.css-Datei verwendet:
```css
    .make-me-light-green {
      background-color: #efe;
      border-color: darkgreen;
    }
    .make-me-dark-green {
      color: darkgreen;
      border-color: #264f71;
    }
```
Achten Sie auf den Punkt (.), der in CSS verwendet wird, um eine Klasse mit diesem Namen zu definieren. Der Punkt darf nicht im Modul-Dateneingabeformular verwendet werden. Das Ergebnis in diesem Beispiel ist wie folgt:

![Ansicht der benutzerdefinierten Modulansicht mit Entwicklerwerkzeugen](../../../en/images/template-tips/module-and-menu-styles/02-templates-edit-module-style-result.png)

Der untere Teil des Bildes zeigt das Browser-Entwicklungstool-Fenster, wobei das `<div>`-Tag des Anmeldemoduls ausgewählt ist. Sie können sehen, dass der benutzerdefinierte Modulklassenstil an die bereits im Modultemplate definierten Stile angehängt wurde. Die nächste Zeile zeigt das `<h3>`-Tag ebenfalls mit der benutzerdefinierten Kopfzeilenklasse, die an bereits definierte Stile angehängt wurde.

Vielleicht gefällt Ihnen dieser Modulstil nicht! Aber dies ist nur eine Lektion darüber, wie man es macht, nicht darüber, was ein gutes Farbschema ausmacht!

## Seitenstile

Es gibt mehrere Möglichkeiten, das Gesamtbild einer Seite anzupassen. Alle Arbeiten erfolgen über das Menüs: Element bearbeiten Formular:

- Die Registerkarte Details bietet eine Option für den Vorlagenstil, aus der Sie eine spezifische Vorlage auswählen können.
- Die Registerkarte Bloglayout enthält die Felder Führender Beitrags-Klasse und Beitrags-Klasse, in die Sie einen Klassennamen eingeben können.
- Die Registerkarte Optionen bietet ein Feld Layout auswählen, aus dem Sie unter den verfügbaren Layouts für alle Elemente wählen können.
- Die Registerkarte Linktyp enthält Felder für eine Linkklasse, eine Link-Icon-Klasse und eine Bildklasse.
- Die Registerkarte Seitendarstellung enthält Felder für eine Seitenklasse.

Es ist der letzte Punkt in dieser Liste, der in diesem Beitrag behandelt wird. Was passiert, wenn `make-me-aliceblue` in dieses Feld eingegeben wird? Und wenn Folgendes in user.css eingegeben wird:
```css
    .make-me-aliceblue {
      background-color: aliceblue;
    }
```
Die Klasse wird dem Body-Tag der Seite hinzugefügt:

![Darstellung der angepassten Seite mit Entwickler-Tools](../../../en/images/template-tips/module-and-menu-styles/03-templates-edit-page-class-result.png)

QED!

*Übersetzt von openai.com*

