---

layout: post
title: "iPads befüllen in 2024"
published: true
date: 2024-03-29
tags: [linux,story]
categories: [linux,story]

---

Es begab sich eines Tages da musste ein VPN auf einem iPad konfiguriert werden. 

Die notwendige App für ein OpenVPN war schnell im App Store auf dem Gerät gefunden und installiert. 

<!--more-->

#### Am Anfang war eine Hürde

Darauf mussten die Zertifikate und die openVPN Definitionsdatei heruntergeladen und bereitgelegt werden. 

Alle Dateien nun auf dem iPad angekommen machte man sich auf um die Konfiguration der Verbindung vorzunehmen. Dies konnte aber nicht manuell in der App erfolgen, hier musste die Definitionsdatei importiert werden. 

Ein Import der Definition ging auch problemlos. Leider konnten aus dem Datei Explorer des iPads nur die Definitionsdatei an die App gesandt werden worauf natürlich die notwendigen Zertifikate fehlten. Ein Import der Zertifikate konnte jedoch nur mit dem iPad mittels Bordmitteln nicht durchgeführt werden. 

#### Anleitungen

In einer Anleitung des VPN Bereitstellers hieß es: „Probier es doch mit iTunes“.  Und dies wurde dann auch angegangen. Als noch Only Windows/Linux User schien dies logisch. Zumal in früheren Bekanntschaften mit "Noch-nicht-Over-the-Air-Updates-Apple-Geräten" dieser Weg üblich war. Nach dem durchprobieren des einen oder anderen USB-C Kabels funktionierte dann doch wirklich mal eins mit Datenkommunikation. 

Hurra! Ein iPad in Windows als Fotospeicher war sichtbar. Die Version 11 von iTunes funktionierte aber nicht mit dem iPad also wurde diese auch nochmal einem Update unterzogen. 

Danach. Leider aber auch keine Besserung. Keine Möglichkeit das iPad im iTunes anzusprechen und die notwendigen Dateien in den „Applikationsordner“ des OpenVPN Programmes zu integrieren. 

Eine rettende Idee kam dann doch noch. Es war doch wirklich so einfach. Warum war man nicht gleich darauf gekommen. Man sollte einfach ein mit Apfel Logo behaftetes Gerät kaufen und da geht alles von Haus aus. 

Ja, Nein! Natürlich nicht. Bevor man einen solchen, meist mit wert behafteten Schritt vollzieht erinnert man sich eventuell noch an eine bestimmte Sache die früher mal funktionierte. 

#### Der Erfolg

Das zweite verfügbare Betriebssystem war neben Windows auch noch diverse Linux‘e. Im besonderen wurde hier dann ein Ubuntu gebootet um an einen Nautilus Dateimanager zu kommen. Durch diverse fuse und gvfs Magie ist Nautilus dazu in der Lage auch die interessantesten Dinge zur Verfügung zu stellen, die an einen PC angeschlossen werden.

Nach dem Anschließen des Gerätes wurde dann auch nach einer kurzen Gedenkpause das erwartete Bild des verbundenen iPads sichtbar. Nicht nur ein Foto Ordner sondern auch die Ordner die von Apps zur Verfügung gestellt werden um per USB, oder MacOS, Daten auf das iPad zu schieben. 

Nach ein paar Hin und Her‘s mit der Reihenfolge der Dateien die hochgeladen wurden konnte dann aber sogar eine erfolgreiche Verbindung mit Zertifikaten über das iPad aufgebaut werden.

#### Das geht so nicht weiter

iTunes war mal "Das Tool" um auf Windows mit Apfel Geräten zu arbeiten. 
Aber leider wurde dies abgelöst durch verschiedenste Programme wie Apple Music. iTunes ist nicht mehr gewollt. Seien wir gespannt wie man in einer Windows Only Welt solche Probleme in Zukunft angeht. 

Das ist kein schöner Umgang für die noch nicht komplett im Apfel Ökosystem eingekauften Kunden, die eventuell nur ein iPad oder auch ein iPhone mit kleinen Dingen füttern wollen. Hier gern ein Pitch für Airdrop in Windows!, was hier allerdings auch nicht geholfen hätte, da die Applikation nur ovpn Dateien annimmt.

Zuletzt noch ein Hoch auf Linux und die fleißigen Arbeiter hinter den Kulissen die uns solch tolle Tools bescheren die auch mal einiges an Ärger in Kürze auflösen können.
