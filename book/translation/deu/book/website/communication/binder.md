(Binder)=
# Binder

In diesem Kapitel werden wir über Project Binder und mybinder.org diskutieren, um die Forschung transparent und interaktiv auszutauschen.

(binder-share)=
## Warum sollten Sie Ihre Arbeit teilen?

Die Motivation für den Austausch von Forschungsausgaben wird im Kapitel {ref}`rrr-open` vertieft.

Kurzum, die gemeinsame Nutzung Ihres Recherchecodes kann Ihnen helfen, die von Ihnen vorgestellten Ergebnisse durch die Darstellung des Prozesses, den Sie durchlaufen haben, um sie zu erreichen. Durch Teilen von Code Wir vermeiden auch, das Rad neu zu erfinden, um ein Forschungsthema voranzutreiben, da die bisherigen Werkzeuge auf der Basis der vorhandenen Werkzeuge aufgebaut werden können.

Das größte Hindernis für den Austausch von Code ist jedoch die Installation von Paketen und das Einrichten der Rechenumgebung, wie wir im nächsten Abschnitt sehen werden. Indem Sie Ihre Arbeit über Plattformen wie mybinder.org teilen:

- Die Installation von Softwarepaketen ist keine Herausforderung mehr
- Menschen, die verschiedene Betriebssysteme verwenden, haben ähnliche Erfahrungen seit der Berechnung auf der Plattform und nicht auf ihrem lokalen Rechner
- Ihre Arbeit kann an ein breiteres Publikum verteilt werden, da die technische Barriere abgebaut wurde

(binder-was)=
## Was ist Project Binder?

Wir haben diskutiert, warum es wichtig ist, Ihre Arbeit zu teilen und wir haben einen Punkt erreicht, an dem wir beschlossen haben, einige Jupyter Notebooks mit Analysecode auf einer Kollaborationsplattform zu veröffentlichen, wie GitHub.

GitHub ist eine großartige Plattform, um Code _statisch zu teilen._. Wenn das Projektarchiv öffentlich ist, kann jeder zu Ihrem Notebook navigieren und den Inhalt lesen. Jedoch ist _der Ausführen von_ Code viel komplizierter, als ihn nur wie GitHub anzuzeigen. Viele voneinander abhängige Teile werden benötigt, um Code auszuführen, wie:

- eine Kopie des Codes selbst;
- die entsprechende Software zum Ausführen;
- alle zusätzlichen Pakete, von denen der Code abhängt, die nicht als Teil der Kernsoftware ausgeliefert werden;
- alle Daten für die Analyse erforderlich;
- und Sie benötigen auch ein paar Hardware (ein Computer!), um es auch verwenden zu können.

Zusätzlich zum Erwerb all dieser Teile Sie müssen sie auch korrekt und so installieren, dass sie nicht beeinflusst werden oder in Konflikt mit anderen Software geraten, die auf Ihrem Rechner läuft. Es ist eine Menge Arbeit!

Wie viel einfacher wäre es, wenn wir **Code im Browser**ausführen könnten, ähnlich wie er angezeigt wird? Dies ist es, was Project Binder zu erreichen beabsichtigt.

Project Binder stellt einem Benutzer folgende Infrastruktur zur Verfügung:

- einige Hardware zum Ausführen von Code, normalerweise ein in der Cloud gehosteter Server, kann aber auch Hardware auf der Prämisse sein;
- eine Rechenumgebung:
  - die Lehrlingssoftware
  - irgendwelche zusätzlichen Paket-Abhängigkeiten
  - erforderliche Eingabedaten
  - und eine Kopie des Codes selbst (Notizbücher oder Skripte);
- eine URL, in der die Umgebung läuft, so dass der Code von Ihnen oder Ihren Mitarbeitern interagiert werden kann.

