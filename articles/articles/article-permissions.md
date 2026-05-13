<!--
{
  "source": "https://docs.joomla.org/J6.x:Access_Control",
  "title": "Beitrag: Bearbeiten - Berechtigungen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Joomla bietet ein ausgeklügeltes *Zugriffskontroll*-System basierend auf *Zugriffsebenen* und *Benutzergruppen*. Es wird im Beitrag über [Zugriffskontrolle](jdocmanal?article=user/users/access-control) im Abschnitt *Benutzer* dieses Handbuchs beschrieben.

Die hier dargestellte Beschreibung bezieht sich auf den *Berechtigungen*-Reiter des Formulars *Beiträge: Bearbeiten*. Die Einstellungen können seltsam erscheinen, falls Sie nicht mit dem Joomla-Zugriffskontrollsystem vertraut sind.

## Screenshot

![Der Beiträge-Berechtigungsreiter mit ausgewähltem Autor](../../../en/images/articles/article-permissions/01-articles-edit-permissions-tab.png)

Es mag überraschend sein, dass ein Autor scheinbar keine Berechtigung hat, einen Beitrag zu bearbeiten!

## Frontend- und Backend-Benutzergruppen

Wenn Sie mit den Standard-Joomla-Benutzergruppen nicht vertraut sind, ist es hilfreich zu wissen, dass *Autor*, *Editor* und *Publisher* Frontend-Benutzergruppen sind. Sie können sich nicht im Backend einloggen. Ihre Arbeit beim Erstellen, Bearbeiten und Veröffentlichen von Beiträgen erfolgt mit Frontend-Beitragsbearbeitungsformularen. *Manager* und *Administrator* sind Benutzergruppen mit Zugriff sowohl auf das Frontend als auch auf das Backend und können Beiträge entweder mit Backend- oder Frontend-Bearbeitungsformularen bearbeiten.

## Bearbeitungszugriff für Autoren

Warum erscheint das Berechtigungsformular so, dass *Bearbeiten* als **Nicht erlaubt (geerbt)**
für die Autorengruppe angezeigt wird?

Es gibt eine einfache Erklärung. Wenn Sie das Bearbeitungsformular schließen und zur Seite *Beiträge: Optionen* über die Schaltfläche *Optionen* in der Toolbar der Beitragsliste gehen, zeigt der *Berechtigungen*-Tab dort, dass ein Mitglied der Autorengruppe zusätzliche Berechtigungen hat: *Erstellen* und *Eigene bearbeiten*. Diese Berechtigungen erlauben es einem Autor, Beiträge zu erstellen und seine eigenen Beiträge zu bearbeiten.

Die Berechtigungen im Formular *Beiträge: Bearbeiten* erlauben es einem Mitglied der Autorengruppe also nicht, Beiträge zu bearbeiten, die von jemand anderem erstellt wurden.
*Übersetzt von openai.com*

