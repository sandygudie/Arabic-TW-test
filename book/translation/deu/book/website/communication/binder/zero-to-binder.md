(z2b)=
# Null zu Binder

In diesem Kapitel werden wir von Grund auf ein Binder-Projekt erstellen: Wir erstellen zuerst ein Repository auf GitHub und starten dann auf mybinder.org. Sektionen, in denen Sie eine Aufgabe erledigen sollen, werden von drei Ampeln 🚦 emojis. Einige Schritte geben dir die Option Python, Julia oder R - klicke auf die Registerkarte deiner bevorzugten Sprache.

```{admonition} Attributions
Dieses Tutorial basiert auf Tim Head's _Zero-to-Binder_ Workshops die hier gefunden werden: <http://bit.ly/zero-to-binder> und <http://bit.ly/zero-to-binder-rise>

Vielen Dank an Anna Krystalli und Oliver Strickson für ihre Hilfe bei der Entwicklung der Inhalte R und Julia bzw. nicht.
```

```{attention}
Binder kann lange dauern, bis sie geladen wird, aber das bedeutet nicht, dass Ihr Binder nicht startet.
Sie können das Fenster immer aktualisieren, wenn Sie die Nachricht "... wird länger zu laden, zu hängen!" sehen.
```

```{admonition} If you are using R...
Wenn du dem R-Pfad folgst, haben wir einige alternative Schritte mit dem [`holepunch` Paket](https://github. om/karthik/holepunch), die deine Umgebung mithilfe eines [rocker base image](https://github.com/rocker-org/rocker) bauen und letztlich schneller bauen und starten sollten.
```

(z2b-reqs)=
## Anforderungen

Sie werden brauchen:

- **Ein paar Code und einige Daten.** Der Code sollte weniger als **10 Minuten in Anspruch nehmen**, und die Daten sollten kleiner als **10 MB** sein. Dies kann bedeuten, dass Sie nur ein Skript aus einem größeren Projekt auswählen oder eine Teilmenge Ihrer Daten mitbringen. Note that it's really important that the code and data can be made **public** because we'll be using the public binder instance.
- **Ein GitHub Account.** Bitte melden Sie sich für einen an, wenn Sie noch keinen haben: <https://github.com/join>

(z2b-step-1)=
## 1. Erstellen eines Repos zur Binderisierung

🚦🚦🚦

````{tabbed} Python
1) Erstellen Sie ein neues Repository auf GitHub namens "my-first-binder"
   - Stellen Sie sicher, dass das Repository **öffentlich**, _nicht private_!
   - Vergessen Sie nicht, das Repo mit einem README zu initialisieren!
2) Erstelle eine Datei namens `hello.py` über das Web-Interface mit `print("Hallo aus Binder!")` in der ersten Zeile und übertrage den `main` Zweig
````

````{tabbed} Julia
1) Erstellen Sie ein neues Repository auf GitHub namens "my-first-binder"
   - Stellen Sie sicher, dass das Repository **öffentlich**, _nicht private_!
   - Vergessen Sie nicht, das Repo mit einem README zu initialisieren!
2) Erstellen Sie eine Datei namens `hallo. l` über die Web-Schnittstelle mit `println("Hallo von Binder! )` in der ersten Zeile und übertrage den `main` Branch
3) Erstelle eine Datei namens `Project. oml` (WARNUNG: die Großschreibung ist wichtig!) mit dem folgenden Inhalt und übertrage sie zu `main`.
   Dies wird Julia in der Binder-Umgebung installieren.

   ```julia
   [compat]
   julia = "1.3"
```
````

````{tabbed} R
1) Erstellen Sie ein neues Repository auf GitHub namens "my-first-binder"
   - Stellen Sie sicher, dass das Repository **öffentlich**, _nicht private_!
   - Vergessen Sie nicht, das Repo mit einem README zu initialisieren!
