<!--
{
  "source": "https://docs.joomla.org/Cache",
  "title": "Cache",
  "description": "", 
  "author": ""
}
-->

## Für Administratoren

Als Administrator bietet Ihnen Joomla die Möglichkeit, Teile Ihrer Website zu cachen. Sie können wählen, ob ganze Webseiten oder nur Teile dieser Seiten gecacht werden sollen. Diese Anleitung erklärt, wie das funktioniert.

Auf einer Joomla-Webseite gibt es 3 Dinge, die gecacht werden können:

1. Die gesamte Seite selbst – der Seiten-Cache
2. Die Ausgabe der Joomla-Komponente für diese Webseite – bekannt als der Ansichts-Cache
3. Die Ausgabe der auf dieser Seite angezeigten Module – bekannt als der Modul-Cache

Es gibt eine Reihe von Cache-Einstellungen, die es Ihnen ermöglichen, zu kontrollieren, was gecacht wird:

1. Das System-Plugin "System – Seiten-Cache"
2. Die Globale Konfiguration, Registerkarte System, Cache-Einstellungen. Hier kann die Option System-Cache eingestellt werden auf
   - AUS – Caching deaktiviert
   - EIN – Konservatives Caching
   - EIN – Progressives Caching
3. Viele Module haben in ihren Optionen eine Registerkarte Erweitert, in der das Caching auf *Global verwenden* oder *Kein Caching* eingestellt werden kann.

Wie unten beschrieben, gibt es auch Regeln für das Caching, die im Joomla-Code implementiert sind und über die Sie keine Kontrolle haben.

Sie können den Cache über die Menüauswahl Administrator → System → Cache leeren löschen. Im Allgemeinen kann man sagen, dass Joomla 3 Stufen des Caches hat, die in ihrer Aggressivität zunehmen:

1. Konservatives Caching
2. Progressives Caching
3. Seiten-Caching

Darüber hinaus können Joomla-Entwickler Caching-Möglichkeiten nutzen, um zum Beispiel das Ergebnis von Datenbankanfragen zu speichern, um die Reaktionsfähigkeit der Seite zu erhöhen. Dies liegt jedoch außerhalb der Fähigkeiten eines Administrators.

## Seiten-Caching

Um dies zu aktivieren, gehen Sie zu Administrator → Erweiterungen → Plugins. Suchen Sie dann das Plugin System – Seiten-Cache und aktivieren Sie es. Dies bedeutet, dass die Seiten der Website nun zwischengespeichert werden und bei erneutem Abruf die zwischengespeicherte Seite bereitgestellt wird, anstatt dass sie von Joomla aus den Informationen in der Datenbank generiert wird. Die zwischengespeicherte Seite wird weiterhin angezeigt, bis sie abläuft – wie im *Cache-Zeit* Parameter unter Administrator → Globale Konfiguration → System-Tab → Cache-Einstellungen definiert.

Wenn Sie diese Seite als Tutorial lesen und das Seiten-Caching testen möchten, ist es am besten, die Cache-Einstellungen der globalen Konfiguration auf folgende Weise festzulegen:

- Cache Handler – Datei
- Pfad zum Cache-Ordner – leer lassen
- Cache-Zeit – 15 (der Standard von 15 Minuten)
- Plattform-spezifisches Caching - Nein
- System-Cache – AUS – Caching deaktiviert

Um zu überprüfen, ob das Seiten-Caching funktioniert, gehen Sie zu einer Website-Seite, die einen Beitrag anzeigt. Nachdem Sie diese Seite angezeigt haben, sollten Sie im Dateisystem ein `cache/page`-Verzeichnis mit einer darin befindlichen Datei finden, die einen Dateinamen wie `xxx-cache-page-yyy.php` hat, wobei xxx und yyy lange Hash-Zeichenketten sind. Joomla muss separate Cache-Seiten für separate URLs speichern, sodass die zweite Zeichenfolge aus hexadezimalen Ziffern ein Hash der URL der Website-Seite ist, um den Dateinamen eindeutig für diese Seite zu machen.

Verwenden Sie dann die Administrator-Funktion, um den Text dieses Beitrags zu ändern und die Website-Seite erneut anzuzeigen. Sie sollten die zwischengespeicherte Version finden, nicht Ihren modifizierten Text.

