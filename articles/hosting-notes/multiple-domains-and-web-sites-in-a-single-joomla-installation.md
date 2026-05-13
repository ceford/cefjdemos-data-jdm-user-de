<!--
{
  "source": "https://docs.joomla.org/Multiple_Domains_and_Web_Sites_in_a_single_Joomla!_installation",
  "title": "Mehrere Domains und Websites in einer einzigen Joomla!-Installation ",
  "description": "", 
  "author": ""
}
-->

**Hinweis:** Dieser Beitrag wurde zuletzt 2012 aktualisiert!

Obwohl es als Best-Practice gilt, jeder Website ihre eigene Domain, Joomla!-Installation und Datenbank zu geben, kann es besondere Bedingungen geben, unter denen eine Multi-Site-Lösung unter einer einzigen Joomla!-Installation gerechtfertigt ist.

## Ein Beispielanwendung

Ein kleines Unternehmen, 'Johnson Candies', hat zwei separate, aber verwandte Marken: *Rote Süßigkeiten* und *Gelbe Süßigkeiten*. Sie benötigen eine einzige Joomla!-basierte Website, auf der beide Süßigkeitentypen sichtbar sind, jeweils mit ihrer eigenen Startseite auf der Joomla!-Seite, die den Domains `www.redjohnsoncandy.com` und `www.yellowjohnsoncandy.com` entspricht.

Zusätzlich benötigt jede Marke und Website **ihr eigenes Design**: eine gelbe Vorlage für die eine; eine rote Vorlage für die andere.

## Vorteile

Durch die Einbeziehung beider Marken in eine einzige Joomla!-Webinstallation kann Johnson Candies Bearbeitungszeit sparen (nur ein Login), Beiträge und Daten zwischen beiden Marken (oder Websites) teilen und eine einzelne Funktion, wie zum Beispiel ein Kontaktformular, für beide Marken nutzen.

## Implementierungsverfahren

### Bereiten Sie Ihre Domains vor

Verwenden Sie eine einzige Domain für Ihr Hosting-Konto, wie gewohnt. Erstellen Sie die erforderlichen Add-on-Domains im Kontrollzentrum Ihres Hosting-Kontos. Für die Zwecke dieses Tutorials verwenden wir `www.redjohnsoncandy.com` zusätzlich zu der Basis-Domain `www.yellowjohnsoncandy.com`.

### Joomla! installieren und einrichten

Installieren und richten Sie Joomla! wie gewohnt ein. Erstellen Sie dann Beiträge, Menüs und Module für jede Seite.

### Vorlagen erstellen

Entwickeln und installieren Sie anschließend die erforderlichen Vorlagen – eine für jede Seite, die Sie haben möchten. Im obigen Beispiel würden Sie eine Vorlage für *Red Candy* mit dem Namen *Red Template* und eine Vorlage für *Yellow Candy* mit dem Namen *Yellow Template* erstellen. Sobald die Vorlagen installiert sind, ordnen Sie sie mithilfe des Joomla!-Vorlagenmanagers im Joomla!-Administratorbereich den entsprechenden Menüpunkten zu.

### Einen Redirect hinzufügen

#### Option #1: Erstellen Sie einen .htaccess (Apache) Redirect

**Hinweis** *Aktivieren Sie zuerst SEF-URLs in Joomla!*

Eine Möglichkeit besteht darin, .htaccess (Apache) zu verwenden, um Anfragen an eine bestimmte Domain auf eine bestimmte Joomla!-Seite umzuleiten.