2) Erstellen Sie eine Datei namens `hallo. ` über die Web-Schnittstelle mit `print("Hallo von Binder! )` in der ersten Zeile und übertrage den `main` Branch
3) Erstelle eine Datei namens `runtime. xt` mit `r-2022-01-01` in der ersten Zeile.
   Dieses Datum stellt den Schnappschuss von [CRAN](https://cran.r-project.org/) dar, die im [RStudio Package Manager](https://packagemanager.rstudio.com) gehostet werden.
   Übertrage diese Datei in den `main`-Zweig.

   ```{note}
   In R kannst du `holepunch::write_runtime()` verwenden, um eine `runtime.txt` im `.binder/` Verzeichnis zu erstellen; es wird mit dem heutigen Datum konfiguriert.
   ```
````
(z2b-public-repo)=
### Warum muss das Repo öffentlich sein?
mybinder.org kann nicht auf private Repositories zugreifen, da dies einen geheimen Token erfordern würde. Das Team von Binder entscheidet, die Verantwortung für den Umgang mit geheimen Token nicht zu übernehmen. mybinder.org ist ein öffentlicher Dienst und ein Beweis für das technologische Konzept. Wenn der Zugriff auf private Repositories eine Funktion ist, die Sie / Ihr Team benötigt, empfehlen wir Ihnen, den Aufbau Ihres eigenen [BinderHub](https://binderhub.readthedocs.io) zu prüfen.
(z2b-step-2)=
## 2. Starte deine erste Repo!
🚦🚦🚦
1) Gehe zu **<https://mybinder.org>** 2) Gib die URL deines Repos in das Feld "GitHub Repo oder URL" ein. Es sollte so aussehen:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) Während du schreibst, erzeugt die Webseite einen Link unter "Kopiere die URL unten. " Box Es sollte so aussehen: **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** 4) Kopieren Sie es, öffne einen neuen Browser-Tab und besuche die URL - Du wirst einen "Spinner" sehen, wenn Binder das Repo startet
Wenn alles reibungslos gelaufen ist, wirst du eine JupyterLab Schnittstelle sehen.
(z2b-background-1)=
### Was passiert im Hintergrund? - Teil 1
Während Sie warten, ist BinderHub (das Backend von Binder) ist:
- Abrufen des Repos von GitHub
- Den Inhalt analysieren
- Erstelle ein Docker-Bild basierend auf deinem Repo
- Starte das Docker-Bild in der Cloud
- Verbinde dich mit ihr über deinen Browser
(z2b-step-3)=
## 3. Skript ausführen
🚦🚦🚦

````{tabbed} Python
1. Wählen Sie im Startfeld "Terminal"
2. Gib im neuen Terminalfenster `python hello.py` ein und drücke 'return
````

````{tabbed} Julia
1. Wählen Sie im Startfeld "Terminal"
2. Gib im neuen Terminalfenster `julia hello.jl` ein und drücke 'return
````

````{tabbed} R
1. Wählen Sie im Startfeld "Terminal"
2. Gib im neuen Terminalfenster `Rscript -e 'source("hello.R")'` ein und drücke dann 'return
````

`Hallo von Binder!` sollte auf das Terminal gedruckt werden.

(z2b-step-4)=
## 4. Pinning-Abhängigkeiten

Es war einfach zu starten, aber unsere Umgebung ist Barebones - Lass uns eine **-Abhängigkeit hinzufügen** hinzufügen!

🚦🚦🚦

````{tabbed} Python
1) Erstelle in deinem Repo eine Datei namens `requirements.txt`
2) Füge eine Zeile hinzu, die lautet: `numpy==1.14.5`
3) Überprüfe nach Tippfehlern! Dann übertrage den `main` Branch
4) besuche **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** erneut in einem neuen Tab
````

