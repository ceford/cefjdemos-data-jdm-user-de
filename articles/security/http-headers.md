<!--
{
  "source": "https://docs.joomla.org/https:",
  "title": "HTTP-Header ",
  "description": "", 
  "author": ""
}
-->

## Zeitschriftenbeitrag

Dieser Beitrag basiert auf einem Beitrag des Joomla! Community Magazins von Brendan Hedges in der Mai 2022 Ausgabe.

Obwohl er für Joomla 4 geschrieben wurde, gilt der Inhalt gleichermaßen für Joomla 5.

## Joomlas neues HTTP-Headers-Plugin für J4

Anknüpfend an den Beitrag des letzten Monats über Sicherheit, Passwörter und Joomlas WebAuthn-Plugin schauen wir uns diesen Monat ein weiteres Joomla-Sicherheitsfeature an, das mit J4 eingeführt wurde. Dabei handelt es sich um das HTTP-Headers-Plugin, das nun Teil der Kernfunktionen von Joomla ist.

Das Internet entwickelt sich ständig weiter, und Joomla bleibt nie dahinter zurück. Deshalb habe ich es zu meiner bevorzugten Plattform für Webentwicklung gewählt. Egal, ob Ihre Website eine kleine lokale Webseite oder eine vollwertige Ecommerce-Plattform mit Millionenumsätzen ist, das Joomla-Framework bietet für jeden etwas und ist immer auf der Suche nach der Implementierung neuer Technologien. Einige davon sind sogar bahnbrechend.

> Die Einführung des HTTP-Headers-Plugins im Kern von Joomla 4 ist ein großer Schritt nach vorne, um Ihre Website vor Angriffen und bösartigen Aktivitäten zu schützen.

Dieses Sicherheitssystem-Plugin hilft Seitenbetreibern, die HTTP-Sicherheits-Header einfach aus Joomlas vertrauter Backend-Oberfläche zu konfigurieren, anstatt umständlich in der htaccess-Datei oder anderen Konfigurationsdateien herumzuwühlen. Oder noch schlimmer, im Webhosting-Cpanel.

Schauen Sie sich an, wie kompliziert dies im Cpanel einzurichten ist, und sagen Sie mir, dass Sie keinen Fehler machen werden! Und das alles unter der Annahme, dass, wenn das Framework einmal in Apache installiert und Verzeichnisse angelegt sind, Sie das richtige Format kennen, um die HTTP-Header hinzuzufügen, die Sie integrieren möchten.

Wie oft haben Sie versucht, einen htaccess-Befehl zu implementieren, nur um Ihre Website neu zu laden und dann mit einem HTTP500-Fehler konfrontiert zu werden?

Das größte Problem ist, dass, wenn das Format Ihrer HTTP-Header nicht perfekt ist, Sie Ihre Website lahmlegen.

Selbst dann, was für eine Website funktioniert, muss nicht unbedingt für eine andere funktionieren. Ein gutes Beispiel dafür ist meine htaccess-Datei und die Art und Weise, wie ich den Browser so einstelle, dass er eine Nicht-www-HTTPS-Version meiner Website lädt:
```
##www zu Nicht-www und http zu https Mixin
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteRule ^ https://meinewebsite.de%{REQUEST_URI} [R=301,L,NE]
##Ende www zu Nicht-www und http zu https Mixin
```

Das funktionierte großartig für mein vorheriges Hosting-Unternehmen. Aber als ich zu einem anderen Host wechselte, funktionierte es nicht mehr. Wer hätte das gedacht!

Der htaccess-Code, den ich jetzt verwenden muss, um das gleiche Ergebnis zu erzielen, sieht so aus:
```
##www zu Nicht-www und http zu https Mixin
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]
RewriteCond %{ENV:HTTPS} !on
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
##Ende www zu Nicht-www und http zu https Mixin
```

Verwirrend, oder? Und wenn Sie einen einzigen Fehler im Format machen, BAM! Sie haben Ihre Website lahmgelegt! Nun, zumindest bis Sie Ihren Code korrigieren.

Deshalb bedeutet die Einfachheit, als Teil des Joomla-Kerns, weniger Frustration, weniger Zeitverschwendung beim Googeln Ihrer Fehler und mehr Zeit für Feierlichkeiten, während Sie sich in Ihrem Stuhl zurücklehnen und Ihre neue Website bewundern.

Schauen wir uns also an, was HTTP-Header eigentlich sind, wie Sie das Plugin finden können und was Sie damit tun können. Es sei jedoch hier erwähnt, dass diese Joomla-Funktion eine fortgeschrittene Funktion von Joomla ist, die eher für datensensible Websites geeignet ist, als die neue Website, die Sie liebevoll über Ihre süßen Kätzchen erstellt haben. Dennoch sollten auch einfache Websites so sicher wie möglich sein, um zu verhindern, dass bösartiger Code ausgeführt wird, nachdem sie Ihre Website gehackt haben.

## Was sind HTTP-Header?

HTTP-Header dürfen nicht mit dem &lt;head&gt;-Abschnitt Ihres HTML-Dokuments verwechselt werden. Sie sind vollkommen unterschiedlich. HTTP-Header sind das Vorwort zwischen Ihrem Webserver und dem Browser. Eine Reihe von Anweisungen, die dem Browser mitteilen, was oder vor allem, was nicht dem Besucher angezeigt werden soll.

Sie können die HTTP-Header und deren Bezug zu einzelnen HTML-Objekten in den Entwicklerwerkzeugen Ihres Browsers sehen. In Google Chrome öffnen Sie die Entwicklerwerkzeuge und dann die Registerkarte Netzwerk. Aktualisieren Sie nun die Webseite und klicken Sie auf ein HTML-Element im linken Bereich. Es wird der HTTP-Header für dieses Element im rechten Bereich angezeigt.

Im Bild unten sehen Sie, dass das hervorgehobene Bild einen HTTP-Status von 200 zurückgibt, also hat der Browser es gefunden. Es gibt auch eine Reihe anderer Informationen, die mit diesem Element verknüpft sind, wie Dateigröße und Bearbeitungsdaten.

![Joomla http headers 1](../../../en/images/security/http-headers/01-http-headers-dev-tools-headers.png)

Wenn eines Ihrer HTML-Elemente nicht angezeigt wird, können Sie möglicherweise auch einen Hinweis auf den Grund in den HTTP-Headern erhalten. In diesem Beispiel wurde das zweite Bild nicht angezeigt, und Sie können der im rechten Bereich angezeigten Information entnehmen, dass keine HTTP-Header-Informationen vorliegen.

Außer der kryptischen Nachricht:

**Referrer-Policy:** „strict-origin-when-cross-origin“

„Strict-origin-when-cross-origin“ bedeutet einfach, dass, wenn ein HTML-Element (in diesem Fall ein Bild) aus einer anderen Quelle (nicht Ihrem Server) geladen wird, die zu diesem Zeitpunkt festgelegte HTTP-Header-Policy eingehalten werden muss. In diesem Beispiel lehnen die HTTP-Header, die im Joomla-Plugin festgelegt sind, alle Bilder ab, die weder von dieser Website noch von einer anderen Website stammen, die explizit in den HTTP-Header-Parametern, die im Joomla HTTP-Header-Plugin festgelegt sind, 'eingeschlossen' ist.

Wenn das Bild also aus dem HTML-Dokument aufgerufen wird, lehnt der Browser es ab und es wird nicht geladen.

![Joomla http headers 2](../../../en/images/security/http-headers/02-http-headers-dev-tools-headers-reject.png)

Dies unterscheidet sich davon, wenn etwas nicht gefunden wird und eine 404-Fehlermeldung „nicht gefunden“ zurückgibt. In diesem Fall wird das Bild immer noch auf dem Server gesucht, auf dem es gehostet wird, aber der Browser hat es nicht gefunden.

![Joomla http headers 3](../../../en/images/security/http-headers/03-http-headers-dev-tools-headers-not-found.png)

## Was das Joomla HTTP Headers Plugin macht

Neben der Anzeige des Browsers und der Rückgabe allgemeiner Informationen über das HTML-Dokument helfen HTTP-Header dabei, Angriffe und Sicherheitslücken auf Ihrer Joomla-Webseite zu mindern. Hier kommt das Joomla HTTP Headers Plugin ins Spiel. Es erreicht dies, indem es HTML-Inhalte basierend auf Ihren Einstellungen im Joomla HTTP Headers Plugin explizit anzeigt.

Durch das Hinzufügen von zusätzlichen sicherheitsbasierten HTTP-Headern zu Ihrer Joomla-Webseite mit dem HTTP Header Plugin, bieten Sie Ihrer Joomla-Webseite eine weitere Sicherheitsebene.

Dies ist wichtig, da eine HTML-Webseite standardmäßig all ihren Inhalt, ob gut oder schlecht, Ihren Besuchern anzeigt. Es sei denn, es wird explizit in den HTTP-Headern der Webseite festgelegt, dies nicht zu tun. Das Plugin ermöglicht dies, indem es Ihnen erlaubt, die fortgeschrittenen Sicherheitsoptionen zu konfigurieren, die Ihnen in der Content-Security-Policy für Ihre Webseite zur Verfügung stehen. Das Plugin kann je nach Ihren Anforderungen unterschiedlich für jede Webseite konfiguriert werden, sodass es eine wirklich flexible Waffe in Ihrem Arsenal gegen Hacker darstellt.

## Warum brauche ich dieses Plugin?

In einer idealen Welt bräuchten Sie es nicht. Jedoch, in der Welt, in der wir leben, gibt es viel zu viele skrupellose Menschen, die Wege suchen, um Geld von Unschuldigen und Unvorsichtigen zu machen. In unserer Welt nennen wir diese Menschen Hacker. Hacker versuchen, Schwachstellen in Software auszunutzen, um finanziellen Gewinn zu erzielen, oft zum Nachteil des Website-Besitzers.

