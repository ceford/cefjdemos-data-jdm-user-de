<!--
{
  "source": "https://docs.joomla.org/J4.x:Child_Templates",
  "title": "Kindvorlagen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Child-Templates verwenden alle Dateien ihrer Parent-Templates, außer für Dateien mit demselben Namen, die Sie im Child-Template platzieren. Dateien von Child-Templates werden durch Joomla-Updates nicht beeinflusst. Sie könnten also Ihre eigene index.php-Datei in ein Child-Template einfügen und damit etwas ganz anderes als das Standardtemplate liefern, zum Beispiel zusätzliche Modulpositionen oder alternative Erweiterungs-Overrides.

Ein Beispiel-Szenario: Angenommen, Sie möchten, dass einige Ihrer Seiten mit einem blauen Thema, den Standardfarben von Cassiopeia, erscheinen und andere Seiten mit einem grünen Thema. Eine einfache Möglichkeit, dies zu erreichen, ist ein Child-Template, das sein eigenes user.css-Stylesheet verwendet.

## Veranschaulichtes Beispiel

Beginnen Sie mit **System → Vorlagen-Panel → Website-Vorlagen**

- Wählen Sie *Cassiopeia Details und Dateien*.
- Wählen Sie die Schaltfläche *Untervorlage erstellen*.
- Füllen Sie das Popup-Dialogfeld für die Untervorlage aus und wählen Sie die Schaltfläche Untervorlage erstellen:

![child template modal create form](../../../en/images/templates/child-templates/01-child-templates-create-green.png)

Die Auswahl von Cassiopeia - Standard im Feld Zusätzliche Vorlagenstile scheint unnötig zu sein (ist das ein Fehler?).

- Wählen Sie *Schließen* aus der Werkzeugleiste, um das Formular der übergeordneten Vorlage zu schließen.
- Wählen Sie die neue Vorlage, *Cassiopeia_green Details und Dateien*, aus der Liste der Vorlagen.

An diesem Punkt gibt es eine Ordnerstruktur, aber nur eine Datei: templateDetails.xml. Diese Datei kann geändert werden, wenn Sie Aspekte der Vorlagenkonfiguration ändern möchten, z.B. Vorlagenpositionen hinzufügen oder entfernen.

### Erstellen Sie eine user.css-Datei

- Wählen Sie die Schaltfläche *Neue Datei* in der Werkzeugleiste.
- Stellen Sie im Formular *Neue Datei erstellen oder hochladen* sicher, dass Sie den Ordner `css` auswählen.
- Geben Sie den Dateinamen mit `user` aus. KEIN Suffix hinzufügen!
- Wählen Sie den Dateityp `.css`.
- Wählen Sie die Schaltfläche *Erstellen*.

![child template create user css form](../../../en/images/templates/child-templates/02-child-templates-create-green-user-css.png)

Die Datei user.css ist leer und bereit für Ihre eigenen benutzerdefinierten Stile. Geben Sie folgendes ein, um das grüne Thema zu starten:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
    a, a:hover, a:focus {
      color: darkgreen;
    }
    .btn-info {
        background-color: darkgreen;
        border-color: #30638d;
        color: #fff;
    }
    .btn-primary, .btn-primary:focus, .btn-primary:hover {
        background-color: darkgreen;
        border-color: var(--cassiopeia-color-hover);
    }

    .btn-check:focus + .btn-info, .btn-info:focus, .btn-info:hover {
        background-color: darkgreen;
        border-color: #264f71;
        color: #fff;
    }
```
Möglicherweise müssen Sie später zu dieser user.css-Datei zurückkehren, um weitere Stile hinzuzufügen.

- Wählen Sie *Speichern & Schließen* oder getrennt *Speichern* und dann *Datei schließen*.
- Wählen Sie *Schließen*, um das Anpassen-Formular zu schließen.

### Menüpunkt

An diesem Punkt wird ein Menüpunkt benötigt, um die Untervorlage zu verwenden. Eine neue Joomla 4-Installation hat das Hauptmenü in der rechten Seitenleiste mit einem Eintrag darin. Das scheint ein guter Ort für einen neuen Menüpunkt zu sein.

- Wählen Sie **Menüs → Hauptmenü** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche *Neu* aus der Werkzeugleiste.
- Geben Sie einen passenden Titel ein, *Green Featured Beiträge* scheint hier passend zu sein.
- Wählen Sie die Schaltfläche **Menüpunkt-Typ → Auswählen**.
- Wählen Sie einen Menüpunkt-Typ aus dem Popup-Dialog für Menüpunkt-Typ - Vorgestellte Beiträge in diesem Beispiel.
- Wählen Sie *cassiopeia_manual - Standard* aus dem Formularfeld *Vorlagenstil*.

![child template menu item edit form](../../../en/images/templates/child-templates/03-child-templates-create-green-menu-item.png)

- Für den Zweck des folgenden Screenshots wurde das Blog-Layout auf Hauptbeiträge: 0, Einführungselemente: 3 und Mehrs­paltige Anordnung: Quer eingestellt.

### Website-Ansicht

- Auf der Startseite Ihrer Website wählen Sie den neu erstellten Menüpunkt.

![site showing custom green theme template](../../../en/images/templates/child-templates/04-child-templates-green-site-result.png)

### Stil bearbeiten

- Wählen Sie **System → Vorlagen-Panel → Vorlagenstile der Website** aus dem Administrator-Menü.
- Wählen Sie *Cassiopeia_green - Standard* aus der Stileliste.
- Ändern Sie den Stilnamen in *Cassiopeia Grün*. Das bringt den Namen in Listen in Ordnung.
- Wählen Sie *Speichern und Schließen*.

*Übersetzt von openai.com*

