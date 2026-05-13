<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Feldparameter ",
  "description": "", 
  "author": ""
}
-->

## Felddaten-Eingabeformular

Im Felddaten-Eingabeformular stehen 16 oder mehr Feldtypen zur Auswahl aus der Listenauswahl zur Verfügung. Die meisten Formularfelder sind bei allen Feldtypen gleich, aber einige ändern sich je nach ausgewähltem Typ. Dieser Beitrag beschreibt die gemeinsamen Parameter für alle Felder. Das Eingabeformular ist auch bei Feldern für **Beiträge**, **Kontakt** und **Benutzer** sowie deren Kategoriefelder gleich.

Eine Felderliste wird zunächst leer sein. Um zu beginnen, zum Beispiel mit Beitragsfeldern:
* Wählen Sie **Neu** aus der Symbolleiste in der Liste Beiträge: Felder.

Das Formular besteht aus einem Titelfeld und vier Registerkarten.

![Allgemeine Registerkarte der Feldparameter](../../../en/images/fields/adding-custom-fields-parameters/01-fields-parameters-general-tab.png)

## Titel

Der Titel wird auf der *Beiträge: Felder* Listen-Seite angezeigt, wo er ausgewählt werden kann, um das Feld zur Bearbeitung zu öffnen. Der Titel wird nicht angezeigt, wenn Sie einen Beitrag erstellen oder im Frontend. Der Titel kann jedoch als Beschriftung verwendet werden und wird im Datenformular für Beiträge angezeigt und kann in der Beitragsanzeige angezeigt werden.

### Allgemeine Registerkarte

#### Im linken Bereich:

- **Typ** Wählen Sie einen der 16 Feldtypen aus der Dropdown-Liste aus. Wenn Sie das Feld speichern, ist dieser Typ dauerhaft. Sie können ihn später nicht ändern.
- **Name** Der Name wird verwendet, um das Feld zu identifizieren. Lassen Sie dies leer und Joomla wird einen Standardwert aus dem Titel einfügen.
- **Beschriftung** Verwenden Sie eine beschreibende Beschriftung für das Feld. Dieser Text ist nicht übersetzbar. Wenn Sie keinen Text für eine Beschriftung eingeben, wird der Titeltext als Beschriftungstext verwendet.
- **Beschreibung** Text, der als Tooltip angezeigt wird, um den Zweck des Feldes während der Dateneingabe zu beschreiben. Dieser Text ist nicht übersetzbar und wird nicht im Frontend angezeigt.
- **Erforderlich** Auf *Ja* setzen, wenn dies ein Pflichtfeld ist, das vor dem Absenden eines Beitrags ausgefüllt werden muss.
- **Nur für Unterformular verwenden** Erklärung erforderlich [ToDo]
- **Standardwert** Legen Sie einen Standardwert fest, wenn dies angemessen ist. Dieser Text ist nicht übersetzbar.
- **Filter** Wählen Sie eine der verfügbaren Optionen aus der Dropdown-Liste aus. Das Feld wird auf Übereinstimmung mit dem ausgewählten Datentyp geprüft.
- **Maximale Länge** Setzen Sie dies, um die Länge der eingegebenen Textdaten zu begrenzen.

### Im rechten Bereich:

- **Status** Wählen Sie einen Veröffentlichungsstatus aus *Veröffentlicht*, *Nicht veröffentlicht*, *Archiviert* oder *Papierkorb*.
  - Veröffentlicht: Das Feld ist beim Bearbeiten eines Beitrags oder eines Kontakts sichtbar. Und es ist im Frontend sichtbar.
  - Nicht veröffentlicht: Das Feld wird Benutzern beim Bearbeiten eines Beitrags oder eines Kontakts nicht angezeigt.
  - Archiviert: Das Feld wird nicht mehr bei der Bearbeitung eines Beitrags oder eines Kontakts angezeigt. Sie können es im Feldmanager öffnen, wenn Sie den Filter auf archiviert setzen.
  - Papierkorb: Das Feld wird gelöscht, befindet sich aber noch in der Datenbank. Es kann mit der Funktion Papierkorb leeren im Feldmanager endgültig aus der Datenbank gelöscht werden.