````{tabbed} Julia
1) In Ihrem Repo, bearbeiten Sie das `Projekt. oml` Datei
2) Füge einen neuen Block hinzu, der lautet:

   ```julia
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) Suche nach Typo! Dann verpflichte dich zu `main`.
4) Besuche **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** erneut in einem neuen Tab
````

````{tabbed} R
1) Erstelle in deinem Repo eine Datei namens `install.R`
2) Füge eine Zeile hinzu, die lautet: `install.packages("readr")`
3) Überprüfe nach Tippfehlern! Dann übertrage den `main` Branch
4) besuche **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** erneut in einem neuen Tab

```{note}
Wenn `holepunch` verwendet wird, können Sie eine `install. `-Datei und fügt den Code automatisch hinzu, um alle Abhängigkeiten in deinem Projekt mit `holepunch::write_install()` zu installieren.
```
````
Dieses Mal klicken Sie auf "Logs erstellen" in der großen, horizontalen grauen Leiste. So kannst du den Fortschritt deines Builds beobachten. It's useful when your build fails or something you think _should_ be installed is missing.

```{note}
Manchmal druckt Binders Build-Logs Dinge in roter Schriftart, wie Warnungen, dass `pip` nicht aktuell ist (`pip` ist oft veraltet, weil es regelmäßig aktualisiert wird! oder Installationsmeldungen, insbesondere wenn Sie R verwenden.
Diese roten Nachrichten bedeuten nicht notwendigerweise ein Problem mit deinem Build und es wird fehlschlagen - es ist nur eine unglückliche Schriftfarbe!
```

(z2b-background-2)=
### Was passiert im Hintergrund? - Teil 2

Dieses Mal liest BinderHub die von Ihnen hinzugefügte Konfigurationsdatei und installiert die spezifische Version des von Ihnen angeforderten Pakets.

(z2b-Abhängigkeiten) =
### Mehr zu Pinning-Abhängigkeiten

````{tabbed} Python
Im obigen Beispiel haben wir zwei Gleichheitszeichen (`==`) verwendet, um die Version von `numpy` anzupinnen.
Dies teilt Binder mit, diese _specific_ Version zu installieren.

Eine andere Möglichkeit, eine Versionsnummer anzupinnen, ist, die größer als oder gleich dem Zeichen (`>=`) zu verwenden, um zu erlauben, dass jede Version über einer bestimmten Version installiert wird.
Dies ist nützlich, wenn Sie viele Abhängigkeiten haben, die voneinander abhängig sind und Binder eine Konfiguration Ihrer Abhängigkeiten finden kann, die nicht miteinander kollidieren, während frühere Versionen, die Ihren Code beschädigen oder ändern könnten, vermieden werden.

Schließlich Sie konnten überhaupt keine Versionsnummer angeben (nur der Name der Bibliothek/Paket), und Binder wird die neueste Version des Pakets installieren.
````

````{tabbed} Julia
Im obigen Beispiel haben wir einen Hash in unsere `Project.toml`-Datei kopiert, die mit der Version des Pakets zusammenhängt, das wir installieren möchten.
Für ein vollständiges Abhängigkeitsdiagramm müssten wir auch eine `Manifest.toml` Datei hinzufügen, die Abhängigkeiten von Abhängigkeiten dokumentiert.
Zwischen diesen beiden Dateien können wir eine exakte Replikation einer Julia Umgebung instantiieren.

Natürlich können wir uns das vorstellen, wenn die Umwelt wächst und die Abhängigkeiten komplexer werden, es würde sehr besteuerend werden, diese Dateien von Hand zu schreiben!
Die Wahrheit ist, dass du es niemals manuell machen würdest, der eingebaute Paketmanager `Pkg` kann sie [automatisch generieren](https://julialang.github.io/Pkg.jl/v1/environments/).
````

````{tabbed} R
Im obigen Beispiel haben wir angegeben, dass wir R in unserem Projekt verwenden wollen, indem wir ein Datum in `runtime.txt` angeben.
Das Datum teilt Binder mit, von welchem CRAN Snapshot zu Quell-R und Paketen stammt.
Diese Schnappschüsse stammen vom [RStudio Package Manager](https://packagemanager.rstudio.com) (RSPM).
Im obigen Beispiel wird der RSPM Snapshot von `r-2022-01-01` verwendet und die Version von R und `readr` zu diesem Zeitpunkt verfügbar und installiert.
Damit der Beispiel-Workflow korrekt funktioniert, stellen Sie bitte sicher, dass Sie kein Datum vor diesem Beispiel-Datum angeben.

Dies bietet einige rudimentäre Paketversionierung für R Benutzer, ist aber nicht so robust wie Pinning Versionen in einer `requirements.txt` in Python.
Für eine robustere und spezifischere Version in R werfen Sie einen Blick auf das [`renv`](https://rstudio.github.io/renv/) Paket.
````

(z2b-step-5)=
## 5. Umgebung überprüfen

🚦🚦🚦

````{tabbed} Python
1) Von der Startleiste aus, wähle "Python 3" im Notizbuch-Bereich aus, um ein neues Notebook
2) Gib folgendes in eine neue Zelle ein:

   ```python
   import numpy
   print(numpy.__version__)
   numpy.random. andn()
   ```

   ```{attention}
   Beachte die beiden Unterstriche auf beiden Seiten der `Version`!
   ```

3) Führen Sie die Zelle aus, um die Versionsnummer zu sehen und eine zufällige Zahl auszudrucken.

   - Drücken Sie entweder SHIFT+RETURN oder den "Ausführen"-Button in der Menüleiste
````

````{tabbed} Julia
1) Von der Startleiste aus, Wählen Sie "Julia" im Notizbuch-Bereich aus, um ein neues Julia Notebook
2) Geben Sie folgendes in eine neue Zelle ein:

   ```julia
   mit Pkg
   Pkg. tatus()
   ```

3) Führen Sie die Zelle aus, um die Versionsnummer auszudrucken

   - Drücken Sie entweder SHIFT+RETURN oder den "Ausführen"-Button in der Menüleiste
````

````{tabbed} R
1) Von der Startleiste aus, wähle "R" im Notizbuch-Sektor, um ein neues R Notebook
2) Gib folgendes in eine neue Zelle ein:

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(system. ile("extdata/mtcars. sv", package = "readr"))
   ```

3) Führen Sie die Zelle

    - Drücken Sie entweder SHIFT+RETURN oder den "Run" Button in der Menüleiste
    Sie sollten folgende Ausgabe sehen:
      - die Versionsnummer der installierten Version von `readr`
      - eine tibble des Inhalts der `mtcars. sv` ist eine csv-Datei im Paket `readr`
