# Custom Element

```javascript
import {PolymerElement} from '@polymer/polymer/polymer-element.js';

 export class PolymerRowBlock extends PolymerElement {
    static get properties() {
        return {...}
    }

    static get template() {
        return html`
            <style></style>
            <!-- template content -->`;
    }
 }
 customElements.define('polymer-row-block', PolymerRowBlock);
```

```html
<script type="module" src="./my-polymer-element.js">
```

<--->

# base class

- `PolymerElement` Extends `HTMLElement`.
- Automatic properties/attributes setter and getter.
- Create shadow DOM tree from the template.
- <span class="text-highlight">**Data system**</span>
  - data binding
  - property change observers
  - computed properties.

<--->

# VS.

- Vanilla Custom Element

```javascript
class RowBlock extends HTMLElement { ... }
```

- Polymer Custom Element

```javascript
class PolymerRowBlock extends PolymerElement { ... }
```

<--->

# Deserializers

- Based on defined `properties` and their types.
- Custom deserializers can be written.
- Better than pass just a string (HTML5 attributes):
  - `"[{title: \"easy\", value: \"2\"}]";`

```html
<polymer-row-block
  title="Polymer Row Block"
  columns='[{"title": "one", "value": "1"}, {"title": "two", "value": "2"}]'
>
</polymer-row-block>
```

<--->

# Shadow DOM

- <span class="text-highlight">**Scoped subtree**</span> inside the custom element.
- <span class="text-highlight">**Shadow tree**</span> elements can't be restyled.

```html
<my-header>
  #shadow-root
  <header>
    <h1>
      <button></button>
    </h1>
  </header>
</my-header>
```

<--->

# Declarative

```javascript
static get template() {
    return html`
        <!-- Begin shadow tree -->
        <style>...</style>
        <div class="row-block-title">{{ title }}</div>
        <dom-repeat items="{{columns}}">
            <template>
                ...
            </template>
        </dom-repeat>
        <!-- End shadow tree -->
    `;
  }
```
