## Rendering Architecture

- *View Engine (4.0)* has some limitations:
  - no tree-shakable;
  - no incremental compilation.
- *Angular Ivy (9.0)* new compiler and runtime:
  - simplify how Angular works internally;
  - incremental compilation;
  - faster compiles and small bundles.


## Incremental DOM

>Every component gets compiled into a series of instructions.
>These instructions create DOM trees and update them in-place when the data changes.

- [Fast](http://google.github.io/incremental-dom/#why-incremental-dom) **view creation** and **change detection**.
- [Better](https://medium.com/google-developers/introducing-incremental-dom-e98f79ce2c5f) *bundle size* and *memory footprint*.


## Back in time: Angular 2.0

- Represents templates as an *imperative rendering operations list*.
- Angular compiler generates *fast template code*.
- Applications were bigger and bigger.
- Generated template too verbose, too many bytes to bundle.
- Need to represent templates with less overhead.


## Angular 4.0 - View Engine

- Different approach.
- Represents templates as a *data structure*.
- Runtime traverses the data structure to
  - create DOM nodes;
  - execute change detection.
- Optimize template size.


## View Engine Template (8.3.9)

<pre><code class="hljs" data-line-numbers="3-6,9-13" data-trim data-noescape>
export function View_AppComponent_0(_l) {
  return i1.ovid(0,
    [
      (_l()(),
      i1.oeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.oted(1, null, ["Welcome to ", "!"]))
    ],
    null,
    function(_ck, _v) {
      var _co = _v.component;
      var currVal_0 = _co.title;
      _ck(_v, 1, 0, currVal_0);
    }
  );
}
</code></pre>

- *View creation* and *change detection*.
- View Engine can execute it.


## Ivy Replace View Engine

- Backward compatible, compiled application must work.
- Same parts as View Engine:
  - template compiler
  - runtime to render and change detection.


## Ivy Architecture

- Angular decorators get compiled to static fields in the decorated class.
- `@Component` becomes `ngComponentDef` static field.
- Code produced in separate `.ngfactory` files *moved into* component class static fields.
- Template function responsible to render template to DOM and to do change detection.


## Angular Ivy (9.0.0-rc.1)

```javascript
class AppComponent {...}
AppComponent.ngComponentDef =
    defineComponent({
        selectors: [['app-root']],
        factory: function() { return new AppComponent();}
    },
    template: function(flags, context) {
        if (rf & 1) {
            elementStart(0, "div", 0);
            elementStart(1, "h1");
            text(2);
            elementEnd();
            elementEnd();
        } if (rf & 2) {...}
    },
    directives: [...]
  });
```


## Ivy Instruction Set

- View Engine has a *single* template interpreter at runtime.
- **Ivy instruction set** is a *set of rendering functions*
  - like an assembly language for templates.
- Template get compiled into two sequences of instructions:
  - *create:* create and insert elements into the DOM;
  - *update:* change detection.