- **Feldgruppe** Wählen Sie Keine oder eine Gruppe aus einer vordefinierten Liste. Gruppen erscheinen als separate Registerkarten im Datenformular für Beiträge.
- **Kategorie** Sie können ein Feld einer oder mehreren Feldkategorien zuweisen. Beachten Sie, dass der Standardwert *Alle* keine *unkategorisierten* Beiträge einschließt.
- **Zugriff** Die Zugriffsberechtigung für die Anzeige dieses Feldes.
- **Sprache** Wählen Sie die Sprache für dieses benutzerdefinierte Feld. Wenn Sie die Mehrsprachigkeitsfunktion von Joomla nicht nutzen, belassen Sie die Standardeinstellung *Alle*.
- **Notiz** Ein optionales Feld, um persönliche Notizen für das Feld zu machen.

### Optionen Registerkarte

![Feldparameter allgemeinen Registerkarte](../../../en/images/fields/adding-custom-fields-parameters/02-fields-parameters-options-tab.png)

#### Formularoptionen

- **Platzhalter** Ein Platzhaltertext, der als Hinweis für die Eingabe im benutzerdefinierten Feld angezeigt wird. Der Platzhalter ist im Backend aktiv, wenn ein Beitrag erstellt wird. Im Frontend sehen Sie ihn nicht.
- **Feldklasse** Die Klassenattribute des Feldes, wenn das Feld dargestellt wird. Wenn unterschiedliche Klassen benötigt werden, listen Sie diese mit Leerzeichen auf.
- **Beschriftungsklasse (Formular)** Die Klassenattribute des Feldes im Bearbeitungsformular. Wenn unterschiedliche Klassen benötigt werden, listen Sie diese mit Leerzeichen auf.
- **Bearbeitbar in** In welchem Teil der Seite soll das Feld angezeigt werden: Webseite, Administrator oder Beide.
- **Showon-Attribut** Zeigen oder verbergen Sie das Feld bedingt abhängig vom Wert anderer Felder. Die syntax, die hier zu verwenden ist, zum Beispiel:
  - `list-of-items:value1[OR]list-of-items:value2` wo
  - list-of-items: Der Name eines bereits erstellten Feldes, von dem dieses Feld abhängt.
  - value1: Der erforderliche Wert im Feld list-of-items, damit dieses Feld angezeigt wird.
  - [OR] Um eine Auswahl zwischen mehreren Feldern zu treffen. In dem Beispiel wird dieses Feld angezeigt, wenn das Feld list-of-items den Wert value1 ODER value2 hat.
  - [AND] Um mehrere Felder zu kombinieren. Dieses Feld wird nur angezeigt, wenn die Felder list-of-items den Wert value1 UND value2 haben.
  - Sie können auch den Wert "nicht gleich" wie in list-of-items!:value1 verwenden. Die Syntax wird dieses Feld nur anzeigen, wenn list-of-items ungleich value1 ist.
  - Um dieses Feld anzuzeigen, wenn das Feld list-of-items ausgewählt wurde und keinen leeren Wert hat, verwenden Sie die Syntax list-of-items!: (ohne einen angegebenen Wert).
  - Hinweis: Unterformularfelder behandeln den Namen von list-of-items anders. Wenn Sie ein Unterformularfeld erstellen und dieses bedingte Feld für ein Feld hinzufügen, das Sie dort erstellen, müssen Sie field[ID] anstelle von list-of-items verwenden, wobei ID die ID des Feldes list-of-items ist. Das showon-Attribut für dieses bedingte Feld, das Sie erstellen, muss daher lauten: field36:value1[OR]field36:value2, wobei 36 die ID des Feldes 'Liste der Artikel' ist. Dies bedarf der Klärung!

#### Anzeigeoptionen

