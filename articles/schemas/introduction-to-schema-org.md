<!--
{
  "source": "https://docs.joomla.org/J5.x:Schema_org",
  "title": "Einführung in Schemas",
  "description": "", 
  "author": ""
}
-->

## Rich Snippets

Rich Snippets (auch bekannt als *Rich Results*) sind normale Google-Suchergebnisse mit zusätzlichen angezeigten Daten. Diese zusätzlichen Daten werden normalerweise aus strukturierten Daten zusammengestellt, die im HTML einer Seite zu finden sind. Häufige Arten von Rich Snippets umfassen Bewertungen, Rezepte und Veranstaltungen. Rich Snippets können Websites helfen, sich in den Suchergebnissen abzuheben, mehr Klicks anzuziehen und den Nutzern ein besseres Verständnis des Inhalts zu bieten, bevor sie durchklicken.

Joomla implementiert Rich Snippets unter Verwendung von JSON-LD. Dies ist eine JavaScript-Notation, die in einem `<script>`-Tag im `<head>`-Element einer HTML-Seite eingebettet ist. Das Markup ist nicht mit dem für den Benutzer sichtbaren Text vermischt. Der Inhalt der Snippets wird in Formularfeldern eingegeben, die mit Plugins implementiert sind.

## Schema.org

Schema.org ist eine gemeinschaftliche, gemeinschaftsbasierte Aktivität mit der Mission, Schemata für strukturierte Daten im Internet, auf Webseiten, in E-Mail-Nachrichten und darüber hinaus zu erstellen, zu pflegen und zu fördern.

Strukturierte Daten sind ein standardisiertes Format zur Organisation und Darstellung von Informationen im Internet. Sie bieten eine Möglichkeit, den Inhalt und die Bedeutung von Daten auf eine strukturierte Weise zu beschreiben, was es Suchmaschinen und anderen Anwendungen erleichtert, die Informationen zu verstehen und zu verarbeiten. Es gibt ausführlichere Informationen auf der [Schema.org-Website](https://schema.org/).

## Joomla-Implementierung

In Joomla werden Rich Snippets mithilfe von strukturierten Daten-Markups basierend auf den Schema.org-Schemas generiert. Jeder Schemata-Typ wird als separates Plugin implementiert. Dies ermöglicht eine modularere und erweiterbare Architektur. Jedes Plugin ist dafür verantwortlich, das Schema-Markup für einen bestimmten Inhaltstyp zu generieren, was mehr Flexibilität und Anpassungsoptionen erlaubt. Dadurch wird es Drittentwicklern erleichtert, zur Entwicklung der strukturierten Datenfunktionen von Joomla beizutragen.

Um zu beginnen, gehen Sie zu **System -> Plugins** und aktivieren Sie das *System - Schema.org* Plugin. Wenn dieses Plugin nicht aktiviert ist, wird es keine Schema-Registerkarte in einem Beitragsbearbeitungsformular geben, selbst wenn alle einzelnen Plugins aktiviert sind.

![List of schema plugins](../../../en/images/schemas/introduction-to-schema-org/01-schema-plugins-list.png)

### System Bearbeiten - Schema.org Plugin

- **Grundtyp** Wählen Sie, ob Ihre Website eine Organisation oder eine Einzelperson repräsentiert.
- **Name** Geben Sie den Namen der Organisation oder Person ein, die die Website repräsentiert.
- **Bild** Fügen Sie Ihr Unternehmens- oder persönliches Bild hinzu
- **Social-Media-Konten** Fügen Sie Ihre Unternehmens- oder persönlichen Social-Media-Konten hinzu. Wählen Sie das grüne Pluszeichen, um Zeilen zum Formular hinzuzufügen.
- Wählen Sie **Speichern & Schließen**.

![edit system schema org plugin](../../../en/images/schemas/introduction-to-schema-org/02-edit-system-schema-org-plugin.png)

### Einen Beitrag bearbeiten

Gehe zu einem deiner Beiträge und fülle die Schema-Formularfelder aus. Wenn der *Schema-Typ* auf *Keine* gesetzt ist, die Standardeinstellung, gibt es keine Felder zum Ausfüllen. Wähle ein beliebiges Schema, um eine Liste von Feldern zu sehen, die für dieses Schema geeignet sind. Der folgende Screenshot zeigt einen Beitrag mit dem gewählten Artikel-Schema:

![edit article scheme form](../../../en/images/schemas/introduction-to-schema-org/03-schema-form-in-an-article.png)

### Ausgabe

Sie werden auf der Webseite nichts mit dem Schema sehen. Wenn Sie jedoch den Seitenquelltext ansehen, sehen Sie einen Skripteintrag, wie im folgenden Beispiel:

```json
	<script type="application/ld+json">{
    "@context": "https://schema.org",
    "@graph": [
        {
            "@type": "Organization",
            "@id": "http://localhost/jcms-testing/#/schema/Organization/base",
            "name": "Joomla Documentation Team",
            "url": "http://localhost/jcms-testing/"
        },
        {
            "@type": "WebSite",
            "@id": "http://localhost/jcms-testing/#/schema/WebSite/base",
            "url": "http://localhost/jcms-testing/",
            "name": "JCMS Testing",
            "publisher": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            }
        },
        {
            "@type": "WebPage",
            "@id": "http://localhost/jcms-testing/#/schema/WebPage/base",
            "url": "http://localhost/jcms-testing/index.php/en/article-en-gb",
            "name": "Article (en-gb)",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebSite/base"
            },
            "about": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            },
            "inLanguage": "en-GB",
            "breadcrumb": {
                "@id": "http://localhost/jcms-testing/#/schema/BreadcrumbList/139"
            }
        },
        {
            "@type": "Article",
            "headline": "Article Schema Test",
            "description": "Latin text used to simulate layouts.",
            "author": {
                "@type": "person",
                "name": "Superman"
            },
            "@id": "http://localhost/jcms-testing/#/schema/com_content/article/1",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebPage/base"
            }
        }
    ]
}</script>
```

Du kannst deine strukturierten Daten über die Google-Seite [Test your structured data page](https://developers.google.com/search/docs/appearance/structured-data) testen.

## Verfügbare Plugins

| Plugin | Beschreibung |
|--------|-------------|
| Beiträge Plugin | Der Ausgangspunkt für die Nutzung von schema.org |
| Blogposting Plugin | Für Blogbeitragsinhalte |
| Buch Plugin | Für Buchinhalte |
| Benutzerdefiniertes Plugin | Für die direkte Eingabe von JSON-LD-Code |
| Event Plugin | Für Veranstaltungsinhalte |
| JobPosting Plugin | Für Jobanzeigeinhalte |
| Organisations-Plugin | Für Unternehmens- und Organisationsinhalte |
| Personen-Plugin | Für Personeninhalte |
| Rezept-Plugin | Für Rezeptinhalte |

*Übersetzt von openai.com*

