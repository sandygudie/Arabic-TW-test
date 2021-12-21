(rr-code-reuse)=
# Wiederverwendbarer Code
Ihr Software-Projekt könnte von einem kleinen Skript zur Datenverarbeitung bis hin zu einem Notebook zur Datenanalyse reichen oder eine Software-Bibliothek, die Ihre Algorithmen implementiert. Unabhängig davon, wie groß oder klein Ihr Software-Projekt ist, ist es wichtig, Ihren Code wiederverwendbar zu machen.

Verschiedene Arten von Software haben unterschiedliche Anforderungen für die Wiederverwendbarkeit: für ein kleines Skript, ausreichende Dokumentation könnte ausreichen, während für eine missionskritische Softwarebibliothek eine gründliche Prüfung erforderlich sein könnte. Auf der grundlegendsten Ebene müssen Sie nur Ihren Code irgendwo online stellen, was wahrscheinlich eine lange Zeit dauern wird. Ein aufwändigerer Ansatz, Ihre Forschungssoftware wiederverwendbarer zu machen, besteht darin, die FAIR-Prinzipien für Forschungssoftware (FAIR4RS-Prinzipien) {cite:ps}`ChueHong2021FAIR4RS` zu befolgen.

Wenn wir über die Wiederverwendbarkeit von Code sprechen, dann ist es nützlich, zu klären, was wir meinen. In der {ref}`Tabelle der Definitionen für die Reproduzierbarkeit<rr-overview-definitions-reproducibility>` haben wir die reproduzierbare Forschung als die Verwendung der gleichen Daten und des gleichen Codes definiert. Wenn wir jedoch über die Wiederverwendung von Code sprechen, kann dies viele Formulare erfordern: Möglicherweise möchten wir den gleichen Code ausführen (für kompilierte Programmiersprachen, dies könnte sogar die selbe Binärdatei sein), oder wir möchten den Quellcode modifizieren und ihn in einer bestimmten Weise an unsere Bedürfnisse anpassen. Freire und Chirigati {cite:ps}`Freire2018Reproduzierbarkeit` bieten ein Framework von verschiedenen Ebenen der Reproduzierbarkeit, je nachdem, was geändert werden kann. Sie definieren die folgenden Ebenen der Reproduzierbarkeit: Wiederholbar, wiederstartbar, tragbar, erweiterbar und modifizierbar.

Wir können die Definitionen der Reproduzierbarkeit auf dem Freire-Rahmen wie folgt zuordnen:

| Freire framework | Definitionen reproduzierbar                                               |
| ---------------- | ------------------------------------------------------------------------- |
| Wiederholbar     | Reproduzierbar (gleiche Daten, gleiche Analyse)                           |
| Erneut starten   | Robust & Replikabel (gleicher Code, verschiedene Daten/Analyse/Parameter) |
| Tragbar          | *Nicht als* angesehen (Name Code/Daten, andere Umgebung)                  |
| Erweiterbar      | (teilweise) Verallgemeinerbar                                             |
| Veränderbar      | (teilweise) Verallgemeinerbar                                             |

Portabilität wurde vorher nicht in Betracht gezogen, sondern für Software eine andere Umgebung (wie z.B. unterschiedliche Hardware, Betriebssystem oder sogar eine Neuinstallation auf vergleichbarer Hardware) können die Funktionsfähigkeit der Software beeinträchtigen (z.B. Abhängigkeiten).

Generalisierbar fasst auch zwei Konzepte zusammen: Erweiterbar (die Fähigkeit, sich in andere Software zu integrieren) und Veränderbar (die Möglichkeit, Teile der Implementierung zu ändern, um ihre Funktionalität zu erweitern).

Im Rest dieses Kapitels stellen wir Ihnen eine Liste von Empfehlungen zur Verfügung, die Sie befolgen können, um sicherzustellen, dass Ihr Code wiederverwendbar ist.

