## How Angular works

- What the framework is doing under the hood?
- How the *application code* and the *Angular framework code* work together?
  


## Angular Parts

- **Angular compiler**, JIT or AOT, build utility.
- **Angular runtime**, framework code that ships with the application and runs in the browser.


## Angular Declarative Syntax

```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: `
    <h1>
      Welcome to {{ title }}!
    </h1>`,
  styleUrls: ['h1 { font-weight: normal; }']
})
export class AppComponent {
  title = 'Angular is awesome!';
}
```

- Make component development easier.
- *Angular runtime* cannot understand it.
- Must be turned into JavaScript.


## Angular Compiler

![alt text](./images/compiler-steps.png)

- **Angular compiler**
  - jump in the TS compilation process.
  - transform *decorators*, *templates* into TS.
- **TypeScript**
  - type check application code.
  - emit JS *Angular runtime* can execute.


## Invoke ngc

In `package.json` add

```javascript
"scripts": {
  ...
  "compile": "ngc"
},
```

In the `tsconfig.json` generate `d.ts` files

```javascript
"compilerOptions": {
  ...
  "declaration": true,
  ...
}
```

- Compiled code with *factory functions*.
- See instructions *Angular runtime* executes.


## Component Defintion

```javascript
export function View_AppComponent_0(_l) {
  return i1.ovid(0,[
      (_l()(),
      i1.oeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.oted(1, null, ["Welcome to ", "!"]))],
    null,function(_ck, _v) {
      var _co = _v.component;
      var currVal_0 = _co.title;
      _ck(_v, 1, 0, currVal_0);
    });
}
```

- `@angular/compiler` generates instructions *Angular runtime* can understand.
- *Angular runtime* implements those instructions to run the application.


## Full Bootstrap Sequence

- Platform
- Application
- Module


## Application Bootstrap

1. **Module bootstrap**, module setup
2. **Component bootstrap**
    1. View creation
    2. Change detection


## Component Bootstrap

<pre><code class="hljs" data-line-numbers="5" data-trim data-noescape>
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,FormsModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
</code></pre>

- Look for the component to bootstrap.
- Locate the *root element*.
- Instantiate of the *root component*.
- **View Creation** to render the root component:
  - *DOM* is created and *directives* instantiated.


## Factory Functions

```javascript
export function View_AppComponent_0(_l) {
  return i1.ovid(0,[(_l()(),
      i1.oeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.0ted(1, null, ["Welcome to ", "!"]))],
      ...});
}
export function View_AppComponent_Host_0(_l) {
  return i1.ovid(0,[
      (_l()(),i1.oeld(0,0,null,null,1,"app-root",[],null,null,null,View_AppComponent_0,RenderType_AppComponent)),
      i1.odid(1, 49152, null, 0, i2.AppComponent, [], null, null)],null,null);
}
var AppComponentNgFactory = i1.occf(
  "app-root",i2.AppComponent,View_AppComponent_Host_0,{},{},[]);
export { AppComponentNgFactory };
```

- Angular compiler generates *factory functions*.
- A factory function tells runtime how to create a component with its dependencies.
- `directiveInject` powers DI looking for services to inject from directive till `providers` module injectors.


## Component Defintion

<pre><code class="hljs" data-line-numbers="5-11" data-trim data-noescape>
class AppComponent {...}

AppComponent.ngComponentDef =
  defineComponent({
    selectors: [['app-root']],
    factory: function() {
      return new AppComponent();
    },
    template: function(flags, context) {
      ...
    },
    directives: [...]
    ...
  });
</code></pre>

- Invoke factory function to create the DOM for that component.


## Template Factory Function

<pre><code class="hljs" data-trim data-noescape>
function(renderFlags, ctx) {
  if (renderFlags & RenderFlags.Create) {
    elementStart(0, 'h1');
    text(1);
    elementEnd();
  }
  if (renderFlags & RenderFlags.Update) {...}
}
</code></pre>

<pre><code class="hljs" data-trim data-noescape>
export function View_AppComponent_0(_l) {
  return i1.ovid(0,[(_l()(),
      i1.oeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.oted(1, null, ["Welcome to ", "!"]))],
    null,
    function(_ck, _v) {
      var _co = _v.component;
      var currVal_0 = _co.title;
      _ck(_v, 1, 0, currVal_0);
    });
}
</code></pre>


## Template Instructions

- Template function composed by a number of *instructions*.
- *Creation instructions* as `element()`, `text()`, `template()`...
- *Update instructions* as `styleProp()`, `attribute()`...


## Element Instruction

```javascript
function element(index, tag, attrs) {
  const el = document.createElement(tag);
  const parent = getCurrentParent();
  setAttributes(el, attrs);
  parent.appendChild(el);
  // track elements as created
  const lView = getView();
  lView[index] = el;
}
```

- Elements are tracked as created in a *internal data array*.
- In *change detection* the element needs to accessed and updated.
- DOM API is expensive and slow.


## Logical View (LView)

```javascript
LView[<h1>, #txt, ..., *directives]
```

- Internal array *for every component instance* to store.
  - its DOM elements;
  - binding values;
  - directive instances (via component factory with DI).


## Template View (TView)

- Directive maching, `ngFor`, `ngIf`, happens once per component.
- Created per *component type*.
- Share data among all instances of a view.
- A component with 5 instances has 5 LView and 1 TView.
- TView is stored in the `ComponentDef`.


## LView and TView

```javascript
LView[<h1>, #txt, <hello-card>, helloCard]

TView[TNode, TNode, TNode, HelloCard.def]
```

- Push *directive instances* into the LView and *directive definitions* into TView at the same index.
- Push DOM elements into LView and *template nodes* into TView.
- TNode are metadata such as tag name or *directive matching*.
- TNode gives the index or range of indexes that match the node.
- Example: `<hello-card>` is created the first time, then
  - it looks for the TNode,
  - TNode will point to the definition (`HelloCard.def`)
  - it can instatiate immediately instantiate without matching.


## Change Detection

Process where binded value are checked and new values are rendered to the view.


## How It Works

- Similar to component creation.
- Invoke all the template functions down the component tree using the *update flag*.