<!--
{
  "source": "https://docs.joomla.org/J4.x:Optional_Technical_Requirements",
  "title": "Optionale Technische Anforderungen",
  "description": "", 
  "author": ""
}
-->

Diese Seite listet *optionale* technische Anforderungen auf, die nicht erforderlich
sind, um Joomla! zu installieren und auszuführen, jedoch für einige interne APIs benötigt werden. Die Liste
wurde für Joomla 4 erstellt.

| Punkt                     | Beschreibung                                                                                                                                   |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Anwendung**             |                                                                                                                                                 |
| JApplicationDaemon        | Erfordert PHPs `ext/pcntl` und `ext/posix`                                                                                                      |
| **Archiv**                |                                                                                                                                                 |
| BZ2                       | Erfordert PHPs `ext/bz2`                                                                                                                        |
| GZip                      | Erfordert PHPs `ext/zlib`                                                                                                                       |
| Zip                       | Erfordert PHPs `ext/zip` oder `ext/zlib`                                                                                                        |
| **Cache**                 |                                                                                                                                                 |
| APC                       | Erfordert PHPs `ext/apc` auf PHP 5.3 oder 5.4, `ext/apcu` auf PHP 5.5 oder 5.6, nicht unterstützt auf PHP 7.x (Hinweis: DIES MUSS ÜBERPRÜFT WERDEN) |
| APCu                      | Erfordert PHPs `ext/apcu` auf PHP 5.3+                                                                                                          |
| CacheLite                 | Erfordert das PEAR Cache_Lite-Paket (getestet auf 1.7.16, funktioniert mit 1.8)                                                                 |
| Memcache                  | Erfordert PHPs `ext/memcache` und einen Memcache-Server (Hinweis: Die Memcache-Erweiterung ist nicht kompatibel mit PHP 7.x)                      |
| Memcached                 | Erfordert PHPs `ext/memcached` und einen Memcached-Server                                                                                       |
| Redis                     | Erfordert PHPs `ext/redis` und einen Redis-Server                                                                                               |
| Wincache                  | Erfordert PHPs `ext/wincache` (nur Windows)                                                                                                     |
| XCache                    | Erfordert PHPs `ext/xcache`                                                                                                                     |
| **Client-Adapter**        |                                                                                                                                                 |
| LDAP                      | Erfordert PHPs `ext/ldap`                                                                                                                       |
| HTTP/Curl                 | Erfordert PHPs `ext/curl`                                                                                                                       |
| HTTP/Socket               | Erfordert die PHP-Funktion `fsockopen()` aktiviert zu sein                                                                                      |
| HTTP/Stream               | Erfordert die PHP-Funktion `fopen()` und `allow_url_fopen` aktiviert zu sein                                                                    |
| **Kryptografie**          |                                                                                                                                                 |
| JCrypt                    | Erfordert PHPs `ext/mcrypt` für alle Chiffren außer SodiumCipher, das `ext/sodium` benötigt                                                     |
| JKeychain                 | Erfordert PHPs `ext/openssl`                                                                                                                    |
| **Datenbank**             |                                                                                                                                                 |
| Microsoft SQL Azure       | Erfordert PHPs `ext/sqlsrv` (die PHP 5.x-Erweiterung unterstützt nur Windows, eine Linux-kompatible Version der Erweiterung ist für PHP 7.x verfügbar) |
| Microsoft SQL Server      | Erfordert PHPs `ext/sqlsrv` (die PHP 5.x-Erweiterung unterstützt nur Windows, eine Linux-kompatible Version der Erweiterung ist für PHP 7.x verfügbar) |
| MySQL                     | Erfordert PHPs `ext/mysql` (nicht unterstützt auf PHP 7.x)                                                                                      |
| MySQLi                    | Erfordert PHPs `ext/mysqli`                                                                                                                     |
| Oracle                    | Erfordert PHPs `ext/pdo` mit Oracle-Unterstützung (nur für 3PD verfügbar; das CMS funktioniert damit nicht)                                     |
| PDO MySQL                 | Erfordert PHPs `ext/pdo` mit MySQL-Unterstützung                                                                                                |
| PostgreSQL                | Erfordert PHPs `ext/pgsql`                                                                                                                      |
| SQLite                    | Erfordert PHPs `ext/pdo` mit SQLite-Unterstützung (nur für 3PD verfügbar; das CMS funktioniert damit nicht)                                    |
| **Bild**                  |                                                                                                                                                 |
|                           | Erfordert PHPs `ext/gd`                                                                                                                         |
|                           | Erfordert PHPs `ext/fileinfo`                                                                                                                   |
| **Sitzung**               |                                                                                                                                                 |
| APC                       | Erfordert PHPs `ext/apc` auf PHP 5.3 oder 5.4, `ext/apcu` auf PHP 5.5 oder 5.6, nicht unterstützt auf PHP 7.x (Hinweis: DIES MUSS ÜBERPRÜFT WERDEN) |
| Memcache                  | Erfordert PHPs `ext/memcache` und einen Memcache-Server (Hinweis: Die Memcache-Erweiterung ist nicht kompatibel mit PHP 7.x)                      |
| Memcached                 | Erfordert PHPs `ext/memcached` und einen Memcached-Server                                                                                       |
| Wincache                  | Erfordert PHPs `ext/wincache` (nur Windows)                                                                                                     |
| XCache                    | Erfordert PHPs `ext/xcache`                                                                                                                     |
| **OPTIONALE VERBESSERUNGEN** |                                                                                                                                                 |
| **String**                |                                                                                                                                                 |
| mbstring                  | Aktivieren Sie PHPs `ext/mbstring` für die phputf8-Bibliothek, um native Funktionen zu verwenden                                                |

*Übersetzt von openai.com*
