<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "Einrichtung der lokalen Umgebung",
    "description": "",
    "author": ""
}
-->

Seit Joomla! 4 haben wir den Entwicklungsprozess geändert. Es ist nicht mehr
möglich, das Repository zu klonen und eine nutzbare Joomla-Installation zu
erhalten.
Wir folgen Best Practices und implementieren einen Build-Prozess für das CMS.

## Kurzanleitung

Die Schritte zur Einrichtung Ihrer Entwicklungsumgebung hängen von Ihrem
Betriebssystem ab. Wir können keine Dokumentation für jedes Betriebssystem (OS)
verfassen. Bitte verwenden Sie Ihre bevorzugte Suchmaschine, um eine
entsprechende Anleitung zu finden.

### Benötigte Tools

1.  PHP – im Grunde dasselbe, was Sie zum Betreiben einer Joomla-Website benötigen, aber
    Sie benötigen die PHP-CLI-Version (Befehlszeilenschnittstelle). (Siehe
    die Seite [Konfigurieren eines LAMPP-Servers für die PHP-Entwicklung](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer – zur Verwaltung der PHP-Abhängigkeiten von Joomla. Hilfe bei der
    Installation von Composer finden Sie in der Dokumentation
    unter <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js – zum Kompilieren der JavaScript- und SASS-Dateien von Joomla. Hilfe bei der
    Installation von Node.js finden Sie in den Anweisungen unter
    <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Hinweis,    Sie benötigen NodeJS 12 oder höher, um Joomla zu installieren.
4.  Git – für die Versionsverwaltung.

### Schritte zum Einrichten der lokalen Umgebung

1.  Repository klonen
2.  Den Branch der neuesten Version auschecken.
3.  Führen Sie `composer install` (Composer = Paketmanager für PHP) im
    Stammverzeichnis des Git-Repositorys aus. (Sie können *--ignore-platform-reqs*
    hinzufügen, wenn PHP-LDAP lokal nicht installiert ist und Sie es nicht
    benötigen.)
4.  Führen Sie `npm ci` (npm = Paketmanager für JavaScript, der Parameter „ci“
    bedeutet „saubere Installation“) im Stammverzeichnis des Git-Repositorys aus.
    (Hinweis: Dafür benötigen Sie npm 10.1.0 oder höher.
    Führen Sie `npm install -g npm@lts` aus, um Ihre npm-Version auf die
    LTS-Version zu aktualisieren.)

Linux- und OSX-Benutzer können den folgenden Bash-Alias einrichten, indem sie
Folgendes in die Datei *~/.bashrc* einfügen:

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Dadurch werden alle kompilierten Dateien auf Ihrem System gelöscht und eine
frische Installation als ein einziger Befehl ausgeführt, indem `jinstall` in
Ihrer Joomla-Installation aufgerufen wird.

## Eine etwas längere Anleitung für den Einstieg

Joomla ähnelt heutzutage vielen anderen Webtools. Es besteht zu einem großen Teil
aus PHP und enthält immer mehr JavaScript-Code. Während die PHP-Programmierung
nicht so viel Vorbereitung benötigt, braucht JavaScript eine umfangreiche
Toolchain. Der Hauptgrund ist, dass niemand Code so schreibt, dass ihn jeder
Browser versteht. Daher muss der Code beispielsweise von ES6 in eine kompatible
JavaScript-Version transpiliert werden. Dasselbe gilt für CSS. Für Joomla
verwenden wir SASS, das in natives CSS umgewandelt wird, damit jeder Browser
es versteht. Der Nachteil ist, dass das Einrichten einer Entwicklungsumgebung
etwas komplizierter ist, aber die Tools machen das Programmieren komfortabler.
Dank Watchern und der automatischen Aktualisierung des Browsers können Sie Ihre
Änderungen in Echtzeit sehen.

### PHP

Es sollte ausreichen, `composer install` auszuführen, da dadurch die in der
Datei *composer.lock* gespeicherten PHP-Abhängigkeiten installiert werden.
Sie können dies beliebig oft tun. Neue Pakete werden nur installiert, wenn
die Datei *composer.lock* geändert wurde. Führen Sie nicht `composer update` aus, da dadurch alle
Pakete auf neuere Versionen aktualisiert und die
Datei *composer.lock* aktualisiert wird.

**Hinweis:** Möglicherweise müssen Sie `composer install` mit der
Option `--ignore-platform-reqs` ausführen, um die in Composer angegebenen
Plattformanforderungen zu ignorieren. Dies ist beispielsweise der Fall, wenn
die LDAP-Erweiterung von PHP nicht installiert ist.

### Node/npm-Skripte

Node.js wird mit einem Paketmanager namens NPM ausgeliefert (in mancher
Hinsicht vergleichbar mit Composer). NPM verfügt über einen `run`-Befehl, und
wir haben einige Skripte vorbereitet, um Ihnen das Leben zu erleichtern. Sie
müssen die Befehle im Stammverzeichnis des Repositorys ausführen, wenn Sie
JS- oder SASS-Dateien geändert haben. Zuvor mussten Sie einmal `npm ci` ausführen, um Abhängigkeiten zu installieren.

#### npm run build:css (bis Joomla 6.1)

Kompiliert SASS-Dateien zu CSS und erstellt außerdem die minimierten Dateien.

#### npm run build:js (bis Joomla 6.1)

Kompiliert und transpiliert die JavaScript-Dateien in das korrekte Format
und erstellt minimierte Dateien.

#### Ab Joomla 6.2 verwenden Sie die folgenden Befehle:

- `npm run build -- -n <extension>`, um eine bestimmte Erweiterung neu zu erstellen 
- Führen Sie `npm run builders-list` aus, um den Namen der Erweiterung zu ermitteln
- `npm run build -- --all`, um alles neu zu erstellen

## Mögliche Probleme

Beim Ausführen von composer install können diese Fehler auftreten

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

Die Lösung besteht darin, composer install mit der Option
`--ignore-platform-reqs` auszuführen, um die in Composer angegebenen
Plattformanforderungen zu ignorieren. Dies gilt, wenn die LDAP-Erweiterung
von PHP nicht installiert ist.

```
    composer install --ignore-platform-reqs
```

Wenn ein Anmeldefehler wie der unten gezeigte auftritt, löschen Sie
die Datei `administrator/cache/autoload_psr4.php`.

![Anmeldefehler in Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)



*Übersetzt von openai.com*