<!--
{
  "source": "https://docs.joomla.org/J4.x:Template_Layouts",
  "title": "Vorlagenlayouts ",
  "description": "", 
  "author": ""
}
-->

## Struktur der Layout-Dateien

In einem **Template** legt jede Erweiterung, die HTML-Ausgabe generiert, den Ausgabe-Code in einer Template-Datei innerhalb der Erweiterungsstruktur ab, oft in einem Ordner namens tmpl. Einige Beispiele:

- /modules/mod_login/tmpl/default.php
- /modules/mod_login/tmpl/default_logout.php
- /components/com_content/tmpl/beitrag/default.php
- /plugins/content/vote/tmpl/vote.php

Bei einem **Template-Override** wird eine Datei mit demselben Namen innerhalb der Template-Dateistruktur erstellt, die anstelle der Datei in der Erweiterungsstruktur verwendet wird. Entsprechende Beispiele:

- /templates/cassiopeia/html/mod_login/default.php
- /templates/cassiopeia/html/mod_login/default_logout.php
- /templates/cassiopeia/html/com_content/beitrag/default.php
- /templates/cassiopeia/html/plg_content_vote/vote.php

Dies ermöglicht es Ihnen, die Ausgabe nach Ihren Bedürfnissen anzupassen. Allerdings haben Sie nicht die Option, zu wählen, ob Sie Ihr Override verwenden möchten oder nicht. Es wird immer verwendet.

In einem **alternativen Template-Layout** erstellen Sie eine Datei mit einem anderen Namen als dem Original, aber im selben Template-Ordner. Der neue Name darf kein Unterstrich-Zeichen enthalten. Sie erstellen auch jede Datei, die den ersten Teil des ursprünglichen Namens teilt. Ein Beispiel:

- /templates/cassiopeia/html/mod_login/expires.php
- /templates/cassiopeia/html/mod_login/expires_logout.php

Dann wird es möglich, zu wählen, ob das originale Standardlayout oder das alternative Layout verwendet werden soll. Die Wahl erfolgt im Bearbeitungsformular des Moduls oder der Komponenten (Registerkarte Erweitert für Module, Registerkarte Optionen für Beiträge). Beachten Sie, dass nicht alle Erweiterungen entweder Overrides oder alternative Layouts erlauben.

**Achtung:** Plugins bieten keinen Mechanismus zur Auswahl alternativer Layouts.

## Modul Alternativlayouts

Ein alternatives Layout für ein Modul zu erstellen, ist ähnlich wie das Erstellen einer Template-Override für ein Modul. In beiden Fällen erstellen Sie einen Ordner namens `templates/.../html/`. Zum Beispiel wäre der Ordner für eine „mod_login“-Template-Override oder ein alternatives Layout für das Cassiopeia-Template `templates/cassiopeia/html/mod_login/`.

Es gibt zwei wichtige Unterschiede zwischen einer Template-Override und einem alternativen Layout. Der erste ist der Dateiname. Für die Template-Override würden Sie die Datei `default.php` nennen, um den Core-Dateinamen zu übernehmen. Für ein alternatives Layout verwenden Sie einen anderen Namen. Die einzige Regel ist, dass **der Dateiname keine Unterstriche enthalten sollte**.

Der zweite wichtige Unterschied ist, dass, im Gegensatz zu Template-Override-Dateien, die automatisch verwendet werden, wann immer das Modul mit dem Override-Template angezeigt wird, eine alternative Layoutdatei nur verwendet wird, wenn Sie sie als Parameter in den Modulparameter-Einstellungen auswählen.

### Ein praktisches Beispiel - mod_login

- Gehen Sie zu **System** → **Site Templates** → **Cassiopeia Details und Dateien**.
- Wählen Sie die Registerkarte **Create Overrides**.
- Wählen Sie aus der Modulliste das Element **mod_login**.
- Im Register **Editor** wählen Sie **html** → **mod_login**, um Ihre neu erstellten Kopien der mod_login-Ausgabetemplates zu sehen.
- Benennen Sie **default.php** um in etwas anderes ohne Unterstrich, in diesem Beispiel **expires.php**.
- Benennen Sie **default_logout.php** um in **expires_logout.php**.

Sie haben jetzt zwei Dateien mit exakt demselben Inhalt wie die Originale. Ändern Sie den Inhalt von expires_logout.php, um eine Nachricht hinzuzufügen, die den Benutzer darüber informiert, wann die Sitzung nach jedem Seitenaufruf ablaufen wird.

Fügen Sie in Zeile 16 direkt unter den vorhandenen use-Befehlen Folgendes hinzu:

```php
use Joomla\CMS\Factory;

date_default_timezone_set('Europe/London');
$config = Factory::getContainer()->get('config');
$lifetime = $config->get('lifetime', 0);
$time = time() + $lifetime * 60;
$endTime = date('H:i:s', $time); // time() gibt bereits eine Zeit in Sekunden zurück
```

