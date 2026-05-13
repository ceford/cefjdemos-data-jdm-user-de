<!--
{
  "source": "https://docs.joomla.org/J6.x:Article_Access_Restriction",
  "title": "Beitrag: Zugriffsbeschränkung ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Es gibt mehrere Gründe, den Zugriff auf Beiträge auf einer Website einzuschränken. Einige Inhalte können bestimmten Benutzern vorbehalten sein, wie zum Beispiel Mitgliedern eines Komitees. Oder die Website kann kommerzielle Inhalte enthalten, die gegen Bezahlung angesehen werden können. Joomla bietet ein leistungsfähiges System der Zugriffskontrollliste (ACL), um den Zugriff einzuschränken. Es wird in einem separaten Beitrag über [Zugriffskontrolle](jdocmanual?article=user/users/access-control) im Benutzerabschnitt dieses Handbuchs beschrieben.

Dieser Beitrag beschreibt die Implementierung der Zugangsbeschränkung im *Beitrag: Bearbeiten* Formular. 

## Einschränkung durch Zugriffsebene

Joomla bietet die Zugriffsebenen, die im folgenden Screenshot zu sehen sind:

![Benutzerzugriffsebenen](../../../en/images/articles/article-access-restriction/01-article-access-user-groups.png)

Die Zugriffsebenen erscheinen im *Inhalt*-Tab des Formulars *Beitrag: Bearbeiten*.

- **Öffentlich** Kann von jedem eingesehen werden – sowohl von angemeldeten als auch von nicht angemeldeten Benutzern.
- **Gast** Diese Zugriffsebene schränkt den Zugriff auf Benutzer ein, die **NICHT** angemeldet sind.
- **Registriert** Diese Ebene beschränkt den Zugriff auf Benutzer, die angemeldet sind. Ein Beitrag mit auf *Registriert* gesetztem *Zugriff* erfordert eine Anmeldung im Frontend, bevor der Beitrag angesehen werden kann.
- **Spezial** Diese Ebene schränkt den Zugriff auf Benutzer ein, die angemeldet sind und sich in einer bestimmten anderen Benutzergruppe als Registriert befinden. Darüber hinaus ist es möglich, Inhalte zu differenzieren, auf die einige angemeldete Benutzer zugreifen können, andere jedoch nicht. Typischerweise könnte dies eine Website sein, auf der Abonnements erforderlich sind, um auf zusätzliche Inhalte zuzugreifen.
- **Super Benutzer** Diese Ebene bedeutet, dass nur ein Super Benutzer auf den Beitrag zugreifen kann. Dies könnte für Beiträge zur Seitenverwaltung verwendet werden.

Beachten Sie, dass es in dieser Liste um das **Ansehen** oder die Berechtigung zum Betrachten von Inhalten geht. Sie können zusätzliche Zugriffsebenen und Benutzergruppen erstellen, um anzupassen, wer was sehen kann.

## Teilweise Beschränkung auf Mehr Lesen

Manchmal möchten Sie den Zugriff auf einen Beitrag einschränken, aber einen uneingeschränkten Zugriff auf einen Vorgeschmack auf den Beitrag ermöglichen. Dies ist eine gängige Methode, um den Zugang zu kommerziellen Inhalten zu bezahlen. Vorgehensweise:

- Finden Sie den Beitrag in der *Beiträge*-Liste, den Sie teilweise einschränken möchten, und öffnen
  Sie ihn zur Bearbeitung.
- Fügen Sie nach dem ersten Absatz einen *Seitenumbruch* ein. Das Werkzeug für den Seitenumbruch befindet sich
  in der *CMS Content*-Liste im TinyMCE-Bearbeitungsformular für Beiträge.
- Setzen Sie das *Zugriffs*-Level des Beitrags auf *Registriert*.
- Wählen Sie **Speichern & Schließen** in der Werkzeugleiste.

### Zugang zu Beiträgen individuell beschränken

Öffnen Sie das Menüelement *Kategorie-Blog* oder *Empfohlene Beiträge*, in dem der Beitrag angezeigt wird.

- Stellen Sie im **Optionen**-Tab **Nicht autorisierte Links** auf **Ja**. Es befindet sich am
  Ende der Optionsliste.
- Wählen Sie **Speichern & Schließen** in der Werkzeugleiste.

### Globaler Zugriff auf Beiträge beschränken

* Setzen Sie die relevanten Kategorien auf die Ansichtsebene *Öffentlich*, ansonsten sind Menüelemente
  für nicht angemeldete Benutzer nicht sichtbar.
* Setzen Sie die Beiträge in den relevanten Kategorien auf die Ansichtsebene Registriert. Dies
  kann durch Auswahl der Beiträge und Verwendung der *Batch*-Schaltfläche erfolgen.
* Gehen Sie zu **Inhalte → Beiträge → Optionen**
* Stellen Sie **Nicht autorisierte Links** im Reiter Beiträge auf **Ja**. Wenn auf Ja gesetzt,
  werden Links zu registrierten Inhalten angezeigt, auch wenn Sie nicht eingeloggt sind.
  Sie müssen sich einloggen, um auf den vollständigen Artikel zuzugreifen.

**Hinweis:** Text in einem Beitrag ohne *Mehr Lesen*-Unterbrechung wird als Introtext behandelt.
Wenn Sie einen Beitrag haben, der nur für registrierte Benutzer bestimmt ist, aber keinen Mehr Lesen-Bereich hat, dann wird der gesamte Beitrag für alle Benutzer sichtbar sein. Fügen Sie also einen Mehr Lesen-Bereich in den Beitrag ein!

*Übersetzt von openai.com*

