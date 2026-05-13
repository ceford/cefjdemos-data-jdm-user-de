<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=help&filename=administrator-help.md",
  "title": "Administrator-Hilfe  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Fast alle Joomla-Administratorseiten haben eine Symbolleiste mit einem **Hilfe**-Button in der oberen rechten Ecke der Seite. Nur Dashboards haben keine Symbolleiste und daher auch keinen Hilfe-Button.

Viele Seiten haben auch einen Button mit der Bezeichnung **Inline-Hilfe umschalten**. Dieser zeigt einfach eine Feldbeschreibung an oder verbirgt sie, falls diese verfügbar ist. Sein Zweck ist es, Unordnung zu reduzieren, aber eine Erinnerung bereitzustellen, wo dies hilfreich wäre. Es wird hier nicht weiter behandelt.

Der **Hilfe**-Button öffnet ein neues Fenster über eine URL, die im Button eingebettet ist. Ein Beispiel:
```
data-url="https://help.joomla.org/proxy/index.php?keyref=Help51:Articles&lang=de"
```
In diesem Fall kommt der Inhalt der Hilfeseite aus einer externen Quelle.

## Die Hilfequelle - eine MediaWiki-Seite

MediaWiki ist die Software, die von Wikipedia verwendet wird. Es handelt sich um ein Freies Open Source Software (FOSS) Paket, das PHP und MySQL nutzt, genau wie Joomla. Sie können es selbst herunterladen und installieren. Theoretisch könnten Sie Ihren eigenen Hilfeserver erstellen und diesen anstelle des gemeinsamen Joomla-Hilfeservers verwenden. In der Praxis müssen Sie wissen, dass MediaWiki-Seiten eine gewisse Bearbeitung benötigen, um als Hilfeseiten geeignet angezeigt zu werden.

Hier kommt der **Proxy** ins Spiel. Er holt die erforderliche Seite aus der MediaWiki-Installation und bereitet sie für die Anzeige als Hilfeseite vor. Sie können eine originale MediaWiki-Seite in diesem Beispiel unter https://docs.joomla.org/Help5.x:Articles sehen und sie bearbeiten, wenn Sie etwas Falsches entdecken.  

## Die globale Hilfe-URL

Die Datei **configuration.php** im Stammverzeichnis einer Joomla-Installation enthält eine Variable `$helpurl`:

```
$helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}&lang={langcode}';
```

Wenn ein Hilfe-Button ausgewählt wird, wird jedes der Elemente in geschweiften Klammern ersetzt. Die Werte {major} und {minor} sind die Versionsangaben Ihrer Installation. Der {langcode} ist der Code Ihrer derzeit ausgewählten Administrator-Sprache, die z.B. en, de oder fr sein könnte.

Die Variable {keyref} ist der Dateiname einer Seite auf dem Hilfeserver, ohne ihren Namensraum. Für die Seite Beiträge ist der relevante Dateiname zufällig *Articles*.

**Hinweis:** `https://docs.joomla.org/` ist die Seite zum Bearbeiten von Hilfeseiten. Aber `https://help.joomla.org/proxy` ist die Seite zum Abrufen von Hilfeseiten.

Es gibt keine Möglichkeit, die Standard-Hilfeserver-URL innerhalb der Administrator-Gesamtkonfiguration-Formulare zu ändern, aber Sie können sie mit einem Texteditor ändern.

Die vollständige Liste der verfügbaren Ersetzungscodes ist:

