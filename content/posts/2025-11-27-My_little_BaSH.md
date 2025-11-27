---

layout: post
title: My little BaSH
date: 2025-11-27
tags: ["blog","linux","script"]
published: true

---

# My little BaSH

BaSH - Die Bourne-Again Shell ist eine freie Unix Shell, die zumeist unter aktuellen Linux Distributionen Ihren Einsatz findet.
Die Bash-Shell ist für viele Linux- und Unix-Nutzer das tägliche Arbeitswerkzeug. Doch während die meisten die grundlegenden Befehle kennen, schlummern in der Bash zahlreiche mächtige Features, die den Arbeitsalltag erheblich erleichtern können.

## Der Reverse-Search: Strg+R

Einer der produktivitätssteigerndsten Shortcuts überhaupt ist die Rückwärtssuche in der Bash-History mit `Strg+R`. Statt mühsam durch die History zu scrollen oder lange Befehle neu zu tippen, kannst du einfach:

```bash
# Drücke Strg+R und tippe dann Teile des gesuchten Befehls
(reverse-i-search)`docker': docker ps -a
```

Die Bash durchsucht deine Command-History und zeigt die passendsten Treffer an. Mit erneutem `Strg+R` springst du zum nächsten Match. Mit `Enter` führst du den gefundenen Befehl aus, mit `Strg+G` oder `Esc` brichst du die Suche ab.

## Source: Skripte ohne Execution-Flag ausführen

Der `.` (Punkt) bzw. `source`-Befehl ist ein mächtiges Werkzeug, das oft übersehen wird:

```bash
# Beide Varianten sind gleichwertig
. ./mein-script.sh
source ./mein-script.sh
```

Der entscheidende Unterschied zu `./mein-script.sh`: Das Skript wird in der **aktuellen Shell** ausgeführt, nicht in einer Subshell. Das bedeutet:

- Das Skript benötigt keine Ausführungsrechte (`chmod +x`)
- Umgebungsvariablen bleiben nach der Ausführung erhalten
- Verzeichniswechsel mit `cd` wirken sich auf deine aktuelle Shell aus

Praktisches Beispiel:

```bash
# projektenv.sh
export PROJECT_PATH="/home/user/mein-projekt"
export API_KEY="geheim123"
cd "$PROJECT_PATH"

# Ausführung
. ./projektenv.sh
# Du bist jetzt im Projektverzeichnis, Variablen sind gesetzt!
```

## Brace Expansion: Mehrere Dateien auf einmal erstellen

Die Bash kann automatisch Zeichenketten expandieren:

```bash
# Erstelle mehrere Dateien gleichzeitig
touch datei{1..5}.txt
# Erzeugt: datei1.txt datei2.txt datei3.txt datei4.txt datei5.txt

# Auch mit Buchstaben
mkdir ordner{A..D}
# Erzeugt: ordnerA ordnerB ordnerC ordnerD

# Kombinationen sind möglich
touch {test,prod}_{config,data}.json
# Erzeugt: test_config.json test_data.json prod_config.json prod_data.json
```

## Parameter-Expansion: String-Manipulation ohne externe Tools

Die Bash bietet eingebaute String-Operationen, die oft sed oder awk überflüssig machen:

```bash
# String-Variable
datei="dokument.pdf.backup"

# Dateiendung entfernen (von hinten, kürzester Match)
echo ${datei%.backup}  # dokument.pdf

# Dateiendungen entfernen (von hinten, längster Match)
echo ${datei%%.*}  # dokument

# Pfad entfernen (von vorne, längster Match)
pfad="/home/user/dokument.txt"
echo ${pfad##*/}  # dokument.txt

# String ersetzen
text="Hallo Welt Welt"
echo ${text/Welt/Bash}  # Hallo Bash Welt (erste Vorkommen)
echo ${text//Welt/Bash}  # Hallo Bash Bash (alle Vorkommen)

# Default-Werte setzen
echo ${VARIABLE:-"Standard"}  # Wenn VARIABLE leer, nutze "Standard"
```

## Command Substitution: Befehlsausgabe elegant nutzen

Moderne Syntax mit `$()` statt Backticks:

```bash
# Alt (funktioniert, aber schwer lesbar bei Verschachtelung)
datum=`date +%Y-%m-%d`

# Modern und besser
datum=$(date +%Y-%m-%d)
backup_name="backup_${datum}.tar.gz"

# Verschachtelung ist einfach lesbar
benutzer=$(grep "$(whoami)" /etc/passwd | cut -d: -f5)
```

## Strg+X, Strg+E: Editor für lange Befehle

Bei komplexen One-Linern wird es schnell unübersichtlich. Mit `Strg+X` gefolgt von `Strg+E` öffnest du deinen Standard-Editor ($EDITOR), um den aktuellen Befehl zu bearbeiten. Nach dem Speichern und Schließen wird der Befehl ausgeführt.

## History-Expansion: Schnellzugriff auf vorherige Befehle

```bash
# Letzter Befehl
!!

# Vorletzter Befehl
!-2

# Letztes Argument des vorherigen Befehls
!$
# Beispiel:
mkdir /var/log/meine-app
cd !$  # wechselt nach /var/log/meine-app

# Alle Argumente des vorherigen Befehls
!*

# Befehl der mit 'docker' beginnt
!docker
```

## Process Substitution: Befehle als Dateien behandeln

```bash
# Vergleiche Ausgaben zweier Befehle
diff <(ls ordner1) <(ls ordner2)

# Mehrere Logs gleichzeitig durchsuchen
grep "ERROR" <(cat app1.log) <(cat app2.log)
```

Die `<()` Syntax erstellt temporäre File-Descriptors, die wie normale Dateien behandelt werden können.

## Arrays: Mehr als nur einfache Variablen

```bash
# Array definieren
dateien=("config.yaml" "data.json" "script.sh")

# Zugriff
echo ${dateien[0]}  # config.yaml
echo ${dateien[@]}  # Alle Elemente
echo ${#dateien[@]}  # Anzahl der Elemente

# Iteration
for datei in "${dateien[@]}"; do
    echo "Verarbeite: $datei"
done

# Array erweitern
dateien+=("neue_datei.txt")
```

## Globbing mit erweiterten Optionen

```bash
# Aktiviere erweiterte Globbing-Optionen
shopt -s extglob

# Alle Dateien außer .txt
ls !(*.txt)

# Nur .jpg oder .png Dateien
ls *.@(jpg|png)

# Mindestens eine Ziffer
ls *[[:digit:]]*

# Recursive Globbing (ab Bash 4.0)
shopt -s globstar
ls **/*.log  # Findet alle .log Dateien in allen Unterverzeichnissen
```

## Zusammenfassung

Die Bash bietet weit mehr als nur die Ausführung einfacher Befehle. Mit diesen Features kann man:

- **Schneller arbeiten** durch intelligente History-Navigation
- **Komplexe Operationen** ohne externe Tools durchführen
- **Skripte robuster gestalten** durch eingebaute String-Manipulation
- **Wiederholende Aufgaben** automatisieren mit Brace Expansion

Viel Spass beim durchprobieren.

