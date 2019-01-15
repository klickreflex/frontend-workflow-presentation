---
presentation:
  controls: true
  # presentation theme
  # === available themes ===
  # "beige.css"
  # "black.css"
  # "blood.css"
  # "league.css"
  # "moon.css"
  # "night.css"
  # "serif.css"
  # "simple.css"
  # "sky.css"
  # "solarized.css"
  # "white.css"
  # "none.css"  
  theme: black.css
  width: 1440
  height: 900
  margin: 0.2
  transition: 'slide' # none/fade/slide/convex/concave/zoom
  enableSpeakerNotes: false

export_on_save:
  html: true
---

<link href="https://cdn.jsdelivr.net/npm/tailwindcss/dist/tailwind.min.css" rel="stylesheet">

<style>
  .list-rest {
    padding: 0 !important;
    list-style: none !immportant;
  }
</style>

<!-- slide data-notes="Einführung" -->
# Frontend 
# <div class="opacity-100 text-blue-light"> :fa-mobile: :fa-cog: :fa-desktop: :fa-wrench: :fa-tablet:</div>
# Workflow


<!-- slide -->
## :fa-road:
## Ziele


<!-- slide vertical="true" -->
## <span class="text-green">:fa-plus:</span> Konsistenz
## <span class="text-green">:fa-plus:</span> Speed of Development

### <span class="text-green">:fa-plus:</span> Wartbarkeit 
### <span class="text-green">:fa-plus:</span> Lesbarkeit  

&nbsp;

### <span class="text-red">:fa-minus:</span> Premature Abstraction
### <span class="text-red">:fa-minus:</span> Cognitive Overload 
### <span class="text-red">:fa-minus:</span> Magic Numbers


<!-- slide vertical="true" -->
# 😱
## Keine Angst! 
<span class="text-green">:fa-check:</span> <span class="opacity-75">Die Sorge vor unvorhergesehen Auswirkungen durch Änderungen minimieren</span>

<!-- slide vertical="true" -->
# 👋
## Onboarding
<span class="text-green">:fa-check:</span> <span class="opacity-75">Neue Entwickler müssen mit wenig Aufwand in Projekte/Teams eingebracht werden können</span>


<!-- slide -->
# 🛠
## Utility First 
 <span class="opacity-75">why?</span>

<!-- slide vertical="true" -->
## :fa-tachometer:
### Dev Speed
&nbsp;
<span class="opacity-75">Entwicklung im HTML: kein Kontext-Switch</span>
&nbsp;
<span class="opacity-75">Vermeidung frühzeitiger Abstraktion</span>
&nbsp;
<span class="opacity-75">Gestaltung im Browser möglich</span>



<!-- slide vertical="true" -->
## :fa-tachometer:
### App Speed
&nbsp;
<span class="opacity-75">Render Performance</span>
&nbsp;
<span class="opacity-75">Niedrige Spezifität</span>
&nbsp;
<span class="opacity-75">File Size</span>


<!-- slide vertical="true" -->
## Immutability

&nbsp;

> Declare a property once and you should be damn sure it’s never going to get overwritten. Fuck specificity.Apply the class you want — margin-bottom, say —  <span class="text-yellow">**and rest assured that no one else’s CSS is going to override it**.</span> The problem here is that CSS isn’t immutable, but be clever in your implementation and it’s kind of like immutability.

-- _Jon Gold_ 


<!-- slide vertical="true" -->
## Hello, my name is…
&nbsp;
>There are only two hard things in Computer Science: cache invalidation and <span class="text-yellow">**naming things**</span>.

*-- Phil Karlton*

<!-- slide vertical="true" -->
### Bekannter Workflow?

1. Namen finden

2. Sass-Komponente anlegen & einbinden

3. Styling schreiben