| Code          | Wird ersetzt durch                                                           |
|---------------|------------------------------------------------------------------------------|
| {app}         | Anwendungsname (z.B. "Administrator" im Joomla CMS-Backend)                  |
| {component}   | Komponentenname (z.B. "com_content" im Beitragsmanager)                      |
| {keyref}      | Hilfe-Bildschirm-Schlüsselreferenz (nach Durchlaufen des Übersetzungssystems)|
| {major}       | Joomla Hauptversionsnummer (z.B. "5" in Joomla 5.6).                         |
| {minor}       | Joomla Nebenversionnummer (z.B. "1" in Joomla 5.1)                           |
| {maintenance} | Joomla Wartungsversionnummer (z.B. "3" in Joomla 5.1.1).                     |
| {language}    | Voller Sprachcode (z.B. "en-GB")                                             |
| {langcode}    | Sprachcode-Teil des Sprachcodes (z.B. "en", wenn der volle Code "en-GB" ist) |
| {langregion}  | Region-Tag-Teil des Sprachcodes (z.B. "GB", wenn der volle Code "en-GB" ist) |

## Globale Hilfe in der Zukunft

Die Nutzung einer MediaWiki-Seite zur Bereitstellung von Hilfeseiten stellt eine gewisse Belastung für diejenigen dar, die die Dokumentation pflegen, und das Verfahren könnte sich in Zukunft ändern. Wenn es eine Änderung gibt, wird wahrscheinlich die Quelle aus vorgefertigten HTML-Dateien bestehen, die mit einer einfachen Änderung der $helpurl-Quell-Domain abgerufen werden.

## Lokale Hilfe für benutzerdefinierte Komponenten

Wenn Sie eine benutzerdefinierte Komponente haben und mit der Bearbeitung von PHP-Quellcode und der Erstellung von Inhalten vertraut sind, können Sie Ihre eigenen individuellen Hilfeseiten erstellen. Nehmen Sie die Jdocmanual-Komponente als Beispiel. Als benutzerdefinierte Komponente gibt es auf der MediaWiki-Seite docs.joomla.org keine Hilfeseiten. Drittanbieterkomponenten dürfen von dort aus keine Hilfeseiten bereitstellen.

Schauen Sie sich dieses Codefragment aus administrator/components/com_jdocmanual/src/View/Manual/ViewHtml.php an:
```
        $tmpl = $app->input->getCmd('tmpl');
        if ($tmpl !== 'component') {
            ToolbarHelper::help('jdocmanual', true);
        }
```
Die Spezifikation des ToolbarHelper::help-Aufrufs ist wie folgt:
```
@param $ref: Der Name der Zieldatei (ohne Dateierweiterung).
@param $useComponent: Verwenden Sie die Hilfedatei im Komponentenverzeichnis.
@param $url: Verwenden Sie diese URL anstelle einer anderen.
@param $component: Name der Komponente, um Hilfe zu erhalten (null für die aktuelle Komponente)
function Toolbar::help(
    string $ref,
    bool $useComponent = false,
    string $url = null,
    string $component = null
): HelpButton
Schreibt eine Hilfetaste für eine gegebene Option (öffnet ein Popup-Fenster).
```
In diesem Beispiel ist **$ref** ein Dateiname, den es zu verwenden gilt, in diesem Fall `'jdocmanual'` (er muss mit der Groß-/Kleinschreibung der Zieldatei übereinstimmen) und **$useComponent** ist `true`, was bedeutet, dass sich die zu verwendende Hilfeseite innerhalb der Komponentendateien befindet unter administrator/component/com_jdocmanual/help/en-GB/jdocmanual.html

Die Verwendung einer Hilfedatei innerhalb der Komponente sollte bedeuten, dass Hilfe niemals fehlt und möglicherweise immer auf dem neuesten Stand ist.

## Benutzerdefinierte Komponente Fernhilfe

Bei der Erstellung der Hilfe-Schaltfläche können Sie $useComponent = false setzen und die URL so einstellen, dass sie auf einen bestimmten Ort auf Ihrer eigenen oder einer externen Seite verweist.

```
ToolbarHelper::help('jdocmanual', false, 'http://example.com/help/en-GB/jdocmanual.html');
```

Alles, was benötigt wird, ist eine HTML-Seite mit dem richtigen Namen am richtigen Ort.

*Übersetzt von openai.com*