(rr-code-reuse-recommendation-checklist)=
## Wie Sie Ihren Code wiederverwendbarer machen
Dieser Abschnitt enthält eine Checkliste mit Empfehlungen, um Ihre Software besser wiederverwendbar zu machen. Der Abschnitt {ref}`rrr-code-reuse-recommendation-details` enthält eine ausführlichere Erläuterung jeder dieser Empfehlungen. Sie können den Empfehlungen folgen, die für Ihre Art von Software besser geeignet sind, und diejenigen überspringen, die in Ihrem Fall nicht relevant sind.

### Wiederholbare Empfehlungen
1. Vergewissern Sie sich, dass Sie es (im Leerzeichen) finden können
1. Vergewissern Sie sich, dass Sie es finden können (in Zeit)
1. Stellen Sie sicher, dass Sie die gleiche Abfolge von Operationen ausführen können
1. Stellen Sie sicher, dass Ihre Umgebung und die Abfolge von Operationen robust sind und kein Mensch benötigt wird, um zu replizieren, was getan wurde
1. Lizenzieren Sie Ihren Code
    - mit einer Lizenz zur Wiederverwendung;
    - mit einer Lizenz, die mit den Abhängigkeitslizenzen kompatibel ist
1. Stellen Sie sicher, dass es zitierbar ist
1. Benötigte Daten einbeziehen
1. Schreibe nützliche Dokumentation*

### Re-Laufende Empfehlungen
1. Hard codierte Bits entfernen und den Code modular machen
1. Testen Sie, ob die von Ihnen erstellten Module verschiedene Typen von Eingabedaten oder Parameter annehmen können
1. Verwandeln Sie die Module in ein Paket/Werkzeugkasten
1. Schreibe nützliche Dokumentation*

### Tragbare Empfehlungen
1. Stellen Sie sicher, dass Sie die Umgebung, in der sie gelebt hat wiederherstellen können
1. Schreibe nützliche Dokumentation*

### Erweiterbare Empfehlungen
1. Schreibe nützliche Dokumentation*

### Änderbare Empfehlungen
1. Stelle sicher, dass dein Code von Menschen lesbar ist
1. Stellen Sie sicher, dass Kommentare vorhanden sind
1. Schreibe nützliche Dokumentation*

Der Beobachtungsleser kann feststellen, dass `Schreiben Sie nützliche Dokumentation` für jede Wiederverwendungsstufe erwähnt wird. Das liegt daran, dass für die Wiederverwendung unterschiedliche Ebenen der Dokumentation erforderlich sind.

### Unterschiedliche Dokumentationsanforderungen für verschiedene Wiederverwendungsstufen
Das Schreiben nützlicher Dokumentation ist eine wichtige Voraussetzung für alle Ebenen der Wiederverwendung. Für die verschiedenen Ebenen der Wiederverwendung gibt es jedoch unterschiedliche Dokumentationsanforderungen:

Die Dokumentation:
- erklärt Benutzung, spezifiziert:
  - was die Software tut; (erforderlich für Wiederholbar)
  - wie es verwendet werden kann; (erforderlich für wiederholbar)
  - welche Optionen/Parameter verfügbar sind. (erforderlich für Wiederholbar)
- enthält Beispiele, wie man es ausführt. (erforderlich für Wiederholbar)
- hat Installationsanweisungen, inklusive guter Beschreibungen für:
  - die Hardware, von der sie abhängt (zum Beispiel GPUs); (benötigt für portable)
  - das Betriebssystem, auf dem die Software getestet wurde; (erforderlich für portable)
  - Software-Anforderungen (wie Bibliotheken und Shell-Einstellungen). (erforderlich für tragbar)

