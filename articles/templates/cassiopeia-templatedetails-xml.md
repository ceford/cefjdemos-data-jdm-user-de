<!--
{
  "source": "https://docs.joomla.org/J4.x:Cassiopeia_templateDetails.xml",
  "title": "Cassiopeia templateDetails.xml  ",
  "description": "", 
  "author": ""
}
-->

## Standort und Zweck

Sie können ein Beispiel einer `templateDetails.xml`-Datei unter **System → Site Templates → Cassiopeia Details und Dateien** einsehen. Sie können sie dort auch bearbeiten, wenn Sie gute Gründe dafür haben. Andernfalls lassen Sie sie besser unverändert! Jedes Template hat eine solche Datei und ein untergeordnetes Template besteht anfänglich aus einer Dateistruktur, die nur aus dieser einen Datei besteht.

Die `templateDetails.xml`-Datei enthält die Daten, die Joomla! benötigt, um das Template zu verwalten und anzuzeigen. Dazu gehören Meta-Daten, die Informationen über das Template liefern, die Speicherorte der Ordner und Dateien, die Template-Modulpositionen und die vom Benutzer auswählbaren Konfigurationsoptionen. Der Inhalt der `templateDetails.xml`-Datei wird von Template zu Template unterschiedlich sein.

## Cassiopeia templateDetails.xml

Dateien im XML-Format haben eine wohl definierte Struktur. Eine XML-Datei muss die korrekte Syntax haben, sonst funktioniert sie nicht!

### XML-Format

Die erste Zeile jeder `templateDetails.xml` muss mit der XML-Doctype-Definition beginnen.

Die nächste Zeile teilt Joomla! mit, dass die Daten in dieser Datei für eine Website-Vorlagenerweiterung bestimmt sind. Alle Vorlagendaten sind innerhalb der öffnenden und schließenden Tags enthalten.

```xml
<extension type="template" client="site">
...
</extension>
```

### Metadaten

Der erste Abschnitt der Vorlagendaten definiert normalerweise die Vorlageninformationen, zum Beispiel: Namen, Daten, Kontaktinformationen, Urheberrechte, Versionsnummer und Beschreibung.

```xml
<extension version="3.1" type="template" client="site">
    <name>cassiopeia</name>
    <version>1.0</version>
    <creationDate>2017-02</creationDate>
    <author>Joomla! Project</author>
    <authorEmail>admin@joomla.org</authorEmail>
    <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
    <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
    <inheritable>1</inheritable>
```

Beachten Sie, dass eine Vorlage, die untergeordnete Vorlagen haben kann, den Inherit-Wert auf 1 gesetzt hat. Untergeordnete Vorlagen haben diesen Wert auf 0 gesetzt. Diese Daten werden in der Ansicht "Templates: Vorlagen (Site)" verwendet, wie unten gezeigt.

![site templates list](../../../en/images/templates/cassiopeia-templatedetails-xml/01-templates-list.png)

Die Beschreibung enthält einen Sprachschlüssel und nicht den tatsächlichen Beschreibungstext. Der Schlüssel wird zur Laufzeit durch den Text ersetzt, der aus einer Sprachdatei abgerufen wird. Die Sprachdateien sind im Sprachabschnitt von `templateDetails.xml` definiert.

![templates edit style form](../../../en/images/templates/cassiopeia-templatedetails-xml/02-templates-edit-style.png)

### Ordner und Dateien

Ordner und Dateien für die Cassiopeia-Vorlage werden an zwei verschiedenen Orten gespeichert. Die PHP- und zugehörigen Dateien werden im Ordner site/templates gespeichert. Die Mediendateien (CSS, Bilder, JS und SCSS) werden im Ordner site/media gespeichert. Diese Speicherorte sind in der XML-Datei wie folgt definiert:

