# GitHub / Visual Studio Code Extension

## Übersicht und Prinzip

GitHub ist eine Plattform zur Verwaltung und Zusammenarbeit an Softwareprojekten. Sie baut auf dem Versionskontrollsystem Git auf und erweitert es um Funktionen für Teamarbeit, Projektorganisation und Automatisierung.

Mit GitHub können Entwickler ihren Code online speichern, Änderungen nachverfolgen und gemeinsam an Projekten arbeiten. 
Wichtige Funktionen sind 
* Pull Requests (für Code-Reviews und Diskussionen), 
* Issues (zur Aufgaben- und Fehlerverwaltung) sowie 
* GitHub Actions (für automatisierte Workflows wie Tests und Deployments).

Besonders in der Open-Source-Community ist GitHub weit verbreitet, da es Entwickler weltweit ermöglicht, unkompliziert zusammenzuarbeiten. Auch Unternehmen nutzen GitHub, um ihre Projekte transparent und effizient zu entwickeln.

Was ist der Zusammenhang zwischen GitHub, Git und GitLab?


| Aspekt         | Git                       | GitHub                                | GitLab                                       |
| -------------- | ------------------------- | ------------------------------------- | -------------------------------------------- |
| **Art**        | Versionskontrollsystem    | Hosting-Plattform                     | Hosting-Plattform                            |
| **Betrieb**    | Lokal, dezentral          | Microsoft (Cloud)                     | GitLab Inc. (Cloud & Self-hosted)            |
| **Fokus**      | Versionierung & Branching | Kollaboration, Open Source, Community | Kollaboration, DevOps, Self-Hosting          |
| **CI/CD**      | Nicht enthalten           | GitHub Actions                        | Integriert (sehr stark)                      |
| **Zielgruppe** | Entwickler allgemein      | Vor allem Open-Source & Unternehmen   | Unternehmen mit Fokus auf DevOps & Kontrolle |

Git = das Werkzeug zum Versionsmanagement.
GitHub = Online-Service, um Git-Repos mit Community-Features zu hosten.
GitLab = Alternative zu GitHub, oft im Unternehmenskontext genutzt, mit starkem Fokus auf DevOps und Self-Hosting.


Übersicht über das Grund-Prinzip:

![alt text](image.png)
Quelle: https://developer.ibm.com/tutorials/d-learn-workings-git/

Im Rahmen dieses Kurses spielen wir anhand von Modellanpassungen an einer INTERLIS Modelldatei die Haupt-Anwendungsfälle mittels Visual Studio Code durch.

## Visual Studio Code

Visual Studio Code (VS Code / VSC) ist ein kostenloser, plattformunabhängiger Code-Editor von Microsoft. Er unterstützt viele Programmiersprachen direkt oder über Erweiterungen und bietet Funktionen wie Syntax-Highlighting, IntelliSense (automatische Code-Vervollständigung), Debugging und eine enge Integration mit Git und GitHub.

Dank seiner großen Auswahl an Erweiterungen und Themes lässt sich VS Code individuell anpassen und eignet sich sowohl für kleine Projekte als auch für professionelle Softwareentwicklung.

