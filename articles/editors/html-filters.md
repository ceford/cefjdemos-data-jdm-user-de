<!--
{
  "source": "https://docs.joomla.org/Entering_raw_HTML_in_editors",
  "title": "HTML-Filter",
  "description": "", 
  "author": ""
}
-->

## HTML-Textarea-Tag

In HTML ist ein mehrzeiliges Eingabefeld als Textarea bekannt. Jeglicher Text zwischen den öffnenden und schließenden Tags wird als Text angezeigt, der HTML-Markup enthalten kann. Beispiel:
```
<textarea><p class="poem">Der schnelle braune Fuchs<br>
springt über den faulen Hund.</textarea>
```
Editoren wie TinyMCE oder Code Mirror verwenden JavaScript, um die Textarea mit einer anderen Anzeige zu überlagern, um WYSIWYG-Dateneingabe und/oder Syntaxhervorhebung zu ermöglichen. Der Umschaltknopf unter einem Editorfeld schaltet zwischen der Textarea-Ansicht und der WYSIWYG-Ansicht um.

Editoransichten werden für den Inhalt von Beiträgen und einigen Modulen verwendet. Allerdings müssen Sie sich bewusst sein, dass nicht alle HTML-Tags und Attribute (wie class="xyz") für alle Benutzer erlaubt sind. Einige oder alle können verschwinden, wenn Sie den Inhalt einer Textarea oder eines Eingabefeldes speichern oder bearbeiten.

Dies wird durch Filtermechanismen verursacht, entweder in der Joomla! Globalen Konfiguration oder in der Editor-Konfiguration. Ein Editorfilter kann umgangen werden, indem im *Benutzerprofil* in den Einstellungen *Kein Editor* ausgewählt wird. Sie können die globalen Filter nicht umgehen, aber Sie können sie an die Zwecke Ihrer Website anpassen.

## Auswahl des Benutzer-Editors

Sie können einen der verfügbaren Editoren auswählen, einschließlich „Keine“, über Ihr Benutzerprofil, das über das Menü Benutzerkonto / Profil bearbeiten oben rechts im Administratorbildschirm verfügbar ist. Das Formular "Profil bearbeiten" enthält eine Registerkarte "Grundeinstellungen" mit einem Feld zur Auswahl eines Editors. Normalerweise ist es auf *- Standard verwenden -* eingestellt, was normalerweise TinyMCE ist. Sie können *Editor Keine* auswählen. Dies umgeht jegliche Filterung von HTML-Tags und -Attributen, die durch die TinyMCE-Konfigurationseinstellungen nicht erlaubt sind.

**Warnung:** Wenn Sie *Editor - Keine* auswählen, um Inhalte mit HTML-Tags zu erstellen, die von einem Editor-Filter nicht zugelassen werden, und dann zum Standardeditor zurückwechseln, sollten Sie darauf achten, diese Inhalte nicht erneut zu bearbeiten und zu speichern, da Sie sonst gefilterte Tags und Attribute verlieren. Es ist leicht, dies versehentlich zu tun, und es gibt keine Warnung.

## Globale Konfiguration: Textfilter

Wählen Sie im Haupt-Dashboard die Option Globale Konfiguration und dann die Registerkarte Textfilter. Die Standardeinstellungen haben *Kein HTML* für die Gruppen Gast, Öffentlich und Registriert ausgewählt. Jede dieser Gruppen könnte die Möglichkeit haben, ein Textfeld auszufüllen, beispielsweise in einem Kontaktformular, das zusätzliche Informationen zu einem Problem anfordert, sodass das automatische Entfernen aller HTML-Tags in der Regel angemessen ist. Andere Gruppen, mit Ausnahme der Super-Benutzer, sind durch die Standard-Verboten-Liste eingeschränkt. Super-Benutzer haben keine Filterung.

![globale Konfiguration der Textfilter](../../../en/images/editors/html-filters/01-global-configuration-filters-tab.png) 

Die Anmerkungen erklären, was in der Standard-Verboten-Liste enthalten ist und wie die anderen Listen verwendet werden.

## TinyMCE-Konfiguration für Textfilter

Editoren werden in Joomla als Plugins implementiert. Der CodeMirror-Editor hat keine Textfiltereinstellungen. Um den TinyMCE-Editor anzupassen, suchen Sie ihn in der Liste der Plugins und wählen Sie ihn aus. Etwa in der Mitte der langen Einstellliste finden Sie ein Feld mit der Bezeichnung *Joomla Textfilter verwenden*, das standardmäßig auf **Aus** steht. Die nächsten drei Felder sind:
* **Verbotene Elemente**: eine Liste von Tags, die immer entfernt werden. Die Standardliste mit *script, applet, iframe* birgt alle Sicherheitsbedenken.
* **Gültige Elemente**: Verwenden Sie diese Liste, um zulässige Tags auf eine Teilmenge aller gängigen HTML-Tags zu beschränken. Beispiel: `a[href|target=_blank],strong/b,div[align],br`
* **Erweiterte gültige Elemente**: Verwenden Sie diese Liste, um ein Element zum bestehenden Standardregelsatz hinzuzufügen oder ein Element im Standardregelsatz zu ändern. Beispiel: `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

Siehe die TinyMCE-Dokumentation für mehr Erklärungen.

Um die TinyMCE-Textfilter zu umgehen und Joomla-Textfilter zu verwenden, stellen Sie *Joomla Textfilter verwenden* auf **Ein**. Die oben beschriebenen drei zusätzlichen Felder verschwinden, da sie nicht verwendet werden.

*Übersetzt von openai.com*