```xml
    <files>
        <filename>component.php</filename>
        <filename>error.php</filename>
        <filename>index.php</filename>
        <filename>joomla.asset.json</filename>
        <filename>offline.php</filename>
        <filename>templateDetails.xml</filename>
        <folder>html</folder>
    </files>
    <media destination="templates/site/cassiopeia" folder="media">
        <folder>js</folder>
        <folder>css</folder>
        <folder>scss</folder>
        <folder>images</folder>
    </media>
```

Dies ist das Muster, das in allen modernen Joomla 4 und 5 Vorlagen zu sehen ist. Die Struktur kann in der Ansicht "Templates: Anpassen (Cassiopeia)" gesehen werden:

![templates customise cassiopeia page](../../../en/images/templates/cassiopeia-templatedetails-xml/03-templates-customise-cassiopeia.png)

### Modulpositionen

Die verfügbaren Modulpositionen sind wie folgt definiert:

```xml
    <positions>
        <position>topbar</position>
        <position>below-top</position>
        <position>menu</position>
        <position>search</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
```

Jedes Tag erstellt eine Modulposition, die in der Positionsliste eines Modul-Bearbeitungsformulars verfügbar ist. Das einfache Format der Positionsliste bedeutet, dass es leicht angepasst werden kann. Zum Beispiel, um eine neue Modulposition zur Liste **in einer untergeordneten Vorlage** hinzuzufügen, fügen Sie einfach ein neues Tag innerhalb des Tags mit einem einzigartigen Namen ein, wobei alle Kleinbuchstaben ohne Leerzeichen verwendet werden. Beachten Sie, dass dies nur die Position zu Modulbearbeitungsformularen hinzufügt und zusätzliche Entwicklungen in anderen Vorlagendateien erforderlich sind, um die neue Position im Frontend anzuzeigen.

Cassiopeia hat genügend Vorlagenpositionen! Wenn Sie denken, dass Sie eine zusätzliche benötigen, liegen Sie wahrscheinlich falsch. Denken Sie daran, dass jedem Modul eine beliebige Anzahl von Modulen zugewiesen werden kann und sie auf der Modulseitenliste in Reihenfolge sortiert werden können. Verfügbare Positionen:

![Cassiopeia template positions diagram](../../../en/images/templates/cassiopeia-templatedetails-xml/04-cassiopeia-template-positions.png)

Sie können auch die Modulpositionen in jeder Vorlage sehen: Gehen Sie zu **System → Site Templates** und wählen Sie die Schaltfläche "Optionen" in der Symbolleiste. Stellen Sie im Optionsformular das Feld "Vorschau Modulpositionen" auf "Aktiviert". Speichern und schließen Sie. Gehen Sie zu Ihrer Website und fügen Sie ?tp=1 an das Ende einer URL hinzu (oder &tp=1, wenn bereits ein ? in der URL ist). Joomla wird alle verfügbaren Vorlagenpositionen anzeigen, auch diejenigen, die nicht verwendet wurden:

![Cassiopeia template positions](../../../en/images/templates/cassiopeia-templatedetails-xml/05-templates-template-positions-by-tp.png)

### Sprachen

Sprachdateien ermöglichen die Übersetzung von statischem Text in der Vorlage. Die Datei tpl_cassiopeia.ini enthält Schlüssel zu Textübersetzungen für Text, der vom Benutzer gesehen wird. Die Datei tpl_cassiopeia.sys.ini enthält Schlüssel zu Textübersetzungen für Text, der vom Administrator gesehen wird.

```xml
    <languages folder="language">
        <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
        <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
    </languages>
```

Die Sprachdateien für die standardmäßige englische GB-Sprache werden in site/language/en-GB/ gespeichert. Andere Sprachen würden ähnlich in Dateien mit dem entsprechenden ISO-Sprachcode gespeichert werden, zum Beispiel fr-FR für Französisch in Frankreich oder de-DE für Deutsch in Deutschland (was sich von Schweizer Deutsch und Österreichischem Deutsch unterscheiden könnte).

### Optionen

