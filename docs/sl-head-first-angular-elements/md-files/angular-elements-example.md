## Angular Elements Example

- Install Angular CLI and scaffold a new project.
```bash
npm install -g @angular/cli@latest
ng new angular-geometry-elements
cd angular-geometry-elements
```

- Add both Angular Elements and the polyfill called [document-register-element](https://github.com/WebReflection/document-register-element) to the configuration file `angular.json`.

```bash
ng add @angular/elements --project=angular-geometry-elements
```


## @Component - the code

<img src="images/geometry-element.png" alt="Angular component" width="75%"/>


## @Component - the detail

- `ViewEncapulation.native` to use the real Shadow DOM if natively available.
- `bootstrap` renamed to `entryComponents` in the `app.module.ts`
- the selector won't be used


## @NgModule - the code
<img src="images/angular-elements-module.png" alt="Angular component module" width="58%"/>


## @NgModule - the detail

```javascript
constructor(private injector: Injector) {
  const el = createCustomElement(AppComponent, {injector});
  customElements.define('geometry-elements', el);
}
```

- returns a special class that can be used with the Custom Element Web API to define a new custom element
- register the Angular Component as Custom Element.


## Creation at Glance

<img src="images/create-element-sequence.png" alt="How to create a Custom Element in Angular">

[angular.io](https://angular.io/guide/elements)


## Build and Pack 1

- No straight forward way to pack an Angular Element component.
- Different approaches, simplest one proposed by Sebastian Eschweiler.

```bash
npm install --save-dev concat fs-extra
```

- use the script `elements-build.js` proposed by [@samjulien](https://twitter.com/samjulien)


## Build and Pack 2

- add new script to `package.json` scripts.

```json
"build:elements": "ng build --prod --output-hashing none && node elements-build.js"
```

- build

```bash
npm run build:elements
```


## Test the Custom Element

```html
  <body>

    <geometry-elements id="el" default-value="circle">
    </geometry-elements>

    <script type="text/javascript" src="geometry-elements.js">
    </script>
    <script>
      document.getElementById("el").addEventListener(
          "selectedValue", function(value){
        alert("Output from the component " + 
            JSON.stringify(value.detail));
      })
    </script>
  </body>
```


## Check the Registration

```javascript
String.prototype.wasRegistered = function() { 
  switch(document.createElement(this).constructor) {
    case HTMLElement: return false; 
    case HTMLUnknownElement: return undefined; 
  }
  return true;
}
```

```javascript
'geometry-element'.wasRegistered()
```