(rr-code-reuse-recommendation-details)=
## Empfehlungen für wiederverwendbaren Code
Stellen Sie sicher, dass Sie (oder jemand andere) Ihren Code wiederverwenden können, um genau das zu tun, was Sie getan haben. Der Abschnitt {ref}`rrr-code-reuse-recommendation-checklist` enthält eine Checkliste mit Empfehlungen, um Ihre Software wiederverwendbarer zu machen. In diesem Abschnitt enthält eine ausführlichere Erläuterung jeder dieser Empfehlungen, mit Zeigern auf andere relevante Teile dieses Leitfadens.

### Wiederholbare Empfehlungen
In diesem Stadium müssen Sie vielleicht nicht einmal den Code öffnen und lesen können Sie wollen nur sicherstellen, dass Sie alle erforderlichen Schritte erneut ausführen und die gleichen Ergebnisse wie Sie hatten.

#### 1. Vergewissern Sie sich, dass Sie es (im Leerzeichen) finden können
Ihr Code muss öffentlich gespeichert und mit Mitarbeitern geteilt werden. Es hat eine einzigartige persistente Identifikation, so dass jeder ihn finden und darauf zugreifen kann.

**Siehe auch**: {ref}`rr-vcs`

#### 2. Vergewissern Sie sich, dass Sie es finden können (in Zeit)
Idealerweise wird die zeitliche Entwicklung des Codes mit Versionskontrolle dokumentiert. Dadurch können Sie eine bestimmte Version aus der Vergangenheit abrufen.

**Siehe auch**: {ref}`rr-vcs`

#### 3. Stellen Sie sicher, dass Sie die gleiche Abfolge von Operationen ausführen können
Oft ist der Mensch, der die Umgebung aufgebaut hat, auch derjenige, der den Code geschrieben hat, und derjenige, der die genaue Reihenfolge der Schritte kennt, die notwendig sind, um den Code erneut ausführen und die Ergebnisse reproduzieren zu können. Dies könnte sicherlich sorgfältig dokumentiert werden, damit ein anderer Mensch es wiederholen kann.

