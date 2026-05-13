<!--
{
  "source": "https://docs.joomla.org/How_do_you_recover_or_reset_your_admin_password%3F",
  "title": "Admin-Passwort-Wiederherstellung ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Normalerweise kann ein Super-User Benutzer und Passwörter in der Benutzerliste hinzufügen, bearbeiten und löschen. In einigen Situationen ist dies möglicherweise nicht möglich. Zum Beispiel, wenn die Person, die das Super-User-Passwort kannte, nicht mehr verfügbar ist. Oder vielleicht hat der Super-User das verwendete Passwort vergessen.

In solchen Fällen stehen dem Site-Administrator zwei Methoden zur Verfügung, um sich als Super-User anzumelden.

## Methode 1: Die Datei configuration.php bearbeiten

Wenn Sie Zugriff auf die Datei `configuration.php` der Joomla-Installation auf Ihrem Server haben, können Sie ein Super-User-Passwort zurücksetzen oder einen neuen Super-User erstellen, sofern Sie sich als Manager oder Administrator anmelden können.

Öffnen Sie die Datei `configuration.php` in einem Texteditor. Ändern Sie zunächst die Dateiberechtigungen auf 644. Ihre Website-Management-Tools, wie cPanel oder Plesk (es gibt auch andere), ermöglichen Ihnen dies normalerweise online. Falls nicht, müssen Sie möglicherweise FTP verwenden, um die Datei herunterzuladen, lokal zu ändern und wieder hochzuladen.

Fügen Sie am Ende der Datei, aber vor der abschließenden geschweiften Klammer, diese Zeile hinzu:
```
    public $root_user='meinname';
```
wobei **meinname** ein Benutzername mit *Manager*- oder *Administrator*-Gruppenzugriff ist, für den Sie das Passwort kennen. Ein Benutzername, der sich in den Gruppen *Author*, *Editor* oder *Publisher* befindet, wird nicht funktionieren, da diese Gruppen keinen Backend-Zugriff haben.

Dieser Benutzer wird jetzt ein temporärer Super-User sein.

Melden Sie sich im Backend an und ändern Sie das Passwort des Super-Users, dessen Passwort Sie nicht haben, oder erstellen Sie ein neues Super-User-Konto. Wenn Sie einen neuen Benutzer erstellen, möchten Sie eventuell den alten Benutzer blockieren oder löschen, je nach Ihrer Situation.

Wenn Sie fertig sind, stellen Sie sicher, dass Sie den Link *Hier klicken, um es automatisch zu versuchen*, verwenden, der im Warnfeld erscheint, um die Zeile zu entfernen, die zur Datei configuration.php hinzugefügt wurde. Falls der Link nicht erfolgreich war, gehen Sie zurück und löschen Sie die hinzugefügte Zeile aus Ihrer configuration.php-Datei mit einem Texteditor.

Wenn Sie keine Benutzer haben, die ihre Passwörter kennen, müssen Sie möglicherweise eine Änderung in Ihrer Datenbank vornehmen.

## Methode 2: Die Datenbank bearbeiten

Wenn die oben genannten Methoden nicht funktioniert haben, haben Sie zwei weitere Optionen, die beide erfordern, direkt mit der MySQL-Datenbank zu arbeiten.

### Ein Passwort in der Datenbank ändern

Die einfachste Option ist, das Passwort des Super Users in der Datenbank auf einen bekannten Wert zu ändern. Dies erfordert, dass Sie Zugriff auf die MySQL-Datenbank mithilfe von phpMyAdmin oder einem anderen Client haben. Diese Anleitung zeigt, wie Sie ein Passwort in das Wort **secret** ändern.

Diese Methode funktioniert nur, wenn der ausgewählte Benutzer zur Gruppe *Manager* oder *Administrator* gehört.

**Stellen Sie sicher, dass Sie das Passwort des Super Users ändern, sobald Sie wieder Zugang haben!**

1. Öffnen Sie phpMyAdmin und wählen Sie die Datenbank für die Joomla!-Seite aus. Dadurch werden die Datenbanktabellen auf der linken Seite des Bildschirms angezeigt.
2. Finden und wählen Sie die Tabelle *#__users*, wobei *#_* das Tabellenpräfix Ihrer Seite ist.
3. Im *Browse*-Modus finden Sie den Benutzer, dessen Passwort Sie ändern möchten, und wählen das Bearbeitungssymbol für diese Zeile aus.
    - Wenn die Liste lang ist, wählen Sie die SQL-Schaltfläche oben aus und verwenden Sie diese Abfrage: <br>
    `SELECT * FROM `xxxxx_users` WHERE `username` = 'Benutzername'`<br>
    wobei Sie Ihr Datenbankpräfix verwenden, um `xxxxx` zu ersetzen, und den Benutzernamen, den Sie finden müssen, anstelle von `Benutzername`.
4. Ändern Sie im Bearbeitungsformular das Passwort zu<br>
    `d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199`<br>
    und wählen Sie die Schaltfläche *Go* am unteren Rand des Formulars. phpMyAdmin sollte die Nachricht *Betroffene Zeilen: 1* anzeigen. Zu diesem Zeitpunkt sollte das Passwort **secret** sein.
5. Melden Sie sich mit diesem Benutzer und Passwort an und ändern Sie das Passwort dieses Benutzers in einen sicheren Wert. Überprüfen Sie alle Benutzer, um sicherzustellen, dass sie legitim sind. Wenn Sie gehackt wurden, möchten Sie möglicherweise alle Passwörter auf der Seite ändern.

### Einen neuen Super User hinzufügen

Wenn das Ändern des Passworts nicht funktioniert oder Sie nicht sicher sind, welcher Benutzer Mitglied der Super User-Gruppe ist, können Sie diese Methode verwenden, um einen neuen Super User zu erstellen.
1. Öffnen Sie phpMyAdmin und wählen Sie die Datenbank für die Joomla!-Seite aus.
2. Wählen Sie die *SQL*-Schaltfläche in der Symbolleiste aus, um eine SQL-Abfrage in der ausgewählten Datenbank auszuführen. Dies zeigt ein Feld namens „SQL-Abfrage(n) in Datenbank xxxxx ausführen“ an.
3. Löschen Sie jeglichen Text in diesem Feld und kopieren und fügen Sie die folgende Abfrage ein. Denken Sie daran, `xxxxx` durch Ihr eigenes Datenbankpräfix zu ersetzen.
    ```
    INSERT INTO `xxxxx_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `xxxxx_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');
    ```
    Wählen Sie die Schaltfläche *Go*, um die Abfrage auszuführen und den neuen Super User zur Tabelle hinzuzufügen.

Zu diesem Zeitpunkt sollten Sie sich mit dem Benutzernamen *admin2* und dem Passwort *secret* im Backend von Joomla! anmelden können.

Nach der Anmeldung gehen Sie zur Benutzerliste und ändern das Passwort in einen neuen, sicheren Wert und fügen eine gültige E-Mail-Adresse zum Konto hinzu.

Wenn die Möglichkeit besteht, dass Sie *gehackt* wurden, stellen Sie sicher, dass alle Benutzer legitim sind, insbesondere alle Mitglieder der Super User-Gruppe.

## Alternative Temporäre Passwörter

**Warnung:** Die auf dieser Seite gezeigten Passwortwerte sind öffentlich bekannt und dienen nur der Wiederherstellung. Um zu verhindern, dass Ihr Konto gehackt wird, sollten Sie ein temporäres Passwort nach dem Einloggen in einen sicheren Wert ändern.

    password = "das ist das MD5 und gesalzene, gehashte Passwort"
    ------------------------------------------------------
    admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm

*Übersetzt von openai.com*

