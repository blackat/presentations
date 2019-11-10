# Custom Element

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

# base class

- `LitElement` is the base class.
- Automatic properties/attributes setter and getter.
- Create shadow DOM tree from the template.
- Data binding, Property change observers, Computed properties.
- TypeScript decorators: `@customElement`, `@property`, etc. also availbale.

<--->

# VS.

- Polymer Custom Element

```html
<dom-repeat items="{{foo}}"></dom-repeat>
```

- LitElement Custom Element

```javascript
const items = this.foo.map(
  item =>
    html`
      <span>${item.prop}</span>
    `
);

return html`
  Item List: ${items}
`;
```

<--->

# Deserializers

- Based on defined `properties` and their types.
- Custom deserializers can be written.
- Better than pass just a string (HTML5 attributes):
  - `"[{title: \"easy\", value: \"2\"}]";`

```html
<lit-row-block
  title="LitElement Row Block"
  columns='[{"title": "one", "value": "1"}, {"title": "two", "value": "2"}]'
>
</lit-row-block>
```

<--->

# Styles

```javascript
static get styles() {
    return css`
      .row-block {
        padding: 10px;
        margin: 10px;
        background: whitesmoke;
      }

      .row-block-column {
        margin: 10px;
        display: inline-block;
      }

      .row-block-column-title {
        font-weight: bold;
      }
    `;
  }
```
