<!--
{
  "source": "https://docs.joomla.org/J5.x:Add_a_class_selector_to_the_create_link_dialog",
  "title": "Beitrag: Bearbeiten - Linkstile ",
  "description": "", 
  "author": ""
}
-->

## Beschreibung

Benutzerdefinierte Linkklassen, die zu den TinyMCE-Editoroptionen hinzugefügt wurden, ermöglichen es Ihnen, schnell einen Beitragslink in einen Button zu verwandeln oder andere visuelle Effekte hinzuzufügen, ohne den HTML-Code direkt bearbeiten zu müssen.

### Schritte zur Verwendung des Klassenselektors

1. Gehen Sie vom Start-Dashboard zur Plugin-Liste und finden Sie das TinyMCE-Plugin.
2. Öffnen Sie das TinyMCE-Plugin und scrollen Sie mit dem ausgewählten Plugin-Tab nach unten zum Ende.
3. Fügen Sie Klassen zur *Linkklassenliste* hinzu, z.B. Bootstrap-Klassen, um stilvolle Buttons zu erstellen. Möglicherweise müssen Sie die Liste von links nach rechts scrollen oder die Bildschirmvergrößerung ändern, um die Hinzufügen-, Entfernen- und Anordnen-Schaltflächen am Ende zu sehen.
4. Speichern & Schließen.

![Set link classes in tinymce](../../../en/images/articles/article-link-styles/01-article-edit-link-style-tinymce.png)

Du kannst Beispiele für Vorlagen, die nativ Bootstrap nutzen, in der offiziellen [Bootstrap-Dokumentation](https://getbootstrap.com/docs/5.3/components/buttons/) finden.

Hier sind einige Klassen, die Sie für Bootstrap-Button-Varianten verwenden können:

- `btn btn-primary` für eine primäre Schaltfläche
- `btn btn-secondary` für eine sekundäre Schaltfläche
- `btn btn-success` für eine Erfolgs-Schaltfläche
- `btn btn-danger` für eine Gefahr-Schaltfläche
- `btn btn-warning` für eine Warn-Schaltfläche
- `btn btn-info` für eine Info-Schaltfläche
- `btn btn-light` für eine helle Schaltfläche
- `btn btn-dark` für eine dunkle Schaltfläche
- `btn btn-link` für eine Link-Schaltfläche

#### Umriss-Button-Alternativen

Sie können auch die Umriss-Schaltflächenvarianten verwenden:

- `btn btn-outline-primary` für einen umrissenen primären Button
- `btn btn-outline-secondary` für einen umrissenen sekundären Button
- … (usw.)

#### Für Schaltflächengrößen fügen Sie diese Klassen hinzu

- `btn-lg` für einen großen Button
- `btn-sm` für einen kleinen Button

Bitte verwenden Sie das Wort Beiträge anstelle von Artikel.

## Einen Link in einem Beitrag erstellen

1. Öffnen Sie einen Beitrag und wählen Sie einen Text, ein Wort oder einen Satz für die Linkerstellung aus.
2. Wählen Sie das Link-Symbol, das erscheint, wenn Sie Text auswählen.
3. Geben Sie die URL für den Link ein.
4. Wählen Sie am unteren Rand des Linkerstellungsdialogs eine der konfigurierten Klassen aus.
5. Speichern Sie den Link.
6. Speichern Sie den Beitrag.
7. Vorschau des Beitrags anzeigen.

![Apply link style in an article](../../../en/images/articles/article-link-styles/02-article-edit-link-style-apply.png)

Und dies ist ein Beispiel, bei dem die Link-Button-Klasse auf `btn btn-sm btn-outline-info` gesetzt wurde und der verknüpfte Text *Bootstrap* ist.

![Preview of a custom Link Button](../../../en/images/articles/article-link-styles/03-article-edit-link-style-preview.png)

## Erweiterte Anwendung: Anwenden benutzerdefinierter Klassen

Diese Funktion ist nicht auf Bootstrap-Klassen beschränkt. Sie können auch Ihre eigenen benutzerdefinierten CSS-Klassen für spezifische Bedürfnisse anwenden. Zum Beispiel können Sie ein Symbol vor dem Link mit einem Hover-Effekt hinzufügen. Dies erleichtert das Styling von Links, ohne den Quellcode des Beitrags ändern zu müssen.