Das Ändern eines Beitrags (oder eines anderen Joomla-Artikels) löscht den Seiten-Cache für die Webseite(n), auf der/denen dieser Beitrag angezeigt wird, nicht. Um den Seiten-Cache zu löschen, gehen Sie zu Administrator → System → Cache leeren. Klicken Sie auf das Kontrollkästchen neben der *Cache-Gruppe* "page" und drücken Sie die Löschen-Schaltfläche. Wenn Sie Ihre Webseite erneut anzeigen, sollte jetzt Ihr geänderter Text angezeigt werden.

Wenn Ihre Website über eine Funktion wie einen Warenkorb verfügt, führt die Anwendung von Seiten-Caching zu Problemen, da die Seiten anzeigen müssen, was der Kunde bereits ausgewählt hat, anstatt eine zwischengespeicherte Seite anzuzeigen, die für alle gleich ist. Sie können jedoch das System-Plugin - Seiten-Cache so konfigurieren, dass bestimmte Menüeinträge oder bestimmte URLs und URL-Bereiche (im Erweiterten Tab) vom Caching ausgeschlossen werden, sodass nur wirklich statische Seiten zwischengespeichert werden.

## Konservatives Caching

Mit konservativem Caching können Sie die Ausgabe von Ansichten aus Komponenten und die Ausgabe von Modulen, die Caching erlauben, zwischenspeichern. Beachten Sie jedoch, dass dies nur auf Seiten funktioniert, die nicht mit dem Seiten-Cache zwischengespeichert werden. Für diese Seiten wird die gesamte Webseite zwischengespeichert, und konservatives Caching wird nicht berücksichtigt.

Um konservatives Caching zu aktivieren:

1. Gehen Sie zu Administrator → System → Globale Konfiguration → System-Tab und stellen Sie innerhalb der Cache-Einstellungen den System-Cache auf EIN – Konservatives Caching.
2. Gehen Sie zu Administrator → Erweiterungen → Module und wählen Sie die Module aus, die Sie zwischenspeichern möchten. Falls dieses Modul Caching erlaubt, sollten Sie unter dem Tab "Erweitert" in der Lage sein, das Caching auf folgende Optionen zu setzen:

- Global verwenden – dieses Modul wird zwischengespeichert (mit der globalen Option, die jetzt auf konservatives Caching gesetzt wurde)
- Kein Caching – dieses Modul wird nicht zwischengespeichert.

(Beachten Sie, dass die Cache-Zeit in der globalen Konfiguration in Minuten und die Cache-Zeit in den Modul-Einstellungen in Sekunden angegeben ist.)

Um zu überprüfen, ob es funktioniert, gehen Sie zu Ihrer Website, **vergewissern Sie sich, dass Sie abgemeldet sind**, und navigieren Sie zu einer Webseite, die einen Beitrag anzeigt. Überprüfen Sie Ihr Dateisystem, und Sie sollten einen Ordner `cache/com_content` finden, der eine Cache-Datei enthält.

Sie finden auch andere Verzeichnisse, wie `cache/com_languages` (da das Anzeigen der Seite das Laden der aktuellen Sprache beinhaltet, und dies ebenfalls zwischengespeichert wird) und auch Verzeichnisse, die sich auf den Modul-Cache beziehen, z.B. `cache/com_modules`. Diese resultieren aus der Verwendung des Caches, den Entwickler innerhalb der Joomla-Anwendung programmiert haben.

Wenn Sie diesen Beitrag bearbeiten und speichern und dann die Seite der Website aktualisieren, werden Sie feststellen, dass die aktualisierte Version des Textes angezeigt wird. Dies liegt daran, dass Joomla bei jeder Speicherung der Bearbeitung den Cache für diesen Beitrag löscht.

Jedoch können Sie demonstrieren, dass der Cache funktioniert, wenn Sie die Cache-Datei im `cache/com_content`-Verzeichnis mit einem einfachen Texteditor bearbeiten. Ändern Sie mit dem Editor einen Buchstaben im Beitragstext in der Cache-Datei und speichern Sie die Datei. Wenn Sie die Webseite dann aktualisieren, sollten Sie die Änderung, die Sie in der Cache-Datei vorgenommen haben, sehen.

Wie können Sie auswählen, welche Komponentenansichten zwischengespeichert werden und unter welchen Umständen? Leider können Sie dies nicht tun. Das wird von den Joomla-Kernkomponentenentwicklern bestimmt und im Komponenten-PHP-Code programmiert. Die Kriterien sind für jede Komponente unterschiedlich. Sie können jedoch leicht entdecken, welche Kriterien verwendet werden, da diese für jede der Site-Komponenten im `DisplayController.php`-Datei der Seite programmiert sind. Zum Beispiel finden wir zum Zeitpunkt dieser Überarbeitung (Joomla-Version 5) für die Kontakte-Komponente in `components/com_contact/src/Controller/DisplayController.php`

