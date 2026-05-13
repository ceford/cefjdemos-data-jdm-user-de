<!--
{
  "source": "https://docs.joomla.org/J4.x:Assorted_Issues",
  "title": "Verschiedene Beiträge  ",
  "description": "", 
  "author": ""
}
-->

## Weiterleitungsproblem nach dem Upgrade auf 4.0.6

Das ist ein Fehler! Zeile 243 von *plugins/system/redirect/redirect.php*:

       $db->updateObject('#__redirect_links', $redirect, 'id');

sollte sein

       $this->db->updateObject('#__redirect_links', $redirect, 'id');

## Eine Seite wird ohne Styling angezeigt

Mögliche Ursache: Ein gzip-Abschnitt in der *.htaccess*-Datei komprimiert die bereits komprimierten CSS- und JavaScript-Dateien.

Siehe diesen Abschnitt der *.htaccess*-Datei:

    ## Diese Direktiven sind nur aktiviert, wenn das Apache-Modul mod_headers aktiviert ist.
    ## Dieser Abschnitt prüft, ob eine .gz-Datei vorhanden ist und streamt sie
    ##     direkt oder fällt darauf zurück, alle Assets im Schnellverfahren zu gzip-komprimieren
    ## Wenn Ihre Webseite nach der Aktivierung seltsam aussieht und Sie
    ##     ERR_CONTENT_DECODING_FAILED im Netzwerk-Tab Ihrer Browserkonsole sehen,
    ##     dann gzip-komprimiert Ihr Server bereits CSS- und JS-Dateien und Sie brauchen diesen
    ##     Block nicht in Ihrer .htaccess zu aktivieren.

    ...

Falls vorhanden, auskommentieren oder entfernen.

## Die Liste der Seitenmodule ist leer

Mögliche Ursache: Die Größe des MySQL-Sortierpuffers ist möglicherweise zu klein.

Gehen Sie mit phpMyAdmin zu **Home**→**Variablen**→**Sortierpuffergröße**.

Sie sollte mindestens 256K und vorzugsweise 512K betragen. Bei einigen Shared-Hosting-Diensten könnte sie auf 128K eingestellt sein. Bitten Sie den Hosting-Dienst darum, sie zu vergrößern.

## Aktualisierung schlägt nach dem Update auf 4.0.4 fehl

Ursache: Eine wesentliche Änderung am Aktualisierungsverfahren betrifft eine kleine Anzahl von Benutzern.

Suchen Sie in *.htaccess* nach dieser Zeile:

    RewriteRule ^administrator/components/com_joomlaupdate/restore\.php$ - [L]

Ändern Sie sie zu:

    RewriteRule ^administrator\/components\/com_joomlaupdate\/extract\.php$ - [L]

Für weitere Informationen siehe:

<a href="https://www.joomla.org/announcements/release-news/5850-changes-to-update-process-that-you-need-to-be-aware-of.html" rel="noreferrer noopener">Änderungen im Aktualisierungsprozess, die Sie kennen sollten</a>

## Beiträge sichtbar in Datenbank und Frontend, aber nicht im Backend

Dies tritt auf, wenn Beiträge direkt in die Datenbank importiert werden, was in Joomla 3 problemlos funktionierte, aber in Joomla 4 nicht. Die Lösung eines Nutzers ist wie folgt:

    Ich habe Beiträge direkt in die Datenbank in die Tabelle #__content importiert, so wie ich es oft in Joomla 3 gemacht habe.
    In Joomla 4 waren sie jedoch nicht sichtbar.

    In Inhalt > Kategorien zählten die Kategorien-Elementzähler die importierten Beiträge.
    Aber sie waren nicht sichtbar unter Inhalt > Beiträge.

    Ich habe es gelöst, indem ich die notwendigen Verweise in der Tabelle #__workflow_associations für jeden importierten Artikel erstellt habe:
    item_id = Beitrags-ID, stage_id = 1 und extension = com_content.article.

Mit diesem Hinweis von einem anderen Nutzer:

Diese Abfrage sollte das für dich erledigen. Ersetze \#\_\_ durch dein eigenes Datenbank-Präfix.

Diese Abfrage verhindert doppelte Einträge in der Workflow-Verknüpfungenstabelle

    INSERT INTO #__workflow_associations (item_id, stage_id, extension) 
    SELECT c.id as item_id, '1', 'com_content.article' FROM #__content AS c 
    WHERE NOT EXISTS (SELECT wa.item_id FROM #__workflow_associations AS wa WHERE wa.item_id = c.id);

*Übersetzt durch openai.com*