Und fügen Sie in Zeile 36 direkt nach der Zeile mit einer endif-Bedingung diesen Code hinzu:

```html
<p class="text-center">
Ihre Sitzung läuft ab um <br><?php echo $endTime; ?>
</p>
```

Schließen Sie die Cassiopeia-Dateien. Wählen Sie **Beiträge** → **Site-Module** und öffnen Sie das Login-Modul. Im Reiter Erweitert, unter Layout finden Sie, dass Sie die Wahl haben zwischen **-- Vom Modul -- / Standard** und **-- Vom Cassiopeia Template -- / expires**.

![login module showing alternative layouts](../../../en/images/templates/template-layouts/01-layouts-module-login.png)

Eine Möglichkeit, diese Funktion zu verwenden, besteht darin, zwei Login-Formulare zu haben, eines mit öffentlichem Zugriff und das andere mit Zugriff für Super-Benutzer. Im letzteren Fall wählen Sie die Option **expires** und nur Super-Benutzer sehen die Erinnerung an die Sitzungsablaufzeit.

Es ist wichtig zu verstehen, dass, wenn es im Modulparameterbildschirm spezifiziert ist, eine alternative Layoutdatei für ein Modul für dieses Modul unabhängig davon verwendet wird, welches Template verwendet wird, um die Seite anzuzeigen, auf der das Modul gezeigt wird. Es liegt daher in der Verantwortung des Administrators sicherzustellen, dass die Layoutdatei in allen Templates, in denen dieses Modul angezeigt werden könnte, wie gewünscht funktioniert.

### Übersetzung

Sie können den Dateinamen mit Sprachüberschreibungen übersetzen. Versuchen Sie das folgende Verfahren:

- Wählen Sie **System** → **Verwaltungspanel** → **Sprachüberschreibungen**.
- Wählen Sie Ihre Sprache und den Administrator-Standort.
- Wählen Sie die Schaltfläche **Neu** und füllen Sie das Formular aus. In diesem Beispiel ist der Sprachschlüssel **TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES** und der Text könnte **Login / Logout mit Ablaufzeit** sein.
- Speichern und schließen Sie und kehren Sie zum Login-Modul-Formular zurück.

![languages edit override form](../../../en/images/templates/template-layouts/02-layouts-language-override-form.png)

Das Modullayout-Auswahlformularfeld mit **expires** übersetzt:

![module alternative layouts select](../../../en/images/templates/template-layouts/03-layouts-example-translated.png)

## Alternative Layouts für Komponenten

Alternative Layouts für Komponenten funktionieren ähnlich wie Modul-Layouts. Eine Datei wird in den gleichen Ordner gelegt, in dem Sie eine Template-Override-Datei platzieren würden. Zum Beispiel, um ein alternatives Layout für einen Beitrag für das Template "cassiopeia" zu erstellen, würden Sie eine Datei im Ordner `templates/cassiopeia/html/com_content/article/` ablegen. Wie bei Modul-Layouts darf die Datei nicht denselben Namen wie die Kern-Datei haben und keine Unterstriche im Namen enthalten. Zudem sollte es in diesem Ordner keine XML-Datei mit dem gleichen Namen geben. (Wir werden XML-Dateien weiter unten unter Menüpunkt-Alternative-Layouts besprechen.)

Sie können einen globalen Wert für Komponenten-Layouts im Optionsfenster der Komponente festlegen. Zum Beispiel gibt es im Fenster Artikel: Optionen einen Parameter *Wählen Sie ein Layout*, wie unten gezeigt:

![optionsformular für Beiträge mit Liste der alternativen Layouts](../../../en/images/templates/template-layouts/04-layouts-articles-options.png)

Wie bei Modul-Layouts werden die Komponenten-Layouts als Parameteroptionen im individuellen Komponenten-Bearbeitungsfenster angezeigt. Zum Beispiel erscheint bei einem Beitrag der Parameter im Reiter Beiträge: Bearbeitungsoptionen, wie unten gezeigt.

![Bearbeitungsformular für Beiträge mit Liste der alternativen Layouts](../../../en/images/templates/template-layouts/05-layout-article-edit.png)

Wie bei anderen Parametern, wird die Einstellung "Global verwenden" die Einstellung aus dem Optionsparameter übernehmen. Die Einstellung "Aus Komponenten-Standard" wird das Standardlayout der Komponente verwenden. Alternative Layouts, die Sie für verschiedene Templates erstellt haben, werden unter jeder Template-Überschrift angezeigt.

Dateinamen können übersetzt werden. Die folgende Zeile:
```ini
    TPL_CASSIOPEIA_COM_CONTENT_ARTICLE_LAYOUT_MYLAYOUT="Nur Titel Kein XML"
```
wird eine Datei namens "mylayout.php" als "Nur Titel Kein XML" übersetzen.

