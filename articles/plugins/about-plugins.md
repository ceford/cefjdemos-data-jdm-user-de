<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=plugins&filename=about-plugins.md",
  "title": "Über Plugins",
  "description": "", 
  "author": ""
}
-->

## Einführung

Plugins sind Joomla!-Erweiterungen, die *im Hintergrund* auf einen Auslöser reagieren. Es gibt ungefähr 160 Kern-Plugins in über 20 Gruppen. Drittanbieter-Entwickler bieten noch viele weitere an. Das folgende Bild zeigt den Anfang der Plugin-Liste, bei der die Listenlänge für den Screenshot auf 5 eingestellt wurde.

![Plugin-Liste](../../../en/images/plugins/about-plugins/01-plugins-list.png)

## Plugin-Typen

Im Plugin-Ordner Ihrer Website sehen Sie die Typen. Zum Beispiel sehen Sie einen **content**-Ordner, der Plugins enthält, die Inhalte manipulieren, und einen **user**-Ordner, der Plugins in Bezug auf Benutzer enthält. Sie können die Liste nach Typ oder Element filtern, wie zum Beispiel *contact*, das möglicherweise mehrere Typen umfasst.

## Plugin-Parameter

Plugins können wenige oder viele Parameter haben. Zum Beispiel bietet das Plugin *Content - E-Mail-Verschlüsselung* die Wahl zwischen zwei Verschlüsselungsmethoden, während das Plugin *Editors - TinyMCE* eine lange Liste optionaler Parameter hat. Alle Plugins haben geeignete Standardeinstellungen. Oft muss lediglich ein bestimmtes Plugin bei Bedarf *aktiviert* oder *deaktiviert* werden.

## Plugin-Ausführung

Die Ausführung eines Plugins wird durch ein *Event* ausgelöst. Zum Beispiel hat der Code, der einen Beitrag zur Anzeige zusammenstellt, Events namens `onContentAfterTitle`, `onContentBeforeDisplay` und `onContentAfterDisplay`. Diese werden genutzt, um benutzerdefinierte Felder an den ausgewählten Positionen zu platzieren.  

## Einzelne Plugins

Nur sehr wenige der einzelnen Plugins sind hier dokumentiert. Sie werden auf der Hilfeseite jedes Plugins behandelt.

*Übersetzt von openai.com*