4. Feststellen, dass die Komponente an anderer Stelle benötigt wird, aber mit blauem Hintergrund
    - BEM-Modifier implementieren `.c-thing--bg-blue` _oder_
    - Komponente untern neuem Namen duplizieren `.c-blue-thing`

5. Repeat

<!-- slide vertical="true" -->
```css
.c-thing { … }
.c-thing--header { margin-top: 1rem; }
.c-thing--subtle { background-color: #dedede; }
.c-thing--big { font-size: 2rem}
.c-thing--positive { color: green; }
.c-thing--negative { color: red; }

```

![knope](/assets/knope.gif)

<!-- slide vertical="true" -->
### How about instead…?

```html
<div class="c-thing mt-4">
<div class="c-thing bg-grey-light">
<div class="c-thing text-xl">
<div class="c-thing text-green">
<div class="c-thing text-red">
```

![happyasiz](/assets/happyasiz.gif)


<!-- slide vertical="true" -->
# 🎉
## Ich muss <span class="opacity-50">~~nicht~~</span> weniger über Naming nachdenken
&nbsp;

Ich kann nur HTML schreiben & committen
&nbsp;
Ich führe keine Magic Numbers (☠️) ein ➡ Konsistenz

<!-- slide vertical="true" -->

1. Layouts <span class="text-yellow">**erst**</span> mit Utilities umsetzen

2. Komponenten extrahieren <span class="text-yellow">**wenn**</span> Muster sich wiederholen.  

&nbsp;

<!-- slide vertical="true" -->
Abstraktion in Komponente mit @apply
![utilities](/assets/utilities_w0o2zv6lq.png)

<!-- slide vertical="true" -->
### Tailwind CSS
![tailwind](/assets/tailwind.png)

> Tailwind provides highly composable, low-level utility classes that make it easy to build complex user interfaces [..]

<!-- slide vertical="true" -->
### Tailwind CSS 

<span class="opacity-75">Utility Framework als PostCSS Plugin:</span>
&nbsp;
<span class="text-green">:fa-check:</span> Unabhängig von CSS-Präprozessoren

<span class="text-green">:fa-check:</span> Konfigurier- und erweiterbar mit JavaScript

<span class="text-green">:fa-check:</span> Alle Utilities anpassbar

<span class="text-green">:fa-check:</span> Nützliche Helper-Funktionen

![andy](/assets/andy.gif)

<!-- slide vertical="true" -->
### Tailwind Beispiel
```html
<div class="bg-white mx-auto max-w-sm shadow-lg rounded-lg overflow-hidden">
  <div class="sm:flex sm:items-center px-6 py-4">
    <img class="block h-16 sm:h-24 rounded-full mx-auto mb-4 sm:mb-0 sm:mr-4 sm:ml-0" src="https://avatars2.githubusercontent.com/u/4323180?s=400&u=4962a4441fae9fba5f0f86456c6c506a21ffca4f&v=4" alt="">
    <div class="text-center sm:text-left sm:flex-grow">
      <div class="mb-4">
        <p class="text-xl leading-tight">Adam Wathan</p>
        <p class="text-sm leading-tight text-grey-dark">Developer at NothingWorks Inc.</p>
      </div>
      <div>
        <button class="text-xs font-semibold rounded-full px-4 py-1 leading-normal bg-white border border-purple text-purple hover:bg-purple hover:text-white">Message</button>
      </div>
    </div>
  </div>
```

<!-- slide vertical="true" -->
![whatthehell](/assets/whatthehell.gif)
## Erste Reaktionen

- „So schlimm wie Inline Styles“ ☠️

- „Müllt das Markup voll“ 🗑

- „Nicht semantisch“ 🤓

<!-- slide vertical="true" -->
### Inline Styles vs Utility-First

&nbsp;

<span class="text-green">:fa-check:</span> Media Queries

```html
<h2 class="text-md lg:text-lg>"
```

&nbsp;

<span class="text-green">:fa-check:</span> Pseudo-Elemente