Sie können mehr als eine Datei für ein Layout haben. Die Anfangsdatei muss ohne Unterstriche benannt sein und alle zusätzlichen Dateien müssen Unterstriche haben.

Alternative Layouts für Komponenten können mit Beiträgen, Kontakten oder Newsfeeds verwendet werden.

Alternative Layouts für Komponenten werden nur verwendet, wenn zwei Bedingungen erfüllt sind: (1) sie sind in den Komponentenparametern angegeben und (2) es gibt keinen Menüpunkt für diese spezifische Komponente. Zum Beispiel, wenn Sie einen oder mehrere Menüpunkte des Typs "Einzelner Beitrag" für einen bestimmten Beitrag eingerichtet haben, wird das alternative Layout für diesen Beitrag nicht verwendet. Stattdessen wird das im Menüpunkt spezifizierte Layout verwendet. Dies ist konsistent mit der allgemeinen Funktionsweise der Komponentenparameter, bei der das spezifischste (in diesem Fall ein einzelner Beitrag-Menüpunkt) das weniger spezifische (in diesem Fall die Beitrag-Parameter) überschreibt.

## Kategoriale Alternative Layouts

Kategoriale alternative Layouts funktionieren wie Komponentenlayouts. Die Regeln zur Festlegung von Layoutdateien sind die gleichen. Der einzige Unterschied besteht darin, dass der Ordner der Kategorieordner und nicht der Komponentenordner ist. Ein alternatives Layout einer Kontaktkategorie für Cassiopeia würde beispielsweise in den Ordner `templates/cassiopeia/html/com_contact/category` gehen.

Sie können Kategorielayouts global im Optionsbildschirm jeder Komponente festlegen. Unten ist ein Beispiel aus den Kontakten: Optionen / Formular Kategorie:

![Kontakte-Komponenten-Optionsformular, das alternative Layouts zeigt](../../../en/images/templates/template-layouts/06-layouts-contacts-options.png)

Kategoriale alternative Layouts erscheinen, wenn Sie eine Kategorie im Formular Komponente: Kategorie bearbeiten / Optionen hinzufügen oder bearbeiten, wie unten gezeigt.

![Kontakte-Komponenten-Optionsformular, das alternative Layouts zeigt](../../../en/images/templates/template-layouts/07-layouts-contacts-category-options.png)

Kategoriale alternative Layouts können für Beiträge, Banner, Kontakte und Newsfeeds verwendet werden.

Wie bei Komponentenlayouts wird ein Kategorielayout nur verwendet, wenn:

1.  es in den globalen oder Kategorienparametern ausgewählt ist.
2.  es keinen Menüpunkt gibt, der speziell für die Kategorie vorgesehen ist.

Wenn ein Menüpunkt für eine bestimmte Kategorie eingerichtet ist, wird stattdessen das im Menü ausgewählte Layout anstelle des alternativen Kategorielayouts verwendet. 


## Beitragskategorie Blog und Liste

Für Beiträge stehen zwei grundlegende Kategorielayouts zur Verfügung: Blog und Liste. Jedes dieser Layouts erscheint im Formular Artikelformular: Optionen, Registerkarte Kategorie unter der Überschrift „Von Komponente“. Alternative Layouts erscheinen ebenfalls in der Liste, wodurch Blog- oder Listen- oder alternative Vorlagenlayouts als Standardkategorielayout entweder global oder beim Bearbeiten einer einzelnen Beitragskategorie ausgewählt werden können.

![Kontaktkomponente-Optionenformular mit alternativen Layouts](../../../en/images/templates/template-layouts/08-layouts-articles-options-category.png)

Das bedeutet, dass Sie, wie bei anderen Layoutoptionen, steuern können, ob Beitragskategorielinks Blog- oder Listenlayouts verwenden. Es ist wichtig zu verstehen, dass diese Option, wie bei anderen Layoutparametern, nur dann wirksam wird, wenn es kein Einzelkategorie-Menüelement für die Kategorie gibt.

## Alternative Menüelemente

Alternative Menüelemente haben einen wichtigen Unterschied zu den anderen. Um ein alternatives Layout für ein Menüelement zu erstellen, müssen Sie eine XML-Datei einfügen, deren Name mit der ursprünglichen Layout-Datei übereinstimmt. Um beispielsweise ein alternatives Menüelement namens "myarticle" für einen Beitrag im Cassiopeia-Template zu erstellen, würden Sie zwei Dateien im Ordner `templates/cassiopeia/html/com_content/article` mit den Namen `myarticle.php` und `myarticle.xml` erstellen. Wenn Sie weitere Layout-Dateien einfügen möchten, müssten Sie diese Dateien mit Unterstrichen im Dateinamen hinzufügen.