Eine Vorlage kann Anzeigeoptionen bieten, die vom Administrator im Formular "Vorlage: Stil bearbeiten" gewählt werden können. Zum Beispiel ermöglicht die Registerkarte "Erweitert" der Cassiopeia-Vorlage einem Administrator, die Marke zu ändern, ein Logo hinzuzufügen, ein Schriftartenschema auszuwählen und mehr.

![templates edit style form advanced tab](../../../en/images/templates/cassiopeia-templatedetails-xml/06-templates-edit-style-advanced.png)

Die Vorlagenoptionen sind innerhalb einer Struktur definiert, die Felder innerhalb von Fieldsets erstellt. Jedes Fieldset erscheint als Registerkarte im Bearbeitungsformular. Dies ist die Struktur, die die Registerkarte "Erweitert" oben erstellt.

```xml
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>
                ...
            </fieldset>
        </fields>
    </config>
```

Einzelne Optionen werden mit dem `<field>` Tag definiert. Jedes `<fieldset>`, und jeder `<field>` Parameter innerhalb eines `<fieldset>`, erfordert einen eindeutigen Namen, der durch ein **name** Attribut definiert ist. Dieser Name definiert den Parameter selbst und wird verwendet, um Einstellungen an die Frontend-Dateien zu übergeben. Jeder Parameter enthält auch ein **label** Attribut und ein **description** Attribut. Der Bezeichnungstext erscheint zusammen mit dem Parameter im Einstellungsbildschirm, um zu identifizieren, wofür die Einstellung verwendet wird, und detailliertere Informationen können in der Beschreibung enthalten sein.

Ein Parameterfeld kann praktisch jede Art von Formulareingabe mit entsprechenden Optionen sein. Dies wird durch das **type** Attribut ausgewählt. Alle notwendigen Optionen, wie z. B. Radiobutton- oder Auswahlmöglichkeiten, sind in `<option>` Tags definiert. CSS-Klassennamen können mit dem **class** Attribut definiert werden und ein Standardwert kann mit dem **default** Attribut definiert werden.

Unten sind die Optionsdefinitionen in der Standard-Cassiopeia-Vorlage. In diesem Beispiel verwenden alle Bezeichnungen, Beschreibungen und Optionen Sprachzeichendefinitionen aus den in den vorherigen Abschnitten definierten Sprachdateien sowie einige aus dem Joomla-Core, sodass sie bei Bedarf in verschiedene Sprachen übersetzt werden können.

```xml
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="logoFile"
                    type="media"
                    default=""
                    label="TPL_CASSIOPEIA_LOGO_LABEL"
                    showon="brand:1"
                />

                <field
                    name="siteTitle"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TITLE"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="siteDescription"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TAGLINE_LABEL"
                    description="TPL_CASSIOPEIA_TAGLINE_DESC"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="useFontScheme"
                    type="groupedlist"
                    label="TPL_CASSIOPEIA_FONT_LABEL"
                    default="0"
                    >
                    <option value="0">JNONE</option>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
                        <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (lokal)</option>
                    </group>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
                        <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
                        <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
                    </group>
                </field>

                <field
                    name="noteFontScheme"
                    type="note"
                    description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
                    class="alert alert-warning"
                />

                <field
                    name="colorName"
                    type="filelist"
                    label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
                    default="colors_standard"
                    fileFilter="^custom.+[^min]\.css$"
                    exclude="^colors.+"
                    stripext="true"
                    hide_none="true"
                    hide_default="true"
                    directory="media/templates/site/cassiopeia/css/global/"
                    validate="options"
                    >
                    <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
                    <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
                </field>

                <field
                    name="fluidContainer"
                    type="radio"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    label="TPL_CASSIOPEIA_FLUID_LABEL"
                    >
                    <option value="0">TPL_CASSIOPEIA_STATIC</option>
                    <option value="1">TPL_CASSIOPEIA_FLUID</option>
                </field>

                <field
                    name="stickyHeader"
                    type="radio"
                    label="TPL_CASSIOPEIA_STICKY_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="backTop"
                    type="radio"
                    label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>
            </fieldset>
        </fields>
    </config>
```