```html
<a class="bg-red hover:bg-blue>"
```

&nbsp;

<span class="text-green">:fa-check:</span> Konsistenz

```html
/* Well defined options… */
<h2 class="text-xl"></h2>" 

/* … vs. Arbitrary Magic Numbers */
<h2 style="font-size: 3.2528rem"></h2>" 
```

<!-- slide vertical="true" -->
#### Unleserlich?
&nbsp;
### ‍Utilities sind expressiv 📢
```html
<ul class="text-white bg-red p-4 mb-4">
```
&nbsp;

### 📜 Gewohnheiten ändern sich
Wer hat BEM sofort geliebt?
<!-- slide vertical="true" -->

#### Unsemantisch?
&nbsp;
### Utilities beschreiben <span class="text-yellow">Styling</span> 🎨
&nbsp;
### <span class="text-yellow">📑 Inhalte  </span> beschreiben ist Aufgabe von HTML!

<!-- slide vertical="true" -->
> You clutter up your DOM with styling directives

&nbsp;

This is true. But I don't have an argument for why that's bad other than that it is stylistically ugly. Which I agree with. But it's fast to render in the browser. And it also has helped me get dev teams to build responsive interfaces more quickly. And those are the things I care about. <span class="text-yellow">**Dev velocity and application performance**</span>.