Indem Sie das HTTP-Header-Plugin von Joomla nutzen, um zu kontrollieren, welche Inhalte Ihren Besuchern geliefert werden, verringern Sie die Chancen, dass Hacker bösartige Website-Inhalte über veraltete, anfällige Plugins an Ihre Besucher ausliefern können. Dies hilft, das Einfügen von schädlichen Skripten auf Ihrer Website zu verhindern.

**Denken wir für eine Minute über diese hypothetische Situation nach.**

Sie haben eine schöne Joomla 3 Website. Diese wurde vor 5 Jahren erstellt und sieht immer noch perfekt aus und funktioniert einwandfrei. Alle Ihre Komponenten, Plugins und Module sind auf dem neuesten Stand. Perfekt, oder?

Nun, nicht ganz, denn als Sie Ihre Website vor 5 Jahren erstellt haben, installierten Sie das trendige Foo Bar Plugin, um "FOO BAR" auf Ihrer Startseite anzuzeigen. Es sah zu Beginn cool aus, aber nach einer Weile änderten Sie Ihre Meinung und löschten das Plugin-Shortcode {foo}FOO - BAR{/bar} von Ihrem Startseiten-Beitrag.

Aber hier ist das Problem: Sie haben das Plugin selbst nicht deaktiviert oder deinstalliert, und seine Nutzung geriet in Vergessenheit. **Das ist etwas, woran wir alle schuldig sind, da bin ich mir sicher.**

Schnellvorlauf bis heute, 5 Jahre später, ist das Plugin immer noch da, veröffentlicht und aktiv auf Ihrer Website, aber es wurde seit 5 Jahren nicht mehr aktualisiert, weil Sie das Plugin längst vergessen haben oder der Autor es nicht mehr unterstützt. Nun hat ein gerissener Typ erkannt, dass dieses Plugin eine Sicherheitslücke hat, die ausgenutzt werden kann, um einen **Cross-Site-Scripting (XSS)**-Angriff auf Ihrer Website zu starten und Ihre nichtsahnenden Besucher zu Opfern zu machen.

Cross-Site-Scripting, auch als XSS bekannt, ist eine Sicherheitslücke auf Ihrer Website, die es einem Angreifer ermöglicht, die Interaktionen zu kompromittieren, die Ihre Benutzer mit Ihrer nun anfälligen Website haben.

Der Angreifer/Hacker nutzt XSS, um Ihre anfällige Website auszunutzen, um ein bösartiges Skript an Ihren nichtsahnenden Benutzer zu senden. Da das Skript von Ihrer Website stammt, weiß oder vermutet der Browser Ihres Benutzers nicht, dass dem Skript nicht vertraut werden sollte, und führt das Skript aus, wenn die Webseite geladen und geöffnet wird.

Auf diese Weise ausgeführte bösartige Skripte können viele Probleme für Ihren Benutzer verursachen, von Diebstahl von Anmeldedaten und Benutzernamen, die in Cookies gespeichert sind, bis hin zum Senden Ihres Benutzers zu gefälschten Phishing-Websites. Skripte können sogar das Aussehen der Webseite ändern, die Ihre Website bereitstellt, und Ihnen unterschiedliche Werbung anzeigen.

Die Verwendung des **HTTP-Header-Plugins von Joomla** hilft, Cross-Site-Scripting zu verhindern, indem sichergestellt wird, dass nur die Skripte und Inhalte, die Sie Ihren Besuchern bereitstellen möchten, tatsächlich bereitgestellt werden. Alles andere wird blockiert.

Im obigen Beispiel hätten Sie das HTTP-Header-Plugin so konfigurieren können, dass nur die JavaScript-(Skript-)Dateien Ihrer Website aus einem angegebenen Ordner oder vielleicht einem CDN, falls Sie eines verwenden, bereitgestellt werden, um den Angriff zu stoppen.

Sie könnten auch verhindern, dass die Website eingebettetes JavaScript im HTML ausführt. Doch seien Sie sich bewusst, dass dies, je nachdem, wie Sie Ihr Website-HTML gestaltet haben, weiter unten zu Problemen führen könnte.

Dies würde dann helfen, die Ausführung von bösartigem JavaScript-Code auf Ihrer Website zu verhindern. Selbst wenn Ihr anfälliges Foo Bar Plugin schuld daran wäre, dass ein Hacker in erster Linie bösartigen Code in Ihre Website injizieren konnte.

**Hinweis:**

> Häufige Schwachstellen auf Websites, die anfällig für XSS-Angriffe sind, sind Benutzer-Eingabeformulare (Benutzer-Login-Seiten, Newsletter-Anmeldeformulare, Kontaktformulare usw.) ohne Validierung und Verschlüsselung.

## Wo ist das HTTP-Header-Plugin?

Das HTTP-Header-Plugin von Joomla finden Sie zusammen mit allen anderen Joomla-Plugins, und es wird auf genau die gleiche Weise aufgerufen, wie Sie es gewohnt sind.

![Joomla http headers 4](../../../en/images/security/http-headers/04-http-headers-plugins.png)

## Verwenden des HTTP-Headers-Plugins

Die Verwendung des HTTP-Plugins von Joomla ist relativ unkompliziert, obwohl es eine gute Idee sein könnte, sich vor dem Ändern der Standardeinstellungen über einige der speziellen Begriffe zu informieren, die mit seiner Verwendung zusammenhängen. Dennoch sollten einige davon bereits bekannt sein.

**Zum Beispiel:**

Beim Umgang mit Bildern sehen Sie den Begriff 'img-src', wobei 'img' für Bilder und 'src' für die gültige Quelle des Bildes steht. Diese Begriffe sind uns bereits aus einfachem HTML bekannt.

Am Ende dieses Beitrags gibt es eine Liste nützlicher Websites mit zusätzlichen Informationen, die Ihnen bei der Verwendung dieses Joomla-Plugins helfen.

## HTTP-Headers Plugin-Einstellungen - Tab 1

Wenn Sie das Plugin öffnen, wird zuerst der Tab mit den grundlegenden Einstellungen angezeigt. Hier können Sie Anpassungen an den X-Frame-Optionen, der Referrer-Policy, der Cross-Origin-Opener-Policy und auch an den erzwungenen HTTP-Headers vornehmen. Es gibt auch einige Links für weitere Informationen, die Ihnen helfen, zu verstehen, was diese Elemente im Detail tun.

**Lassen Sie uns jedes dieser Elemente der Reihe nach betrachten.**

![Joomla http headers 5](../../../en/images/security/http-headers/05-http-headers-plugins-tab-plugin.png)

### X-Frame-Optionen

Die erste Einstellung betrifft die X-Frame-Optionen. **Sie ist standardmäßig aktiviert.**

Diese Option ermöglicht es Ihnen zu entscheiden, ob Ihre Websiteinhalte auf einer anderen Website in einem &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; oder &lt;object&gt; angezeigt werden können. Wenn Sie diese Option deaktivieren, kann jede andere Website Ihre Inhalte in einem &lt;iframe&gt; anzeigen.

Sobald sie aktiviert ist, wird ein 'x-frame-options: SAMEORIGIN'-Tag zu Ihren Website-Headers hinzugefügt. Dieses Tag ermöglicht es Ihnen weiterhin, Ihre eigenen Inhalte auf Ihrer eigenen Website in einem &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; oder &lt;object&gt; anzuzeigen. Aber niemand sonst kann Ihre Inhalte in einem &lt;iframe&gt; auf ihrer eigenen Website anzeigen.

![Joomla http headers 6](../../../en/images/security/http-headers/06-http-headers-plugins-headers.png)

Der X-Frame-Optionen-Header hilft, Ihre Website und Ihre Benutzer vor **‘Click-Jacking‘**-Angriffen zu schützen. Dabei platziert ein Angreifer ein &lt;iframe&gt; auf seiner eigenen Website und legt die Quelle des &lt;iframe&gt; als Ihre Website fest. Dann verwendet der Angreifer mehrere transparente Ebenen seiner eigenen Website darüber.

Dies täuscht einen Benutzer, auf einen Button oder Link auf der transparenten oberen Schicht zu klicken, weil der Benutzer glaubt, er klickt auf einen Link im darunterliegenden &lt;iframe&gt;.

Der Angreifer **“kapert“** also Klicks, die ursprünglich für die eingebettete Seite gedacht waren, und leitet sie zu einer anderen Webseite um.

Noch ernster wird es, wenn ähnliche Praktiken verwendet werden, um Tastenanschläge für Passwort- und Benutzernamen-Login-Daten von E-Mail-Konten, Social-Media-Konten und natürlich Ihrem Bankkonto zu sammeln.

Die meisten modernen Browser unterstützen X-Frame-Optionen, was großartig ist. Daher wäre meine Empfehlung, diese Einstellung im HTTP-Headers Plugin zu aktivieren, um Ihre Nutzer vor 'Click-Jacking' zu schützen.

**Die meisten modernen Browser unterstützen die X-Frame-Optionen.**

