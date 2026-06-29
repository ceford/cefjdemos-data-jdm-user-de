<!--
{
  "source": "https://docs.joomla.org/J4.x:How_to_Show_a_Calendar_Month_List_of_Archived_Articles_Using_a_Module",
  "title": "Archivierte Beiträge",
  "description": "", 
  "author": ""
}
-->

## Einführung

Das Archivieren von Beiträgen ist eine der Möglichkeiten, wie Joomla! dabei hilft, die Beiträge einer Website zu verwalten, da es hilft, Unordnung im Backend zu reduzieren. Aber welche Website-Besucher sollten Zugriff auf archivierte Beiträge haben?

Eine Möglichkeit, dies zu tun, besteht darin, eine Kalender-Monatsliste von archivierten Beiträgen mit einem der Kernmodule von Joomla anzuzeigen. In diesem Beispiel wird ein **Archivierte Beiträge Modul** so eingestellt, dass es in der Seitenleiste der Website angezeigt wird.

## Modul *Beiträge - Archiviert* erstellen

Verwenden Sie eine der folgenden Methoden:
* Wählen Sie den **Module**-Eintrag im Home Dashboard. Oder...
* Wählen Sie **Inhalt / Site-Module** aus dem Administrator-Menü.
* Wählen Sie den **Archivierte Beiträge**-Eintrag aus der Liste der Module (Site).

Dies wird das neue Modul erstellen und es zur Konfiguration öffnen.

## Konfiguration des Moduls

Für die Standardnutzung des Moduls gibt es nur wenige Einstellungen:

- **Titel** Geben Sie einen Namen für das Modul ein.
- **\# der Monate** Legen Sie die Anzahl der Monate fest, die Sie anzeigen möchten. Diese
erscheinen als Links im Frontend. Stellen Sie dies mithilfe der Auf- / Ab-Pfeile ein oder
geben Sie direkt eine Zahl in das Feld ein.
- **Titel Anzeigen/Verbergen** Wählen Sie, ob der Titel angezeigt werden soll, indem Sie auf
*Anzeigen* oder *verbergen* umschalten.
- **Position** Legen Sie eine Position fest, an der Sie das Modul im
Frontend anzeigen möchten. Die Positionen werden durch Ihre Vorlage vorgegeben. Dieses Beispiel verwendet Joomlas
Cassiopeia-Vorlage *Seitenleiste Rechts* Position.
- **Status** Standardmäßig ist der Modulstatus **Veröffentlicht**. Andere Optionen sind
**Unveröffentlicht** und **Papierkorb**.
- **Start der Veröffentlichung** Sie können den Beginn der Veröffentlichung des
Moduls planen.
- **Ende der Veröffentlichung** Sie können planen, wann die Veröffentlichung des
Moduls gestoppt wird.
- **Zugriff** Wenn Sie steuern möchten, wer das Modul im Frontend sehen kann, können Sie eine Zugriffsberechtigung wählen.
- **Reihenfolge** Wird verwendet, um zu steuern, wo das Modul innerhalb der
von Ihnen gewählten Position angezeigt wird. Zum Beispiel können Sie eine Anzahl von
Modulen in der Seitenleiste haben und möchten, dass dieses Modul oben oder unten – oder
zwischen anderen in der Seitenleiste – angezeigt wird. Es kann anfangs etwas verwirrend sein, da das Feld eine nummerierte Position und einen Modulnamen anzeigt. Der Name
kann ein unveröffentlichtes Modul sein. Wichtig ist, dass die niedrigste Nummer oben und die höchste Nummer unten steht.
- **Notiz** Es kann hilfreich sein, das Notizfeld zu verwenden, wenn Sie z.B.
den gleichen Modultyp an mehreren Stellen verwenden.

### Menüzuweisung Registerkarte

Standardmäßig wird das Modul **auf allen Seiten** veröffentlicht.

Alternativ können Sie über eine Dropdown-Liste wählen **Keine Seiten**, **Nur
auf den ausgewählten Seiten** oder **Auf allen Seiten außer den ausgewählten**. Die
letzten beiden Optionen bieten Ihnen einen Menübaum der auf der Webseite verwendeten Menüs, auf denen Sie Seiten auswählen/abwählen können.

### Weitere Einstellungen

Der **Erweitert**-Tab hat Einstellungen im Zusammenhang mit dem Layout des Moduls, wenn es
ausgegeben wird.

Der **Berechtigungen**-Tab erlaubt Ihnen zu kontrollieren, was Benutzergruppen mit
dem Modul machen können.

## Veröffentlichen des Moduls

Wenn Sie bereit sind, wählen Sie die Schaltfläche **Speichern & Schließen**.

Das Modul wird in der Seitenleiste der Webseite veröffentlicht und zeigt eine Liste von Links an, die durch die Anzahl der im Modul festgelegten anzuzeigenden Monate bestimmt wird.

![Beispiel für ein Modul mit archivierten Beiträgen](../../../en/images/modules/articles-archived-module/01-modules-archived-articles.png)

## Tipps

Je mehr archivierte Beiträge Sie haben, desto größer ist die Anzahl der Links, die vom Modul angezeigt werden. Es kann sinnvoller sein, die Anzahl der Links durch die Verwendung von Kategorien zu begrenzen oder Sie können mehrere Archivierte Beiträge Module mit entsprechendem Namen verwenden.

*Übersetzt von openai.com*  