[@mrmrs](https://github.com/tachyons-css/tachyons/issues/12#issuecomment-598289672) (Autor von Taychons)

<!-- slide vertical="true" -->
### Tailwind: `@apply` rule
```html
<button class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded">
  Button
</button>
```

⬇

```css

.btn-blue {
  @apply .bg-blue .text-white .font-bold .py-2 .px-4 .rounded;
}
.btn-blue:hover {
  @apply .bg-blue-dark;
}

```

<!-- slide vertical="true" -->
### Tailwind Media Query Syntax
```html
<div class="bg-purple sm:bg-green md:bg-blue lg:bg-red">
```

```js
    screens: {
        'sm': '30em',
        'md': '48em',
        'lg': '64em',
        'xl': '75em',
    },
```


<!-- slide vertical="true" -->
### Optionen & Helper
&nbsp;
```js
    options: {
        prefix: '',
        important: false,
        separator: ':',
    },
```
&nbsp;

`@responsive { … }` 

`@variants hover, focus { … }`

`font-size: config('textSizes.xl')`


<!-- slide -->
# ▽
## Inverted Triangle CSS 
(ITCSS)

<!-- slide vertical="true" -->
## Elements
## Objects
## Components

![itcss](/assets/itcss.png)<!-- slide vertical="true" -->


<!-- slide vertical="true" -->
## Elements
&nbsp;
```css
p {
    margin-top: 0;
    margin-bottom: 1.5em;
}
```
&nbsp;
<span class="text-green">:fa-check:</span> grundlegendes Styling von HTML-Tags

<span class="text-green">:fa-check:</span> sollte site-weit gültig sein

<!-- slide vertical="true" -->
## Objects
&nbsp;
```css
.o-container {
    max-width: 74rem;
    padding: 0 2rem;
}
```
&nbsp;
<span class="text-green">:fa-check:</span> <span class="opacity-75">Definieren design-agnostisches Layout </span>

<span class="text-green">:fa-check:</span> <span class="opacity-75">Namespace: Präfix `o-` </span>
&nbsp;
<span class="opacity-75">z.B. Media Object, Kacheln, Grids, Container</span>

<!-- slide vertical="true" -->
## Components
&nbsp;
```css
.c-card {
    background-color: #fff;
    box-shadow: 0 0 2rem rgba(0, 0, 0, .15);
}
```
&nbsp;
<span class="text-green">:fa-check:</span> <span class="opacity-75">Gestaltete Komponenten</span>
<span class="text-green">:fa-check:</span> <span class="opacity-75">Namespace: Präfix `c-`</span>

<!-- slide -->
### 🗄 Dateien & Ordner

```scss
// Inject Tailwind's base styles (think of an enhanced normalize.css)
@tailwind preflight;

// Configuration: Variables used across the project
@import 'configuration/settings';

// Tools: Mixins and functions used across the project, do not create any CSS output if not called
@import 'tools/mappy-breakpoints';

// Elements: Styles that go directly on HTML elements, no classes or ids
@import 'elements/body';

// Objects:  Cosmetic free design patterns, e.G. containers, grid systems, tiles.
@import 'objects/container';

// Components: Designed UI components
@import 'components/button';

// Utilites provided by Tailwind
@tailwind utilities;
```

<!-- slide vertical="true"-->
### 📝 Files

- Lower Case <span class="opacity-50">`_card.scss`</span>

- Minus als Trennzeichen <span class="opacity-50">`_news-list.scss`</span>

- 4 Spaces Indentation <span class="opacity-50">`....`</span>

- Auf jeden Block folgt eine Leerzeile

- Sass im SCSS-Style

- Sass-Partials beginnen mit Underscore <span class="opacity-50">`_card.scss`</span>

<!-- slide -->
## ✳️
### Selektoren
&nbsp;
<span class="opacity-50">Basis-Styling über</span> **Element-Selektoren**

<span class="opacity-50">Weiteres Styling ausschließlich über</span> **Klassen**

<span class="opacity-50">Spezifitätskrieg vermeiden, </span>**Kaskade flach halten**

**IDs**<span class="opacity-50"> nur für Sprung-Links und Target-Selector</span>

<span class="opacity-50">JavaScript nur via</span> **data-attributes** <span class="opacity-50">ansprechen</span>



<!-- slide vertical="true"-->

##  👎 Don't
```scss
.c-product-teaser {
    div {
        + div {
            a { … }
        }
    }

    h2 { … }
    h3 { … }
    p { … }
    
    figure img { … }
    div:not(:first-of-type) a:last-of-type { … }
    div + div {
        a { … }
    }

    figure img { … }    
}
```
&nbsp;
⛔️ Schwer erfassbar

⛔️ DOM muss präsent sein

⛔️ Enge Kopplung ans Markup


<!-- slide vertical=true -->
### 👍 Do
```scss 
.c-product-teaser { … }

// Teaser Intro (= first column)
.c-product-teaser__intro { … }
.c-product-teaser__title { … } 
.c-product-teaser__text { … }

// Teaser Products (= second column)
.c-product-teaser__products { … }
.c-product-teaser-products__image { … }
.c-product-teaser-products__title { … }
.c-product-teaser-products__link { … }
```
&nbsp;
✅ Flach und Expressiv 

✅ Unabhängig von DOM-Änderungen

✅ Verständlich ohne Wissen über das Markup

<!-- slide vertical=true -->
### Klassennamen
- ✅ englisch  

- ✅ Lowercase BEM

- ✅ Double-Dash Modifiers

- ✅ **kurz aber eindeutig**  

- ⛔️ über-spezifisch

<!-- slide vertical=true -->
### Klassennamen

&nbsp;

| 👎 | 👍 |
|---|---|
| `.c-detailspage`  | `.c-detail` |
| `.c-fondscomparison-table` | `.c-funds-list` |
| `.c-product-teaser-with-background-image` | `.c-product-teaser c-product-teaser--background-image`|
| `.c-fondscomparison-hint` | `.c-hint` |

 
<!-- slide vertical=true -->
### Nesting
⛔ ️Don't 
```scss
.block {
  &__element { … }
}
```

Suche nach `.block__element` findet den Selektor nicht, daher:
&nbsp;
✅ ️Do
```scss
.block__element { …}
```

<!-- slide vertical=true -->
## :fa-sort-amount-desc:
### Property Sort Order
&nbsp;
Layout vor Dekoration:
<div class="opacity-50">(font-sizing → positioning → box model → colors/effects)</div>

&nbsp;
Konformität durch einheitliche <span class="text-yellow">**Sass-Lint**</span>-Konfiguration


<!-- slide -->
# 🙅‍
## CSS & Sass Anti Patterns

⛔️ Sass @extend
⛔️ Sass Color Functions
⛔️ Komponenten-Margins
⛔️ Background Shorthand
⛔️ margin: 0 auto

<!-- slide vertical=true -->
# 🙅‍ Avoid
### Sass @extend

```css
a.icon-listen-bl:hover,
.event-related .box-title a:hover,
.category-related .box-title a:hover,
.readmore a:hover,
.footer a:hover,
.pagination a:hover,
.news a:hover,
.latest-tweet .date a:hover,
.feature .box-header .title a:hover,
.caption .title a:hover,
.full-agenda-link a:hover,
.article a:hover,
.medialib-nav a:hover,
.timeline-months a:hover,
.Timeline .feature .box-footer a:hover,
.news a:focus,
.latest-tweet .date a:focus,
.feature .box-header .title a:focus,
.caption .title a:focus,
.full-agenda-link a:focus,
.article a:focus,
.medialib-nav a:focus,
.timeline-months a:focus,
.Timeline .feature .box-footer a:focus {
    text-decoration: underline;
}
```


<!-- slide vertical=true -->
## ‍‍‍🙅‍ Avoid: Sass Color Functions
```scss
.this { background-color: lighten($color-primary, 3.5%) }  
.that { background-color: lighten($color-primary, 3.2%) }  
.another { background-color: lighten($color-primary, 2.9%) }  
```
&nbsp;
Besser:
‍<span class="text-green">:fa-check:</span> zentrale Farbdefintion = Konsistzenz


<!-- slide vertical=true -->
## 🙅‍ Avoid: Komponenten-Margins
```scss
.thing { margin-bottom: 2rem }  
.thing--other-margin { margin-bottom: 4rem  }  
```
&nbsp;
Besser:

<span class="text-green">:fa-check:</span> kontextneutrale Komponenten
<span class="text-green">:fa-check:</span> Abstände über Utilty-Klassen


<!-- slide vertical=true -->
## 🙅‍ Avoid: Background Shorthand 
```css
background: red;
```
⬇
```css
background-image: initial;
background-position-x: initial;
background-position-y: initial;
background-size: initial;
background-repeat-x: initial;
background-repeat-y: initial;
background-attachment: initial;
background-origin: initial;
background-clip: initial;
background-color: red;
```

&nbsp;
> You should only ever do as little as you need to do and nothing more.

--_Harry Roberts_

<!-- slide vertical=true -->
## 🙅‍ Avoid: Margin: 0 auto für horizontale Zentrierung

&nbsp;
Besser:
```css
margin-right: auto 
margin-left: auto 
```
&nbsp;
<span class="text-green">:fa-check:</span> keine unerwünschten Nebenwirkungen auf vertikale Abstände

<!-- slide data-background="assets/styleguide-bg.png" -->
# <div class="text-grey-darkest">Styleguide</div>

<!-- slide vertical="true"-->
## Warum ein Styleguide?

![smart](/assets/smart.gif)

<span class="text-green">:fa-check:</span> FE unabhänig von BE

<span class="text-green">:fa-check:</span> Schnelle Iterationen

<span class="text-green">:fa-check:</span> Schnell präsentable Ergebnisse


<!-- slide vertical=true -->
## 📦
### Styleguide Skeleton
<div class="opacity-50">vorkonfiguriertes Fabricator-Setup</div>
&nbsp;

 <span class="text-green">:fa-check:</span> Ordner- und Dateistruktur

 <span class="text-green">:fa-check:</span> Tailwind CSS Setup

 <span class="text-green">:fa-check:</span> PurgeCSS 

 <span class="text-green">:fa-check:</span> mappy-breakpoints


<!-- slide vertical=true -->
![styleguide-structure](/assets/styleguide-structure.png)

Ordner- und Dateistruktur

<!-- slide vertical=true -->
![styleguide](/assets/styleguide.png)
Styleguide im Browser

<!-- slide vertical=true -->
### Templating im Styleguide
&nbsp;
<span class="text-green">:fa-check:</span> Komponenten mit Frontmatter dokumentieren

<span class="text-green">:fa-check:</span> Komponenten als Partials aufbauen

<span class="text-green">:fa-check:</span> Modifier und Utilities als Parameter übergeben

<span class="text-green">:fa-check:</span> Seiten aus Komponenten zusammensetzen

<!-- slide vertical=true -->
![components](/assets/components.png)
Definition einer Komponente

<!-- slide vertical=true -->
![component-in-page](/assets/component-in-page.png)
Einsatz einer Komponente in einer Page


<!-- slide vertical=true -->
![tailwind-in-action](/assets/tailwind-in-action.png)
Tailwind einsetzen

<!-- slide vertical=true -->
![tailwind-config](/assets/tailwind-config.png)
Tailwind anpassen

<!-- slide vertical=true -->

### 🗜 PurgeCSS
<div class="opacity-50">remove unused CSS</div>

&nbsp;

### `toolkit.css 434 KB` 
⬇
### `toolkit.css 31 KB`



<!-- slide vertical=true -->
### 🛠 Mappy Breakpoints
<div class="opacity-50">Sass Mixin für Media Queries</div>

```scss
$breakpoints: (
    'sm': 480px,  // 30em
    'md': 768px,  // 48em
    'lg': 992px,  // 62em
    'xl': 1180px  // 73.75em
);

@include mappy-bp(sm md) { }
// = @media screen and (min-width: 30em) and (max-width: 47.9375em) 
```
&nbsp;
<span class="text-green">:fa-check:</span> Zentrale Breakpoint-Verwaltung in Sass-Map

<span class="text-green">:fa-check:</span> Automatische Konversion `px` ➡ `em`

<span class="text-green">:fa-check:</span> Max-Queries automatisch `-1px`
&nbsp;
<div class="opacity-25">(Breakpoints müssen mit Tailwind-Config synchron gehalten werden)</div>


<!-- slide -->
![thanks](/assets/thanks.gif)


&nbsp;
<div class="opacity-50">Slides: http://bit.ly/feworkflow</div>

<!-- slide -->
### 📚 Further Reading
- [CSS Utility Classes and "Separation of Concerns"](https://adamwathan.me/css-utility-classes-and-separation-of-concerns/) von Adam Wathan
- [In Defense of Utility First CSS](https://frontstuff.io/in-defense-of-utility-first-css) von Sarah Dayan
- [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/) von Nicholas Gallagher
- [CSS and Scalability](http://mrmrs.github.io/writing/2016/03/24/scalable-css/) von Adam Morse
- [Rationalizing Functional CSS](https://marcelosomers.com/writing/rationalizing-functional-css/) von Marcelo Somers
- [Full re-write in 10 days with tachyons and functional CSS: A case study](https://hackernoon.com/full-re-write-with-tachyons-and-functional-css-a-case-study-part-1-635ccb5fb00b#.c6zw5yr6b) von Simon Vrachliotis
- [Kiss My Classname: A Counterpoint](https://medium.com/@johnpolacek/kiss-my-classname-a-counterpoint-3ca41f0aed1a) von John Polacek
- [Functional Programming, CSS, and your sanity](http://jon.gold/2015/07/functional-css/) von Jon Gold
- [How is tachyons different from inline styles?](https://github.com/tachyons-css/tachyons/issues/12)
- [CSS Shorthand Syntax Considered an Anti-Pattern](https://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/) von Harry Roberts
- [Manage large CSS projects with ITCSS](https://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528) von Harry Roberts
