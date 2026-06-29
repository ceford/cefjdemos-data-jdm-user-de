<!--
{
  "source": "https://docs.joomla.org/J4.x:Template_SVG_Logos",
  "title": "SVG-Logo-Vorlagen ",
  "description": "", 
  "author": ""
}
-->

## Cassiopeia-Logo

Das Standardvorlagen-Template von Joomla 4, Cassiopeia, verwendet das Wort CASSIOPEIA als Markenlogo. Es erscheint oben auf jeder Seite, es sei denn, Sie setzen Marke im Formular "Vorlagen: Stil bearbeiten", auf der Registerkarte Erweitert auf Nein, oder Sie verwenden ein Titelwort anstelle einer Grafik. Dieses Wort ist tatsächlich eine skalierte Vektorgrafik (SVG)-Datei. Sie können eine alternative Grafik wählen, jedoch ist es ziemlich knifflig, ein alternatives SVG-Logo zu erstellen und zu verwenden. Diese kurze Anleitung kann hilfreich sein.

## Inkscape

Inkscape ist eine quelloffene, plattformübergreifende Vektorgrafikanwendung, das bedeutet, dass Sie es kostenlos herunterladen und auf Linux, Mac oder Windows verwenden können. Um zu starten, gehen Sie auf die Inkscape-Website und laden Sie die Version für Ihren Laptop oder Desktop-Computer herunter. Starten Sie Inkscape, und Sie sind bereit, ein SVG-Markenzeichen-Logo zu erstellen. Der untenstehende Screenshot zeigt Inkscape in der Mitte der Erstellung eines neuen SVG-Logos.

![Erstellung eines Inkscape-Logos](../../../en/images/templates/template-svg-logos/01-templates-svg-logos-inkscape.png)

## Anweisungen

Für diesen Beitrag wird ein Logo benötigt, das **GREEN CASSIOPEIA** in der gleichen Größe wie **CASSIOPEIA** im Standardlogo zeigt, nämlich 32 Pixel hoch:

1. Starten Sie Inkscape, passen Sie das Fenster auf eine angenehme Größe an, wählen Sie Ansicht / Zoom / Seite zoomen
2. Wählen Sie das Textwerkzeug, gekennzeichnet mit einem A im linken Werkzeugmenü
3. Wählen Sie Arial, Fett, 40 und px
4. Ziehen Sie, um ein Feld zu definieren, das den größten Teil der Seitenbreite einnimmt
5. Geben Sie den Text ein: GREEN CASSIOPEIA
6. Wählen Sie Ansicht / Auswahl zoomen
7. Wählen Sie das Auswahlwerkzeug, gekennzeichnet durch einen Pfeil - oben im linken Werkzeugmenü
8. Sperren Sie die horizontalen und vertikalen Größenwerte - das Schlosssymbol in der oberen Leiste
9. Stellen Sie die Maßeinheit auf px ein
10. Ändern Sie die Höhe auf 32 - Sie werden sehen, wie das Logo auf die neue Größe wechselt
11. Wählen Sie Pfad / Objekt in Pfad umwandeln - keine sichtbare Änderung, aber die Worte sind nicht mehr Text
12. Wählen Sie Datei / Dokumenteigenschaften
13. Wählen Sie Größe an Inhalt anpassen
14. Zoomen Sie heraus, um eine bessere Ansicht zu erhalten
15. Stellen Sie die Füllung auf Weiß ein - klicken Sie auf das weiße Feld in der unteren Farbpalette
16. Datei / Speichern unter
    lokalen-Site-Root/images/headers/green-cassiopeia-optimised.svg
    1. Wenn Sie woanders speichern, müssen Sie einen Dateimanager oder FTP verwenden, um die SVG-Dateien hochzuladen. Die Medienkomponente kann SVG-Dateien verwenden, aber derzeit lädt sie diese nicht hoch.
17. Wählen Sie Optimierte SVG (.svg) aus der Dateitypen-Liste unten im Speichern-Dialog.
18. Speichern Sie, OK für alle Standardeinstellungen im Optimierten SVG-Ausgabeformular
19. Setzen Sie einige Joomla-Administratoroptionen, um die Verwendung von SVG-Dateien zu ermöglichen
20. Gehen Sie zu Inhalt / Medien / Optionen
    1. Fügen Sie zu den erlaubten Erweiterungen hinzu: ,svg
    2. Fügen Sie zu den erlaubten Bild-Erweiterungen (Dateitypen) hinzu: ,svg
    3. Fügen Sie zu den erlaubten MIME-Typen hinzu: ,image/svg+xml
21. Speichern & Schließen
22. Gehen Sie zu System / Seitentemplates / Optionen
    1. Fügen Sie zu den gültigen Bildformaten hinzu: ,svg
23. Speichern & Schließen
24. Gehen Sie zu System / Seitentemplatestile
25. Wählen Sie Ihr Template
26. Verwenden Sie im erweiterten Reiter im Logo-Feld die Auswahl, um Ihr neu erstelltes Logo zu finden
27. Speichern und laden Sie Ihre Seite neu

![inkscape logo creation result](../../../en/images/templates/template-svg-logos/02-templates-svg-logos-inkscape-result.png)

*Übersetzt von openai.com*