Unser Ziel ist es, alle Anfragen an die Red Candy-Domain auf eine bestimmte Seite der Joomla!-Seite umzuleiten. In diesem Beispiel leiten wir alle Anfragen an `www.redjohnsoncandy.com` auf eine Kategorie-Blog-Seite um. Sie hätten diesem Menüpunkt zuvor die 'Red Candy'-Vorlage zugewiesen, um die Illusion einer separaten Seite zu erzeugen.
```apache
#Die folgende Regel funktioniert, aber sie ändert den angezeigten Domainnamen.
RewriteCond %{HTTP_HOST} ^(www\.)?redjohnsoncandy\.com$
RewriteRule (.*) http://www.yellowjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12 [R=301,L]
```
Nun, das funktioniert – aber Sie können den Nachteil sofort erkennen. Obwohl der Benutzer die Red Candy-Seite erfolgreich sieht, wird er immer noch den Yellow Candy-Domainnamen sehen. Leider, wenn Sie sowohl .htaccess als auch Domain-Parking (technisch ein Redirect) verwenden, ist dies notwendig, um eine Schleife zu vermeiden.

#### Option #2: Erstellen Sie einen PHP-Header-Redirect

Diese Lösung hat den Vorteil, dass die Illusion getrennter Domains/Websites für den Besucher erhalten bleibt. Anstatt .htaccess (Apache) für unseren Redirect zu verwenden, nutzen wir eine der Vorlagen auf der Seite.

In diesem Beispiel ist die Basis-Domain `www.redjohnsoncandy.com`. Sie haben eine Vorlage für diesen Bereich mit dem Namen *Red Template* erstellt. Der Trick besteht darin, die index.php-Datei von 'Red Template' zu öffnen und die folgenden Codezeilen **ganz am Anfang** der Haupt-index.php der Installation hinzuzufügen.

```php
<?php
$domain = $_SERVER["HTTP_HOST"];
$uri = $_SERVER["REQUEST_URI"];
$url = $domain . $uri;

if (($url == "redjohnsoncandy.com/") ||
   ($url == "www.redjohnsoncandy.com/")) {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.redjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12");
}
?>
```

Hier ist der Vorteil: Der Besucher wird nun zur entsprechenden *Red Site*-Seite weitergeleitet, der die *Red Template*-Vorlage zugewiesen ist, **nur** im Fall, dass sie unter dem 'red site'-Domainnamen angekommen sind. Andernfalls wird die bedingte PHP-Regel ignoriert und die Yellow Site wird geladen.

Es ist wichtig, auch die URI (die URL, die der reinen Domain folgt) anzufordern, damit Sie Weiterleitungen innerhalb derselben Domain vornehmen können. Wenn die URI in der URL unsichtbar ist, wird die Variable zu einem "/"-Zeichen. Deshalb müssen Sie Ihre reine URL mit einem "/"-Zeichen am Ende vergleichen. Auf diese Weise können Sie 301-Weiterleitungen innerhalb derselben Domain vornehmen. Andernfalls erzeugen Sie eine Endlosschleife im Weiterleitungsprozess.

#### Option #3: Erstellen Sie einen PHP-Header-Redirect für mehrere Domains mit spezifischen Domain-Weiterleitungen für benutzerdefinierte Vorlagen

Lösung für einen Webspace mit verschiedenen Domains, einer Joomla-Installation und je nach ankommender Domain eine Umleitung auf eine andere Standardseite. Fügen Sie den folgenden PHP-Code **als allererstes** in die Haupt-index.php der Installation ein. Um eine andere Domain zuzuweisen, kopieren/fügen Sie einfach die "if"-Funktion und bearbeiten Sie sie mit den Werten der anderen Domain in gleicher Weise. Weiterhin müssen Sie die Vorlage-Ansichten einrichten, indem Sie verschiedene Modul-Element-/Link-Aliase zuweisen und Vorlage-Ansichten innerhalb des Joomla!-Vorlagenmanagers einrichten. Die Aliaseinstellung ist notwendig, wenn Sie SEF-Einstellungen verwenden.
```php
<?php
$domain = $_SERVER["SERVER_NAME"];
$requri = $_SERVER['REQUEST_URI'];
if (($domain == "www.example.de" && $requri == "/" ||
   $domain == "example.de"))  {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.example.de/index.php?option=com_content&view=article&id=6");
}
?>
```
*Übersetzt von openai.com*

