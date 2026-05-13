<!--
{
  "source": "https://docs.joomla.org/Localhost",
  "title": "Schema.org - Benutzerdefiniert ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das benutzerdefinierte Schema-Plugin wird verwendet, um benutzerdefinierte Informationen im Rohformat JSON-LD einzugeben. Es ist kein Schema-Org-Typ.

Öffnen Sie ein Beitragsbearbeitungsformular und wählen Sie die Registerkarte Schema, um einen Schematyp auszuwählen und die Daten für diesen Typ festzulegen. Wenn ein Schematyp nicht in der Liste vorhanden ist, kann sein Plugin deaktiviert sein. Die in jedes Feld einzugebenden Werte sind größtenteils selbsterklärend.

Dies ist ein Beispiel für ein handgefertigtes Rich Snippet:

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Your Article Title",
  "description": "A brief description of the article.",
  "timeRequired": "PT5M"
}
```

Die *timeRequired*-Eigenschaft repräsentiert die geschätzte Lesezeit im ISO 8601-Dauerformat. In diesem Fall bedeutet PT5M *5 Minuten*.

## Beispiel-Screenshot

Unten steht ein Beispiel für ein benutzerdefiniertes Schemafeld in einem Beitragsbearbeitungsformular.

![A custom schema edit form](../../../en/images/schemas/custom/01-edit-schema-custom.png)

*Übersetzt von openai.com*