Im Rahmen dieses Kurses betrachten wir die Erweiterungen
* INTERLIS 2 (https://marketplace.visualstudio.com/items?itemName=geowerkstatt.InterlisLanguageSupport)
* sowie das in VSC integrierte Werkzeug "Source control"


## Beispiel-Anwendungsschritte

### 1. Ein Repository klonen

Zweck: Eine lokale Ablage des Remote-Repositories anlegen

Vorgehen:

1. Öffne VSC ohne die Angabe einer Datei oder eines Verzeichnisses und öffne Source Control
2. Du hast nun die Möglichkeit, ein Repsoitory zu klonen: ![alt text](image-1.png)
3. Trage als URL https://github.com/agiktsh/beispiel_repository.git ein
4. Setze ein lokales Verzeichnis in welches die Dateien des remote Repositories kopiert werden sollen (Repsoitory Destination)

Hinweis:
Das lokal angelegte Verzeichnis ist ein gewöhnliches Verzeichnis und umfasst lediglich noch ein (versteckter) .git Ordner. Er enthält alle Informationen, die Git benötigt, um die Versionsverwaltung zu ermöglichen.

### 2. Lokales Repository mit VSC öffnen / Workspace Datei anlegen

Zweck: Zugriff auf lokales Repository und Projektdatei erstellen

Vorgehen:

1. Öffne VSC und dann das Verzeichnis mit Deinem lokalen Repository
2. Prüfe unter dem Source Control Widget, dass VSC das Verzeichnis als versionskontrolliertes Verzeichnis erkennt
3. Speichere dieses Projekt als neuer Workspace über das Kontextmenu 'Datei'

### 3. Eine .gitignore-Datei anlegen

Zweck: Wir lernen, wie spezifische Dateien von der Versionskontrolle ausgeschlossen werden können

Vorgehen:

1. Wechsle ins Widget Source Control
2. Die vorher angelegte Workspace-Datei (```.code-workspace```) wird als veränderte Datei angezeigt (U: Untracked)
3. Da wird diese selbst nicht in die Code-Verwaltung aufnehmen wollen, soll sie ignriert werden. Selektiere sie dazu und wähle über die rechte Maustaste ```'Add to .gitignore'```
4. Die Datei verschwindet nun aus der Liste der veränderten Dateien

### 4. Neuer Ordner und Dateien anlegen

Zweck: Neue Elemente in die Code-Verwaltung aufnehmen

Vorgehen:

1. Lege über den Explorer einen neuen Ordner namens ```config``` an
2. Lege anschliessend innerhalb dieses Ordners eine neue Datei mit dem Namen ```valid-<NAME>.config``` an (wobei <NAME> Deinem Vornamen entspricht)
3. Kontrolle in 'Source control' die durch Git festgestellten Änderungen im lokalen Repo

### 5. Änderungen committen

Zweck: Die bis anhin erstellten Änderungen festschreiben

Vorgehen:

1. Wechsle in 'Source control' 
2. Trage als Commit Message 'initiale Anpassungen vornehmen' oder etwas Ähnliches ein
3. Schreibe diese Änderungen nun mittels Commit im lokalen Repository fest

Hinweis:
Für Commit Messages wird typischerweise der Imperativ-Stil verwendet und es wird beschrieben, was gemacht wurde und nicht wie oder warum es gemacht wurde.
✅ Add feature X
❌ Added feature X
❌ Adding feature X
Die dabei eingesetzte Sprache soll sich an der Repository-Sprache orientieren. 

### 6. Änderungen pushen

Zweck: Die Änderungen im lokalen Repository ins remote Repository schreiben

Vorgehen:

1. Führe nun die Funktion 'Publish Branch' aus
2. Die Eingabe einer Message ist optional (aber guter Stil)
3. Kontrolle nun über https://github.com/agiktsh/beispiel_repository was nun genau am remote Repository passiert ist

Hinweis:
Wir haben nun alle gemeinsam am sogenannten 'Main'-Branch individuelle Änderungen gemacht. Der Main-Branch ist der Hauptentwicklungsast und umfasst typischerweise den produktiven, stabilen Stand des Codes dar.

### 7. Eigenen Branch erstellen

Zweck: Die nun folgenden Änderungen an der ILI-Datei nehmen wir in getrennten Entwicklungsästen vor. Getrennte Branches unterstützen eine sichere Weiterentwicklung und kontrollierte Überführung in die Hauptentwicklung. Wir schaffen uns damit isolierte Arbeitsbereiche pro Vorhaben (zB. Variante, Fix, Experiment, etc.). 

Vorgehen:

1. In der Fusszeile von VSC wird ganz links der aktive Branch angezeigt. Der ist aktuell wohl auf ```main``` gesetzt. Klicke auf diese Schaltfläche und
2. wähle anschliessend aus der Befehlszeile die Option ```+ Create new branch...``` und
3. gebe den Namen ```Entw. <NAME>``` ein (wobei <NAME> Deinem Vornamen entspricht)

Hinweis:
Branches können sowohl im remote Repository wie auch im lokalen Repository eröffnet werden. Das Endresultat ist dasselbe. Kriterium für die eine oder andere Variante ist, ob die Entwicklungen von mehreren oder nur einer Personen erfolgen soll.

### 8. Modellanpassungen auf isoliertem Branch integrieren

Zweck: Änderungen an einer Modelldatei integrieren, prüfen und auf den Branch pushen

Vorgehen:
(Die folgenden Änderungen führen wir individuell und unabhängig voneinander aus)

0. Kontrolliere, dass Du die nun folgenden Änderungen auf dem richtigen Branch ausführst
1. Öffne die Datei SH_Pflegeplanung_Fliessgewaesser_V2_0 in VSC
2. Nehme die Anpassungen in der Modelldefinition gemäss Deinem Arbeitsauftrag vor
3a. Tipp: Setze die Formatierung der INTERLIS-Modelldatei über die rechte Maustaste 'Format Document...' neu
3b. Tipp: Platziere den Cursor in Zeile 178 auf ```Coord2``` und rufe über die rechte Maustaste 'Peek>Peek Definition' auf. VSC zeigt Dir nun die exakte Typendefinition an.
3c. Tipp: Platziere den Cursor in Zeile 66 auf ```Units``` und rufe über die rechte Maustaste 'Go To Definition' auf. VSC öffnet Dir nun das referenzierte Modell.
4. Öffne nun das Terminal mit welchem Programmaufrufe oder andere Systembefehle gemacht werden können
5. Kompiliere die Datei neu über ili2c und das folgende Statement im Terminal ```java -jar "C:\Program Files\INTERLIS\ili2c\ili2c.jar" .\SH_Pflegeplanung_Fliessgewaesser_V2_0.ili ``` (der Pfad zu ili2c.jar muss allenfalls angepasst werden)
6. Wenn die Kompilierung mit ```Info: ...compiler run done ...``` endet, dann ist die angepasste ILI-Datei valid.
7. Über CTRL+SHIFT+P und die Option 'INTERLIS 2: Generate markdown documentation' kannst Du nun eine Markdown-Definition einer tabellarischen Modellbeschreibung aufrufen
8. Über CTRL+SHIFT+P und die Option 'INTERLIS 2: Show INTERLIS Diagram view' kannst Du nun eine UML-Anzeige Deiner Modellbeschreibung anzeigen
9. Committe die Änderung nun mit einer passenden Beschreibung
10. Pushe die Änderung nun auf das remote Repository

### 9. PullRequest erstellen

Zweck: Ein PullRequest stellt einen Zwischenschritt dar, welcher es ermöglicht, dass die Änderung durch weitere Personen kontrolliert werden, bevor sie in den Haupt-Entwicklungsast integriert werden.

Vorgehen:

1. Zur Eröffnung des PR's wechselst Du wieder nach https://github.com/agiktsh/beispiel_repository
2. Wähle Deinen Branch > anschliessend wird Dir angezeigt, welche Änderungen vorliegen und Du kannst den PullRequest eröffnen
3. Gebe einen Beschreibung an. Auch hier gilt: Imperativ-Stil, kurze Beschreibung worum es geht, allenfalls Issue-Nummer referenzieren (#111)
4. Lade anschliessend Personen aus dem Team als Approver Deines PullRequests ein.


### 10. PullRequest reviewen und freigeben

Zweck: Du wechselst jetzt den Hut und prüfst Änderungen (in Form von PullRequests) von Team-Kolleg:innen und machst dazu wenn nötig Bemerkungen.

Vorgehen:

1. Spreche Dich mit den Kolleg:innen ab, wer welchen PullRequest reviewed
2. Schaue Dir anschliessend die verschiedenen Commits (Änderungen) des PRs an und nutze die Möglichkeit, Kommentare anzufügen
3. Du kannst den PR nun genehmigen (approve) oder begründet abweisen (decline)

Hinweis:
CodeReviews-Kommentare werden häufig mit einem Präfix versehen, welcher den Hinweis grob kategorisiert:

* NIT: („Nitpick“) -> Kleinigkeit, keine Pflichtänderung. (Beispiel: NIT: Variable name could be shorter.)

* SUG: („Suggestion“) -> Vorschlag, den man übernehmen kann, aber nicht muss. (Beispiel: SUG: Consider using a switch here for clarity.)

* PP: („Personal Preference“) -> Persönliche Vorliebe des Reviewers, kein Muss. (Beispiel: PP: I’d write this function inline, but that’s up to you.)

* NB: („Nota Bene“ / „Beachte“) -> Hinweis auf etwas Wichtiges, das man im Kopf behalten sollte. (Beispiel: NB: This library is deprecated in newer versions.)

* BLOCK: oder MUST: -> Kritischer Punkt – sollte vor dem Merge geändert werden. (Beispiel: BLOCK: This query will fail on null values.)


### 11. PullRequest in den Main-Branch mergen

Zweck: Hat ein PullRequest den Review überstanden, können die Änderungen aus dem jeweiligen Branch in den Hauptentwicklungsast (oder auch einen beliebig anderen Ast) übernommen werden. Das stellt den Abschluss der entsprechenden Modifikation dar.

Vorgehen:

1. Sofern keine sog. Merge-Konflikte bestehen, erscheint auf der Seite des PullRequests nun die Option, den PullRequest zu mergen und zu schliessen.


### 12. GitHub Actions für automatische Kompilierung integrieren





## Begriffe

| Begriff        | Bedeutung                 | 
| -------------- | ------------------------- | 
| Klonen        |     | 
| Branch        |     | 
| Commit        |     | 
| Merge        |     | 
| PullRequest        |     | 

## Erweiterte Aspekte

### Konfliktmanagement

### GitHub Actions


### Arbeitsaufträge

Die folgenden Modifikationen können in der Beispiel-Modelldatei vorgenommen werden:

| Auftrag        | Beschreibung                 | 
| -------------- | ------------------------- | 
| 1        |  ```Arbeitsart_Code.Beschreibung: TEXT*250```   | 
| 2        |  ```Pflegeziel_Code.Inaktiv : INTERLIS.BOOLEAN;```   |
| 3        |  ```FaunaVorgehen_Code: UNIQUE Aktivitaet, Inaktiv;```   |
| 4        |  ```BauwerkMoebilierung.Kontrollmassnahme: BAG {0..9} OF ...```   |
| 5        |  ```BauwerkMoebilierungBauwerkgsmoeblierungskontrolleAssoc: BauwerkMoebilierung -<> {1} BauwerkMoebilierung;```   |