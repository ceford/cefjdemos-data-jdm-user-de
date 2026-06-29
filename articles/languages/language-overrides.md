<!--
{
  "source": "https://docs.joomla.org/J4.x:Language_Overrides",
  "title": "Sprachüberschreibungen ",
  "description": "", 
  "author": ""
}
-->

## Speicherorte der Sprachdateien

Die meisten Joomla!-Sprachdateien befinden sich in Sprachordnern: einer im Stammverzeichnis der Website und ein weiterer im Administrator-Ordner. Jede Sprache hat ihr eigenes Unterverzeichnis, basierend auf den sprachlichen Codes des RFC3066-Standards. Jede Erweiterung speichert ihre Übersetzungen mit einem Namen, der sich aus dem Namen der Erweiterung ableitet. Einige Beispiele:

    siteroot/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.sys.ini

Die Dateien enthalten Zeilen, die aus einem Schlüssel und seiner Übersetzung bestehen:

    COM_CONTENT="Beiträge"
    COM_CONTENT_ADD_NEW_MENU_ITEM="Neuer Menüpunkt"
    COM_CONTENT_ARTICLE_CONTENT="Inhalt"
    COM_CONTENT_ARTICLES_TABLE_CAPTION="Tabelle der Beiträge"
    COM_CONTENT_ARTICLES_TITLE="Beiträge"

Der Joomla!-PHP-Code verwendet den Schlüssel. Dieser wird zur Laufzeit durch die Textübersetzung ersetzt. Die .ini-Datei enthält Übersetzungen, die von der Erweiterung verwendet werden. Die sys.ini-Dateien enthalten Übersetzungen, die Joomla! zur Verwaltung der Erweiterung verwendet. In einer Sprachdatei können Hunderte von Zeilen enthalten sein.

Drittanbieter-Erweiterungen wird empfohlen, ihre Sprachdateien in den Sprachordnern innerhalb der Erweiterung zu speichern. So sind sie vor dem Löschen sicher, falls ein Administrator entscheiden sollte, eine Sprache zu deinstallieren. Beispiel:

    siteroot/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.sys.ini

**Bearbeiten Sie niemals eine Joomla!-Kern- oder Drittanbieter-Sprachdatei! Alle von Ihnen vorgenommenen Änderungen gehen beim nächsten Update verloren. Wenn Sie die Formulierung eines Sprachelements ändern möchten, verwenden Sie die formale Sprach-Override-Komponente.**

Sprach-Overrides sind Ihre Ersetzungen für Kern- oder Erweiterungsübersetzungen. Dabei handelt es sich um einzelne Übersetzungen, ein oder zwei, nicht um eine ganze Datei! Die Sprach-Overrides für eine bestimmte Sprache werden alle in einer Datei gespeichert:

    siteroot/language/overrides/en-GB.override.ini
    siteroot/language/overrides/fr-FR.override.ini
    siteroot/language/overrides/de-DE.override.ini

    siteroot/administrator/language/overrides/en-GB.override.ini
    siteroot/administrator/language/overrides/fr-FR.override.ini
    siteroot/administrator/language/overrides/de-DE.override.ini

### Lade-Reihenfolge der Sprachen

Beim Laden jeder Seite werden zuerst die en-GB-Sprachübersetzungen geladen. Dies stellt sicher, dass keine Schlüssel für die Benutzer der Website sichtbar sind. Wenn eine andere Sprache verwendet wird, werden die Übersetzungen für diese Sprache als nächstes geladen, wodurch die en-GB-Übersetzungen ersetzt werden. Andere Sprachen hinken bei der Erstellung von Übersetzungen oft hinterher, sodass Benutzer gelegentlich Wörter oder Phrasen in Englisch neben denen ihrer eigenen Sprache sehen können.

Schließlich werden Übersetzungen aus der Sprach-Override-Datei geladen. Dies ermöglicht es der Website, alternative Wörter oder Phrasen zu verwenden, die lokalen Gegebenheiten besser entsprechen.

## Sprachüberschreibungen

Gelegentlich möchten Sie einen einzelnen übersetzten Spracheintrag durch etwas ersetzen, das besser zu den örtlichen Gegebenheiten passt. Ein häufiges Szenario ist, wenn Sie eine Vorlagenüberschreibung oder ein Layout erstellen und etwas Inhalt hinzufügen möchten, der einen neuen Sprachschlüssel verwendet. Das folgende Beispiel veranschaulicht einen Fall, bei dem dem Logout-Layout des Login-Moduls, beschrieben in dem Beitrag über Vorlagenlayouts, etwas Text hinzugefügt wurde. Das alternative Layout hat diesen Code:

```html
<p class="text-center">
Ihre Sitzung wird um <br><?php echo $endTime; ?> ablaufen
</p>
```

Für eine mehrsprachige Seite in Englisch, Französisch und Deutsch muss der Code geändert werden:

```html
<p class="text-center">
<?php echo Text::_('TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT')?><br><?php echo $endTime; ?>
</p>
```

Hinweis: Wenn Sie das Tutorial zum Vorlagenlayout verfolgt haben, haben Sie möglicherweise bereits einen Schlüssel TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES, der als „Läuft ab“ übersetzt wird. Dieser wird jedoch in siteroot/administrator/language/overrides verwendet.

Der neue Schlüssel kann nun in jede Sprache übersetzt werden. Die Übersetzungen werden in siteroot/language/overrides gespeichert.

- Wählen Sie **System **→** Verwaltungspanel **→** Sprachüberschreibungen**
- Wählen Sie Ihre Sprache und den Standort der Website.
- Wählen Sie die **Neu**-Schaltfläche und füllen Sie das Formular aus. In diesem Beispiel ist der Sprachschlüssel **TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT** und der Text könnte sein **Ihre Sitzung wird um ablaufen**
- Speichern & Schließen Sie das Formular.
- Wiederholen Sie den Übersetzungsprozess für jede Sprache.

![Formular zur Bearbeitung von Sprachüberschreibungen](../../../en/images/languages/language-overrides/01-language-overrides-edit.png)

Abschließend überprüfen Sie, ob die Übersetzung implementiert wurde.

![Ergebnis der Überschreibung im Anmeldeformular der Website](../../../en/images/languages/language-overrides/02-language-overrides-custom-logout.png)

*Übersetzt von openai.com*

