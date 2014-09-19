<link href="styles/font-awesome/css/font-awesome.css" rel="stylesheet">

##Web Components
###Il modello a componenti per il Web
![Club degli Sviluppatori](images/cds.png) ![Web Component](images/wc.png) ![Nicola Sanitate](images/profile.png)

---

In principio il Web era semplice

----

<img src="images/tech-before.png">

----

Le nostre pagine erano semplici

----

![CERN 1999](images/cern-1999.png)

----

Col passare tempo il Web è diventato più complesso

----

![Tech After](images/tech-after.png)

----

WebApp

----

![Hangout 2014](images/hangout-2014.png)

----

Il Web è la piattaforma giusta per **ESEGUIRE** applicazioni?

<span class="fragment fade-in"><img src="images/clint-eastwood-yes.gif" style="height:300px"></span>

----

Il Web è la piattaforma giusta per **DISTRIBUIRE** applicazioni?

<span class="fragment fade-in"><img src="images/daft-punk-yes.gif" style="height:300px"></span>

----

Il Web è la piattaforma giusta per **REALIZZARE** applicazioni?

<span class="fragment fade-in"><img src="images/indiana-jones-chin-rub.gif" style="height:300px"></span>

---

##Analizziamo il problema

![Sherlock Holmes](images/sherlock-holmes.png)

----

Il Web è composto da **ELEMENTI**

![LEGO](images/lego.png)

----

Elementi **INCAPSULATI**

<select style="font-size:32px; width: 300px">
  <option>Small</option>
  <option>Medium</option>
  <option>Large</option>
  <option>X-Large</option>
  <option>XX-Large</option>
</select>

```xml
<select>
  <option>Small</option>
  <option>Medium</option>
  <option>Large</option>
  <option>X-Large</option>
  <option>XX-Large</option>
</select>
```

----

Elementi **CONFIGURABILI**

<select id="size" size="6" multiple style="font-size:32px; width: 300px">
  <option disabled>Small</option>
  <option disabled>Medium</option>
  <option selected>Large</option>
  <option>X-Large</option>
  <option>XX-Large</option>
</select>

```xml
<select id="size" size="6" multiple>
  <option disabled>Small</option>
  <option disabled>Medium</option>
  <option selected>Large</option>
  <option>X-Large</option>
  <option>XX-Large</option>
</select>
```

----

Elementi **COMPONIBILI**

<select style="font-size:32px; width: 300px">
  <optgroup label="Small">
    <option>Small</option>
  </optgroup>
  <optgroup label="Medium">
    <option>Medium</option>
  </optgroup>
  <optgroup label="Large">
    <option>Large</option>
    <option>X-Large</option>
    <option>XX-Large</option>
  </optgroup>
</select>

```xml
<select>
  <optgroup label="Small">
    <option>Small</option>
  </optgroup>
  <optgroup label="Medium">
    <option>Medium</option>
  </optgroup>
  <optgroup label="Large">
    <option>Large</option>
    <option>X-Large</option>
    <option>XX-Large</option>
  </optgroup>
</select>
```

----

Elementi **PROGRAMMABILI**

```javascript
var foo = mySelect.selectedIndex;
```

----

Ma cosa succede se vogliamo costruire nuovi elementi?

----

###Carousel / Slideshow

![Carousel](images/carousel.png)

----

###Carousel / Slideshow

```xml
<div id="carousel-example-generic" class="carousel slide" data-ride="carousel">
  <!-- Indicators -->
  <ol class="carousel-indicators">
    <li data-target="#carousel-example-generic" data-slide-to="0" class="active"></li>
    <li data-target="#carousel-example-generic" data-slide-to="1"></li>
    <li data-target="#carousel-example-generic" data-slide-to="2"></li>
  </ol>

  <!-- Wrapper for slides -->
  <div class="carousel-inner">
    <div class="item active">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
    <div class="item">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
    <div class="item">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
    <div class="item">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
    <div class="item">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
    <div class="item">
      <img src="..." alt="...">
      <div class="carousel-caption">
        ...
      </div>
    </div>
  </div>

  <!-- Controls -->
  <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
    <span class="glyphicon glyphicon-chevron-left"></span>
  </a>
  <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
    <span class="glyphicon glyphicon-chevron-right"></span>
  </a>
</div>
```

