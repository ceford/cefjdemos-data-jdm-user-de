<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Verschieben des Installationsverzeichnisses -->

Oftmals installieren Sie Joomla in einem Unterverzeichnis und möchten es dann in ein höheres Verzeichnis verschieben. Hier ist ein kurze Anleitung, wie Sie das tun können.

Angenommen, Sie haben Joomla im folgenden Ordner installiert: public_html/tryjoomla. Nun da Sie mit der Seite zufrieden sind, möchten Sie es nach public_html verschieben.

1. Verschieben Sie alle Dateien aus dem Unterverzeichnis (d.h., public_html/tryjoomla) in das obere Verzeichnis (d.h., public_html). Sie können dafür Ihren bevorzugten FTP-Client oder das Kontrollpanel verwenden, das Ihr Hosting-Dienstleister bereitstellt.
2. Laden Sie die Datei configuration.php herunter und öffnen Sie sie in einem Texteditor.
3. Entfernen Sie einfach den Ordnernamen tryjoomla aus dem Pfad. Suchen Sie nach den folgenden Zeilen:
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/username/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';
    ```
    Ändern zu:
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/administrator/logs';
    var $tmp_path = '/home/username/public_html/tmp';
    var $ftp_root = 'public_html';
    ```
    Hinweis: Die Variable \$live_site muss selten einen Wert haben. Wenn ihr jedoch während der Installation ein Wert zugewiesen wurde, bearbeiten Sie auch diesen Pfad.
    ```
    var $live_site = 'http://www.example.com/tryjoomla';
    ```
    Ändern zu:
    ```
    var $live_site = 'http://www.example.com';
    ```
4. Überprüfen Sie die .htaccess-Datei Ihrer Seite. Der Unterordner sollte dort ebenfalls entfernt werden. Die RewriteBase-Direktive sollte auskommentiert sein. Überprüfen Sie auf eine RewriteRule, die das alte Unterverzeichnis enthält.
5. Stellen Sie sicher, dass keine Weiterleitungsbefehle zum alten Unterverzeichnis in Ihrem Hosting-Kontrollpanel vorhanden sind.
6. Wenn Sie den Cache aktiviert haben, melden Sie sich im Administrator-Backend an (das jetzt unter `http://www.example.com/administrator` und nicht mehr unter `http://www.example.com/tryjoomla/administrator` erreichbar ist). Gehen Sie zu System / Cache und löschen Sie alle Cache-Dateien.

*Übersetzt von openai.com*