Die XML-Datei verwendet dasselbe Format wie die Kern-Menüelement-XML-Dateien. Dies ermöglicht nicht nur die Erstellung eines benutzerdefinierten Layouts für dieses Menüelement, sondern auch die Erstellung angepasster Parameter. Beispielsweise könnten Sie einige Parameter ausblenden oder neue Parameter hinzufügen.

Alternative Menüelemente werden angezeigt, wenn Sie einen Menüelementtyp auswählen, wie unten gezeigt.

![Menüelement-Auswahlliste](../../../en/images/templates/template-layouts/09-layouts-menu-blog-menu-creation.png)

Alternative Menüelemente werden verwendet und funktionieren auf dieselbe Weise wie Standard-Menüelemente. Da sie bereits auf benutzerdefinierten Layouts basieren, gelten Template-Overrides nicht für alternative Menüelemente.

Wie oben angegeben, haben Menüelement-Layouts Vorrang vor Komponenten- oder Kategorien-Alternativlayouts.

Die Übersetzung von alternativen Menüelementen erfolgt mit den folgenden Tags in den XML-Dateien. Das Format ist `"TPL_"<Template-Name>_<Komponente>_<Ansicht>_<Menüelement-Name>_<Tag-Typ>`. Zum Beispiel werden diese Zeilen unten den Titel, die Option und die Beschreibung für ein alternatives Menüelement namens "catmenuitem" übersetzen.
```
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE="cassiopeia Benutzerdefiniertes Kategorie-Layout"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION="cassiopeia Benutzerdefiniert"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC="Beschreibung für das benutzerdefinierte cassiopeia-Kategorie-Layout."
```
Diese Zeichenfolgen müssen zu
`administrator/language/overrides/en-GB.override.ini` hinzugefügt werden, aber Sie können das oben beschriebene Sprachüberschreibeformular verwenden.

Das catmenuitem.xml würde mit folgendem beginnen:

```xml
<?xml version="1.0" encoding="utf-8"?>
<metadata>
   <layout title="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE" option="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION">
      <help
         key = "JHELP_MENUS_MENU_ITEM_ARTICLE_SINGLE_ARTICLE"
      />
      <message>
         <![CDATA[TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC]]>
      </message>
   </layout>
```

## Steuerung der Vorlage für alternative Menüelemente

Wie oben besprochen, macht das Vorhandensein einer XML-Datei ein alternatives Layout zu einem Menüelement. Das Format der XML-Datei entspricht dem Format der XML-Dateien für Kern-Menüelemente. Mit dieser XML-Datei können Sie die Parameter hinzufügen, die Sie für dieses Menüelement einschließen möchten. Diese können die gleichen wie bei einem der Kern-Menüelemente sein, oder Sie können Kern-Parameter weglassen oder neue hinzufügen. Beachten Sie, dass, wenn Sie neue Parameter hinzufügen, diese zwar in der Layout-Datei verwendet, jedoch nicht in den Kernmodell- oder Ansichtsdateien verwendet werden.

Es ist auch möglich, Parameter-Einstellungen für Kern-Parameter zu überschreiben. Ein Beispiel hierfür ist die Steuerung, mit welchen Vorlagen ein alternatives Menüelement-Layout angezeigt werden kann. In einigen Fällen möchten Sie möglicherweise erlauben, dass ein benutzerdefiniertes Menüelement mit jeder Vorlage der Website angezeigt wird. In anderen Fällen möchten Sie das Layout des Menüelements auf eine bestimmte Vorlage beschränken. In dieser Situation würden Sie einfach den folgenden Parameter zur XML-Datei des Menüelements hinzufügen:

```xml
<fields>
  <field
    name="template_style_id"
    type="templatestyle"
    label="COM_MENUS_ITEM_FIELD_TEMPLATE_LABEL"
    description="COM_MENUS_ITEM_FIELD_TEMPLATE_DESC"
    filter="int"
    template="cassiopeia"
    class="inputbox">
  </field>
 </fields>
 ```

Dies wird den Kern-Parameter `template_style_id` überschreiben. Indem die Vorlage in diesem Fall auf "cassiopeia" gesetzt wird, wird der Benutzer darauf beschränkt, nur Vorlagenstile für die "cassiopeia"-Vorlage auszuwählen.

## Weitere Informationen

-  Grundlagen
  der Vorlage
-  Cassiopeia-Vorlagenordner und
  -dateien
-  Anpassung
  der Cassiopeia-Vorlage
-  Vorlagen-
  Overrides
-  Vorlagen-
  Layouts
-  Cassiopeia Vorlagen vereinfacht - Eine Fallstudie -
  eine einfache Vorlage basierend auf Cassiopeia

*Übersetzt von openai.com*

