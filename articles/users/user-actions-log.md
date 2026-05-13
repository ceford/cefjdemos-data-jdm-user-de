<!--
{
  "source": "https://docs.joomla.org/J4.x:User_Actions_Log",
  "title": "Benutzeraktionsprotokoll ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die Benutzeraktionsprotokoll-Komponente (com_actionlogs) bietet eine Infrastruktur zur Erstellung eines Protokolls der Website-Aktivitäten. Die protokollierten Aktionen können vom Site-Administrator fein abgestimmt werden. Drittanbieter-Erweiterungen können sich in die Komponente einhängen, um benutzerdefinierte Nachrichten hinzuzufügen oder das System Standard-Administratoraktionen verarbeiten zu lassen.

**Hinweis:** Nur Super User haben Zugriff auf die Benutzeraktionsprotokoll-Komponente.

## Benutzertätigkeiten-Protokoll

Um die Liste der Benutzertätigkeiten-Protokolle anzusehen:

- Wähle **Benutzer → Benutzertätigkeiten-Protokoll** im Administrator-Menü.

![Benutzertätigkeiten-Logliste-Seite](../../../en/images/users/user-actions-log/01-user-actions-log-list.png)

Von dieser Seite aus hat ein Super-User einen globalen Überblick über alle Benutzeraktivitäten, die auf der Website durchgeführt wurden.

- Ausgewählte als CSV exportieren: Diese Schaltfläche exportiert nur die im sichtbaren Bereich ausgewählten Einträge.
- Alle als CSV exportieren: Diese Schaltfläche exportiert alle Einträge. Die Filter werden ignoriert.
- Löschen: Diese Schaltfläche löscht die ausgewählten Einträge.
- Protokoll löschen: Diese Schaltfläche löscht alle Protokolleinträge.
- Optionen: Ein Konfigurationsformular zum Festlegen der Protokollierungsoptionen.

## Optionen

Das Formular "Benutzeraktionsprotokoll: Optionen" ermöglicht dem Superuser, auszuwählen, welche Ereignisse protokolliert werden sollen und ob IP-Adressen in die Protokolldaten aufgenommen werden sollen.

![Seite mit den Benutzeraktionsprotokoll-Optionen](../../../en/images/users/user-actions-log/02-user-actions-log-options.png)

## Plugins

Das Aktionsprotokollsystem verwendet eine Reihe von Plugins:

### Aktionsprotokoll - Joomla

Wenn dieses Plugin aktiviert ist, protokolliert es die Kernaktionen der Benutzer, einschließlich solcher Aktionen wie Anmelden/Abmelden, Beitrag aktualisieren, Modul hinzufügen. Das Plugin hat keine Parameter.

### System - Benutzeraktionsprotokoll

Wenn dieses Plugin aktiviert ist, definiert es die Anzahl der Tage, nach denen die Protokolle gelöscht werden. Ein Wert von null bedeutet, dass die Protokolle nie automatisch gelöscht werden.

### Datenschutz - Aktionsprotokolle

Wenn dieses Plugin aktiviert ist, exportiert es die Aktionsprotokolldaten für einen Datenschutzantrag eines Benutzers.

## Modul "Letzte Aktionen"

Dieses Modul wird nur für Superuser im Home-Dashboard angezeigt.

![Benutzeraktionen-Log-Modul](../../../en/images/users/user-actions-log/03-user-actions-log-module.png)

## So verbinden Sie eine Erweiterung mit dem System

Bitte zögern Sie nicht, diesen Abschnitt zu bearbeiten, indem Sie ihn verbessern oder korrigieren.

### Komponenten-Installationsskript

Fügen Sie die Erweiterung der Tabelle (`#__action_logs_extensions`) hinzu, damit sie in der Konfiguration der Benutzeraktionsprotokolle erscheint.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Wenn es fehlschlägt, wirft es eine RuntimeException
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Fügen Sie die Erweiterungskonfiguration der Tabelle (`#__action_log_config`) hinzu, damit Ihre Aktionsdaten erfasst werden.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transaktion';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Wenn es fehlschlägt, wirft es eine RuntimeException
                // Fügen Sie das Objekt in die Tabelle ein.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Natürlich wäre es am besten, einige Überprüfungen durchzuführen, um sicherzustellen, dass der Datensatz nicht bereits existiert.

### Komponenten-Helfer

In diesem Beispiel wird der Komponenten-Helfer verwendet, um die Speicherung von Aktionen durchzuführen.
```php
       /**
         * Transaktionsdetails im Protokolldatensatz aufzeichnen
         * @param   object  $user    Spart sich das erneute Abrufen des aktuellen Benutzers.
         * @param   int     $tran_id  Die gerade erstellte oder aktualisierte Transaktions-ID
         * @param   int     $id  Übergebene ID-Referenz aus dem Formular zur Identifizierung, ob neuer Datensatz
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // Holen Sie sich die Komponentendetails wie die ID
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // Holen Sie sich die Transaktionsdetails zur Verwendung im Protokoll zur einfachen Referenz
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transaktion";
            if ($id === 0) { $type = 'Neue '; } else { $type = 'Aktualisierung '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Holen Sie sich das Modell von einer anderen Komponente für die Verwendung
         * @param   string  $name    Der Modellname. Optional. Standardmäßig mein eigenes aus Sicherheitsgründen.
         * @param   string  $prefix  Der Klassenvorsatz. Optional
         * @param   array   $config  Konfigurationsarray für das Modell. Optional
         * @return object   Das Modell
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Front-End-Transaktionsformular

Jetzt, da die Grundlagen gelegt sind, müssen wir nur den Prozess auslösen. Wir erfassen Informationen über eine Transaktion, die erstellt oder aktualisiert wurde, und wir haben ein Modell namens `transactionform.php`. Es ist in der Speichermethode, dass wir ein Protokoll erfassen wollen.
```php
       // Der Code oberhalb dieses Punktes überprüft und tut, was er tun soll, und dann nach dem erfolgreichen Speichern des Datensatzes überprüfen wir die Parametereinstellung, um zu sehen, ob die Protokollierung erforderlich ist, und übergeben Schlüsselinformationen an recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // Transaktionsprotokoll auslösen, falls erforderlich
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // Informationen sammeln und in einem neuen Aktionsprotokolldatensatz protokollieren
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### Sprachdatei

Schließlich, um bei der Aktionsprotokoll-Auflistung im Admin-Bereich von Joomla zu helfen, wollen wir einige Schlüsselelemente der Daten in der Sprachdatei en-GB/com_mycomponent.ini anzeigen lassen.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="Benutzer {username} hat eine Transaktion ( {type} ) erstellt"
```

*Übersetzt von openai.com*