----

###Le pecche delle tecnologie Web

<ul>
  <li class="fragment fade-in">Riuso</li>
  <li class="fragment fade-in">Estendibilità</li>
  <li class="fragment fade-in">Incapsulamento</li>
  <li class="fragment fade-in">Modularità</li>
  <li class="fragment fade-in">Manutenibilità</li>
</ul>

----

![Facepalm Polarbear](images/facepalm-polarbear.png)

----

###Carousel / Slideshow

```xml
<carousel>
  <img src="..." alt="...">
  <img src="..." alt="...">
  <img src="..." alt="...">
</carousel>
```

---

Da oggi questo è possibile grazie a

##Web Components

<div class="fragment fade-in">
![Homer Hurra](images/homer-hurra.png)
<br>
Hurray!
</div>

----

Una collezione di **standard emergenti**

che permettono agli sviluppatori di **estendere HTML**

----

Il mondo delle Web Components comprende:

* ###Template
* ###Custom Elements
* ###Shadow DOM
* ###HTML Imports

---

##Template

![Cake mold](images/cake-mold.png)

----

![Shock](images/shock.gif)

...not a new concept

----

Come definire un client-side templating DOM-based?
![Homer thoughtful](images/homer-thoughtful.png)
<h3 class="fragment">&lt;template&gt;</h3>

----

###Come si definisce

```xml
<template id="my-template">
  <img src="" alt="great image">
  <div class="comment"></div>
</template>
```

----

###Proprietà del template content

* non viene renderizzato
* non ha side effects
* non figura direttamente nel DOM

----

###Come si usa

```javascript
var t = document.querySelector('#my-template');
var clone = document.importNode(t.content, true);

// Populate the src at runtime.
clone.querySelector('img').src = 'logo.png';
document.body.appendChild(clone);
```

----

###Esempio

```xml
<button onclick="useIt()">Cliccami</button>
<div id="container"></div>

<template id="my-template">
  <div>Provengo da una &lt;template&gt;.</div>
  <_script_>alert('Grazie!')</_script_>
</template>
```

```javascript
function useIt() {
  var t = document.querySelector('#my-template');
  var clone = document.importNode(t.content, true);

  document.querySelector('#container').appendChild(clone);
}
```

---

##Custom Elements

![FIAT 500](images/fiat-500.png)

----

Permettono di definire nuovi tipi di elementi HTML

----

###Come si definisce

```javascript
var XFoo = document.registerElement('x-foo');
```
oppure

```javascript
var XFoo = document.registerElement('mega-button', {
  prototype: Object.create(HTMLButtonElement.prototype),
  extends: 'button'
});
```

----

Unica regola dei Custom Elements

<h3 class="fragment fade-in">Usare nomi con **"-"**</h3>

----

###Come si usa

```xml
<x-foo></x-foo>
```

oppure

```xml
<button is="mega-button">
```

----

###Metodi di lifecycle

```javascript
var MyElement = document.registerElement('my-element', {
  prototype: Object.create(HTMLElement.prototype),

  // createdCallback, attachedCallback, detachedCallback
  attributeChangedCallback: {
    value: function(attr, oldVal, newVal) {
      ...
    }
  }
});
```

----

**Custom Elements** + **Template**

```xml
<my-tag></my-tag>

<template id="my-template">
  <p>Sono in my-tag e provengo da una &lt;template&gt;.</p>
</template>
```

```javascript
var proto = Object.create(HTMLElement.prototype, {
  createdCallback: {
    value: function() {
      var t = document.querySelector('#my-template');
      var clone = document.importNode(t.content, true);
      this.appendChild(clone);
    }
  }
});

document.registerElement('my-tag', { prototype: proto });
```

---

##Shadow DOM

![Shadow man](images/shadow-man.png)

----

Risolve il problema dell’incapsulamento del DOM

----

![Shadow DOM](images/shadow-dom.png)

----

###Come si usa

```xml
<button>Hello, world!</button>
```

```javascript
var host = document.querySelector('button');
var root = host.createShadowRoot();
root.textContent = 'Ciao, mondo!';
```

----

![Shadow DOM 1](images/shadow-dom-1.png)

----

###E il contenuto dell'host?

```xml
<button>Nicola</button>
```