````

```{attention}
Wenn Sie dieses Notebook speichern, wird es **nicht** im GitHub Repo gespeichert.
Änderungen zurück zum GitHub Repo durch den Container zu schieben ist mit Binder nicht möglich.
**Alle Änderungen, die du innerhalb des Binders vorgenommen hast, gehen verloren, sobald du das Browserfenster schließst.**
```

(z2b-step-6)=
## 6. Teile deine Arbeit

Bei Binder geht es nur darum, deine Arbeit einfach zu teilen und es gibt zwei Wege, dies zu tun:

- Teile die **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** URL direkt
- Besuche **[https://mybinder. rg](https://mybinder.org)**, geben Sie die URL Ihres Repositories ein und kopieren Sie das Markdown oder ReStructured Text Snippet in Ihr `README. d` Datei. Dieses Snippet wird ein Abzeichen anzeigen, das Leute anklicken können, was wie folgt aussieht: ![Binder](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) Füge den **Markdown** Snippet von **<https://mybinder.org>** zu `README.md` Datei in deinem Repository hinzu
   - Die graue Leiste mit einem Bindeabzeichen wird sich entfalten, um die Snippets zu zeigen. Klicken Sie auf das Symbol der Zwischenablage neben dem mit "m" markierten Feld, um den Markdown Snippet automatisch zu kopieren. 2) Klicke auf das Abzeichen, um sicherzustellen, dass es funktioniert!

(z2b-step-7)=
## 7. Zugriff auf Daten in Ihrem Binder

Eine andere Art der Abhängigkeit für Projekte sind **Daten**. Es gibt verschiedene Möglichkeiten, Daten in Ihrem Binder verfügbar zu machen, abhängig von der Größe Ihrer Daten und Ihren Einstellungen für die Freigabe.

(z2b-kleine Dateien)=
### Kleine öffentliche Dateien

Der einfachste Ansatz für kleine, öffentliche Datendateien besteht darin, diese direkt in Ihr GitHub Repository hinzuzufügen. Sie werden dann direkt in die Umgebung eingekapselt und zusammen mit Ihrem Code versioniert.

Dies ist ideal für Dateien bis zu **10MB**.

(z2b-mittel-Dateien)=
### Mittlere öffentliche Dateien

Um auf mittlere Dateien **von ein paar 10 MB bis zu ein paar hundert MB zuzugreifen,**, Sie können eine Datei mit dem Namen `postBuild` zu Ihrem Repo hinzufügen. Eine `postBuild` Datei ist ein Shell-Skript, das als Teil der Bildkonstruktion ausgeführt wird und nur einmal ausgeführt wird, wenn ein neues Bild erstellt wird, nicht jedes Mal, wenn der Binder gestartet wird.

