---

title: "New Blog in da House 2"
date:  2023-05-12
include_toc: true
tags: [blog,hugo,themes,css,github,workflow]
published: true

---

Der neue Blog, mit vielen kleinen aber feinen CSS und HTML Zutaten. Und all das mit Versionierungstricks bis hin zur Auslieferung per Github-Agenten.
<!--more-->

Was ist ein schöneres Event als einen Blog mit neuem Content zu versorgen?

Genau!

Den Blog komplett neu zu bauen. Aus diesem Grund, und wegen unten beschriebenen, kommt hier ein neues Grundgerüst, das nun hoffentlich noch ein paar Jahre halten wird. 

##### ToDo Liste

- [x] [Hugo als Unterbau]( {{< ref "#hugo-als-unterbau" >}} )
- [x] [Dark/Light Theme]( {{< ref "#die-dunkle-und-helle-seite" >}} )
- [x] [Codefelder auch mit solarized Farben versehen]( {{< ref "#farbiger-code" >}} )
- [x] [Hugo Startseite attraktiv machen]( {{< ref "#startseite-attraktiv-machen" >}} )
- [x] [Hugo Responsive Design]( {{< ref "#hugo-responsiveness" >}} )
- [ ] List of Content (Posts Archive automatisch)
- [x] [Workflow in Github für Seitenbau]( {{< ref "#workflow-in-github" >}} )
- [x] [Shortcodes. Aber eventuell auch nicht.]( {{< ref "#shortcodes" >}} )

#### Hugo als Unterbau

Für den neuen Blog wollte ich ein System einsetzen das losgelöst von einem Rechner funktioniert. Ich möchte nicht mehr die Abhängigkeit Laptop oder Rechner haben um neuen Content in den Blog zu hacken.

Dies ist am Ende dann mit vielen verschiedenen Systemen möglich.
Zur Auswahl standen solche Dinge wie [Ghost](https://ghost.org/) oder weiter die Option [Jekyll](https://jekyllrb.com/) zu nutzen.
Da Jekyll aber generell sehr schwerfällig ist und der Ansatz von [Hugo](https://gohugo.io/) mir sehr zu sagt (Eine Binary zum Kompilieren und keine komplette Ruby Umgebung notwendig), habe ich mal einen Blogbau damit in Angriff genommen.

Hugo, *the world's fastest framework for building websites* ist natürlich schon einmal das korrekte Statement in meine Richtung. Ich wollte einen Static Site generator, der klein ist, auf möglichst vielen Plattformen läuft falls man mal kein Internet zur Verfügung hat, und den ich natürlich durch den Einsatz von "Nur Dateien" auch möglichst schön in [Git](https://git-scm.com) zu verpacken und zu versionieren sind.


#### Die Dunkle und Helle Seite

Licht und Schatten.
Mit diesen beiden Wörtern ist eigentlich schon alles gesagt.
Der Blog soll ohne viel KlimBim auskommen und wie früher zu den guten alten 
Zeiten nur das nötigste übertragen.

Nach ein paar Tests mit zwei CSS Dateien wurde ich auf das Snippet von 
[noestreich](https://github.com/noestreich) aufmerksam.
[Das Snippet](https://gist.github.com/noestreich) beschreibt die Wahl von z.B.
iOS, die dann über die "Systemsteuerung" funktioniert.

[Solarized-CSS](https://thomasf.github.io/solarized-css/)

Daraufhin kann die Styles Datei gebaut werden.
Da wir hier eine helle und eine Dunkle Seite haben und es viel zu überflüssig ist zwei Dateien einzubauen können wir auch die Dateien mittels diff vergleichen und die unterschiede mit in eine Styles Datei bauen.
Dies sieht dann so aus:

``` css
@media (prefers-color-scheme: dark) {
	// dark content here
	}	
```

In diesem Tag befinden sich dann die Unterschiede zum light Theme. Damit kommt man schon einmal ein gutes Stück weiter.

#### Farbiger Code

Was natürlich immer mal wieder auffiel war das die Codefelder noch nach den Hugo Standards Coloriert waren. Dies springt natürlich einem Designsensitivem Menschen sofort ins Auge und sollte tunlichst abgestellt werden.
Hier musste also eine Umcolorierung her, die dann natürlich dem Solarized Farbschema folgte, jedoch indirekt zu dem ausgewähltem.

Da hier immer die Hugo eigene Mechanik griff musste zu einem Trick gewechselt werden.
In der [Dokumentation zum Syntax Highlighting](https://gohugo.io/content-management/syntax-highlighting/#generate-syntax-highlighter-css) wird beschrieben das mit der folgenden Option in der config.toml das reguläre AUTO-CSS Feature für die Codeblöcke ausgeschaltet werden kann:

``` toml
markup.highlight.noClasses = false
```

Um die nötigen CSS Codes herauszufischen ist nun folgendes nötig:

``` bash
hugo gen chromastyles --style=solarized-light > solarized-light-syntax.css
hugo gen chromastyles --style=solarized-dark > solarized-dark-syntax.css
```

Die beiden herausfallenden Styles können dann ebenso in die vorhandene CSS Datei mit eingepflegt werden, da diese nur auf die Code-Boxen reagieren.

#### Startseite attraktiv machen

Ein paar kosmetische Eingriffe in das triste Dasein der umrandeten Fenster konnte mittels der folgenden Zeile gelöst werden.

``` css
border-radius: 18px 50px 26px;
```


#### Hugo Responsiveness

Am Ende kamen die Überlegungen auf die Seite natürlich auf Mobilgeräten auch vernünftig anschaubar zu gestalten.
Dies führte schnell zu der Seite [HTML Responsive Web Design](https://www.w3schools.com/html/html_responsive.asp).

Im Prinzip benötigt man für den ersten Schritt nur den folgenden Meta Tag im Header, damit die Browser den Content anpassen können:

``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Ich werde die Anzeige der Seite noch finetunen damit auch eine angenehme User Experience auf allen Geräten vorhanden ist, jedoch funktionniert die Seite so erstmal.

#### Workflow in Github

Der Workflow in Github kann direkt in Github-Pages konfiguriert werden, oder aber man benutzt die auf der [Hugo Seite](https://gohugo.io/hosting-and-deployment/hosting-on-github/) angegebene hugo.yml die dann auch die neueste Version von Hugo nutzt.

Hier ist es also nur ein Klick, ein Commit und nach einem Push wird die seite vernünftig für github Pages gebaut.

#### Shortcodes

Shortcodes können in Hugo dafür verwendet werden auf verschiedene Dinge zu verweisen.
Hier kommen ein paar feine Beispiele die schon in Hugo ohne extra Plugins vorhanden sind.

- figure

  Hiermit kann man Bilder in Schön einbinden, mit Beschreibung und eventuell einer Vergabe einer bestimmten Klasse pro figure Tag.

- gist
	
	GitHub gists können hiermit einfach integriert werden. Dies kann bestimmt öfters vorkommen in Zukunft.

- instagram
	
	Wer möchte kann Instagram Posts einbinden unter der Vorraussetzung das hier auch ein Access_Token mit verdrahtet wird.

- param

  Hiermit können verschiedenste Parameter von der Seitenstruktur mit in den Fliesstext mit eingefügt werden.

- tweet

  Tweets können hier sichtbar und in gewohnter Ansicht auf der Seite hinterlegt werden.

- Vimeo
	
	Einbinden von Vimeo Videos auf der eigenen Seite.

- YouTube
	
	YouTube Videos sind mittels dieser integrierten Shortcodes einzubinden.
