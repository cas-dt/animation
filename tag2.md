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

## CSS-Animation

Die CSS Eigenschaft animation fasst folgende Eigenschaften zusammen:

```css
    animation-name            /* Referenz für @keyframes, siehe unten          */
    animation-duration        /* Sekunden oder Millisekunden                   */
    animation-timing-function /* linear, ease, ease-in, ease-in-out, ease-out  */
    animation-delay           /* Sekunden oder Millisekunden                   */
    animation-iteration-count /* 0–infinite                                    */
    animation-direction       /* normal, reverse, alternate, alternate-reverse */
```

### @keyframes

In der CSS-Regel ```@keyframes```, gefolgt vom Namen einer Animation, werden die Werte definiert, zwischen denen interpoliert wird: Start, Schluss und bei Bedarf Zwischenschritte. Erlaubt sind Angaben in Prozenten von 0–100, dazu `$1` und `$1` für Anfang und Ende der Animation.

```css
    @keyframes grow {
        from { transform: scale(1); }  /* statt 'from' ginge auch '0%' */
        to   { transform: scale(2); }  /* statt 'to' ginge auch '100%' */
    }

    .cas-dt { animation: grow 2s ease 0 infinite alternate; }
```

### Anmerkungen

Die Reihenfolge der Werte ist nur teilweise geregelt. Als erstes muss der Name aufgeführt werden. Falls Dauer und Verzögerung definiert werden, muss die Dauer zuerst angegeben werden.
Für ältere Browser-Versionen sind Vendor-Prefixes notwendig:

```css
    -webkit-animation  {}  @-webkit-keyframes  {}  /* Chrome/Safari      */
    -moz-animation     {}  @-moz-keyframes     {}  /* Firefox            */
    -ms-animation      {}  @-ms-keyframes      {}  /* Internet Explorer  */
    -o-animation       {}  @-o-keyframes       {}  /* Opera              */
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

## Timing Functions (‘ease’)

Eine Bewegung muss nicht mit konstanter Geschwindigkeit ablaufen. Die verschiedenen Varianten von «ease»-Werten entsprechen kurvenförmigen Beschleunigungswerten über die Dauer einer Animation.

```css
    linear	              [konstante Geschwindigkeit]
    ease	              [[langsamer Start, langsames Ende]
    ease-in	              [[langsamer Start, Beschleuigung am Ende]
    ease-out              [Schneller Start, Verlangsamung gegen Ende]
    ease-in-out           [langsamer Start, langsames Ende (Variante)]
    cubic-bezier(n,n,n,n) [Eigene Kurve]
```

## :hover und :active

Die CSS Pseudoklassen `:hover` und `:active` bezeichnen Zustände eines HTML-Elements. `:hover` bezeichnet ein Element, über dem der Cursor schwebt, `:active` steht für ein Element, das angeklickt wird (Maustaste gedrückt).
Ein Problem im Zusammenhang mit CSS-Transitions stellt sich bei Touch-Devices. Das Tippen mit dem Finger entspricht dem Klick mit der Maus oder dem Trackpad. Die Pseudoklasse `:hover` existiert auf Tablets und Smartphones nicht: es gibt nur `:active`.
Nun lässt sich mit JavaScript erreichen, dass das einmalige Antippen eines Elements als `:hover` interpretiert wird, und erst das zweite Tippen als `:active`.
Mit JavaScript lässt sich nicht nur beliebig manipulieren, wie der Browser Quelltext verarbeitet, sondern auch wie er Interaktionen prozes-siert. Es stellt sich natürlich die Frage, wie sinnvoll es ist, eine Art der Interaktion, die auf den Eigenschaften des Cursors basiert, in eine Umgebung ohne Cursor zu Übersetzen.

## Links

* [Handout (PDF)](Handout_CSS-Animation.pdf)

## CSS Animation

* [CSS Tricks – Animation](https://css-tricks.com/almanac/properties/a/animation/)
* [Mozilla Developer Network – @keyframes](https://developer.mozilla.org/de/docs/Web/CSS/@keyframes)
* [CSS Tricks – Transition](https://css-tricks.com/almanac/properties/t/transition/)
* [CSS Animatable Properties](oli.jp/2010/css-animatable-properties/)
* [CSS Animation Rocks](https://cssanimation.rocks/)
* [CSS Transitions Standard](www.w3.org/TR/css3-transitions/)
* [W3C Working Draft – CSS Animations Standard](www.w3.org/TR/css3-animations/)
* [Paul Lewis & Paul Irish – High Performance Animations](www.html5rocks.com/en/tutorials/speed/high-performance-animations/)
* [Val Head, All the right moves screencast](https://vimeo.com/channels/alltherightmoves/)
* [Sarah Drasner - Complex Responsive Animations](https://youtu.be/09_8edPAsR8)
* [Why iOS 7 is making some users sick](http://www.theguardian.com/technology/2013/sep/27/ios-7-motion-sickness-nausea)
* [Stop Gratuitous UI Animation](https://medium.com/@sophie_paxtonUX/stop-gratuitous-ui-animation-9ece9aa9eb97#.v22v5b1qg)
* [Your UI isn’t a Disney Movie](https://medium.com/startups-venture-capital/your-ui-isn-t-a-disney-movie-703f7fbd24d2#.xvmbjo31q)

## Codepen

* [codepen.io – Amelia Bellamy-Royds](http://codepen.io/AmeliaBR/)
* [codepen.io – Sarah Drasner](http://codepen.io/sdras/)
* [codepen.io – Chris Gannon](http://codepen.io/chrisgannon/)
* [codepen.io – CJ Gammon](http://codepen.io/cjgammon/)
* [codepen.io – Val Head](codepen.io/valhead)
* [codepen.io – Lego Mushroom](http://codepen.io/sol0mka/) 
* [codepen.io – Anna Tudor](http://codepen.io/thebabydino/) 
* [codepen.io – Tiffany Rayside](http://codepen.io/tmrDevelops/)
* [codepen.io – Rachel Smith](codepen.io/rachsmith)
* [codepen.io – Petr Tlchy](http://codepen.io/ihatetomatoes/)
* [codepen.io – Joni Trythall](http://codepen.io/jonitrythall/)


## jQuery

[Codecademy – jQuery Lehrgang](www.html5rocks.com/en/tutorials/speed/high-performance-animations/)

## Theorie

* [Disney's 12 Basic Principles of Animation](https://en.wikipedia.org/wiki/12_basic_principles_of_animation)
* [http://the12principles.tumblr.com/](http://the12principles.tumblr.com/)