```javascript
var host = document.querySelector('button');
var root = host.createShadowRoot();
root.innerHTML = 'Ciao <content></content>. Sei il benvenuto!';
```

----

![Shadow DOM 2](images/shadow-dom-2.png)

----

**Shadow DOM** + **Custom Elements** + **Template**

```xml
<p>Non sono nello Shadow DOM</p>
<my-tag>Nicola</my-tag>

<template id="my-template">
  <p>Ciao <content></content>. Sono nello Shadow DOM di my-tag e provengo da una &lt;template&gt;.</p>
</template>
```

```javascript
var proto = Object.create(HTMLElement.prototype, {
  createdCallback: {
    value: function() {
      var t = document.querySelector('#my-template');
      var clone = document.importNode(t.content, true);
      this.createShadowRoot().appendChild(clone);
    }
  }
});

document.registerElement('my-tag', { prototype: proto });
```

```css
p { color: orange; }
```

---

##HTML Imports

![Import-Export](images/import-export.png)

----

Un modo di includere documenti HTML

in altri documenti HTML

----

###Come si usa

```xml
<head>
  <link rel="import" href="/path/to/import/stuff.html">
</head>
```

```javascript
var content = document.querySelector('link[rel="import"]').import;
```

----

Attenti agli &lt;script&gt;:

* Vengono eseguiti all'import
* Non bloccano il parsing della main page
* Fanno riferimento a **"window"** del documento importatore

----

**All together now**
```xml
<template id="my-template">
  <p>Ciao <content></content>. Sono nello Shadow DOM di my-tag e provengo da una &lt;template&gt;.</p>
</template>
```

```javascript
var importDoc = document.currentScript.ownerDocument;

var proto = Object.create(HTMLElement.prototype, {
  createdCallback: {
    value: function() {
      var t = importDoc.querySelector('#my-template');
      var clone = document.importNode(t.content, true);
      this.createShadowRoot().appendChild(clone);
    }
  }
});

document.registerElement('my-tag', { prototype: proto });
```

-----------------------

```xml
<head>
  <link rel="import" href="shadow-dom-for-import.html">
</head>
<body>
  <my-tag>Nicola</my-tag>
</body>
```

---

##Conclusioni

----

###Le pecche delle tecnologie Web

* Riuso <span class="fragment fade-in" style="color:green">✓</span>
* Estendibilità <span class="fragment fade-in" style="color:green">✓</span>
* Incapsulamento <span class="fragment fade-in" style="color:green">✓</span>
* Modularità <span class="fragment fade-in" style="color:green">✓</span>
* Manutenibilità <span class="fragment fade-in" style="color:green">✓</span>

----

Questo significa che abbiamo risolto tutti i nostri problemi?

![WOW](images/wow.png)

----

![Browser support](images/browser-support.png)

----

Polymer | X-Tag&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

![Polymer](images/polymer.png) ![X-Tag](images/x-tag.png)

----

##My two cents

Web Components + EcmaScript 6

svincolano il progettista di UX dai limiti del browser

----------

<div class="fragment fade-in">
Il futuro del Web passa da loro
<h3>Stay tuned!</h3>
</div>

---

#&lt;thank-you /&gt;

--------------------

|                                              |                                                                         |
|----------------------------------------------|-------------------------------------------------------------------------|
|<i class="fa fa-linkedin-square fa-lg"></i>   |[it.linkedin.com/in/nsanitate](http://it.linkedin.com/in/nsanitate)      |
|<i class="fa fa-twitter-square fa-lg"></i>    |[@n_sanitate](https://twitter.com/n_sanitate)                            |
|<i class="fa fa-google-plus-square fa-lg"></i>|[plus.google.com/+NicolaSanitate](http://plus.google.com/+NicolaSanitate)|
|<i class="fa fa-github-square fa-lg"></i>     |[github.com/nsanitate](https://github.com/nsanitate)                     |

----

##Riferimenti

[hyperakt.com](http://hyperakt.com/items/google-evolution)

[w3.org](http://www.w3c.org)

[html5rocks.com](http://www.html5rocks.com)

[css-trick.com](http://www.css-trick.com)

[webcomponents.org](http://webcomponents.org)

[polymer-project.org](https://www.polymer-project.org)

[x-tags.org](http://x-tags.org)