Siehe [Binders `postBuild` Beispiel](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) für weitere Verwendungen des `postBuild` Skripts.

```{note}
Neue Bilder werden nur dann erstellt, wenn Binder einen neuen Commit sieht, nicht jedes Mal, wenn Sie auf den Binder-Link klicken.
Daher werden die Daten nur einmal heruntergeladen, wenn das Docker-Image erstellt wird, nicht jedes Mal, wenn der Binder gestartet wird.
```

(z2b-groß)=
### Große öffentliche Dateien

Es ist nicht praktisch, große Dateien in Ihr GitHub Repo zu legen oder diese direkt in das Bild einzubinden, das Binder erstellt. Die beste Option für große Dateien ist, eine auf das Datenformat spezialisierte Bibliothek zu verwenden, um die Daten so zu streamen, wie Sie sie verwenden oder sie auf Wunsch als Teil Ihres Codes herunterzuladen.

Aus Sicherheitsgründen ist der ausgehende Verkehr Ihres Binders nur auf HTTP/S oder GitHub Verbindungen beschränkt. Sie können FTP-Seiten nicht zum Abrufen von Daten auf mybinder.org nutzen.

(z2b-private-Dateien)=
### Private Dateien

Es gibt keine Möglichkeit, auf Dateien zuzugreifen, die von mybinder.org nicht öffentlich sind. Sie sollten alle Informationen in Ihrem Binder als öffentlich betrachten, was bedeutet:

- es sollte in deiner GitHub Repo keine Passwörter, Token, Schlüssel usw. geben;
- Sie sollten keine Passwörter in einen Binder eingeben, der auf mybinder.org läuft;
- Sie sollten Ihren privaten SSH-Schlüssel oder API-Token nicht in einen laufenden Binder hochladen.

Um den Zugriff auf private Dateien zu unterstützen Sie müssten einen lokalen Einsatz von [BinderHub](https://binderhub.readthedocs.io) erstellen, bei dem Sie selbst über die Sicherheitsabwägungen entscheiden können.

```{note}
Der Aufbau eines BinderHub ist keine einfache Aufgabe und wird normalerweise von IT/RSE-Gruppen aus Gründen des Managements von Wartung, Sicherheit und Governance übernommen.
Das soll jedoch nicht heißen, dass sie die _only_ Gruppen von Personen sind, die einen BinderHub bauen sollten/könnten.
```

(z2b-step-8)=
## 8. Daten mit `postBuild` abrufen

🚦🚦🚦

````{tabbed} Python
1) Gehe zu deinem GitHub Repo und erstelle eine Datei namens `postBuild`
2) In `postBuild`, füge eine einzige Zeile zum Lesen hinzu: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` ist ein Programm, das Inhalte von Web-Servern abruft.
     Diese Zeile extrahiert den Inhalt aus der bitly URL und speichert ihn in den Dateinamen der `-O`-Flagge (Kapital "O", nicht Null), in diesem Fall `gapminder. sv`.
     Das `-q` Flag sagt `wget`, dies ruhig zu tun, was bedeutet, dass es nichts auf die Konsole drucken wird.
3) Aktualisieren Sie Ihre "Anforderungen". xt`-Datei, indem du eine neue Zeile mit `pandas` hinzufügst und eine neue Zeile mit `matplotlib` hinzufügst
   - Diese Pakete sind nicht notwendig, um die Daten herunterzuladen, aber wir werden sie verwenden, um die CSV-Datei zu lesen und ein Plot zu erstellen
4) Klicke auf das Binder-Abzeichen in deiner README um deinen Binder zu starten

Sobald der Binder gestartet ist, Sie sollten sehen, dass eine neue Datei erscheint, die nicht Teil Ihres Repos war, wenn Sie auf das Abzeichen klicken.

Visualisieren Sie die Daten nun durch das Erstellen eines neuen Notizbuchs (wählen Sie "Python 3" aus dem Notizbuch-Bereich) und führen Sie den folgenden Code in einer Zelle aus.

