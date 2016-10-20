# Animation in CSS

## Typen von Animationen

Grundsätzlich lassen sich in CSS zwei Typen von Animationen definieren: nicht Interaktive (CSS-Animation) und Interaktive (CSS-Transitions).

CSS-Animationen starten automatisch, CSS-Transitions sind abhängig vom Zustand eines Elements, siehe `:hover` und `:active`.

## Was lässt sich animieren?

### Faustregel 1

Es lassen sich alle Eigenschaften animieren, die mit numerischen Werten definiert werden.

### Faustregel 2

Interpolieren von Position, Grösse, Drehung und Deckkraft verbraucht wenig Rechenleistung

```css
transform: translate(npx, npx); /* Position, Pixelwert */
transform: scale(n);            /* Grösse, Faktor      */
transform: rotate(ndeg);        /* Rotation, Winkel    */
opacity:   n;                   /* Deckkraft, 0–1      */
```

Weitere Information zur CSS-Eigenschaft `transform` finden sich z.B. im [entsprechenden Artikel des Mozilla Developer Networks](https://developer.mozilla.org/de/docs/Web/CSS/transform).

## CSS-Animation

Die CSS Eigenschaft ‘animation’ fasst folgende Eigenschaften zusammen:

```css
animation-name            /* Referenz für @keyframes, siehe unten          */
animation-duration        /* Sekunden oder Millisekunden                   */
animation-timing-function /* linear, ease, ease-in, ease-in-out, ease-out  */
animation-delay           /* Sekunden oder Millisekunden                   */
animation-iteration-count /* 0–infinite                                    */
animation-direction       /* normal, reverse, alternate, alternate-reverse */
animation-fill-mode       /* none, forwards, backwards, both               */
animation-play-state      /* paused, running                               */
```

### @keyframes

In der CSS-Regel ```@keyframes```, gefolgt vom Namen einer Animation, werden die Werte definiert, zwischen denen interpoliert wird: Start, Schluss und bei Bedarf Zwischenschritte. Erlaubt sind Angaben in Prozenten von 0–100, dazu `from` und `to` für Anfang und Ende der Animation.

```css
@keyframes grow {
    from { transform: scale(1); }  /* statt 'from' ginge auch '0%' */
    to   { transform: scale(2); }  /* statt 'to' ginge auch '100%' */
}

.cas-dt { animation: grow 2s ease 0 infinite alternate; }
```

### Anmerkungen

#### Reihenfolge der Werte in ‘animation’

Die Reihenfolge der Werte ist nur teilweise geregelt. Als erstes muss der Name aufgeführt werden. Falls Dauer und Verzögerung definiert werden, muss die Dauer zuerst angegeben werden.

#### Text animieren / inline-block

Achtung beim Animieren von Text: Inline-Elemente wie `<p>` erstrecken sich über die ganze Spalte, dadurch ist der Referenzpunkt meist anderswo als erwartet (der Referenzpunkt ist beispielsweise das Zentrum einer Rotation).

Um beispielsweise ein kurzes Wort zu rotieren, kann die Darstellungsform von inline zu inline-block geändert werdn, dadurch passt sich die Grösse des Elements an seinen Inhalt an.

Um zu sehen, wie gross ein Element ist, kann es helfen, einen `border: solid 1px black;` darum zu zeichnen oder den `background: hotpink;` zu färben.

```css
.kurzes-wort {
     display: inline-block;
}
```

#### Vendor Prefixes

Für ältere Browser-Versionen sind [Vendor-Prefixes](https://developer.mozilla.org/en-US/docs/Glossary/Vendor_Prefix) notwendig:

```css
-webkit-animation  {}  @-webkit-keyframes  {}  /* Chrome, Safari, neuere Opera Versionen */
-moz-animation     {}  @-moz-keyframes     {}  /* Firefox                                */
-ms-animation      {}  @-ms-keyframes      {}  /* Internet Explorer                      */
-o-animation       {}  @-o-keyframes       {}  /* ältere Opera Versionen                 */
```

## CSS Transitions

Die CSS Eigenschaft transition fasst folgende Eigenschaften zusammen:

```css
transition-property  [Eine CSS-Eigenschaft]
transition-duration  [Sekunden oder Millisekunden]
transition-timing-function  [linear, ease, ease-in, ease-in-out, ease-out]
transition-delay  [Sekunden oder Millisekunden]
```

### Beispiel

Einblenden eines HTML-Elements mit der Klasse «cas-dt».

```css
.cas-dt {
    color: black;
    opacity: 0.5;
    transition: opacity 0.5s ease-out 0;
}

.cas-dt:hover {
    opacity: 1;
}
```

## Timing Functions (ease)

Eine Bewegung muss nicht mit konstanter Geschwindigkeit ablaufen. Die verschiedenen Varianten von «ease»-Werten entsprechen kurvenförmigen Beschleunigungswerten über die Dauer einer Animation.

```css
linear	              /* konstante Geschwindigkeit                  */
ease	              /* langsamer Start, langsames Ende            */
ease-in	              /* langsamer Start, Beschleuigung am Ende     */
ease-out              /* Schneller Start, Verlangsamung gegen Ende  */
ease-in-out           /* langsamer Start, langsames Ende (Variante) */
cubic-bezier(n,n,n,n) /* Eigene Kurve                               */
```

## :hover und :active

Die CSS [Pseudo-Klassen](https://developer.mozilla.org/de/docs/Web/CSS/Pseudo-classes) `:hover` und `:active` bezeichnen Zustände eines HTML-Elements. `:hover` bezeichnet ein Element, über dem der Cursor schwebt, `:active` steht für ein Element, das angeklickt wird (Maustaste gedrückt).

Ein Problem im Zusammenhang mit CSS-Transitions stellt sich bei Touch-Devices. Das Tippen mit dem Finger entspricht dem Klick mit der Maus oder dem Trackpad. Die Pseudoklasse `:hover` existiert auf Tablets und Smartphones nicht: es gibt nur `:active`.

Mit JavaScript lässt sich erreichen, dass das einmalige Antippen eines Elements als `:hover` interpretiert wird, und erst das zweite Tippen als `:active`. Mit JavaScript lässt sich nicht nur beliebig manipulieren, wie der Browser Quelltext verarbeitet, sondern auch wie er Interaktionen prozes-siert. Es stellt sich natürlich die Frage, wie sinnvoll es ist, eine Art der Interaktion, die auf den Eigenschaften des Cursors basiert, in eine Umgebung ohne Cursor zu Übersetzen.

Wie mit der Problematik umgegangen wird, ist Ermessenssache und hängt davon ab, ob CSS-Transitions je nach Art des Endgeräts unterschiedlich gehandhabt werden.

### Referenzbeispiele

* [Erste Animation](http://codepen.io/oolong32/pen/pgovXK)
* [Einfache Animation](http://codepen.io/oolong32/pen/MYEKBM)
* [Text rotieren](http://codepen.io/oolong32/pen/jrQZJV)
* [Text rotieren in 3D](http://codepen.io/oolong32/pen/GoRRoX?editors=1100)
* [Animierte Hintergrundfarbe](http://codepen.io/oolong32/pen/avemyg)
* [Transition: Animierte Links](http://codepen.io/oolong32/pen/wKVgNz)
* [Transition: nach Media Query](http://codepen.io/oolong32/pen/VewYqY?editors=1100)

## Übung

Aufgabe: Den HTML- und CSS-Code unten in CodePen übertragen. Titel mit `animation` auszeichnen, Links mit `transition`. Einmal dezent, einmal extravagant. CodePen-Link per Slack an die Lehrperson.

Hilfestellung zu [CSS-Animation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations) und zu [CSS-Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions) und zur Eigenschaft [transform](https://developer.mozilla.org/de/docs/Web/CSS/transform).

```html
<div id="spalte">
  <h1>Bienengarnele</h1>

  <p>Die <a href="https://goo.gl/isGxxf">Bienengarnele</a> (Caridina logemanni) ist eine aus <a href="https://goo.gl/Dqtzjz">Hongkong</a> stammende <a href="https://goo.gl/qKC2a0">Süßwassergarnele</a> (Atyidae) aus der <a href="https://goo.gl/t0JIDA">Gattung Caridina</a>. Wegen ihres attraktiven Erscheinungsbildes und ihrer relativ unproblematischen
    Haltung wird sie häufig in Aquarien gepflegt. Eine rote Farbvariante wird unter der Bezeichnung „Crystal Red“ oder auch „Kristallrote Zwerggarnele“ gehandelt.</p>
  <ul>
    <li><a href="goo.gl/biLu8m" target="_blank">Crystal Red</a></li>
    <li><a href="https://goo.gl/Dzrk4f" target="_blank">Black Bee</a></li>
    <li><a href="https://goo.gl/TtQOlF" target="_blank">Red Bee</a></li>
    <li><a href="https://goo.gl/efXvib" target="_blank">Snow White</a></li>
    <li><a href="https://goo.gl/8ee8pY" target="_blank">Blue Bolt</a></li>
    <li><a href="https://goo.gl/GVzACx" target="_blank">Panda</a></li>
    <li><a href="https://goo.gl/G6KwLY" target="_blank">Red Ruby</a></li>
  </ul>
  <img src="https://goo.gl/GVzACx" alt="Panda Garnele">
</div>
```

```css
#spalte {
  width: 700px;
  margin: 0 auto;
}

h1 {
  display: inline-block;
  animation-name: titel;
  animation-duration/* Sekunden oder Millisekunden */
  animation-timing-function/* linear, ease, ease-in, ease-in-out, ease-out */
  animation-iteration-count/* 0–infinite */
  animation-direction/* normal, reverse, alternate, alternate-reverse */
}

@keyframes titel {
  from { /* Eigenschaft: Anfangswert; */ }
  to { /* Eigenschaft: Endwert; */ }
}

a:link,
a:visited {
  /* eigenschaft: wert1;
  transition: eigenschaft 2s; */
}

a:hover {
  /* eigenschaft: wert2; */
}

img { width: 100%; height: auto; }

/*
Bonus: die Links im Text lassen sich von den Links in der Liste unterscheiden:
p a {}
li a {}
*/
```

Das [Ganze in CodePen](http://codepen.io/oolong32/pen/xEmGQW).

## Links

* [Handout (PDF)](Handout_CSS-Animation.pdf)

## Vertiefende Artikel

* [Rebecca Ussai – The Principles of UX Choreography](https://medium.com/@becca_u/the-principles-of-ux-choreography-69c91c2cbc2a#.o932lmttu)
* [Val Head, All the right moves screencast](https://vimeo.com/channels/alltherightmoves/)
* [Val Head, Designing Safer Web Animation For Motion Sensitivity](http://alistapart.com/article/designing-safer-web-animation-for-motion-sensitivity)
* [Val Head, UI Animation and UX: A Not-So-Secret Friendship](http://alistapart.com/article/ui-animation-and-ux-a-not-so-secret-friendship)
* [Val Head, More Resources for Accessible Animations](http://alistapart.com/blog/post/more-resources-for-accessible-animations)
* [Sarah Drasner - Complex Responsive Animations](https://youtu.be/09_8edPAsR8)
* [Pasquale D’Silva – Transitional Interfaces](https://medium.com/@pasql/transitional-interfaces-926eb80d64e3#.8g5i5zet8)
* [Adrian Zumbrunnen – Smart Transitions](http://www.smashingmagazine.com/2013/10/smart-transitions-in-user-experience-design/) 
* [Amit Daliot – Functional Animation In UX Design](http://www.smashingmagazine.com/2015/05/functional-ux-design-animations/)
* [Donovan Hutchinson – Animating Your Brand](https://24ways.org/2015/animating-your-brand/)

### Disney’s 12 Basic Principles of Animation

* [Disney’s 12 Basic Principles of Animation](https://en.wikipedia.org/wiki/12_basic_principles_of_animation)
* [http://the12principles.tumblr.com/](http://the12principles.tumblr.com/)
 
## Kritik

* [Stop Gratuitous UI Animation](https://medium.com/@sophie_paxtonUX/stop-gratuitous-ui-animation-9ece9aa9eb97#.v22v5b1qg)
* [Your UI isn’t a Disney Movie](https://medium.com/startups-venture-capital/your-ui-isn-t-a-disney-movie-703f7fbd24d2#.xvmbjo31q)
* [ Why iOS 7 is making some users sick ](http://www.theguardian.com/technology/2013/sep/27/ios-7-motion-sickness-nausea)

## Coding / Specs

* [Mozilla Developer Network – Using CSS Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
* [Mozilla Developer Network – Using CSS Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)
* [Mozilla Developer Network – @keyframes](https://developer.mozilla.org/de/docs/Web/CSS/@keyframes)
* [CSS Tricks – Animation](https://css-tricks.com/almanac/properties/a/animation/)
* [CSS Tricks – Transition](https://css-tricks.com/almanac/properties/t/transition/)
* [CSS Animatable Properties](oli.jp/2010/css-animatable-properties/)
* [CSS Animation Rocks](https://cssanimation.rocks/)
* [CSS Transitions Standard](www.w3.org/TR/css3-transitions/)
* [W3C Working Draft – CSS Animations Standard](www.w3.org/TR/css3-animations/)
* [Paul Lewis & Paul Irish – High Performance Animations](www.html5rocks.com/en/tutorials/speed/high-performance-animations/)

## Codepen Accounts im Zusammenhang mit Animation

* [codepen.io – Amelia Bellamy-Royds](http://codepen.io/AmeliaBR/)
* [codepen.io – Anna Tudor](http://codepen.io/thebabydino/) 
* [codepen.io – Chris Gannon](http://codepen.io/chrisgannon/)
* [codepen.io – CJ Gammon](http://codepen.io/cjgammon/)
* [codepen.io – Lego Mushroom](http://codepen.io/sol0mka/) 
* [codepen.io – Tiffany Rayside](http://codepen.io/tmrDevelops/)
* [codepen.io – Joni Trythall](http://codepen.io/jonitrythall/)
* [codepen.io – Petr Tlchy](http://codepen.io/ihatetomatoes/)

## JavaScript, jQuery et al

* [jquery UI](http://jqueryui.com/)
* [jquery Effects](http://jqueryui.com/effect/)
* [Popmotion.js – The JavaScript motion engine](http://popmotion.io/)
* [Mo.js – Motion for the web](http://mojs.io)
* [Skrollr – Prallax scrolling for the masses](url)
* [ScrollMagic – The javascript library for magical scroll interactions](http://scrollmagic.io/)

## Ungeordnete

* [https://www.google.com/design/spec/animation/](https://www.google.com/design/spec/animation/)
* [https://de.pinterest.com/julient/animated-uxui/](https://de.pinterest.com/julient/animated-uxui/)
* [http://www.materialup.com/posts/c/inspiration/animation](http://www.materialup.com/posts/c/inspiration/animation)
* [http://capptivate.co](http://capptivate.co)
* [http://hoverstat.es](http://hoverstat.es)
* [https://www.consumerbarometer.com/en/insights/](https://www.consumerbarometer.com/en/insights/)