In diesem Beispiel schließt das `<fieldset name="advanced">` Tag alle Parameter ein und verwendet das **name** Attribut, um die *Erweitert* Registerkarte in der Schnittstelle zu erstellen. Alles, was nötig ist, um eine weitere Registerkarte in der Schnittstelle zu erstellen, ist ein weiteres `<fieldset>` Tag mit einem anderen **name** Attribut. Mit diesem Wissen ist es relativ einfach, so viele zusätzliche Registerkarten und Parameter in einer Vorlage zu erstellen, wie nötig.

Eine potenzielle Verwendung von zusätzlichen Parametern ist in Overrides oder Layouts für entweder Eltern- oder Kindvorlagen.

## Zusammenfassung

Dies ist die templateDetails.xml-Datei, die von Cassiopeia verwendet wird:

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension type="template" client="site">
    <name>cassiopeia</name>
    <version>1.0</version>
    <creationDate>2017-02</creationDate>
    <author>Joomla! Projekt</author>
    <authorEmail>admin@joomla.org</authorEmail>
    <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
    <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
    <inheritable>1</inheritable>
    <files>
        <filename>component.php</filename>
        <filename>error.php</filename>
        <filename>index.php</filename>
        <filename>joomla.asset.json</filename>
        <filename>offline.php</filename>
        <filename>templateDetails.xml</filename>
        <folder>html</folder>
    </files>
    <media destination="templates/site/cassiopeia" folder="media">
        <folder>js</folder>
        <folder>css</folder>
        <folder>scss</folder>
        <folder>images</folder>
    </media>
    <positions>
        <position>topbar</position>
        <position>below-top</position>
        <position>menu</position>
        <position>search</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
    <languages folder="language">
        <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
        <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
    </languages>
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNEIN</option>
                    <option value="1">JJA</option>
                </field>

                <field
                    name="logoFile"
                    type="media"
                    default=""
                    label="TPL_CASSIOPEIA_LOGO_LABEL"
                    showon="brand:1"
                />

                <field
                    name="siteTitle"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TITLE"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="siteDescription"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TAGLINE_LABEL"
                    description="TPL_CASSIOPEIA_TAGLINE_DESC"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="useFontScheme"
                    type="groupedlist"
                    label="TPL_CASSIOPEIA_FONT_LABEL"
                    default="0"
                    >
                    <option value="0">JKEIN</option>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
                        <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (lokal)</option>
                    </group>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
                        <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
                        <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
                    </group>
                </field>

                <field
                    name="noteFontScheme"
                    type="note"
                    description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
                    class="alert alert-warning"
                />

                <field
                    name="colorName"
                    type="filelist"
                    label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
                    default="colors_standard"
                    fileFilter="^custom.+[^min]\.css$"
                    exclude="^colors.+"
                    stripext="true"
                    hide_none="true"
                    hide_default="true"
                    directory="media/templates/site/cassiopeia/css/global/"
                    validate="options"
                    >
                    <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
                    <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
                </field>

                <field
                    name="fluidContainer"
                    type="radio"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    label="TPL_CASSIOPEIA_FLUID_LABEL"
                    >
                    <option value="0">TPL_CASSIOPEIA_STATIC</option>
                    <option value="1">TPL_CASSIOPEIA_FLUID</option>
                </field>

                <field
                    name="stickyHeader"
                    type="radio"
                    label="TPL_CASSIOPEIA_STICKY_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNEIN</option>
                    <option value="1">JJA</option>
                </field>

                <field
                    name="backTop"
                    type="radio"
                    label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNEIN</option>
                    <option value="1">JJA</option>
                </field>
            </fieldset>
        </fields>
    </config>
</extension>
```

*Übersetzt von openai.com*