**Siehe auch**: [CodeRefinery Lektion über Reproduzierbare Forschung](https://coderefinery.github.io/reproducible-research/)

#### 4. Stellen Sie sicher, dass Ihre Umgebung und die Abfolge von Operationen robust sind und kein Mensch benötigt wird, um zu replizieren, was getan wurde
Sie wollen sich nicht auf Menschen verlassen. Sie neigen dazu, Fehler zu machen, auch wenn sie keine schlechten Absichten haben. Sie möchten, dass Ihre Umgebung Skripte erstellt und bei Bedarf neu erstellt wird und dass Ihre Abfolge von Operationen durch ein Pipeline-Skript ausgeführt wird, das alle Schrittfolgen verbindet.

**Siehe auch**: {ref}`rr-renv-options`

#### 5. Lizenzieren Sie Ihren Code
Stellen Sie sicher, dass Sie eine Lizenz an Ihren Code anhängen und angeben, wie Sie zitiert werden wollen, wenn jemand sie wiederverwendet. Ziehen Sie in Erwägung, eine permissive Lizenz zu verwenden, die eine Wiederverwendung erlaubt. Außerdem sollten Sie eine Lizenz wählen, die mit den Lizenzen von Bibliotheken oder Paketen kompatibel ist, von denen Ihre Software abhängt.

**Siehe auch**: {ref}`rr-licensing-software`, {ref}`rr-licensing-software-permissive`, {ref}`rr-licensing-Kompatibilität`

#### 6. Stellen Sie sicher, dass es zitierbar ist
Stellen Sie sicher, wie Sie zitiert werden wollen, wenn jemand es wiederverwendet.

**Siehe auch**: {ref}`cm-citable-cite-software`

#### 7. Benötigte Daten einbeziehen
Wenn die Software von einer Art von Daten abhängt, sollten die Daten verfügbar sein

**Siehe auch**: {ref}`rr-rdm-data`

### Re-Laufende Empfehlungen
Stellen Sie sicher, dass Sie (oder andere) es wiederverwenden können, um das zu tun, was Sie getan haben, aber mit verschiedenen Daten/unterschiedlichen Parametern

#### 1. Hard codierte Bits entfernen und den Code modular machen
Sie möchten keine detaillierten Angaben zu Ihren Daten oder Analyseparametern in den Code eintragen. Wenn etwas zu einer wiederverwendbaren Funktion werden kann, trennen Sie es von den hardcodierten Parametern und verwandeln es in etwas (wieder)machbares für sich. Machen Sie die Module rein: Bei gleicher Eingabe gibt eine reine Funktion immer den gleichen Wert zurück.

**Siehe auch**: [Lektion für die Entwicklung modularer Code](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/modular-code-development/master/talk.md/#1)

#### 2. Testen Sie, ob die von Ihnen erstellten Module verschiedene Typen von Eingabedaten oder Parameter annehmen können
Möglicherweise wissen Sie noch nicht, wie Ihr Code in Zukunft wiederverwendet wird aber Sie können verhindern, wie es nicht verwendet werden soll, wenn Sie testen können, welche Parameter erlaubt sind.

**Siehe auch**: [CodeRefinery Lektion zum automatisierten Testen](https://coderefinery.github.io/testing/motivation/)

#### 3. Verwandeln Sie die Module in ein Paket/Werkzeugkasten
Trennen Sie noch mehr die Besonderheiten Ihres Projekts mit den Bits die in anderen Projekten oder von anderen Personen wiederverwendet werden können.

**Siehe auch**: {ref}`rr-renv-package`, [Packaging software](https://scicomp.aalto.fi/scicomp/packaging-software/), [Softwarepakete in Python](https://aaltoscicomp.github.io/python-for-scicomp/packaging/)

### Tragbare Empfehlungen
Portabilität bezieht sich auf die Fähigkeit, Software in eine neue Umgebung zu übertragen. Dies könnte sich auf eine identische (aber nicht identische) Maschine beziehen, kann aber auch auf eine neue Hardware-Architektur, ein Betriebssystem und dergleichen verweisen. Beides ist wichtig für die Wiederverwendung von Software.

#### 1. Stellen Sie sicher, dass Sie die Umgebung, in der sie gelebt hat wiederherstellen können
Die Umwelt ist eine zerbrechliche Momentaufnahme in der Zeit, die den Kodex stillschweigend begleitet. Es kann den Menschen umfassen, der die Software betrieben hat, die Schritte, die der Mensch zur Erstellung der Daten gemacht hat die Hardware, das Betriebssystem, die Bibliotheken, externe Pakete/Toolboxen/Abhängigkeiten. All dies kann sorgfältig dokumentiert werden, damit ein anderer Mensch alle genau gleichen Schritte wiederholen kann.

**Siehe auch**: {ref}`rr-renv`

### Erweiterbare und änderbare Empfehlungen
Stelle sicher, dass andere auf deinem Code bauen können, um ihn zu erweitern und zu verbessern.

#### 1. Stelle sicher, dass dein Code von Menschen lesbar ist
Es zahlt oft mehr Code für andere Menschen zu schreiben, damit sie ihn lesen können (einschließlich Ihres zukünftigen Selbst). Ein kryptischer Oneliner mit obskuren Variablennamen ist nicht schneller oder effizienter, als den einen Liner in mehrere Schritte mit lesbaren Variablennamen aufzuteilen, die Sinn machen. Darüber hinaus wird die Verwendung von Codierungskonventionen anderen Lesern helfen.

**Siehe auch**: {ref}`rr-code-style-and-formatting`, {ref}`rr-code-quality-advantages`

#### 1. Stellen Sie sicher, dass Kommentare vorhanden sind
Schreiben Sie Kommentare, bevor Sie den aktuellen Code schreiben. Stellen Sie sich vor, jemand könnte einfach die Kommentare lesen und alle Code-Bits zwischen den Kommentaren überspringen und ein vollständiges Bild von dem, was vor sich geht, als würde man den ganzen Code lesen.