- **Anzeigeklasse** Die Klasse des Feldcontainers in der Ausgabe.
- **Wertklasse** Die Klasse des Feldwerts in der Ausgabe.
- **Beschriftung** Zeigen oder Verbergen der Beschriftung.
- **Beschriftungsklasse (Ausgabe)** Die Ausgabeklasse der Beschriftung, wenn die Beschriftung angezeigt wird.
- **Automatische Anzeige** Joomla bietet einige Inhaltsereignisse, die während des Inhaltsherstellungsprozesses ausgelöst werden. Dies ist der Ort, an dem definiert wird, wie die benutzerdefinierten Felder in den Inhalt integriert werden sollen. Sie können *Nach Titel*, *Vor der Anzeige des Inhalts*, *Nach der Anzeige des Inhalts* oder *Nicht automatisch anzeigen* wählen.
- **Präfix** Fester Text, der vor einem Feld angezeigt wird, zum Beispiel £.
- **Suffix** Fester Text, der nach einem Feld angezeigt wird, zum Beispiel EUR.
- **Layout** Wählen Sie ein Layout aus den verfügbaren Vorlagen und Überschreibungen.
- **Anzeige bei Nur-Lese** Wählen Sie aus *Vererben*, *Ja* oder *Nein*. Wenn das Feld nur lesezugriff hat (möglicherweise hat der Benutzer nicht die erforderliche Zugriffsebene), sollte das Feld angezeigt oder versteckt werden.

#### Intelligente Suche

- **Suchindex** Wählen Sie aus der Liste der Optionen. Warnung: Wenn *Durchsuchbar machen* ausgewählt ist, wird der Inhalt aus dem Feld mit den Anzeigezielen des Inhaltselements indexiert. Dies kann zu unerwarteter Informationsoffenlegung führen.

### Veröffentlichung Registerkarte

![Feldparameter allgemeinen Registerkarte](../../../en/images/fields/adding-custom-fields-parameters/03-fields-parameters-publishing-tab.png)

### Berechtigungen Registerkarte

Die Berechtigungen für jede Benutzergruppe sind selbsterklärend für die Aktionen *Löschen*, *Bearbeiten* und *Status bearbeiten*. Die Berechtigungen zeigen, wer was mit dem gesamten Feld tun darf – also z. B. es löschen, ändern oder dessen Veröffentlichung aufheben.

![Feldparameter allgemeinen Registerkarte](../../../en/images/fields/adding-custom-fields-parameters/04-fields-parameters-permissions-tab.png)

Die Berechtigung *Benutzerdefinierten Feldwert bearbeiten* kann verwirrend sein. Sie legt fest, wer den Inhalt des Feldes ändern darf. Standardmäßig ist sie für alle Gruppen außer den Super Benutzern auf **Nicht erlaubt (Vererbt)** gesetzt. Zwei Beispiele:

* **Benutzerdefinierte Registrierungsdaten**
  Angenommen, Sie erstellen ein Benutzerfeld für *Geschlecht*, das einem Benutzerregistrierungsformular hinzugefügt wird. Dies könnte eine Liste oder eine Radio-Button-Auswahl sein, mit der ein Benutzer *männlich* oder *weiblich* auswählen kann. In diesem Fall muss die Berechtigung für die Gruppe „Öffentlich“ auf *Erlaubt* gesetzt werden. Andernfalls kann ein Gastbenutzer kein Geschlecht auswählen. Da alle anderen Gruppen von „Öffentlich“ erben, kann ein registrierter Benutzer die Geschlechtsangabe im Profil nach dem Login ändern.
* **Artikelkommentar**
  Angenommen, Sie möchten einem Autor erlauben, einen Kommentar zu einem Artikel hinzuzufügen. Dies könnte ein Textfeld mit begrenzter Länge sein. In diesem Fall muss die Berechtigung für die Gruppe „Autor“ auf *Erlaubt* gesetzt werden. Die Gruppen „Redakteur“ und „Publisher“ erben diese Einstellung, wenn das Formular gespeichert wird. Die Gruppen „Manager“ und „Administrator“ haben zwar die Bearbeitungsberechtigung für Artikel, jedoch nicht für benutzerdefinierte Feldwerte – es sei denn, der Wert für „Manager“ wird ebenfalls auf *Erlaubt* gesetzt.

*Übersetzt von openai.com*

