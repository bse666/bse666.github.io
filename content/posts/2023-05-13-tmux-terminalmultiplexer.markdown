---

title: "TMUX - TerminalMUltipleXer"
date: "2023-05-13"
tags: [linux,unix,osx,mac,ubuntu,console]
published: "true"

---

[TMUX](https://github.com/tmux/tmux/wiki), ein Terminal MUltipleXer.


``` bash
Terminal? 
Das Schwarz weiße ding?
Ist das überhaupt interessant?
```

<!--more-->
oh jaa. Terminals sind quasi so alt wie die Computer selbst (eigentlich was jünger). Früher waren Terminals einfache Anzeigegeräte für entfernt stehende und Riesige Rechenmaschinen. Mittlerweile dürfen sich auch alle Schwarz-Weiss-Eingabekonsolen auf Basis von Linux, BSDs oder anderen Betriebssystemen Terminals nennen.

Ein Terminal hat hier die Aufgabe Textausgabe vom Rechner auf den Bildschirm zu bringen. Mal ist dies etwas langweiliger, mal aber auch etwas bunter und mit transparenten Hintergründen.

Ein Terminal in Linux z.B. hat eigentlich in der normalen Form nur einen andemeldeten User und kann eine Bildschirmseite Text ausgeben.
Dieser Text kann dann vom Benutzer manipuliert und mit Befehlen versehen wieder in den Rechner eingegeben werden, allerdings alles immer noch auf Basis einer Kommandozeile.

Hier kommt `TMUX` ins Spiel. Mittels TMUX ist es möglich das bestehende "langweilige" Terminal in ein multigeplextes umzuwandeln.
Hier wird quasi ein Programm Bildschirmfüllend gestartet, das dann in der Lage ist verschiedene Fenster zu öffnen und auch mit Tabs verschiedenste Variationen an geöffneten Terminals zu erstellen.
Mit einer Maus kann ebenfalls Text kopiert und/oder eingefügt werden, oder die Größen der Panes verändert werden.

Hier nur ein paar Beispiele wo so etwas sinnvoll sein könnte:
- OS Updates auf vielen Linux Maschinen die gleichzeitig laufen sollen und überwacht werden müssen. Hier kann TMUX mit parallelen eingaben auf allen geöffneten Fenstern helfen.
- Oder Tabs für die sortierung von remote Sessions.
- Die Initialisierung von weiteren TMUX Sessions auf Remote Geräten. #Tmuxception


TMUX selbst ausprobieren kann man am Besten in Ubuntu mit dem Befehl
```bash
$ sudo apt install tmux
```

Sollte das Programm installiert sein und mit einem Befehl wie
```bash
$ tmux
```

ist dann ein schneller Einstig mit der Default-Tastenbelegung CTRL-b gewährleistet.
In Zukunft werde ich eventuell hier noch auf einige Dinge aus meiner `tmux.conf` hinweisen, diese kann aber auch auf github eingesehen werden.
