<!--
{
  "source": "https://docs.joomla.org/J4.x:Switching_Templates",
  "title": "Vorlagen wechseln ",
  "description": "", 
  "author": ""
}
-->

## Site- und Administrator-Templates

Joomla 4 wird mit einem einzigen Site-Template, Cassiopeia, und einem einzigen Administrator-Template, Atum, geliefert. Sie können zusätzliche Templates von Drittanbietern beziehen, sowohl kostenlos als auch kostenpflichtig, und Sie können Ihre eigenen Templates erstellen, am einfachsten als Child-Templates.

Es ist unwahrscheinlich, dass Sie ein alternatives Administrator-Template verwenden möchten, daher behandelt dieser Beitrag nur alternative Site-Templates. Zur Veranschaulichung wurde ein Child-Template mit einem grünen Thema erstellt, wie im Beitrag über Child-Templates beschrieben. Außerdem ist auf der zur Veranschaulichung verwendeten Website die Testmuster-Daten installiert.

## Standardvorlagenstil

Eine Ihrer Vorlagen muss als Standard markiert sein. Diese wird für alle Seiten verwendet, außer für einzelne Seiten, die eine alternative Vorlage angeben. Um die Standardvorlage festzulegen:

- Wählen Sie **System → Vorlagen-Panel → Website-Vorlagenstile** im Administrator-Menü aus.
- Wählen Sie eine der Schaltflächen in der Standardspalte aus.

![Vorlagen-Website-Stile Listenansicht](../../../en/images/template-tips/switching-templates/01-switch-templates-styles-list.png)

Schauen Sie sich Ihre Website an, um zu überprüfen, dass alle Seiten die Standardvorlage verwenden.

## Verwendung eines alternativen Stils

Joomla ermöglicht es Ihnen, einen Stil für eine bestimmte Seite über die Menüzuweisung auszuwählen. Die Auswahl kann entweder über das Template-Stil-Formular oder das Menü-Bearbeitungs-Formular erfolgen. Beide Methoden führen zum gleichen Ergebnis. Die erste Methode ist praktischer, wenn es darum geht, eine Gruppe von Menüpunkten auszuwählen, die zu demselben Menü gehören.

### Methode der Zuweisung über das Template-Menü

Aus der Liste der Vorlagenstile:

- Wählen Sie einen Stil, der **nicht** als Standard festgelegt ist. Der gelbe Stern zeigt den Standardstil an.
- Wählen Sie die Registerkarte Menüzuweisung.
- Wählen Sie einzelne Menüpunkte aus oder schalten Sie alle Elemente in einem Menü um.
- Speichern

![templates style edit page menu assignment tab](../../../en/images/template-tips/switching-templates/02-switch-templates-styles-edit-style-menu-assignment.png)

In diesem Beispiel wurden alle Menüpunkte im Menü `Main Menu Testing` ausgewählt. Gehen Sie zu Ihrer Website zurück und wählen Sie einen der Menüpunkte aus, die das ausgewählte Template verwenden sollen.

### Methode der Menüeinzelheiten

Diese Methode wird verwendet, um das Template für einzelne Menüpunkte festzulegen.

- Wählen Sie **Menüs → \[Menüname\]** aus dem Administrator-Menü.
- Wählen Sie einen Menüpunkt aus der Spalte Titel aus, um das Bearbeitungsformular zu öffnen.
- Wählen Sie im Feld **Template-Stil** den gewünschten Template-Stil aus.
- Speichern

![templates menus edit item form showing style selection](../../../en/images/template-tips/switching-templates/03-switch-templates-styles-edit-menu-style.png)

Gehen Sie zu Ihrer Website zurück und wählen Sie den geänderten Menüpunkt, um zu überprüfen, ob er mit dem ausgewählten Template-Stil angezeigt wird.

*Übersetzt von openai.com*