```php
    public function display($cachable = false, $urlparams = [])
    {
        if ($this->app->getUserState('com_contact.contact.data') === null) {
            $cachable = true;
        }
```

Das bedeutet, dass die Ansichten, die mit Kontakten verknüpft sind, zwischenspeicherbar sind, es sei denn, es gibt Sitzungsdaten, die durch com_contact.contact.data gekennzeichnet sind – was der Fall sein wird, wenn in der Benutzersitzung der Benutzer ein Kontaktformular angezeigt hat (z.B. auf einer Seite, die durch einen Menüpunkte vom Typ Kontakte → Einzelkontakt angezeigt wird).

Die entsprechende Datei für Beiträge `components/com_content/src/Controller/DisplayController.php` enthält:

```php
    public function display($cachable = false, $urlparams = false)
    {
        $cachable = true;

        /**
         * Setzen Sie den standardmäßigen Ansichtsname und das Format aus der Anfrage.
         * Beachten Sie, dass wir a_id verwenden, um Kollisionen mit dem Router und der Rückkehrseite zu vermeiden.
         * Das Frontend ist etwas unordentlicher als das Backend.
         */
        $id    = $this->input->getInt('a_id');
        $vName = $this->input->getCmd('view', 'categories');
        $this->input->set('view', $vName);

        $user = $this->app->getIdentity();

        if (
            $user->get('id')
            || ($this->input->getMethod() === 'POST'
            && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive'))
        ) {
            $cachable = false;
        }
```

Der Ausdruck `$user->get('id')` ist wahr, wenn dieser ein angemeldeter Benutzer ist. Dies bedeutet, dass Beiträge für angemeldete Benutzer nie zwischengespeichert werden. Die nachfolgenden Ausdrücke beziehen sich auf andere Bedingungen, bei denen das Caching nicht durchgeführt wird, auch wenn der Benutzer nicht angemeldet ist.

Auf diese Weise können Sie feststellen, unter welchen Umständen Caching durchgeführt wird, aber es ist nicht ratsam, diese zu ändern. Sie können auch demonstrieren, dass Module zwischengespeichert werden, indem Sie das Joomla Breadcrumbs-Modul verwenden, sicherstellen, dass es in einer Modulposition auf der Webseite angezeigt wird, seine Caching-Option einstellen und die zwischengespeicherte Datei in cache/mod_breadcrumbs manuell bearbeiten.

## Progressives Caching

Wie beim konservativen Caching wird auch beim progressiven Caching die Ausgabe von Komponentenansichten und Modulen zwischengespeichert. Der funktionale Unterschied zwischen den beiden besteht darin, dass beim progressiven Caching **für abgemeldete Benutzer alle Module immer zwischengespeichert werden**. In diesem Fall hat die Auswahl der Option *Kein Caching* für ein Modul keine Auswirkung. Wenn die Caching-Speicheroption auf *Datei* eingestellt ist, finden Sie die Cache-Datei der Module (die Ausgabe aller Module wird in derselben Datei gespeichert) im Verzeichnis `cache/com_modules`.

Um das progressive Caching zu aktivieren, gehen Sie zu Administrator → System → Globale Konfiguration → Reiter System und stellen Sie unter *Cache-Einstellungen* den *System-Cache* auf *AN – Progressives Caching*.

Was die Bedingungen für das Caching von Joomla-Kernkomponentenansichten betrifft, gibt es **keinen Unterschied zwischen konservativem und progressivem Caching**. Unabhängig davon, was Sie auf einigen Websites und in Antworten auf Stack Overflow-Fragen lesen, ist es nicht der Fall, dass sich konservatives Caching auf den Fall bezieht, wenn der Benutzer nicht angemeldet ist, und progressives Caching auf den Fall, wenn der Benutzer angemeldet ist.

## Zusammenfassung

Eine Zusammenfassung der Cache-Arten finden Sie unten.

### Seitenweises Caching