Project Binder hat alle bewegten Teile zusammengepackt, die es herausfordern, Rechenarbeiten in eine einfach zu bedienende Oberfläche zu teilen. Es gibt eine **kostenlose und öffentliche** Version dieser Schnittstelle unter [**mybinder.org**](https://mybinder.org).

Die Zeichentrickserie unten von Juliette Taka zeigt einen Workflow auf, den Wissenschaftler mit Binder übernehmen könnten.

```{figure} ../figures/binder-comic.png
---
Name: binder_comic
alt: Eine Abbildung der Schritte, die eine Person unternehmen kann, um ein binderisiertes Projekt zu erstellen.
---
Figure credit: [Juliette Taka, Logilab und das OpenDreamKit Projekt](https://opendreamkit.org/2017/11/02/use-case-publishing-reproducible-notebooks/)
```

Mehr über Project Binder und mybinder.org erfahren Sie auf der [Seite von mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

(binder-disam)=
### Unklarheit

In diesem Abschnitt gibt es einige verwandte Begriffe, die hier für Klarheit skizziert werden:

- **Projektbinder**: Eine offene Gemeinschaft, die es ermöglicht, teilbare, interaktive und reproduzierbare Umgebungen zu erstellen. Die technologische Leistung dieses Projekts ist ein {ref}`rrr-binderhub`.
- **BinderHub**: Eine Cloud-basierte Infrastruktur zur Erzeugung von Bindern. Die am häufigsten verwendete ist [mybinder.org](https://mybinder.org), die vom Project Binder Team gepflegt wird. Es basiert auf einer Reihe von Open-Source-Tools, einschließlich [JupyterHub](https://z2jh.jupyter.org), für die Bereitstellung von Cloud-Rechenressourcen für Benutzer über einen Browser; und [`repo2docker`](https://repo2docker.readthedocs.io/)für das Erstellen von Docker-Bildern aus Projekten. Da es sich um ein offenes Projekt handelt, ist es möglich, andere BinderHubs zu erstellen, die spezialisierte Konfigurationen unterstützen können. Eine solche Konfiguration könnte die Authentifizierung beinhalten, damit private Repositories unter engen Mitarbeitern geteilt werden können.
- **Ein Binder**: Eine freigegebene Version eines Projekts, die in einer reproduzierbaren Rechenumgebung eingesehen und interagiert werden kann, die über einen Webbrowser in der Cloud läuft. Durch die Automatisierung der Installation der Rechenumgebung (wie im Kapitel {ref}`rrr-renv` diskutiert), Project Binder verwandelt den Overhead einer solchen Umgebung in den Akt der gemeinsamen Nutzung einer URL.
- **[mybinder.org](https://mybinder.org)**: Ein öffentlicher und freier BinderHub. Da es öffentlich ist, sollten Sie es nicht verwenden, wenn Ihr Projekt persönliche oder vertrauliche Informationen (wie Passwörter) benötigt.
- **Binderize**: Der Prozess zum Erstellen eines Binders aus einem Projekt.

(binder-angemessen)=
## Wann ist es angebracht, mybinder.org zu benutzen?

Die Aufrechterhaltung eines kostenlosen, anonymen Dienstes in der Wolke ist eine Menge ehrenamtlicher Arbeit und kostet viel Geld. Um die laufenden Kosten etwas zu reduzieren, legt mybinder.org für jede laufende Binder-Instanz Rechenbeschränkungen auf. Diese Einschränkungen sind:

- 1 CPU, und
- 1 GB RAM.

Daher ist mybinder.org **nicht** ein geeigneter Ort, um zum Beispiel End-zu-End-Replikationen von Machine Learning-Workflows durchzuführen!

Und das ist der Hauptgrund, warum dieses Kapitel über Binder in den "Leitfaden für Kommunikation" aufgenommen wurde. Mit diesen rechnerischen Einschränkungen bietet sich mybinder.org sehr gut an, interaktive Demonstrationen und Lernressourcen für Softwarepakete oder Forschungsanalysen zu veranstalten. In diesem Szenario wollen die Leute, die auf den Binder-Link klicken, wahrscheinlich etwas lernen und durch einen zeitraubenden Modell-Trainingsprozess zu sitzen, wird ihnen wahrscheinlich nicht helfen, das zu erreichen. Instead, you could provide pre-trained models or instructions on how to train the models on their own hardware and _come back_ to the Binder for the remainder of the interactive tutorial.

Wann ist es also angebracht, mybinder.org zu benutzen?

- When you want to _communicate_ something in an interactive manner, such as short analyses, tutorials, or even blogs! Schau dir [Achintya Raos Blog powered by mybinder.org](https://blog.achintyarao.in/about/) an!
- Wenn der Code und die zugehörigen Daten (falls relevant) öffentlich verfügbar sind
- Wenn der Code, den du interaktiv ausführen möchtest, keine Menge an Ressourcen oder spezialisierten Ressourcen benötigt (zum Beispiel GPUs)

(binder-faqs)=
## FAQ

Viele häufige Fragen werden auf der [Über mybinder.org Seite](https://mybinder.readthedocs.io/en/latest/about/about.html) beantwortet.

### Wie kann ich meine Änderungen wieder in meinem Projektarchiv speichern?

Leider können Sie das nicht. Zumindest nicht von der Kommandozeile in einer laufenden Binder-Instanz.

Zurückschreiben in ein gehostetes Repository, ob auf GitHub oder einer anderen Plattform, benötigt eine Art Anmeldeinformation, um Sie zum Schreiben in dieses Projektarchiv zu bevollmächtigen. Und wie bereits erwähnt, mybinder. rg ist ein gänzlich öffentlicher Dienst und Sie sollten unter keinen Umständen sensible Informationen für eine laufende Binder-Instanz zur Verfügung stellen.

Doch Mybinder. rg führt ein Add-on namens [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) aus, das einen Download-Button zur lokalen Speicherung Ihrer Notebooks bietet _auch wenn Ihr Browser seine Verbindung mit der Cloud-Infrastruktur verloren hat, die die Berechnung bereitstellt!_ Das bedeutet, dass Sie Ihren Fortschritt lokal speichern können, aktualisieren Sie Ihr Repository mit Ihren gespeicherten Notizbüchern und starten Sie Ihren Binder mit den aktualisierten Notebooks neu.

```{figure} ../figures/binder_notebook_banner.jpg
---
Name: binder_notebook_banner
alt: Ein Screenshot der Kontrollleiste eines Jupyter Notebooks mit einem Download-Button, der durch ein violettes Rechteck hervorgehoben wird.
---
Benutze diesen "Download"-Button in einem Jupyter Notebook auf mybinder. rg wird es Ihnen ermöglichen, Ihre Notebooks lokal zu speichern, auch nachdem die Binder-Instanz von den Rechenressourcen getrennt wurde.
```

### Wie kann ich mit meinen Kollegen auf mybinder.org zusammenarbeiten?

Es ist nicht unmöglich, aber es gibt definitiv Platz, diese Funktion im Vergleich zu anderen "kostenlosen Cloud-Rechendiensten" zu entwickeln.

Diejenigen, die daran interessiert sind, erfahren Sie mehr in [diesem Diskurseintrag](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) und im [`jupyterlab-link-share` repository](https://github.com/jtpio/jupyterlab-link-share).

### Wie unterscheidet sich mybinder.org von Google Colab?

Google Colab bietet eine "Küchensenkung"-Rechenumgebung mit vielen der populärsten Datenwissenschaften-Softwarepakete vorinstalliert. Im Gegensatz dazu baut mybinder.org maßgeschneiderte Images für jedes Projektarchiv, speziell für die Installation der Pakete in Ihren Konfigurationsdateien.

### Kann ich mich mit `INSERT DATENPROVIDER HIER` verbinden?

Netzwerkverbindungen auf mybinder.org sind zu Sicherheits- und Missbrauchszwecken ziemlich begrenzt. Dabei sollten Sie sich mit einem externen Datenanbieter verbinden können, solange er die folgenden zwei Kriterien erfüllt:

- Es kann über eine HTTP/HTTPS-Verbindung erreicht werden
- Sie benötigen keine Zugangsdaten für den Zugriff auf die Daten

Vergessen Sie nicht, dass mybinder.org ein gänzlich öffentlicher Dienst ist und unter keinen Umständen sollten Sie vertrauliche Informationen, wie beispielsweise Anmeldeinformationen, an eine Binder-Instanz weitergeben.

(binder-segue)=
## So erstellen Sie ein Binder-Read-Projekt

Das nächste Kapitel enthält ein [Null-Binder Tutorial](z2b) , das Sie durch die Erstellung Ihres ersten Binder-fertigen Projekts auf GitHub führt.
