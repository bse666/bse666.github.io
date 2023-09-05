---

title: "VIM Tutorial 01"
description: "VIM Basics"
date:  2023-09-04
published: true
tags: [vim,linux,coding,tutorial]

---

Lasst uns doch mal ein bisschen über [VIM](https://www.vim.org) reden. Ich möchte hier einmal aufzeigen das VIM mehr als nur ein Texteditor ist und es viele versteckte Funktionen gibt die nicht jeder auf die, vielleicht sogar ersten Jahre, erkennt.

<!--more-->

Ein Anreiz dafür hat mir die Seite von [valuableDEV___](https://thevaluable.dev/vim-advanced/) gegeben. Viele der dort stehenden Dingen waren mir nicht bekannt und eröffnen in der Entwicklung und täglichen Arbeit so viel mehr Möglichkeiten.

Aber fangen wir hier doch erstmal mit den Basics an.


#### VI-Modi

ViM enthält drei Modi in der sich der Editor befinden kann. Es gibt den Bewegungsmodus und den Edit/Insert Modus. Der dritte Modus ist der Command Modus, in dem manuell Kommandos im Editor eingetippt werden können.
Im Insert Modus kann Text verändert werden, im Bewegungsmodus kann sich im Text bewegt werden.

#### Bewegung

Willst du VIM wirklich lernen benötigst du Tastenkenntnis. 
In VIM steuert man den Curser mit Bewegungsangaben und zwar in Schema "1 Zeichen nach Rechts", "Eine Zeile nach unten", "Vier Zeilen tiefer", "Ans Ende der Zeile springen".
Da das alles garnicht schwer ist und auch das Lernen dieser Kombinationen ist mit einigen wenigen Handgriffen und Englischkenntnissen schnell durchschaut.

Damit aber die ganze Thematik besser in das Fingergedächtnis über gehen kann sollte der erste Schritt sein die Pfeiltasten komplett zu deaktivieren.
Dies geschieht in der Datei ~/.vim/vim.conf mittels der Zeilen

``` bash
noremap <Up> <Nop>
noremap <Down> <Nop>
noremap <Left> <Nop>
noremap <Right> <Nop>
```

Ab diesem Punkt muss man nun die vom Gott der Terminals ( also des VIM Gottes ) erdachte Bewegungsmethodik nutzen um sich in der geöffneten Datei umherzubewegen. Dies beinhaltet folgendes Schemata, das ich mir aus einem Help-File des BSD gemopst habe:

```
             ^
             k              Hint:  The h key is at the left and moves left.
       < h       l >               The l key is at the right and moves right.
             j                     The j key looks like a down arrow.
             v
```

Nun könnte man sagen man stellt diese ganze Geschichte auch noch um und möchte sich eventuell mit jklö bewegen als Nutzer eines Deutschen Layout's, aber wer möchte schon sicher gehen das sich auf allen Systemen die man nutzt auch die Deutsche Sprache in den Einstellungen wiederfindet.

#### Editieren

Auffällig ist wenn man sich dann mal zurecht findet auch das man irgenwie nichts so richtig eintippen kann wie in ein Windows Notepad oder ein Linux Gnome-Edit. Das liegt in diesem Fall an den Modi die in VIM verwendet werden.
In den guten Alten Tagen wo man an Terminal's gearbeitet hat, und nicht in Terminals, ja ich meine die Kisten die nur ein Monitor und Tastatur waren und an eine raumgroße Unix Kiste im Keller einer Uni angeschlossen waren, an diesen Terminals war die Refresh-Rate nicht die beste und auch die Geschwindigkeit nicht die beste, da alle später mit DOOM die Server ausgelastet hatten. Hier wurde sich etwas ausgedacht.

Dadurch das man den Bewegungsmodus, ja ich glaub das passt besser, nutzt um sich im Text zu bewegen und nur bei Änderungen dem Editor Befehle gibt um den Text anzupassen, kann man sich auch auf nicht performanten Rechnern oder Verbindungen vernünftig im Text bewegen und muss nicht zwei Sekunden warten bis der Cursor hinterhinkt.

Hier einmal ein paar Beispiele, all diese Dinge löst man aus dem Bewegungsmodus aus.

###### Löschen

	'dd' löscht die unter dem Cursor liegende Zeile.
	'C' löscht die Zeile von Beginn des Cursors und springt in den Insert Modus

###### Hinzufügen

Hinzufügen von Text geht mit verschiedenen Methoden.

	'a' lässt den Cursor hinter das aktuelle Zeichen springen.
	'A' springt an das Ende der Zeile in den Insert-Modus.
	'I' springt an den Anfange der Zeile in den Insert-Modus.
	'i' ist der wahrscheinlich häufigst genutzer Shortcut und springt direkt in die Eingabe unter dem Cursor.

###### Ersetzen

	'r' ersetzt das unter dem Cursor stehende Zeichen mit einem eingetippten.
	'R' springt in den Ersetzungsmodus wo jedes getippte Zeichen das darunterliegende ersetzt.

#### Speichern

	':w' Speichert eine Datei, fragt nach dem Namen wenn keine Datei geöffnet war.

#### Verlassen

Das Best gehühteste Geheimnis und auch das wahrscheinlich größte Meme unter allen Linux-nutzenden werde ich hier nicht niederschreiben.
Guckt euch die Help Datei an. ( RTFM )

#### Schlußwort

Was mir am meisten geholfen hat in der anfänglichen Lernkurve mit VIM ist ein Stück Software, das schon mitgeliefert ist, oder ist es nur ein Script (?), jedoch wäre dies was ich jedem ans Herz legen würde wenn ViM gelernt werden will.

ViMTUTOR - oder auch vimtutor ist ein Befehl der bei den meisten "Standard"-Installationen eines VIMs mitkommt.

Hier können Sachen ausprobiert, getestet und sogar wieder neu angefangen werden, ohne das man sich selbst seine Dateien zerbrezelt. Man wird hier an der Hand genommen und in die einzelnen Funktionen des EEditors eingeführt. \\
Dies ist sogar lokalisiert auf die jeweilige OS Sprache verfügbar ( zumindest so bei deutschem Ubuntu ).

Dies sollte sich jeder anschauen der hier mal reinschnuppern will, und das geht auch in einer Virtualbox mit einem Standard Ubuntu Image als Boot-ROM, so macht man nix kaputt und kann testen bis die Virtuelle Maschine aufgibt. Viel Spass dabei.

Und ansonsten muss man einfach mal eine Woche lang für alle Arbeiten mit Text ViM nutzen, dann kommt die Routine schon von allein. Wer nach einer Woche VIM sagt das ist nichts für mich kann natürlich gern weiter den Editor nutzen, aber ich vermute das dies nicht viele sind.
