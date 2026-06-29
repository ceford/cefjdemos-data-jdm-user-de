<!--
{
  "source": "https://docs.joomla.org/Customising_the_Smart_Search_results_page",
  "title": "Layout-Überschreibungen für intelligente Suche",
  "description": "", 
  "author": ""
}
-->

## Ergebnisseiten

Die Smart-Search-Komponente verfügt über fünf Layout-Dateien, die Sie überschreiben können, um ein Layout nach Ihrem eigenen Geschmack zu erstellen. Um den Prozess über das Administrator-Menü zu starten:

* Wählen Sie **System / Site-Templates / Cassiopeia-Details und -Dateien**.
* Wählen Sie den Tab **Overrides erstellen**.
* Wählen Sie im Komponentenbereich **com_finder**.
* Wählen Sie den Punkt **Suche**.
* Wählen Sie im Editor-Bereich **html / com_finder / search** aus, um die Liste der erstellten Override-Dateien anzuzeigen.

Diese Dateien werden durch Joomla-Updates nicht beeinflusst, aber Sie könnten daran erinnert werden, sie zu überprüfen, falls die ursprünglichen Quellen aktualisiert werden.

## Die Suchansicht (Standardlayout)

Die Suchansicht im Standardlayout ist in mehrere Teile unterteilt: das Standardlayout, das Formularlayout, das Ergebnisslayout und das Sortierlayout.

### Das Standardlayout (default.php)

Dieses Layout ist sehr einfach. Es definiert lediglich die Struktur, in der das Suchformular und die Suchergebnisse angezeigt werden. Dieses Layout ist auch dafür verantwortlich, das Standard-CSS-Stylesheet für Smart Search zu laden, das sich in `media/com_finder/css/finder.css` befindet. Es könnte sinnvoll sein, dies zu ändern, um Ihre eigenen CSS-Regeln für Smart Search zu laden.

### Das Formularlayout (default_form.php)

Dieses Layout definiert den Code, der erforderlich ist, damit das Suchformular korrekt funktioniert. Das Layout verwendet JavaScript-Code, daher muss darauf geachtet werden, Selektoren zu bewahren, die nicht verändert werden sollten, es sei denn, Sie wissen, was Sie tun.

Die View-Methode `getFields` enthält eine Reihe versteckter Felder, die für eine zuverlässige Suche erforderlich sind. Der Suchbegriff wird durch das Eingabefeld mit dem Namen "q" definiert.

### Das Ergebnisslayout (default_results.php)

Dieses Layout erzeugt die Liste der übereinstimmenden Ergebnisse für den Suchbegriff. Es befasst sich auch mit der Seitennummerierung und lädt für jedes einzelne Suchergebnis ein eigenes Layout.

### Das Ergebnislayout (default_result.php)

Dieses Layout wird geladen, um ein einzelnes Ergebnis anzuzeigen.

### Das Sortierlayout (default_sorting.php)

Dieses Element ist nur vorhanden, wenn "Sortierfelder anzeigen" auf Ja gesetzt wurde und ein oder mehrere Zusätzliche Sortierfelder im Menüpunkt-Tab "Erweitert" ausgewählt sind.

*Übersetzt von openai.com*

