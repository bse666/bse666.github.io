---

title: "Git für alle(s)"
layout: "post"
date: "2012-10-05"
tags: ["linux","debian","git","vcs","ubuntu"]
published: "true"

---

Git kann gut und gerne viele Daten verwalten.
Der Vorteil von Git gegenüber "normalen" VCS (Version Control System) liegt klar auf der Hand.

<!--more-->

```
"Git ist eine freie Software zur verteilten Versionsverwaltung von Dateien, die ursprünglich für die Quellcode-Verwaltung des Kernels Linux entwickelt wurde."
- Wikipedia -
```

Die Bedienung ist um einiges einfacher.
Komplexe Merge-Strukturen werden meist automatisch abgearbeitet.
Verwaltung von vielen Binärdateien
Schnelles Austeilen der Repositories durch "packen"
 Als Beispiel nehmen wir hier ein Linux System auf dem Git installiert wird.
Debian hat sich mittlerweile bei mir sehr fein eingebürgert auf Serversystemen.
```
$ apt-get install git
```
Das war es auch schon. :)
Bevor wir starten sollten erstmal die Userdaten gesetzt werden.
```
$ git config --global user.name "Name Hier Hin"
$ git config --global user.email  Name@meinedomain.firma.com
```
Es geht nun weiter mit dem Erstellen eines Repository.
```
$ mkdir project.git
$ cd project.git
$ git init
```
Mit Hilfe von "git init" kann das aktuelle Verzeichnis schnell zu einem Git Repository umgewandelt werden. Es wird nun ein ".git" Ordner erstellt in dem Git seine Datenbank pflegt.
Nun werden wir neue Dateien hinzufügen. Diese können natürlich auch hineinkopiert werden.
```
$ echo "test" > NewFile
$ git add NewFile
```
Mit "git add " können Dateien oder Ordnerstrukturen zur Versionierung hinzugefügt werden. Wenn man nun das ganze "committed", also die Änderungen abspeichern will macht man dies wie folgt:
```
$ git commit -a
```
Nun öffnet sich der favorisierte Consolen Editor in dem man dann einen Commit-Grund angeben kann wie z.B. "Erster Commit. Repo mit Daten gefüllt.". Dann speichert man dies ab und Git errechnet die Hash-Werte der Dateien und pflegt all dies unter seinem .git Verzeichnis.
Nun kann man auch gerne mit Branches rumspielen.
```
$ git branch #listet alle Branches
$ git branch neueBranch # erstellt eine neue Branch mit dem Namen: "neueBranch"
```
Branches sind gut für die Erarbeitung neuer Features.

```
Die wichtigste Regel bei der Nutzung von git:
Commit, Commit, Commit.
Es kann nie genug commit'ted werden.
```
