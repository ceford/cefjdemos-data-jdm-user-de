<!--
{
  "source": "https://docs.joomla.org/How_do_you_password_protect_directories_using_htaccess%3F",
  "title": "Verzeichnisse mit einem Passwort schützen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Vielleicht möchten Sie ein Verzeichnis oder eine gesamte Website vor öffentlichem Zugriff schützen. Ein Grund hierfür ist, den öffentlichen Zugriff auf eine Entwicklungsseite zu verweigern. Nur diejenigen, die den Benutzernamen und das Passwort kennen, erhalten Zugang. Ein weiterer Grund könnte Paranoia sein – zum Beispiel der Schutz des Administrator-Ordners, sodass Benutzer einen Benutzernamen und ein Passwort eingeben müssen, nur um Zugriff auf das Joomla-Administrator-Login-Formular zu erhalten.

Die hier beschriebene Methode ist für Apache-Server unter Verwendung einer *.htaccess*-Datei.

### Warnhinweis von Apache.org

Die einfache Authentifizierung sollte nicht als sicher im Sinne einer besonders strengen Definition von sicher betrachtet werden. Auch wenn das Passwort auf dem Server verschlüsselt gespeichert wird, kann es dennoch im Klartext vom Client zum Server über das Netzwerk gesendet werden. Jeder, der mit einem beliebigen Paket-Sniffer mithört, kann den Benutzernamen und das Passwort lesen, während sie übertragen werden.

Der Benutzername und das Passwort werden mit jeder Anfrage übermittelt, nicht nur, wenn der Benutzer sie zuerst eingibt. Der Paket-Sniffer muss also nicht zu einem besonders günstigen Zeitpunkt lauschen, sondern lediglich lange genug, um irgendeine einzelne Anfrage über das Netz zu sehen.

Darüber hinaus werden die Inhalte selbst ebenfalls unverschlüsselt über das Netzwerk übertragen, sodass, wenn die Website sensible Informationen enthält, der gleiche Paket-Sniffer Zugriff auf diese Informationen hätte, selbst wenn der Benutzername und das Passwort nicht verwendet werden, um direkten Zugriff auf die Website zu erlangen.

Verwenden Sie keine einfache Authentifizierung für etwas, das echte Sicherheit erfordert. Für die meisten Benutzer ist dies ein Nachteil, da nur wenige Menschen sich die Mühe machen oder die notwendige Software oder Ausrüstung haben, um Passwörter herauszufinden. Wenn jedoch jemand den Wunsch hätte, sich Zugang zu verschaffen, bräuchte er dafür sehr wenig.

Eine einfache Authentifizierung über eine SSL-Verbindung hingegen wird sicher sein, da alles verschlüsselt wird, einschließlich des Benutzernamens und des Passworts.

## Verwendung von cPanel

Wenn Sie einen Hosting-Dienst verwenden, sollten Sie dessen Methode zum Verzeichnisschutz nutzen. Beispielsweise hat cPanel eine Option namens Verzeichnisschutz. Bei Auswahl können Sie zu einem beliebigen Verzeichnis navigieren und einen Namen dafür festlegen. Sie haben dann die Möglichkeit, einen Benutzername und ein Passwort für das benannte Verzeichnis zu erstellen. Einfach?

Wenn Sie nun in das geschützte Verzeichnis schauen, finden Sie eine neue .htaccess-Datei, die etwas enthält wie das Folgende, um den Joomla-API-Ordner zu schützen:

```
#----------------------------------------------------------------cp:ppd
# Abschnitt, verwaltet von cPanel: Passwortgeschützte Verzeichnisse -cp:ppd
# - Bearbeiten Sie diesen Abschnitt der htaccess-Datei nicht!       -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/username/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Abschnittsende, verwaltet von cPanel: Passwortgeschützte Verzeichnisse -cp:ppd
#----------------------------------------------------------------cp:ppd
```
Es ist wichtig zu wissen, dass der Verzeichnisschutz von cPanel möglicherweise dieselbe .htaccess-Datei verwendet, die von Joomla für andere Zwecke verwendet wird.

Wenn Sie in die zitierte passwd-Datei schauen, sehen Sie den von Ihnen bereitgestellten Benutzernamen und die verschlüsselte Version des Passworts.

Der Schutz kann entfernt werden, indem Sie den Vorgang wiederholen und das Kontrollkästchen `Dieses Verzeichnis mit einem Passwort schützen.` deaktivieren. Dadurch wird der Authentifizierungsabschnitt aus der .htaccess-Datei entfernt. Es entfernt nicht die .htaccess-Datei!

## .htaccess-Regeln

Sie können alle erforderlichen Schritte manuell durchführen. Dieses Tool kann helfen:

<a href="https://www.htaccessredirect.net/"
   rel="nofollow noreferrer noopener"><em>.htaccess</em>-Generator</a>

Es erstellt die notwendigen Dateien für Sie. Sie müssen den Benutzernamen,
das Passwort und den Pfad angeben.

Füllen Sie die beiden Abschnitte aus: **Datei mit Passwortschutz** und **htpasswd-Generator** und wählen Sie dann die Schaltfläche `Code generieren` aus. Sie erhalten den Text für die .htaccess-Datei und den Text für die .htpasswd-Datei in separaten Feldern zurück. Beispiele:
```
//Datei mit Passwortschutz
<Files /admin>
AuthName "Prompt"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Übersetzt von openai.com*

