# Tag 1, Grundlagen und eine Übung mit Pixate

## Eine Faustregel

Problemlos animieren lässt sich alles, was sich in folgende Animationstypen gliedern lässt: Wachsen/Schrumpfen, Bewegen von A nach B, Rotieren, Einblenden/Ausblenden. Auch das Verzerren könnte man in diese Liste aufnehmen, aber hier gibt es schon Vorbehalte.

Problematisch ist alles, was eine Verwandlung beinhaltet. Z.B. Das überführen von Text in eine geometrische Form, von einem Film in ein Vektorbild etc. Alles was nach Trickfilm riecht, sollte sicherheitshalber mit dem Prädikat «technisch nicht machbar» versehen werden.

Animation am Bildschirm bedingt Interplation: wenn es Eigenschaften mit Zahlenwerten gibt, die manipulierbar sind, dann ist eine Animation grundsötzlich möglich.

## Terminologie

### Interpolation

Von Interpolation wird gesprochen, wenn die Zwischenschritte für den Übergang von einem Ausgangswert zu einem Zielwert vom Computer errechnet werden. Der Computer «interpoliert» von einem Wert zum anderen.
Die einfachste Art von Interpolation ist die Lineare: ein Wert wird in regelmässigen Schritten verändert, bis der Zielwert erreicht wird.

### Ease

Von ‘ease’ wird gesprochen, wenn eine Animation nicht mit gleichmässiger Geschwindigkeit («linear») verläuft, sondern wenn sich die Interpolation der animierten Werte über die Zeit kurvenförmig entwickelt.

* [Google Developer Web Fundamentals – The Basics of Easing](https://developers.google.com/web/fundamentals/design-and-ui/animations/the-basics-of-easing)
* [Easings.net](http://easings.net/de)

### Event

«Event» bedeutet im Zusammenhang mit User Interfaces ein Vorkommnis, das von einer Software registriert werden kann. Das kann ein Signal im Netzwerk sein, z.B. eine Verbindung, die Zustande kommt. Oder ein Zeitpunkt, der erreicht wird.
Ein Event kann auch eine Interaktion des Benutzers sein, z.B. ein Klick oder dass der Cursor sich in einen bestimmten Bereich bewegt.
Events können dazu dienen, einen Prozess in Gang zu setzen, also z.B. eine Animation auszulösen.

## Software, Tools

### Keynote

Wenn Interaktivität nicht notwendig ist, kann Keynote ein gutes Mittel zum visualisieren bewegter Inhalte sein. Es sollte aber nichts komplexes sein.

* [Prototyping Animation with Keynote](https://robots.thoughtbot.com/animating-with-keynote)
* [Material Design Video in Keynote](https://vimeo.com/100377108)

### Pixate

Am 4. Oktober 2016 hat Pixate mitgeteilt, dass die Software nicht weiter entwickelt wird. Der Download-Link wurde entfernt, die Video-Tutorials waren am 7. Oktober noch online.

* [Pixate](http://pixate.com)
* [Pixate Video Tutorials](http://www.pixate.com/education/video-tutorials/)

### Origami

Von Facebook entwickelte Prototyping Software. Unkonventionelles Interface, sieht aber interessant aus. Gratis.

#### Voraussetzungen

* Als Apple Developer registriert
* Installation von Quartz Composer

#### Links

* [Origami Download](http://facebook.github.io/origami/download/)
* [Origami Tutorial](http://facebook.github.io/origami/tutorials/)

## Software für Animation

### Axure

Axure ist eine Prototyping Software, die zwar nicht primär auf Animation zielt, aber einige Möglichkeiten dafür anbietet.

[axure.com](http://www.axure.com/)

### Framer.js

Interessanter Ansatz mit dreigeteiltem GUI. Bedingt JavaScript (bzw. CoffeeScript) Kenntnisse.

* [Framer.js](https://framerjs.com/)
* [Framer.js Youtube Channel](https://www.youtube.com/channel/UCW5gUZ7lKGrAbLOkHv2xfbw)

### Flinto

Flinto ist mit Sketch kompatibel.

* [Flinto](https://www.flinto.com/)
* [Sketch Together Youtubekanal](https://www.youtube.com/channel/UCZHkx_OyRXHb1D3XTqOidRw)

### Principle

Dürfte vom Funktionsumfang her ähnlich wie Flinto sein. Es scheint auch hier Schnittstellen zu Sketch zu geben.

* [Principle](http://principleformac.com/)
* [Sketch Together Youtubekanal](https://www.youtube.com/channel/UCZHkx_OyRXHb1D3XTqOidRw)

### Adobe XD (Experience Design)

Adobe plant wieder einmal etwas grösserers, es gibt aber erst eine [Testversion](https://www.adobe.com/products/experience-design.html).

### Adobe After Effects

Was Photoshop für Bilder ist, ist After Effects für Film. Das ist das professionellste Tool für Animation, aber im Zusammenhang mit UI Design ist das mit Kanonen auf Spatzen geschossen.

## Übung mit Pixate

Einfache «Automaten» herstellen. Ziel: schnelle Produktion simpler Interfaces. 2. Einfacher Workflow von Skizze bis Video.

* Ein Knopf, zwei Zustände
* Wer sicher ist, kann versuchen, zwei- bis dreistufige Abläufe zu machen.
* Immer zuerst eine kleine Skizze anfertigen, um die Gedanken zu ordnen.
* Jeweils ein ganz kurzes Video davon aufnehmen und mir mit Slack schicken.

[Auflistung der Eigenschaften](http://help.pixate.com/knowledgebase/articles/665635-3i-conditions), die in Bedingungen abgefragt werden können.

Stand: 7.10.2016
