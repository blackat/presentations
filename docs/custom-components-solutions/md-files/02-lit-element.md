# LitElement

- **Core concepts** -
  - Extends the `LitElement` class.
  - `LitElement` extends `HTMLElement` class.
  - Templating, data-binding, attribute deserialization, property change observation.
  - Easier the standard Web Component.
  - Directly develop a custom element.
  - <a href="../sl-litelement-galvanize/" target="_blank">More...</a>

<--->

# Example

```javascript
import { LitElement, html } from "lit-element";

// Extend the LitElement base class
class LitElementRowBlock extends LitElement {
  static get properties() {
    return {...}
  }
  render() {
    return html`
      <!-- template content -->
      <p>A paragraph</p>
    `;
  }
}
// Register the new element with the browser.
customElements.define("lit-row-block", LitElementRowBlock);
```

```html
<script type="module" src="./litelement-row-block.js">
```

<--->

# Deserializers

```html
<lit-row-block
  title="LitElement Row Block"
  columns='[{"title": "one", "value": "1"}, {"title": "two", "value": "2"}]'
>
</lit-row-block>
```

- Based on type properties.
- Support custom deserializer.