![Http headers browser support](../../../en/images/security/http-headers/07-http-headers-plugins-xframe-browser-support.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Merkpunkte

Stellen Sie dies auf aktivieren. Dies wird global einschränken, was mit &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; oder &lt;object&gt; auf Ihrer Website gemacht werden kann. Um Ausnahmen hinzuzufügen, verwenden Sie 'Force HTTP Headers', um granulare Ausnahmen zu definieren.
</div>

### Referrer-Policy

Der nächste Punkt auf der Liste im ersten Tab ist die **Referrer-Policy**. Wenn diese aktiviert ist, können Sie wählen, wie viele Ihrer potenziellen Website-Daten an eine andere Website übertragen werden, wenn ein Link oder ein anderes HTML-Objekt auf Ihrer Website angeklickt wird.

Häufig sehen wir dies als HTML-Attribut auf &lt;a&gt;-Tags, wo Sie einen Link als &lt;a href=”https://someplace.com” rel=”noreferrer”&gt;Click Me&lt;/a&gt; formatieren könnten. Das noreferrer-Tag hält die Details der sendenden Webseite geheim vor der empfangenden Webseite. Dies geschieht durch das Entfernen der Referral-Informationen aus dem HTTP-Header der Webseite.

Sich der Daten bewusst zu sein, die Ihre Website möglicherweise an eine andere von Ihnen verlinkte Website ‘leakt‘, ist ein wichtiger Aspekt, um Ihre Website und ihre Benutzer zu sichern.

Dies ist besonders wichtig, wenn Sie Benutzerregistrierungen zulassen, sensible Daten enthalten oder Ihre Website Geldtransaktionen bearbeitet. Das HTTP-Headers Plugin von Joomla hilft dabei, dies auf globaler Ebene zu kontrollieren, anstatt auf der Ebene einzelner Links.

Standardmäßig ist die Referrer-Policy Ihrer Website auf ‘strict-origin-when-cross-origin’ gesetzt. Dies blockiert keine der Referrer-Daten von der ursprünglichen Webseite, es sei denn, sie werden an eine weniger sichere HTTP-Seite gesendet. Da jedoch die meisten Webseiten heutzutage HTTPS verwenden, ist dies jetzt ein größeres Problem als früher.

![Joomla http headers 8](../../../en/images/security/http-headers/08-http-headers-plugins-headers-referer-policy.png)

Es gibt natürlich viele unschuldige Verwendungen dieser ‘geleakten‘ Daten, wenn Sie keine Referrer-Policy für Ihre Website festlegen. Diese könnten Daten umfassen, die von der verlinkten Website für Analysen, Protokollierungen oder optimiertes Caching gesammelt wurden.

Leider nutzt nicht jede referenzierte Website Ihre ‘geleakten‘ Daten für solch unschuldige Operationen. Nehmen Sie das folgende Szenario als Beispiel.

Die meisten Websites, die Benutzerregistrierungen erlauben, haben einen Link zum Zurücksetzen des Passworts neben ihrem Anmeldeformular auf einer Anmelde-/Registrierungs-Webseite. Es ist auch wahrscheinlich, dass die Webseite andere Links zu externen Websites enthält, Social-Media-Links oder vielleicht einige ‘Nützliche Links’ im Footer.

Diese führen alle aus Ihrer sicheren Umgebung heraus. Nun, wenn keine Referrer-Policy vorhanden ist, ist es möglich, dass der Referrer-Header, der ausgegeben wird, wenn auf einen dieser Links von dieser Anmelde-Webseite geklickt wird, den Passwort-Zurücksetzungs-Link enthält. Sowie andere Informationen, die Sie mit dieser externen Website geteilt haben.

Dies könnte ein Sicherheitsrisiko für den Benutzer darstellen, indem seine Daten gefährdet werden.

Aufgrund des potenziellen Sicherheitsrisikos auf dieser Art von datensensitiver Seite ist es auch eine gute Praxis, alle Inhalte von Drittanbietern von der Seite zu entfernen. Dies würde alle Links und Inhalte einschließen, die in &lt;iframes&gt; bereitgestellt werden, wie z. B. Social-Media-Widgets und YouTube-Videos. Da Daten, die auf dieser Seite eingegeben werden, über den Referrer-Header an diese Seiten gesendet werden könnten, wenn Sie auf dieses niedliche Katzenvideo klicken, das gerade aufgetaucht ist.

Das HTTP-Headers Plugin von Joomla adressiert dieses Problem, indem Sie aus einer von 8 Referrer-Policies auswählen können, um eine Referrer-Policy für Ihre Website zu etablieren. Jede mit ihren eigenen Grenzen, wann und wie viele Daten geteilt werden.

![Joomla http headers 9](../../../en/images/security/http-headers/09-http-headers-plugins-headers-referer-policy-setting.png)

Schauen wir uns diese an. Es gibt eine ausgezeichnete Beschreibung auf der Mozilla Headers Seite, die sie wie folgt beschreibt:

* **no-referrer**<br>
    Der Referrer-Header wird weggelassen: gesendete Anfragen enthalten keine Referrer-Informationen.
* **no-referrer-when-downgrade**<br>
    Senden Sie den Ursprung, Pfad und die Abfragezeichenfolge im Referrer-Header, wenn das Sicherheitsniveau des Protokolls gleich bleibt oder verbessert wird (HTTP→HTTP, HTTP→HTTPS, HTTPS→HTTPS). Senden Sie den Referrer-Header nicht für Anfragen an weniger sichere Ziele (HTTPS→HTTP, HTTPS→file).
* **origin**<br>
    Senden Sie nur den Ursprung im Referrer-Header. Zum Beispiel sendet ein Dokument unter https://example.com/page.html den Referrer https://example.com/.
* **origin-when-cross-origin**<br>
    Bei einer Anfrage innerhalb desselben Ursprungs und auf derselben Protokollebene (HTTP→HTTP, HTTPS→HTTPS) den Ursprung, Pfad und die Abfragezeichenfolge senden. Senden Sie nur den Ursprung für Anfragen an andere Ursprünge und weniger sichere Ziele (HTTPS→HTTP).
* **same-origin**<br>
    Senden Sie den Ursprung, Pfad und die Abfragezeichenfolge für Anforderungen innerhalb desselben Ursprungs. Senden Sie den Referrer-Header nicht für Anforderungen an andere Ursprünge.
* **strict-origin**<br>
    Senden Sie nur den Ursprung, wenn das Sicherheitsniveau des Protokolls gleich bleibt (HTTPS→HTTPS). Senden Sie den Referrer-Header nicht an weniger sichere Ziele (HTTPS→HTTP).
* **strict-origin-when-cross-origin (Standard)**<br>
    Senden Sie den Ursprung, Pfad und die Abfragezeichenfolge bei einer Anfrage innerhalb desselben Ursprungs. Senden Sie für Anfragen an andere Ursprünge nur den Ursprung, wenn das Sicherheitsniveau des Protokolls gleich bleibt (HTTPS→HTTPS). Senden Sie den Referrer-Header nicht an weniger sichere Ziele (HTTPS→HTTP).
    **Hinweis:** Dies ist die Standardrichtlinie, wenn Sie keine Richtlinie angeben oder wenn der angegebene Wert ungültig ist. Früher war der Standard keine Referrer-Richtlinie-bei-Herabstufung.
* **unsafe-url**<br>
    Senden Sie den Ursprung, Pfad und die Abfragezeichenfolge bei jeder Anfrage, unabhängig von der Sicherheit.
    **Warnung:** Diese Richtlinie wird möglicherweise private Informationen aus HTTPS-Ressourcen-URLs an unsichere Ursprünge lecken. Überlegen Sie sorgfältig die Auswirkungen dieser Einstellung.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Merkpunkte

Als guter Anfangspunkt würde ich, wenn es keinen Grund gibt, es anders zu machen, diese auf ‘no-referrer’ einstellen, also eine pauschale ‘nichts teilen’-Politik für Ihre Website. Oder 'origin-when-cross-origin', was es Ihnen erlauben würde, den Verkehr auf URLs innerhalb Ihrer eigenen Website zu analysieren (also kein Datenleck), aber nur Ihre Domain als verweisende Domain an die externe Website zu senden, da keine ‘extra‘ Daten aus der URL an den Referrer-Header angehängt werden.
</div>

### Cross-Origin-Opener-Policy

Die dritte Option zum Einstellen im ersten Tab ist die Cross-Origin-Opener-Policy, welche ein browserbasiertes Sicherheitsfeature ist, das Ihnen ermöglicht, verschiedene **‘Browser Context Groups‘** voneinander zu trennen.

![Joomla http headers 10](../../../en/images/security/http-headers/10-http-headers-plugins-headers-cross-origin-opener-policy.png)

Ein gutes Beispiel dafür ist die Verwendung von Pop-ups. Hier wird die ursprüngliche Browser-Kontextgruppe (alle Texte, Bilder, Links etc.) von einer neuen Browser-Kontextgruppe getrennt, die erstellt und dann im Pop-up angezeigt wird.

![Joomla http headers 10](../../../en/images/security/http-headers/11-http-headers-plugins-headers-cross-origin-opener-popup.png)

> Diese HTTP-Header-Option ist recht tiefgehend und komplex, obwohl es nur 3 Optionen gibt. Ich ermutige Sie daher, die unten stehenden Links zu überprüfen, um ein besseres Verständnis dafür zu bekommen, warum diese Option auf Ihrer Website eingestellt werden sollte. Sowie um mehr über einige der erweiterten Funktionen zu erfahren, die Ihnen zur Verfügung stehen, wenn diese Option aktiv ist.

Die Cross-Origin-Opener-Policy hilft, ein historisches Schlupfloch zu schließen, wie Browser Daten zwischen verschiedenen Kontextgruppen teilen, besonders wenn Pop-ups auf der Website verwendet werden.

Die Festlegung Ihrer **COOP** wird Ihnen helfen, Datensicherheitsbedrohungen zu mindern, die häufigste davon wird als **‘Spectre’** bezeichnet. Spectre macht Daten, die in derselben Browsing-Kontextgruppe wie Ihr Code geladen sind, potenziell für einen Hacker lesbar. Spectre ermöglicht es, die Zeit, die bestimmte Operationen dauern, zu messen. Dadurch können diese Hacker erraten, was sich im CPU-Cache befindet. Wenn sie damit erfolgreich sind, wissen sie, was sich im Prozessspeicher befindet. Sie haben damit Zugriff auf Ihre Daten. Diese könnten sensibel sein.

**COOP** funktioniert, indem Ihre original HTML-Dokumentdaten von den HTML-Daten getrennt werden, die in einem Pop-up aus dem Originaldokument angezeigt würden. Dies hilft, sogenannte **cross-origin attacks oder XS-Leaks** zu verhindern.

Dieser Prozess ist vergleichbar mit dem bekannten rel=”noopener”, den wir auf regulären Links verwenden. Aber, im Gegensatz zu rel=”noopener”, das nur auf ausgehende Links aktiv ist, beschränken Dokumente, die eine cross-origin-opener-policy im HTTP-Header durch das Joomla Plugin gesetzt haben, Daten in beide Richtungen. Dokumente mit aktiver COOP-Policy werden also nicht im HTTP-Header referenziert, und die window.opener HTTP-Header-Eigenschaft des neuen Fensters wird auf null gesetzt.

Beim Setzen dieser Option im Joomla HTTP-Header-Plugin haben Sie drei Optionen zur Verfügung.

* **unsafe-none**<br>
    Dies ist der Standardwert. Es erlaubt Ihrem Dokument, seiner Opener-Browsing-Kontextgruppe hinzugefügt zu werden, es sei denn, der Opener selbst hat eine cross-origin-opener-policy von same-origin oder same-origin-allow-pop-ups.
* **same-origin-allow-popups**<br>
    Diese Option behält Verweise auf neu eröffnete Fenster oder Tabs, die entweder keine cross-origin-opener-policy setzen oder sich selbst von der Isolation abmelden, indem sie eine cross-origin-opener-policy von unsafe-none setzen.
* **same-origin**<br>
    Isoliert die Browser-Kontext-Gruppe nur zu gleichartigen Dokumenten. Über die Herkunft hinausgehende Dokumente werden nicht in derselben Browsing-Kontextgruppe geladen.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Merkpunkte

Ein guter Startpunkt für Ihre Website wäre, diese Option im Plugin auf same-origin zu belassen, was die Standardeinstellung ist. Dies wird es ermöglichen, Inhalte Ihrer eigenen Website/Domäne erfolgreich in Pop-ups zu laden, aber den Zugriff auf Elemente einschränken, die aus einer externen Quelle stammen und in einem Pop-up geladen werden.

Wie zu Beginn dieses Abschnitts erwähnt, sind bestimmte erweiterte Funktionen von der Cross-Origin-Isolierung abhängig. Funktionen wie SharedArrayBuffer-Objekte oder Performance.now()-Methoden, die bestimmte Service-Worker für ungedrosselte Timer benötigen, sind nur verfügbar, wenn Ihr Dokument einen Cross-Origin-Opener-Policy-HTTP-Header mit dem Wert 'same-origin' eingestellt hat.
</div>

### Erzwungene HTTP-Headers

Die letzte Option, auf die Sie sich im ersten Tab konzentrieren sollten, sind die erzwungenen HTTP-Headers, die nicht mit 'Force HTTPS' in den allgemeinen Joomla-Einstellungen zu verwechseln sind.

![Joomla http headers 11](../../../en/images/security/http-headers/12-http-headers-plugins-force-http-headers.png)

Dieser Abschnitt des Joomla HTTP-Headers Plugins ermöglicht es Ihnen, falls gewünscht, eine Auswahl ‘anderer‘ Headers hinzufügen, die nicht explizit in den Plugin-Tabs aufgeführt sind, sowie die Einbindung einiger, die enthalten sind, zu erzwingen.

Aus der Dropdown-Liste haben Sie derzeit 10 Optionen zur Auswahl. Es ist jedoch wichtig zu beachten, dass einige dieser Optionen **im Laufe der Zeit entfernt werden können**, da sich die Header-Richtlinien, auf die sie verweisen, ändern oder neu gestaltet werden können.

Die aktuellen HTTP-Headers, die Sie hier direkt einstellen können, zielen auf die folgenden ab:

Weitere Informationen zu jedem Feature erhalten Sie auf der Mozilla Developers Website.

#### Content-Security-Policy (Liste)

Der Content-Security-Policy-Antwortheader ermöglicht es Websites, Ressourcen zu kontrollieren, die der Benutzer für jede Webseite laden darf. Richtlinien spezifizieren meist Server-Ursprünge und Skript-Endpunkte. Dies hilft, Cross-Site-Scripting-Angriffe zu verhindern.
Mozilla: Content-Security-Policy

#### Content-Security-Policy-Report-Only

Der HTTP Content-Security-Policy-Report-Only-Antwortheader ermöglicht es Webentwicklern, mit Richtlinien zu experimentieren, indem ihre Auswirkungen überwacht (aber nicht durchgesetzt) werden.
Mozilla: Content-Security-Policy-Report-Only

#### Cross-Origin-Opener-Policy (COOP)

Der HTTP Cross-Origin-Opener-Policy (COOP)-Antwortheader ermöglicht es Ihnen sicherzustellen, dass ein oberstes Dokument keine Browser-Kontextgruppe mit über die Herkunft hinausgehenden Dokumenten teilt.
Mozilla: Cross-Origin-Opener-Policy

COOP wird Ihr Dokument prozess-isolieren, und potenzielle Angreifer können nicht auf Ihr globales Objekt zugreifen, wenn sie es in einem Pop-up öffnen würden, und verhindert einen Satz von Cross-Origin-Angriffen, genannt **XS-Leaks**.

#### Expect-CT (Wird eingestellt)

Der Expect-CT-Header erlaubt es Websites, sich zur Berichterstattung und/oder Durchsetzung von Certificate-Transparency-Anforderungen zu verpflichten, um zu verhindern, dass die Verwendung von falsch ausgestellten Zertifikaten unbemerkt bleibt.
Mozilla: Expect-CT (Wird eingestellt)

#### Feature-Policy (Jetzt veraltet)

Der HTTP Feature-Policy-Header bietet einen Mechanismus, um die Nutzung von Browser-Funktionen im eigenen Frame und in Inhalten innerhalb eines &lt;iframe&gt;-Elements im Dokument zu erlauben und zu verweigern.
Mozilla: Feature-Policy

#### Permissions-Policy

Dies ist der Ersatz für die oben genannte Feature-Policy.
Mozilla: Permissions-Policy (Ersetzt Feature Policy oben)

#### Referrer-Policy (in der Liste)

Der Referrer-Policy-HTTP-Header steuert, wie viele Referrer-Informationen (die mit dem Referrer-Header gesendet werden) in Anfragen enthalten sein sollen.
Mozilla: Referrer-Policy

#### Report-To

Teil der Content-Security-Policy. Das Content-Security-Policy Report-To-HTTP-Antwortheader-Feld weist den Benutzeragenten an, Berichtsendpunkte für einen Ursprung zu speichern.
Mozilla: Report-To

Die Report-to-Direktive soll die veraltete Report-uri-Direktive ersetzen, wird aber bisher von den meisten Browsern noch nicht unterstützt.

#### Strict-Transport-Security

Der HTTP Strict-Transport-Security-Antwortheader (oft abgekürzt als HSTS) informiert Browser, dass die Seite nur über HTTPS aufgerufen werden sollte und dass zukünftige Versuche, darauf über HTTP zuzugreifen, automatisch in HTTPS umgewandelt werden sollen.
Mozilla: Strict-Transport-Security

Dies ist sicherer als einfach eine HTTP-zu-HTTPS (301)-Umleitung auf Ihrem Server zu konfigurieren, bei der die initiale HTTP-Verbindung immer noch anfällig für einen Man-in-the-middle-Angriff ist.

#### X-Frame-Options (in der Liste)

Der X-Frame-Options HTTP-Antwortheader zeigt an, ob ein Browser eine Seite in einem &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; oder &lt;object&gt; rendern darf oder nicht. Websites können dies verwenden, um Click-Jacking-Angriffe zu vermeiden, indem sie sicherstellen, dass ihre Inhalte nicht in andere Websites eingebettet werden.
Mozilla: X-Frame-Options

Die zusätzliche Sicherheit wird nur bereitgestellt, wenn der Benutzer, der auf das Dokument zugreift, einen Browser verwendet, der X-Frame-Options unterstützt.

Der X-Frame-Options-Header hat untergeordnete Elemente namens frame-ancestors, die die Frame-Options-Header ersetzen. Wenn eine Ressource beide Richtlinien hat, wird die frame-ancestors-Richtlinie durchgesetzt und die X-Frame-Options-Richtlinie ignoriert.

Mit dem HTTP-Header-Wertefeld können Sie die Werte festlegen, die Sie befolgen lassen möchten, und sie Ihrer Website, der Admin-Site oder beiden zuweisen.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Merkpunkte

Es sei darauf hingewiesen, dass die Unterstützung von HTTP-Headers durch Browser variiert, daher ist es eine gute Idee, vor der Implementierung Ihrer Wahl von HTTP-Headers deren Browser-Unterstützung für Ihre potenziellen Zielgruppen zu überprüfen.

Wenn Sie eine Reihe von HTTP-Headers für Ihre Website festlegen und der Browser des Benutzers diese Header-Option nicht unterstützt, wird der Browser sie ignorieren.
</div>

## Einstellungen des HTTP-Header-Plugins - TAB 2

### Strict-Transport-Security (HSTS)

**Die Strict Transport Security Policy-Registerkarte ist standardmäßig deaktiviert.**

![Joomla http headers 12](../../../en/images/security/http-headers/13-http-headers-plugins-headers-strict-transport-security.png)

Ich liebe es, zu recherchieren. Denn manchmal stößt man auf einen echten OMG!-Moment. Dies ist einer dieser Momente.

Wikipedia sagt:

> Netscape Communications entwickelte 1994 HTTPS für seinen Netscape Navigator-Webbrowser. Ursprünglich wurde HTTPS mit dem SSL-Protokoll verwendet. Als sich SSL zu Transport Layer Security (TLS) weiterentwickelte, wurde HTTPS im Mai 2000 formell durch RFC 2818 spezifiziert. Google kündigte im Februar 2018 an, dass sein Chrome-Browser HTTP-Sites ab Juli 2018 als „Nicht sicher“ kennzeichnen würde. Diese Maßnahme sollte Website-Betreiber ermutigen, HTTPS zu implementieren, um das World Wide Web sicherer zu machen.“ ……

Wer hätte gedacht, dass Netscape die HTTPS-Protokolle schon so lange erfunden hat? Was noch überraschender ist, ist, wie lange es gedauert hat, bis es im Internet, wie wir es heute kennen und lieben, implementiert wurde.

Seit Jahren haben sie uns überredet, gedrängt und schließlich bedroht, HTTPS auf all unseren Websites zu implementieren. Die meisten von uns haben nachgegeben und das World Wide Web ist nun endlich sicher. Oder?

Es gibt jedoch einige Widerständler, Hardliner oder vergessene Websites, die immer noch nur HTTP verwenden, um ihre Inhalte zu liefern, wenn auch mit einer Google/Firefox usw. „Diese Webseite ist unsicher“-Warnung.

Eine schnelle Google-Suche brachte mehrere veraltete Listen dieser „Nur-HTTP Schuldigen“-Websites zu Tage. Obwohl viele Websites seit der Veröffentlichung dieser Listen auf HTTPS aktualisiert wurden, gab es einige offensichtliche Ausnahmen von Organisationen, von denen man gedacht hätte, dass sie es besser wissen sollten.

Zum Beispiel:

* NGINX (http://nginx.org/)
* GNU (http://www.gnu.org/)
* Die Universität von Washington (http://www.washington.edu/)

Laut w3techs.com laufen etwa 20% aller Websites immer noch nur auf HTTP.

**Warum ist das ein Problem?**

Das ist ein Problem, weil alle Daten, die von einem Benutzerbrowser gesendet und empfangen werden, das Risiko haben, abgefangen zu werden. Wir kennen dies als **Man-in-the-Middle-Angriff**. Jetzt mag dies keine wichtige Überlegung sein, wenn Ihre Website nur Bilder von niedlichen Kätzchen bietet.

![snapshot of cute kittens](../../../en/images/security/http-headers/14-http-headers-plugins-headers-kittens.jpg)

Aber sogar einfache Websites können Opfer von Hackern und Angreifern werden, die **Click-Jacking** und andere Cross-Origin-Angriffe implementieren, die Ihren Benutzern schaden.

Eine Website, die keine Benutzerdaten oder Anmeldeinformationen austauscht, **sollte dennoch HTTPS verwenden**.

**Okay, kommen wir zurück zum Thema.**

Wie Sie bereits wissen, besteht der ganze Sinn von HTTPS darin, eine sichere Verbindung zwischen dem Browser des Benutzers und Ihrem Server herzustellen. Eine Verbindung, bei der jeder Datenaustausch in einer sicheren Umgebung stattfindet, die nicht von Dritten abgefangen und kopiert werden kann. Ein Mann in der Mitte.

![man in the middle attack](../../../en/images/security/http-headers/15-http-headers-plugins-headers-man-in-middle.png)

Aber wussten Sie, dass, wenn Ihr **HTTPS SSL-Zertifikat** nicht **TLS** verwendet, Ihre „sichere“ Verbindung nicht so sicher ist, wie Sie es erwarten würden? Nicht TLS-HTTPS-Verbindungen sind immer noch **anfällig für Man-in-the-Middle-Angriffe**.

Obwohl ein alter Blogbeitrag, erklärt dieser Beitrag schön, wie ein Man-in-the-Middle-Angriff funktioniert.

Browser haben TLS weitgehend übernommen.

Und TLS 1.3 ist nicht direkt mit früheren Versionen kompatibel, es sei denn, es wird im Kompatibilitätsmodus ausgeführt. Dies könnte für einige ein Problem darstellen.

![tls certicate information](../../../en/images/security/http-headers/16-http-headers-plugins-headers-tls.png)

Die Verwendung des Joomla HTTP-Header-Plugins zur Behandlung von Strict-Transport-Security (HSTS) hilft, Man-in-the-Middle-Angriffe zu mindern, indem die Verwendung von TLS im Webbrowser Ihrer Besucher erzwungen wird. TLS stellt sicher, dass alle Webkommunikation auf der Client-Seite über eine sichere Transportschicht erfolgt.

**Verwenden Sie eine 301-Weiterleitung, um die nicht sichere HTTP-Version Ihrer Website auf die sichere HTTPS-Version umzuleiten?**

Die meisten Leute tun das. 301-Weiterleitungen sind Anweisungen, die die meisten Website-Besitzer in ihrer htaccess-Datei einrichten. Sie informieren Google darüber, dass die Version der Website, die verwendet werden soll, die HTTPS (sichere) ist. Das Problem dabei ist, dass **die 301 nur eine URL-Weiterleitung ist**, sodass Ihre Website trotzdem einen Teil der anfänglichen Verbindung über HTTP herstellt.

Anders als Verbindungen zwischen einem Benutzer und einem Website-Server, die HSTS verwenden, wobei der Server automatisch nur HTTPS verwendet.

HSTS hat jedoch eine Schwäche, da die erste anfängliche Verbindung zwischen dem Browser des Benutzers und dem Website-Server immer noch über HTTP erfolgt. Aber alle nachfolgenden Verbindungen werden automatisch per HTTPS verbunden, bis das HTTP-Header-Ablaufdatum erreicht ist und dieses Header zurückgesetzt wird.

Dies unterscheidet sich von einer Standard-301-Weiterleitung, bei der jede Seitenladung eine anfängliche HTTP-Anfrage zur Einleitung der HTTPS-Verbindung beinhaltet.

Es gibt eine Lösung für diese Schwäche in den HTTP-Headers HSTS-Einstellungen, aktivieren Sie „Preload“.

Dadurch wird das „Preload“-Tag dem Antwort-Header hinzugefügt.

In den Einstellungen gibt es auch eine **Link Preload-Liste**. Dies ist eine Liste, die in vielen modernen Browsern fest vercodet ist. Die Liste informiert den Browser, dass die Verbindung zu example.com nur über HTTPS hergestellt werden sollte. So wird die Notwendigkeit beseitigt, die anfängliche Verbindung überhaupt über HTTP herzustellen.

![hsts preload](../../../en/images/security/http-headers/17-http-headers-plugins-headers-enter-domain.png)

Sobald HSTS im Joomla HTTP-Header-Plugin eingerichtet ist, werden alle erforderlichen Tags in den HTTP-Antwort-Header eingefügt. Dies informiert jeden Browser eines Benutzers, der versucht, eine Verbindung zu Ihrem Server herzustellen, dass alle Verbindungen **über HTTPS erfolgen müssen**, unabhängig davon, ob dies in Ihrem HTML angegeben ist oder nicht.

Zusammenfassend ist die Verwendung des Joomla HTTP-Header-Plugins zur Integration von HSTS anstelle der Abhängigkeit von 301-Weiterleitungen, um Ihre Inhalte über HTTPS bereitzustellen, eine wichtige Sicherheitsverbesserung. Eine Verbesserung, die hilft, **Man-in-the-Middle-Angriffe** zu stoppen und Ihren Benutzern eine sichere Umgebung zu bieten.

HSTS gilt für die gesamte Domain, im Gegensatz zu einer 301-Weiterleitung, die nur für einen bestimmten URI-Pfad gilt.

HSTS verwendet einen separaten Browser-Cache, der normalerweise getrennt ist, sodass er nicht leicht oder versehentlich gelöscht werden kann.

HSTS kann in einen Browser vorab geladen werden. Dies stellt sicher, dass ein Benutzer nur mit HTTPS eine Verbindung zu Ihrem Server herstellt, unabhängig davon, ob er die Site zuvor besucht hat oder nicht.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Fazit

Aktivieren: HSTS

Max-Age festlegen: Der Standard ist 1 Jahr (31536000) Sekunden, aber einige empfehlen, dies auf 2 Jahre (63072000) Sekunden einzustellen.

Aktivieren: Subdomains - Wenn Sie Subdomains haben, stellen Sie sicher, dass Sie ein gültiges SSL-Zertifikat haben, um sie entweder einzeln oder als Wildcard von Ihrer Hauptdomain abzudecken.

Aktivieren: Preload

Zuletzt, die Anmeldung Ihrer Domain auf der HSTS-Preload-Liste.
</div>

## Plugin-Einstellungen für HTTP-Header - TAB 3

### Content Security Policy (Tab 3)

**Der Content Security Policy-Tab ist standardmäßig deaktiviert.**

Wenn Sie die Content Security Policy von Joomla über das HTTP-Header-Plugin aktivieren, teilen Sie dem Browser Ihrer Besucher genau mit, welche Assets von Ihrem Server geladen werden. Dies ist eine großartige Methode, um sicherzustellen, dass Sie nur die Inhalte liefern, die Sie tatsächlich bereitstellen möchten.

![Inhalts-Sicherheitsrichtlinie Tab](../../../en/images/security/http-headers/18-http-headers-plugins-headers-csp.png)

Eine wirksame Content Security Policy ist eine effektive Methode, um **Cross-Site Scripting (XSS)** und **Click-Jacking**-Angriffe zu stoppen, die von Ihrer Website ausgehen.

Cross-Site Scripting, auch bekannt als **XSS-Angriff**, ist ein Angriff auf Ihre Website, bei dem ein bösartiges Skript in eine nichtsahnende und sonst vertrauenswürdige Website „eingespritzt“ wird. Angreifer finden einen Schwachpunkt, der normalerweise dort liegt, wo ein Benutzer Daten eingeben kann.

Veraltete Komponenten, die Benutzereingaben zulassen, beispielsweise nicht validierte Kommentarformulare, könnten Schwachstellen aufweisen, die in einem Cross Site Scripting-Angriff ausgenutzt werden können. Aus diesem Grund ist es eine gute Idee, Ihre Joomla-Komponenten immer zu aktualisieren und diese Möglichkeiten zu minimieren.

**Verwenden wir das infizierte Kommentformular als Beispiel:**

Ihre Website verwendet am Ende eines Beitrags ein Kommentformular, um Benutzerdiskussionen zu sammeln, wie viele Websites es tun. Das ist großartig.

Ihre Kommenterweiterung von dubiose-joomla-erweiterungen.com funktioniert einwandfrei und Ihre Benutzer lieben sie. Aber Sie haben es seit 5 Jahren nicht mehr aktualisiert, und die Entwickler haben es längst aufgegeben.

Jetzt, 5 Jahre später, merkt Herr Hacker, dass er aufgrund einer Schwachstelle im Code für die Kommentarkomponente einen bösen Code in einem Kommentar verstecken kann, der sonst harmlos aussieht.

Was dieser Code schließlich tut, variiert, aber Sie können sicher sein, dass jedes Mal, wenn Ihre harmlose Beitragsseite mit den Kommentaren geladen wird, dieser böse Code ebenfalls geladen und ausgeführt wird. Immerhin ist es Teil des HTML, und der Browser weiß nicht, dass es nicht dort sein sollte oder nicht vertrauenswürdig ist.

Also läuft der böse Code. Vielleicht überprüft er Ihre Cookie-Daten. Vielleicht stiehlt er sensible Daten, die der Browser enthält. Oder vielleicht lädt er Anzeigen von Online-Casinos oder Erwachsenen-Websites. Vielleicht lädt er sogar die HTML Ihrer unschuldigen Webseite über diese niedlichen Kätzchen von einer externen JavaScript-Datei vollständig neu, um die Kreditkartendaten Ihrer Benutzer zu stehlen.

**Tatsächlich kann zu diesem Zeitpunkt ein Skript ausgeführt werden, um fast alles zu erreichen.**

Eine gute Content Security Policy hilft, diese Art von Angriff zu stoppen, selbst wenn Ihre kompromittierte Kommentarextension das Ziel von Herrn Hacker wird.

Das geschieht, weil das Joomla HTTP-Header-Plugin die CSP als HTTP-Response-Header liefert, **was dem Browser ausdrücklich sagt, was zu laden ist**. In den Einstellungen des CSP-Tabs im HTTP-Header-Plugin können Sie direkt **28 Richtlinien** ansprechen. Die Richtlinien helfen, Ihre Website zu sichern, indem sie nur genehmigte Quellen für Ihre Dateien und Inhalte verwenden.

Das obige Angriffsbeispiel endete damit, dass eine JavaScript-Datei aus einer anderen Quelle geladen wurde, um die HTML-Ausgabe auf dem Bildschirm zu ändern. Dies hätte verhindert werden können, indem die Richtlinie script-src 'self' in der Joomla-CSP im Plugin hinzugefügt wurde.

![Richtlinie Self](../../../en/images/security/http-headers/19-http-headers-plugins-headers-policy-directive.png)

In diesem Beispiel lädt der Browser JavaScript-Dateien im HTML-Dokument nur, wenn sie von Ihrer Domain stammen. Alle anderen JavaScript-Dateien werden abgelehnt, einschließlich der von Herrn Hacker.

Während das zur Sicherung Ihrer Website beiträgt, kann es auch andere legitime JavaScript-Dateien, die Sie beim Rendern der Webseite auf dem Bildschirm laden möchten, stoppen. Diese externen Dateien können als weiße gelistete Quellen in derselben Richtlinie hinzugefügt werden. Zum Beispiel, wenn Sie Bootstrap von einem CDN verwenden, würden Sie hinzufügen:
```
script-src 'self' https://cdn.jsdelivr.net
```
In diesem Beispiel, wenn Sie Probleme haben, Bootstrap vom CDN, https://cdn.jsdelivr.net, zu laden, könnten Sie versuchen, die vollständige URL zur benötigten Bootstrap-Datei hinzuzufügen. Sie würden Ihre Richtlinie also so formatieren: `script-src 'self' https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js`.

![Richtlinie Self](../../../en/images/security/http-headers/20-http-headers-plugins-headers-policy-directive-self.png)

Das Hinzufügen dieser externen Quellen wäre einfacher auf einer neuen Website zu implementieren, während Sie sie erstellen. Aber wenn Sie Ihren gerenderten HTML mit Dev-Tools durchforsten, sollten Sie in der Lage sein, alle externen Dateien zu finden, die bereits auf Ihrer bestehenden Website verwendet werden, und sie in Ihre CSP aufzunehmen.

Beim Hinzufügen von Richtlinien zu Ihrer Content Security Policy im HTTP-Header-Plugin gibt es eine **Reihe von Kernwerten**, die Sie verwenden können, um zu definieren, was explizit vom Browser geladen werden soll. Dies sind die grundlegenden, um Ihr erstes Content Security Policy einzurichten.

Andere Optionen sind für einige der fortgeschritteneren Richtlinien verfügbar, eine vollständige Liste und Beispiele für deren Verwendung finden Sie auf der Website des Content Security Policy (CSP) Quick Reference Guide.

* **'none'** blockiert die Nutzung dieser Art von Ressource.
* **'self'** entspricht dem aktuellen Ursprung (aber keine Subdomains).
* **'unsafe-inline'** erlaubt die Verwendung von Inline-JS und CSS.
* **'unsafe-eval'** erlaubt die Nutzung von Mechanismen wie eval().

Also, lassen Sie uns einige dieser Richtlinien anschauen. Hier ist eine Liste einiger der Richtlinien, die im Joomla HTTP-Header-Plugin verfügbar sind, zusammen mit einer kurzen Beschreibung, bereitgestellt von Content Security Policy. Ich würde Ihnen empfehlen, diese Website für mehr Informationen und Beispiele zu besuchen.

<dl>
<dt>default-src</dt>
<dd>Die default-src-Richtlinie definiert die Standardrichtlinie zum Abrufen von Ressourcen wie JavaScript, Bilder, CSS, Schriftarten, AJAX-Anfragen, Frames, HTML5-Medien.<br>
BEISPIEL-POLITIK FÜR DEFAULT-SRC<br>
default-src 'self' https://cdn.example.com
</dd>
<dt>script-src</dt>
<dd>Definiert gültige Quellen für JavaScript.<br>
BEISPIEL-POLITIK FÜR SCRIPT-SRC<br>
script-src 'self' https://js.example.com
</dd>
<dt>style-src</dt>
<dd>Definiert gültige Quellen für Stylesheets oder CSS.<br>
BEISPIEL-POLITIK FÜR STYLE-SRC<br>
style-src 'self' css.example.com
</dd>
<dt>img-src</dt>
<dd>Definiert gültige Quellen für Bilder.<br>
BEISPIEL-POLITIK FÜR IMG-SRC<br>
img-src 'self' https://img.example.com https://example.com
</dd>
<dt>connect-src</dt>
<dd>Gilt für XMLHttpRequest (AJAX), WebSocket, fetch(), &lt;a ping&gt; oder EventSource. Wenn nicht erlaubt, emuliert der Browser einen 400-HTTP-Statuscode.<br>
BEISPIEL-POLITIK FÜR CONNECT-SRC<br>
connect-src 'self'
</dd>
<dt>font-src</dt>
<dd>Definiert gültige Quellen für Schriftressourcen (geladen über @font-face).<br>
BEISPIEL-POLITIK FÜR FONT-SRC<br>
font-src https://font.example.com https://example.com
</dd>
<dt>object-src</dt>
<dd>Definiert gültige Quellen für Plugins, z.B. &lt;object&gt;, &lt;embed&gt; oder &lt;applet&gt;.<br>
BEISPIEL-POLITIK FÜR OBJECT-SRC<br>
object-btnjsrc 'self'
</dd>
<dt>media-src</dt>
<dd>Definiert gültige Quellen für Audio und Video, z.B. HTML5 &lt;audio&gt;, &lt;video&gt;-Elemente.<br>
BEISPIEL-POLITIK FÜR MEDIA-SRC<br>
media-src https://media.example.com
</dd>
<dt>frame-src</dt>
<dd>Definiert gültige Quellen für das Laden von Frames. In CSP Level 2 wurde frame-src zugunsten der child-src-Direktive veraltet. CSP Level 3 hat frame-src nicht mehr als veraltet klassifiziert und es wird weiterhin auf child-src zurückgreifen, wenn diese nicht vorhanden ist.<br>
BEISPIEL-POLITIK FÜR FRAME-SRC<br>
frame-src 'self'
</dd>
<dt>sandbox</dt>
<dd>Ermöglicht einen Sandbox für die angeforderte Ressource ähnlich dem iframe sandbox Attribut. Die Sandbox wendet eine Same-Origin-Policy an, verhindert Pop-ups, es werden keine Plugins geladen und die Skriptausführung wird blockiert. Sie können den Sandbox-Wert leer lassen, um alle Einschränkungen beizubehalten, oder Werte hinzufügen: allow-forms, allow-same-origin, allow-scripts, allow-pop-ups, allow-modals, allow-orientation-lock, allow-pointer-lock, allow-presentation, allow-popups-to-escape-sandbox, und allow-top-navigation.<br>
BEISPIEL-SANDBOX-POLITIK<br>
sandbox allow-forms allow-scripts
</dd>
<dt>report-uri</dt>
<dd>Instru
iert den Browser, Berichte über Richtlinienfehler an diese URI zu senden. Sie können auch Content-Security-Policy-Report-Only als HTTP-Header-Name verwenden, um den Browser anzuweisen, nur Berichte zu senden (blockiert nichts). Diese Richtlinie ist in CSP Level 3 zugunsten der report-to-Direktive veraltet.<br>
BEISPIEL REPORT-URI<br>
report-uri /some-report-uri
</dd>
<dt>child-src</dt>
<dd>Definiert gültige Quellen für Web Worker und verschachtelte Browsing-Kontexte, die über Elemente wie &lt;frame&gt; und &lt;iframe&gt; geladen werden.<br>
BEISPIEL-POLITIK FÜR CHILD-SRC<br>
child-src 'self'
</dd>
<dt>form-action</dt>
<dd>Definiert gültige Quellen, die als HTML &lt;form&gt;-Aktion verwendet werden können.<br>
BEISPIEL-POLITIK FÜR FORM-ACTION<br>
form-action 'self'
</dd>
<dt>frame-ancestors</dt>
<dd>Definiert gültige Quellen für das Einbetten der Ressource mithilfe von &lt;frame&gt;, &lt;iframe&gt;, &lt;object&gt;, &lt;embed&gt;, &lt;applet&gt;. Das Setzen dieser Richtlinie auf 'none' sollte ungefähr dem X-Frame-Options: DENY entsprechen. Wenn diese Richtlinie aktiv ist und der Browser sie unterstützt, überschreibt sie die Einstellungen in den X-frame-options.<br>
BEISPIEL-POLITIK FÜR FRAME-ANCESTORS<br>
frame-ancestors 'none'
</dd>
<dt>plugin-types</dt>
<dd>Definiert gültige MIME-Typen für Plugins, die über &lt;object&gt; und &lt;embed&gt; aufgerufen werden. Um ein &lt;applet&gt; zu laden, müssen Sie application/x-java-applet spezifizieren.<br>
BEISPIEL-POLITIK FÜR PLUGIN-TYPES<br>
plugin-types application/pdf
</dd>
<dt>base-uri</dt>
<dd>Definiert einen Satz erlaubter URLs, die im src-Attribut eines HTML-Basis-Tags verwendet werden können.<br>
BEISPIEL-POLITIK FÜR BASE-URI<br>
base-uri 'self'
</dd>
<dt>report-to</dt>
<dd>Definiert einen Berichtsgruppen-Namen, der durch einen Report-To HTTP-Antwort-Header definiert ist. Weitere Informationen finden Sie in der Reporting API.<br>
BEISPIEL-RICHTLINIE REPORT-TO<br>
report-to groupName
</dd>
<dt>worker-src</dt>
<dd>Beschränkt die URLs, die als Worker, Shared Worker oder Service Worker geladen werden dürfen.<br>
BEISPIEL-POLITIK FÜR WORKER-SRC<br>
worker-src 'none'
</dd>
<dt>manifest-src</dt>
<dd>Beschränkt die URLs, aus denen Anwendungsmanifestdateien geladen werden können.<br>
BEISPIEL-POLITIK FÜR MANIFEST-SRC<br>
manifest-src 'none'
</dd>
<dt>prefetch-src</dt>
<dd>Definiert gültige Quellen für Anforderungs-Caching und Vorab-Rendering, zum Beispiel über das link-Tag mit rel="prefetch" oder rel="prerender":<br>
BEISPIEL-POLITIK FÜR PREFETCH-SRC<br>
prefetch-src 'none'
</dd>
<dt>navigate-to</dt>
<dd>Beschränkt die URLs, zu denen das Dokument auf jede mögliche Weise navigieren darf. Zum Beispiel, wenn ein Link angeklickt wird, ein Formular eingereicht wird oder window.location aufgerufen wird. Wenn form-action vorhanden ist, wird diese Richtlinie für Formulareinreichungen ignoriert. Umsetzungsstatus<br>
BEISPIEL-POLITIK FÜR NAVIGATE-TO<br>
navigate-to https://example.com
</dd>
</dl>

Das Joomla HTTP-Header-Plugin gibt Ihnen auch die Möglichkeit, **einige globale Parameter im Content Security Policy-Tab festzulegen**.

![Joomla http headers 14](../../../en/images/security/http-headers/21-http-headers-plugins-headers-csp-global.png)

Sie können wählen, ob die CSP auf Ihre Website, die Admin-Website oder beides mit der Client-Einstellung angewendet werden soll.

Die ‘Nur-Bericht’-Option lässt Sie Ihre Direktiven testen und sie mit Dev Tools auf Fehler überprüfen, bevor sie live gehen. Es macht immer Spaß, den Grund für CSP-Fehler in der Google-Konsole zu finden!

Als nächstes ist die ‘Nonce’-Einstellung. Nonce, was ‘einmalig verwendete Zahl’ bedeutet, ist ein System, das eine zufällig generierte Zeichenfolge auf einen Inline &lt;script&gt;- oder &lt;style&gt;-Tag anwendet, der über die Joomla-API in Ihr HTML integriert ist. Diese Instanzen werden normalerweise von Drittentwicklern von Joomla-Komponenten / Modulen / Plugins implementiert, wenn Sie diese zusätzliche Funktionalität zu Ihrer Website hinzufügen.

Im Bild unten sehen Sie das &lt;style&gt;-Tag mit einem 'nonce‘-Rel-Attribut, das von der Akeeba Backup-Komponente zu den CSS &lt;styles&gt; hinzugefügt wurde, die meinem HTML-Dokument hinzugefügt wurde.

![Joomla http headers 16](../../../en/images/security/http-headers/22-http-headers-plugins-headers-akeeba-style.png)

Interessanterweise enthalten der grundlegende Joomla-JavaScript- und CSS-Code, der dem HTML-Dokument hinzugefügt wird, derzeit keine 'nonce'-Tags. Das liegt daran, dass **sie Teil des ‚Kerns‘** sind und nicht über die Joomla API hinzugefügt werden.

Wenn Sie den ‘Nonce‘-Schalter in den CSP-Einstellungen aktivieren, ermöglichen Sie, dass diese Inline-Skripte und -Stile vom Browser als 'sicher‘ interpretiert werden. Sie müssen auch das Joomla {nonce}-Tag in Ihrer Script-src-Richtlinie auf script-src 'self' {nonce} setzen. Als Fallback für ältere Browser, die 'nonces‘ nicht unterstützen, können Sie auch {script-hashes} nach dem {nonce}-Platzhalter hinzufügen, wie dies script-src 'self' {nonce} {script-hashes} (achten Sie auf den Abstand). Aber vergessen Sie nicht, **Script-Hashes** zuerst zu aktivieren.

![Joomla nonce settings](../../../en/images/security/http-headers/23-http-headers-plugins-headers-nonce-settings.png)

Joomla generiert zufällig die 'nonce‘-Textzeichenfolge und fügt sie den &lt;style&gt; und &lt;script&gt;-Tags hinzu. Wenn Sie die 'nonce‘-Option in den Plugin-Einstellungen aktivieren, wird die Textzeichenfolge an den HTTP-Header übergeben. Der Browser interpretiert dann denHTTP-Header und verarbeitet das passende &lt;script&gt; oder &lt;style&gt;. Gleichzeitig entfernt er die Nonce-Textzeichenfolge aus dem gerenderten HTML im Browser.

![Joomla nonce style](../../../en/images/security/http-headers/24-http-headers-plugins-headers-nonce-style.png)

Das wiederum verhindert, dass Herr Hacker die Nonce-Textzeichenfolge kapern und sie seinem eigenen eingespritzten Code hinzufügen kann. Selbst wenn Herr Hacker erfolgreich sein bösartiges JavaScript in Ihr HTML einfügt, wird der Browser es blockieren.

### Skript-Hashes

Wir alle wissen, dass wir kein Inline-JavaScript in unser HTML einfügen sollen, es sollte in einer my-javascript.js-Datei geschrieben und dem &lt;head&gt; oder kurz vor dem &lt;/body&gt;-Tag platziert werden. Aber wir alle tun es gelegentlich.

Das Problem ist, dass, wenn Sie dies tun, und dann der CSP-Direktive ‘script-src 'self'’ alle Inline-JavaScripts standardmäßig blockiert werden. Es ist so konzipiert, dass es verhindert, dass das von Herrn Hacker eingefügte JavaScript auf Ihrer Website ausgeführt werden kann.

Es gibt ein Override dafür mit der Direktive script-src 'unsafe-inline', die das Inline-JavaScript von Herrn Hacker ermöglicht, sowie Ihren vertrauenswürdigen Code. Dies ist offensichtlich nicht die beste Option.

**Skript-Hashes zur Rettung!**

Das HTTP-Header-Plugin von Joomla sammelt automatisch alle &lt;styles&gt; und &lt;scripts&gt;, **die über die Joomla API** in die Website eingefügt wurden. Es generiert dann die entsprechenden Hashes und sendet sie über den HTTP-Header. Der Browser generiert dann die Hashes auf der Site selbst und bestätigt, dass die Hashes übereinstimmen. Wenn das der Fall ist, werden die Skripte ausgeführt, andernfalls werden sie blockiert.

Um dieses Plugin-Feature zu aktivieren, schalten Sie den Schalter auf **'Aktiviert'**. Dann fügen Sie in Ihrer Script-src-Richtlinie den Wert 'self' {script-hashes} hinzu. Wenn Sie die 'Nonce‘-Funktion verwenden, sowie 'Skript-Hashes‘, setzen Sie den Direktiven-Wert wie im obigen Nonce-Beispiel.

![Joomla script hashes](../../../en/images/security/http-headers/25-http-headers-plugins-headers-csp-script-hashes.png)

**Jetzt ist das clever.**

Aber noch besser ist, dass wir dieselbe Idee manuell auf Skript-Hashes anwenden können und sie unserer Direktive script-src 'self' hinzufügen. Es wird ein wenig Arbeit erfordern, um es einzurichten und zu warten, aber es könnte Ihr Leben retten, wenn Sie JavaScript zu einem Beitrag oder benutzerdefinierten Modul hinzugefügt haben.

Es gibt detailliertere Möglichkeiten, dies mit einem sha256-, sha384- oder sha512-Hash-Generator zu tun. Aber da die meisten Leute nur kleine JavaScript-Snippets zu ihrem Beitrag oder benutzerdefinierten Modul hinzufügen, lassen wir Google’s Dev Tools die Arbeit für uns erledigen.

Der Prozess ist einfach. Der einzige Unterschied ist, wie wir den Hash generieren.

Angenommen, Sie haben das Joomla HTTP-Header-Plugin aktiviert, CSP ist aktiv und Sie haben die Direktive script-src 'self' gesetzt und gespeichert.

Schritt 1 - Fügen Sie Ihr Inline-JavaScript in Ihren Beitrag oder Ihr benutzerdefiniertes Modul ein und speichern Sie es. Vergessen Sie nicht, die Editor-Einstellungen anzupassen, um zu verhindern, dass der Editor Ihren Code beim Speichern entfernt.

Schritt 2 - Navigieren Sie zu Ihrer Webseite mit Ihrem Skript darin. Öffnen Sie die Dev Tools und im Reiter Konsole sehen Sie einen Fehler, der so aussieht:

Refused to execute inline script because it violates the following Content Security Policy directive: "script-src 'self'". Either the 'unsafe-inline' keyword, a hash ('sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='), or a nonce ('nonce-...') is required to enable inline execution.

![Joomla script hashes](../../../en/images/security/http-headers/26-http-headers-plugins-headers-csp-script-hashes-tools-error.png)

Schritt 3 - Jetzt müssen Sie nur noch den Hash aus der Fehlermeldung in Ihre JavaScript-Direktive im Plugin kopieren/einfügen und erneut speichern:

script-src 'self' 'sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='

![Joomla script hashes](../../../en/images/security/http-headers/27-http-headers-plugins-headers-csp-script-src-self-hash.png)

Laden Sie als nächstes Ihre Webseite erneut und überprüfen Sie erneut mit den Google Dev Tools. Der Fehler ist nun verschwunden und der Browser lädt Ihr Skript auf der Webseite.

**Hinweis:** Es gibt immer noch einen Fehler in meinem Beispiel, da das JavaScript, das zu meinem Beitrag hinzugefügt wurde, nicht vollständig ist. Aber es zeigt, dass der Inline-Code wenigstens versucht zu funktionieren.

Das Hinzufügen von Hashes zu Ihrem Inline-Code ist eine gute Möglichkeit, diese im HTTP-Header auf die Whitelist zu setzen, damit sie weiterhin ausgeführt werden, während alle Inline-Codes, die nicht explizit gehasht und zu Ihrer CSP hinzugefügt wurden, weiterhin blockiert werden. Somit wird Herr Hackers Versuch, Ihre Website zu kompromittieren, vereitelt.

![Joomla script hashes](../../../en/images/security/http-headers/28-http-headers-plugins-headers-csp-script-src-self-hash-tools-error.png)

**Hinweis:**

Wenn Sie Ihr JavaScript ändern, müssen Sie Ihren Hash neu berechnen und den Wert in der CSP-Richtlinie ändern.

Wenn Sie Probleme haben, Ihre Hashes zum Funktionieren zu bringen, gibt es 3 häufige Probleme,
Sie finden Lösungen auf der Seite Verwenden eines Hashs mit der CSP
Webseite.

Strikte Dynamik

Wenn Sie die strikte Dynamik-Option in Ihrem CSP aktivieren, wird die explizite Berechtigung, die Sie einem Skript über einen Hash oder Nonce gegeben haben, auf jedes andere Skript angewendet, das direkt mit ihm verbunden ist oder von ihm aufgerufen wird. Diese Aktion überschreibt auch Standardrichtlinien wie 'self' oder 'unsafe-inline', die in Ihren allgemeinen CSP-Direktiven auf diese Child-Skripte angewandt werden. Sie werden ignoriert.

Stil-Hashes

Der Style Hash von CSP funktioniert genau so wie die JavaScript-Hashes oben, aber benutzen Sie dies, wenn Sie CSS &lt;style&gt;-Blöcke in den HTML-Körper einfügen. Durch das Verwenden von 'Skript-Hashes' **aktivieren** Sie das Plugin-Feature und setzen eine style-src Policy Directive, um es mit dem Wert 'self' {style-hashes} zu referenzieren.

![Joomla style hashes](../../../en/images/security/http-headers/29-http-headers-plugins-headers-csp-style-hash.png)

**Hinweis:**

Wenn Sie Ihr Inline-CSS ändern, anstelle von CSS, das durch die Joomla-API erstellt wurde, müssen Sie Ihren Hash erneut berechnen und den Wert in der CSP-Richtlinie ändern.

Frame-Vorfahren ‘self’

Diese Option im Plugin ermöglicht es, dass eine Seite innerhalb eines iFrames gerahmt wird, aber nur von derselben Site.

Wenn Sie explizit erlauben möchten, dass eine andere Website Ihre Inhalte rahmt, können Sie eine spezifische Direktive ‘frame-src’ einrichten.

![Joomla style hashes frame src](../../../en/images/security/http-headers/30-http-headers-plugins-headers-csp-style-hash-frame-src.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Ergebnis

Manchmal ist es einfacher, eine gute CSP auf einer neuen Website zu erstellen, wenn Sie die benötigten externen Ressourcen aufbauen.

Es ist wichtig, die vollständige, korrekte Basis-URL für die erlaubte Domain in der CSP-Richtlinie zu verwenden. Zum Beispiel: https://www.meinewebsite.de oder https://www.eineanderewebsite.com

Es ist auch möglich, Unterdomänen mit derselben CSP zu adressieren, indem Wildcards verwendet werden. Zum Beispiel: https://*.example.org.

Nicht alle Browser unterstützen alle Richtlinien.

CSP unterstützt sha256-, sha384- und sha512-Hashes.
</div>

## Abschließende Bemerkung / Fazit:

Beim Schreiben dieses Beitrags ist mir klar geworden, dass ich dieses riesige Thema nur an der Oberfläche behandelt habe.

Ich finde es spannend, mehr über Themen zu erfahren, die ich zuvor ignoriert oder über die ich nichts wusste. Geht es Ihnen genauso?

Die Schlussfolgerung, zu der ich bei der Recherche zum Thema HTTP-Header und insbesondere zur Verwendung des neuen J4-Plugins von Joomla zur Festlegung dieser Header gelangt bin, ist, dass wir alle dieses Thema beherrschen müssen. Es gibt viel zu viele Leute (Hacker) da draußen, die nur darauf warten, die Gelegenheit zu nutzen, um Websites mit schwacher Sicherheit anzugreifen. Helfen Sie Ihren Nutzern also nicht, Opfer zu werden.

Viel Spaß beim Erforschen des Joomla HTTP-Headers Plugins und lernen Sie, wie es dazu beitragen kann, Ihre Website zu sichern.

Ich empfehle jedoch, dass Sie vor dem Start noch etwas mehr zu diesem interessanten Thema recherchieren. Unten finden Sie Links, die Ihnen bei Ihrer eigenen Recherche helfen. Sie werden ein viel besseres Verständnis dafür bekommen, wie das Internet funktioniert und wie Ihre Website damit interagiert.

### Zur Referenz

Sollten Sie das Plugin zurücksetzen müssen, wurde das HTTP-Headers Plugin mit den folgenden Optionen installiert:

Das Plugin ist standardmäßig aktiviert.

* Die HSTS- und CSP-Tabs sind standardmäßig deaktiviert.
* Die X-Frame-Optionen sind standardmäßig aktiviert.
* Die Referrer-Policy ist anfänglich auf: strict-origin-when-cross-origin gesetzt.
* Die Cross-Origin-Opener-Policy ist anfänglich auf same-origin gesetzt.

Wenn Sie bis hierhin gelesen haben und dachten „Das ist nicht fair, was ist mit J3?“, „Warum können wir nicht die gleichen Funktionen in Joomla 3 haben?“. Gute Nachrichten: Das können Sie. Sie müssen das Plugin jedoch vom [JED herunterladen.

Wenn Sie Ihre HTTP-Header mit dem Joomla 4 Plugin eingerichtet haben, können Sie Ihre HTTP-Header auf der Website Security Headers testen.

Wie haben Sie abgeschnitten?

Seien Sie sich bewusst, dass die Aktivierung des HTTP-Headers Plugins unerwartete Effekte auf der Benutzeroberfläche haben kann.

Abschließend möchte ich Tobias Zulauf & Ced Keiflin für ihren Beitrag danken, diesen Beitrag rechtzeitig fertigzustellen!
<!--
### Weitere Lektüre:

Hier sind einige der Webseiten, die ich für die Recherche zu diesem Beitrag verwendet habe. Sie sind voll von nützlichen Informationen zu diesem Thema.

* https://docs.joomla.org/J4.x:Http_Header_Management
* https://csp.withgoogle.com/docs/index.html
* https://content-security-policy.com/
* https://scotthelme.co.uk/content-security-policy-an-introduction/
* https://scotthelme.co.uk/csp-cheat-sheet/
* https://support.cpanel.net/hc/en-us/articles/1500001533562-How-to-add-nosniif-CORS-HSTS-Clickjack-and-X-Xss-Protection-headers-on-a-per-domain-basis
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy
* https://developer.mozilla.org/en-US/docs/Web/Security/Referer_header:_privacy_and_security_concerns
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Opener-Policy
* https://web.dev/why-coop-coep/
* https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer
* https://developer.mozilla.org/en-US/docs/Web/API/Performance/now
* https://www.troyhunt.com/clickjack-attack-hidden-threat-right-in/
* https://scotthelme.co.uk/hsts-the-missing-link-in-tls/
* https://scotthelme.co.uk/wifi-pineapple-karma-sslstrip/
* https://help.upguard.com/en/articles/4581202-what-s-the-difference-between-using-hsts-and-doing-a-301-redirect
* https://content-security-policy.com/hash/
* https://content-security-policy.com/frame-ancestors/
* https://content-security-policy.com/nonce/

Computer-Icons erstellt von Freepik - Flaticon

Server-Icons erstellt von Freepik - Flaticon

Deutsche Übersetzung dieses Beitrags: https://www.jug-zueri.ch/artikel/das-http-headers-plugin-in-joomla-4

Russische Übersetzung dieses Beitrags, Teil 1: https://habr.com/ru/articles/697214/

Russische Übersetzung dieses Beitrags, Teil 2: https://habr.com/ru/articles/704778/
->
*Übersetzt von openai.com*

