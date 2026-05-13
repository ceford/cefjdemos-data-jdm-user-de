<!--
{
  "source": "https://docs.joomla.org/J5.x:Schema_org",
  "title": "Schema.org - BlogPosting ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Der Schema-Typ BlogPosting ist für Beiträge gedacht, die für einen Blog erstellt wurden, um Suchmaschinen zu helfen, den Blogbeitrag besser zu verstehen und relevante Informationen anzuzeigen. Weitere Informationen finden Sie im Schema Org [BlogPosting schema type](https://schema.org/BlogPosting). Es gibt einen separaten [Blog schema type](https://schema.org/Blog) für Blog-Websites, aber dieser ist in Joomla noch nicht implementiert.

Das Schema liefert Suchmaschinen Informationen wie:

- Bild: Das Hauptbild des Beitrags
- Überschrift: Der Titel des Beitrags
- Beschreibung: Eine kurze Beschreibung des Beitrags
- Autor
    - Typ: Auswahl zwischen Organisation oder Person
    - Name: Der Name der Organisation oder Person, die den Beitrag verfasst hat
    - URL: Die Webadresse der Organisation oder der Person, die den Beitrag verfasst hat
    - E-Mail: Die E-Mail-Adresse der Organisation oder der Person, die den Beitrag verfasst hat
    - Adresse
        - Ort: Die Stadt, Provinz, der Ort für die Organisation oder Person, die den Beitrag verfasst hat
        - Postleitzahl: Die Postleitzahl für die Organisation oder Person, die den Beitrag verfasst hat
        - Straßenadresse: Die Straßenadresse für die Organisation oder Person, die den Beitrag verfasst hat
- Veröffentlichungsdatum: Das Datum, an dem der Beitrag veröffentlicht wurde, der den Beitrag verfasst hat
- Änderungsdatum: Das Datum, an dem der Beitrag geändert wurde, der den Beitrag verfasst hat
- Allgemeines Feld: Wird verwendet, um benutzerdefinierte Eigenschaften zu definieren, die im Standardformular nicht definiert sind

Öffnen Sie ein Beitragsbearbeitungsformular und wählen Sie die Registerkarte Schema, um einen Schematyp auszuwählen und die Daten für diesen Typ festzulegen. Wenn ein Schematyp nicht in der Liste vorhanden ist, kann sein Plugin deaktiviert sein. Die Werte, die in jedes Feld eingegeben werden müssen, sind größtenteils selbsterklärend.

Der Abschnitt *Generisches Feld* ermöglicht das Eingeben von *Titel*- und *Wert*-Paaren zusätzlich zu den Standardfeldern.

## Beispiel-Screenshot

Nachfolgend ein Beispiel eines BlogPosting-Schemas in einem Beitragsbearbeitungsformular.

![A blogposting schema edit form](../../../en/images/schemas/blogposting/01-edit-schema-blogposting.png)

*Übersetzt von openai.com*

