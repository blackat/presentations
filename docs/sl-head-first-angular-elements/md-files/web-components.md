## Web Components v1

A set of <span class="text-highlight">Web Platform APIs</span> to create new custom, reusable, encapsulated HTML tags that can be used everywhere.

```html
<!doctype html>
<html lang="en">
    <head>
        <title>Custom Component</title>
    </head>
    <body>
        <icon-text></icon-text>
    </body>
</html>
```


## [Web Components][web components] Specs

- <span class="text-highlight">**Custom Elements:**</span> design and use new DOM elements.
- <span class="text-highlight">**Shadow DOM:**</span> encapsulated style and markup in web components, like a scoped subtree inside the Custom Element.
- <span class="text-highlight">**HTML templates:**</span> HTML template element.
- <span class="text-highlight">**HTML Imports:**</span> include and reuse HTML documents.

[web components]:https://developer.mozilla.org/en-US/docs/Web/Web_Components


## Custom Elements Demo

<iframe src="https://stackblitz.com/edit/custom-element-head-first?embed=1&file=index.js" frameborder="0" scrolling="no" width="900" height="500"/>

<!--
## Custom Elements

<img src="images/custom-element-full.png" alt="Simple Custom Element implementation" width="70%"/>
-->


## Shadow DOM

```javascript
const shadowRoot = this.attachShadow({mode: 'open'});
```

Attaches a shadow DOM tree to the specified element and returns a reference to its `ShadowRoot`

- root node of a DOM subtree rendered separately from a document's main DOM tree
- `open` JavaScript can access internal features.


## Attributes: for data in

```html
<!-- Use attributes to pass configuration in. -->
<icon-text
    text-content="craft with passion"
    text-icon="fa-angular">
</icon text>
```

```javascript
class IconText extends HTMLElement {

    // read the text-content element attribute
    const textContent = this.getAttribute('text-content');

    // read the text icon element attribute
    const textIcon = this.getAttribute('text-icon');
}
```


## Attributes: observation

```javascript
class IconText extends HTMLElement {

    // attributeChangedCallback will use this
    static get observedAttributes() {
        return ['text-content'];
    }

    constructor() { ... }

    ...

    attributeChangedCallback(attrName, oldVal, newVal) {
        // do something fancy please
    }
}
```

```javascript
const iconText = document.querySelector('icon-text');
iconText.setAttribute('text-icon', 'rocket');
```


## Properties: getters, setters

```javascript
class IconText extends HTMLElement {

    constructor() {
        this.textContent = this.getAttribute('text-content');
    }

    get textContent() {
        return this.textContent;
    }

    set textContent(value) {
        this.textContent = value;
    }
```

```javascript
const iconText = document.querySelector('icon-text');
iconText.textContent = 'some fancy stuff here';
```


## Events: for data out

```javascript
class IconText extends HTMLElement {

    // Use custom events to pass small information out.
    onTextChange() {
        let event = new CustomEvent(‘onTextChange’,{text});
        this.dispatchEvent(dateChangeEv);
    }
}
```

```javascript
const iconText = document.querySelector('icon-text');

iconText.addEventListener('onTextChange', (text) => { 
    // do something fancy please
})
```


## Lifecycle Hooks: reactions

```javascript
class IconText extends HTMLElement {

    // invoked when element is appended to the DOM
    connectedCallback(){ ... }

    // invoked when element is disconnected to the DOM
    disconnectedCallback(){ ... }

    // invoked when element's attributes is added, removed, changed
    attributeChangedCallback(attrName, oldVal, newVal) { ... }

    // invoked when element is moved to a new document
    adoptedCallback(){ ... }
}
```