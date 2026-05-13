<!--
{
  "source": "https://docs.joomla.org/How_do_you_put_a_module_inside_an_article%3F",
  "title": "Module innerhalb von Beiträgen  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Sie möchten in der Regel Module in irgendeiner Weise mit Beiträgen verknüpfen. Module werden normalerweise Modulpositionen zugewiesen, und die Modulpositionen erscheinen an einer Stelle auf der Webseite, die durch das Template festgelegt wird. Allerdings ist es manchmal nützlich, ein Modul tatsächlich in einen Beitrag einzubetten. Joomla hat ein Plugin namens *Inhalt - Module laden*, um dies zu ermöglichen. Wenn es aktiviert ist, kann ein Modul auf drei verschiedene Arten in einen Beitrag eingebettet werden:

```
    {loadposition position,[style]}
    {loadmodule mod_type,the title,[style]}
    {loadmoduleid moduleId}
```

Dabei ist `style` einer der Werte für den Modulstil aus dem Reiter „Erweitert“ im Formular zur Dateneingabe des Moduls, zum Beispiel html, outline, table, card oder noCard. 

## loadposition

Um ein Modul in einem Beitrag einzufügen, veröffentlichen Sie das Modul auf einer Position und laden diese Position im Beitrag wie folgt:

1. Erstellen Sie ein Modul und setzen Sie dessen Position auf ***myposition***. ***myposition*** kann jeder Wert sein, der nicht mit einer bestehenden Template-Position in Konflikt steht. Geben Sie im Modulbearbeitungsformular die Position ***myposition*** ein und drücken Sie Enter, anstatt sie aus der Dropdown-Liste auszuwählen.
2. Weisen Sie das Modul **Alle** Menüelemente zu. Dadurch wird sichergestellt, dass es immer angezeigt wird, egal wie der Besucher zum Beitrag gelangt ist. Das Modul wird nur angezeigt, wenn Sie den Befehl verwenden, um das Modul in einem Beitrag zu laden.
3. Bearbeiten Sie den Beitrag und fügen Sie den Text ***{loadposition myposition}*** an der Stelle ein, an der das Modul angezeigt werden soll.

**Hinweis:** Wenn das Plugin *Content - Load Modules* deaktiviert ist, wird der Text *{loadposition myposition}* unverändert im Beitrag angezeigt. Außerdem sollte der Name der Position komplett in Kleinbuchstaben geschrieben werden. CamelSchreibweise wird fehlschlagen.

## loadmodule

Die Syntax *{loadmodule yyy}* sucht nach dem ersten Modul, dessen **Typ** mit dem String 'yyy' übereinstimmt. So könntest du ein *mod_login* Modul laden, indem du {loadmodule login} in deinen Text einfügst. Der Typ ist nicht so offensichtlich! Zum Beispiel hat der Sprachumschalter den Typ **languages**. Um den Typ zu finden, musst du die Liste der Modulordner mit einem Dateimanager/Explorer durchsehen und den *mod_* Teil des Ordnernamens weglassen.

Wenn du eine bestimmte Instanz eines Moduls laden möchtest, weil du mehr als ein Login-Modul hast, z. B. mit den Titeln Login 1, Login 2 usw., musst du {loadmodule mod_modType, modTitle} verwenden, wobei **mod_modType** mod_login wäre und **modTitle** der Name/Titel ist, den du deiner Instanz dieses Moduls gegeben hast. Im obigen Beispiel würdest du dann mit **{loadmodule mod_login Login 2}** enden.

Du kannst auch den Stil hinzufügen, der für die Darstellung des Moduls verwendet wird. Um dies zu tun, füge den Stil als dritten Parameter hinzu, wie {loadmodule login,Login 2,xhtml}. Wenn du keinen Stil hinzufügst, wird keiner verwendet.

## loadmoduleid

Die *{loadmoduleid z}* Syntax sucht nach dem Modul, dessen `id` der
Nummer `z` entspricht. So könnten Sie das Modul mit der id 200 laden, indem Sie
*{loadmoduleid 200}* in Ihren Text einfügen. Diese Variante verwendet keine zusätzlichen
Parameter wie den `style` Parameter.

## Editor-Schaltfläche

Wenn das Editor-xtd-Plugin *Schaltfläche - Modul* aktiviert ist, können Sie die Editor-Schaltfläche *Modul* verwenden, um die oben beschriebenen Tags einfacher in den Editor-Text einzufügen. Die Modulliste verfügt über eine Schaltfläche in der Titelspalte, um nach ID einzufügen, und eine Schaltfläche in der Positionsspalte, um nach Position einzufügen.

## Module innerhalb von Module

Es ist möglich, ein Modul innerhalb eines *Custom HTML* Moduls einzufügen. Diese werden von Inhalts-Plugins auf die gleiche Weise wie Beiträge verarbeitet.

Es kann zu Formatierungsproblemen kommen, da der Stil des *Custom HTML* Moduls den Stil des eingeschlossenen Moduls umgibt. Das ist der Grund, warum die *Modul*-Schaltfläche im Editor in Modulen des Typs *Custom* nicht verfügbar ist.

*Übersetzt von openai.com* 

