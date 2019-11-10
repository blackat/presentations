## Custom Elements Typings

```javascript
const anchor: HTMLAnchorElement = document.createElement('a');

const geometryElement: HTMLElement = 
            document.getElementById('geometry-element');
```

- The correct type cannot be inferred, hence the generic type `HTMLElement` is returned.
- Static type checking and auto-complete does not work very well.


## Get Accurate Typings - Cast

```javascript
const geometryElement: HTMLElement = 
            document.getElementById('geometry-element')
            as NgElement & 
            WithProperties<{defaultValue: string}>;

geometryElement.defaultValue = 'circle';
```

Easy fix but awful if type required in different places.


## Get Accurate Typings - Global

```javascript
declare global {
  interface HTMLElementTagNameMap {
    'geometry-element': NgElement & WithProperties<{defaultValue: string}>;
  }
}
```

Augment the `HTMLELementTagNameMap`, used by TypeScript to infer the type of a returned element based on its tag name such as `document.createElement()` and `document.querySelector()`.