- **Konfiguration**: Eingebautes Plugin (Administrator → Erweiterungen → Plugin-Manager → System - Seiten-Cache)
- **Cacht**: jede gesamte Seite Ihrer Website
- **Basierend auf**: URL
- **Weitere Informationen**:
  - Optionales Browser-Caching: Cacht auch im Browser/Computer Ihrer Besucher
  - Cacht nur Seiten für Gastbesucher (nicht für angemeldete Besucher). Seien Sie vorsichtig bei der Verwendung dieses Plugins, wenn Sie eine interaktive Website haben, bei der Sie Inhalte basierend auf Sitzungs-/Cookie-Informationen anstelle nur der schlichten URL bereitstellen möchten. Funktionen wie ein Warenkorb werden nicht funktionieren.

### Ansichts-Caching

- **Konfiguration**: Globale Konfiguration → Cache
- **Cacht**: jede Ansicht einer Komponente
- **Basierend auf**: URL, Ansicht, Parameter, ...
- **Weitere Informationen**: Entwickler von Komponenten müssen dies in ihrem Code einbeziehen, damit es funktioniert. Meistens wird dies nicht gemacht. Die Joomla-Hauptinhaltskomponente verwendet dies, jedoch nur für Gastbesucher Ihrer Website, obwohl dies nicht für jede Komponente zwingend ist.

### Modul-Caching

- **Konfiguration**: Globale Konfiguration → Cache
- **Cacht**: jedes Modul (individuell angepasst über die Erweiterten Parameter jedes Moduls)
- **Basierend auf**: der Modul-ID, den Ansichtsebenen des Benutzers und dem *Itemid*-Parameter in der HTTP-Anfrage
- **Weitere Informationen**: Sie müssen es bei einigen Modulen deaktivieren, um Probleme zu vermeiden

### Weiteres Caching

Wenn Sie andere Cache-Systeme und -Möglichkeiten erkunden möchten, sollten Sie sich die Erweiterungen von Drittanbietern rund um das Caching ansehen.

### Cache-Engines oder -Speicher

- **Konfiguration**: Globale Konfiguration → Cache

Hier können Sie auswählen, welches System Ihre Webseite für das gesamte Caching verwenden soll. Einige Optionen sind: APC, Eaccelorator, File, Memcache, Redis, XCache.

APC beispielsweise cached auch Ihren PHP-Opcode.

## Für Entwickler

<div class="alert alert-warning">
Dieser Abschnitt muss für Joomla! 4/5 überarbeitet werden.
</div>

Die Klasse **JCache** ermöglicht viele verschiedene Arten und Ebenen des Cachings. Die folgenden Unterklassen wurden speziell entwickelt, aber Sie können auch Ihre eigenen hinzufügen oder die Hauptklasse auf viele verschiedene Weisen verwenden.

Vergessen Sie nicht, dass die erste Ebene des Caches, die Sie antreffen, jede tiefere Caching-Ebene überschreibt. Ich nehme an, dass zu viele Ebenen auch kontraproduktiv sind (*das muss jedoch noch überprüft werden*).

- **JCacheView** speichert und gibt die Ausgabe einer bestimmten Ansicht (im MVC) zurück. Eine Cache-ID wird automatisch aus der URI, der spezifischen Ansicht und ihrer spezifischen Methode generiert, aber Sie können auch Ihre eigene angeben.

Dies kann automatisch über die Anzeige-Funktion des Basis-Controllers erledigt werden. Zum Beispiel im Controller Ihrer Komponente:

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true fordert Caching an.
        }
    }

Es gibt auch einige urlparams zu berücksichtigen. Schauen Sie sich dieses
[Joomla StackExchange](http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000) an.

Beachten Sie außerdem, dass keine Aktualisierungen (wie Treffer oder Besuchszahlen) aktualisiert werden (es sei denn, Sie fügen dies außerhalb dieser Methode und damit in einem tieferen MVC-Teil hinzu).

- **JCachePage** speichert und gibt den Hauptinhalt der Seite zurück.
- **JCacheCallback** speichert und gibt die Ausgabe und Ergebnisse von Funktionen oder Methoden zurück.

Wenn Sie Abfragen zwischenspeichern möchten, ist dies eine gute Klasse dafür, wie hier gezeigt: Caching verwenden, um Ihren
Code zu beschleunigen.

- **JCacheOutput** speichert und gibt Ausgaben zurück.

Dies ist eher dafür gedacht, einen bestimmten Teil des PHP-Codes zu cachen. Es funktioniert wie ein Ausgabepuffer, aber zwischengespeichert.

*Übersetzt von openai.com*