```python
%matplotlib inline

import pandas

data = pandas.read_csv("gapminder.csv", index_col="country")

Jahre = Daten. olumns.str.strip("gdpPercap_") # Jahr aus den letzten 4 Zeichen jedes Spaltennamens
data.columns = Jahre extrahieren. stype(int) # Jahreswerte in ganze Zahlen konvertieren Speichere Ergebnisse zurück in Daten

Daten. oc["Australien"]. lot()
```

```{note}
Siehe diese [Software Carpentry Lektion](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) für weitere Informationen.
```
````

````{tabbed} Julia
1) Gehe zu deinem GitHub Repo und erstelle eine Datei namens `postBuild`
2) In `postBuild`, füge eine einzige Zeile zum Lesen hinzu: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` ist ein Programm, das Inhalte von Web-Servern abruft.
     Diese Zeile extrahiert den Inhalt aus der bitly URL und speichert ihn in den Dateinamen der `-O`-Flagge (Kapital "O", nicht Null), in diesem Fall `gapminder. sv`.
     Das `-q` Flag sagt `wget`, dies ruhig zu tun, was bedeutet, dass es nichts auf die Konsole drucken wird.
3) Aktualisieren Sie Ihr `Projekt. oml` Datei durch Hinzufügen neuer Abhängigkeiten zu `[deps]` mit den folgenden Zeilen:

   ```julia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plots = "91a5bcdd-55d7-5caf-9e0b-520d859cae80"
   ```

   - Diese Pakete sind nicht notwendig, um die Daten herunterzuladen, aber wir werden sie verwenden, um die CSV-Datei zu lesen und ein Plot zu erstellen
4) Klicken Sie auf das Binder Abzeichen in Ihrer README um Ihren Binder zu starten

Sobald der Binder gestartet hat, wird der Binder gestartet Sie sollten sehen, dass eine neue Datei erscheint, die nicht Teil Ihres Repos war, wenn Sie auf das Abzeichen klicken.

Visualisieren Sie die Daten nun durch das Erstellen eines neuen Notizbuchs (wählen Sie "Julia" aus dem Notizbuch-Bereich) und führen Sie den folgenden Code in einer Zelle aus.

```julia
benutzt DataFrames
mit CSV
mit Plots

data = CSV.read("gapminder. sv", DataFrame)

# Entpacken Sie die Zeile entsprechend Australien
aus_gdp = data[:, :country] . = "Australien", :]
aus_gdp = Matrix(aus_gdp[:, :end])[:] # als Vektor

# Die Jahre als Ints aus den Spaltennamen extrahieren
Jahre = [x[end-3:end] für x in names(data)[2:end]]
Jahre = parse. Int, Jahre)

# Plot
plot(Jahre, aus_gdp)
```
````

````{tabbed} R
1) Gehe zu deinem GitHub Repo und erstelle eine Datei namens `postBuild`
2) In `postBuild`, füge eine einzige Zeile zum Lesen hinzu: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` ist ein Programm, das Inhalte von Web-Servern abruft.
     Diese Zeile extrahiert den Inhalt aus der bitly URL und speichert ihn in den Dateinamen der `-O`-Flagge (Kapital "O", nicht Null), in diesem Fall `gapminder. sv`.
     Das `-q` Flag sagt `wget`, dies ruhig zu tun, was bedeutet, dass es nichts auf die Konsole drucken wird.
3) Aktualisiere deine `install.R` Datei, um zwei zusätzliche Abhängigkeiten zu installieren: `"tidyr"` und `"ggplot2"`. Um dies zu tun, geben Sie einen Zeichenvektor der benötigten Pakete anstelle eines einzelnen Zeichenstrings in `install.packages()` ein. Der Installationsbefehl sollte nun so aussehen:

   ```r
   Installation. ackages(c("readr", "tidyr", "ggplot2"))
   ```

    - Diese Pakete sind nicht notwendig, um die Daten herunterzuladen, aber wir werden sie zum Lesen der CSV-Datei verwenden verarbeiten und ein Plot machen
Klicken Sie auf das Binde-Abzeichen in Ihrer README um Ihren Binder zu starten

