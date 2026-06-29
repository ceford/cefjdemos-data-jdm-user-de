<!--
{
  "source": "https://docs.joomla.org/J5.x:Enhancing_Password_Security_with_Symbolic_Characters",
  "title": "Benutzer-Passwort-Sicherheit",
  "description": "", 
  "author": ""
}
-->

## Einführung

Im *Benutzer: Optionen* Formular auf dem Tab *Passwortoptionen* sind die Mindestwerte für *Zahlen*, *Symbole*, *Großbuchstaben* und *Kleinbuchstaben* standardmäßig alle auf 0 gesetzt. Für eine bessere Sicherheit sollten diese Werte auf 1 gesetzt werden. Neue oder geänderte Passwörter müssen dann jeweils eines dieser Zeichen enthalten.

## Symbole

Das *Open Worldwide Application Security Project* (OWASP) empfiehlt, dass alle Sonderzeichen, die auf einer Standard-US-Tastatur verfügbar sind, erkannt und akzeptiert werden, wenn es um Passwortrichtlinien geht.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Es ist nicht offensichtlich, aber diese Liste beinhaltet das Leerzeichen.

[OWASP: Passwort-Sonderzeichen](https://owasp.org/www-community/password-special-characters)

Vor Version 5.2 konnten diese Symbole in Passwörtern verwendet werden, aber einige von ihnen wurden nicht als Symbole für die Passwortvalidierung erkannt: 
```
@[]£^+±~<>/'",.
``` 

*Übersetzt von openai.com*  