Nach dem Start des Binders Sie sollten sehen, dass eine neue Datei erscheint, die nicht Teil Ihres Repos war, wenn Sie auf das Abzeichen klicken.

Visualisieren Sie die Daten nun durch das Erstellen eines neuen Notizbuchs (wählen Sie "R" aus dem Notizbuch-Bereich) und führen Sie den folgenden Code in einer Zelle aus.

```r
library(readr)
library(tidyr)
library(ggplot2)

data <- read_csv("gapminder. sv") %>%
    pivot_longer(-country,
                 names_to = "Jahr",
                 values_to = "gdpPercap",
                 names_prefix = "gdpPercap_",
                 names_transform = list(year = as. nteger))

data[data$country == "Australia", ] %>%
    ggplot(aes(x = Jahr, y = gdpPercap)) +
    geom_line()
```
````
(z2b-beyond-notebooks)=
## Ändere die Schnittstelle
Während dieses Tutorials haben wir die JupyterLab-Schnittstelle benutzt. Dies ist die Standardschnittstelle für neu erstellte Binder-Instanzen. Dies ist jedoch nicht die einzige auf mybinder.org verfügbare Schnittstelle, die Classic Notebook View und RStudio sind ebenfalls verfügbar. (Eine R-Umgebung muss installiert sein, damit RStudio verfügbar ist.)
Sie können auf die verschiedenen Schnittstellen auf unterschiedliche Art und Weise zugreifen. Der einfachste Weg ist, die Tasten im JupyterLab Launcher zu verwenden, aber Sie können URL-Parameter bereitstellen, um direkt eine bestimmte Schnittstelle (oder Datei! wenn die Binder-Instanz gestartet wird. Wir werden nun drei Wege behandeln, wie Sie Ihre Binder-URL verändern können, um zwischen den Schnittstellen zu navigieren.
### von innerhalb eines laufenden Binders
Hier ist die Struktur der URL innerhalb einer laufenden Binder-Instanz mit JupyterLab:
> **https://<some-prefix>.mybinder.org/user/<a composite of your username, repo name and a hash>/lab**
You can change the interface from JupyterLab to either the Classic Notebook or RStudio by changing the `/lab` part of the URL to:
- **Classic Notebook:** `/tree`
- **RStudio:** `/rstudio`
### by changing the mybinder.org launch link
Here is the launch link you have been using throughout this tutorial:
> **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD**
You can access each interface by appending once of the following to the end of you URL:
- **Jupyter Notebook:** `?urlpath=tree`
- **JupyterLab:** `?urlpath=lab`
- **RStudio:** `?urlpath=rstudio`
### by using the mybinder.org form
You can also set the interface when constructing your launch link on the mybinder.org website (instead of editing the URL directly) as demonstrated in the below gif.

```{figure} https://user-images.githubusercontent.com/1448859/53651127-4dabe900-3c46-11e9-8684-2cfde840d4ce.gif
---
name: changing_interfaces
alt: A gif demonstrating how to change the interface of a Binder on the mybinder.org website
---
Use the "URL to open" option on the mybinder.org site to select your interface
```

(z2b-over-to-you)=
## Now over to you!

Now you've binderized (bound?) this demo repo, it's time to binderize the example script and data you brought along!

**Some useful links:**

- Choosing languages:
  - **<https://mybinder.readthedocs.io/en/latest/howto/languages.html>**
- Configuration files:
  - **<https://mybinder.readthedocs.io/en/latest/using/config_files.html>**
- Example Binder repos:
  - **<https://mybinder.readthedocs.io/en/latest/sample_repos.html>**
- Getting data:
  - With `wget`: **<https://github.com/binder-examples/getting-data>**
  - With `quilt`: **<https://github.com/binder-examples/data-quilt>**
  - From remote storage: **<https://github.com/binder-examples/remote_storage>**

**Advanced usage patterns:**

- Separating content from envorinment with `nbgitpuller` to reduced rebuilds:
  - **<https://discourse.jupyter.org/t/tip-speed-up-binder-launches-by-pulling-github-content-in-a-binder-link-with-nbgitpuller/922>**
- Tips for reducing the start-up time of your repository:
  - **<https://discourse.jupyter.org/t/how-to-reduce-mybinder-org-repository-startup-time/4956>**
