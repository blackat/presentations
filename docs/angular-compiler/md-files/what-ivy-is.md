## Ivy

- *View Engine* (4.0), the rendering architecture, has some limitations.
- *Angular Ivy* (9.0) is the new compiler and new runtime to replace View Engine.
- Ivy simplifies how Angular works internally and allows incremental compilation
  - faster compiles and small bundles.


## Angular 2.0

- Research on how to fast create and update the DOM.
- Represents templates as an imperative list of rendering operations.
- Angular compiler generates fast templates code.
- Applications start to be bigger.
- Angular generated template was too verbose, too many bytes to bundles.
- Different approach to represent templates with less overhead.


## Angular 4.0 - View Engine

- Represents templates as a data structure.
- Runtime traveres the data structure to create DOM nodes or execute change detection.
- Optimize template size.


## View Engine Template (8.0)

```javascript
export function View_AppComponent_Host_0(_l) {
  return i1.ɵvid(
    0,
    [
      (_l()(),i1.ɵeld(0,0,null,null,1,"app-root",[],null,null,null,View_AppComponent_0,RenderType_AppComponent)),
      i1.ɵdid(1, 49152, null, 0, i2.AppComponent, [], null, null)
    ],
    null,
    null
  );
}
```

- Part of a View Engine template of a component.


## Ivy Replace View Engine

- Backward compatible, compile and application in Ivy must have the same behavior than View Engine.
- Same parts: template compiler and runtime for rendering and change detection.


## Ivy Architecture

- Angular decorators get compiled to static fields on the types they decorate.
- `@Component` becomes `ngComponentDef` static field.
- Code produced in separate `.ngfactory` files *moved into* component class static fields.
- Static fields meta-data tells runtime how to render and update a component.
- Template function responsible to render template to DOM and to do change detection.


## Ivy Instruction Set

- View Engine has a single template interpreter at runtime.
- Ivy has a set of rendering functions called *Ivy instruction set*, like an assembly language for templates.
- Template get compiled to two sequences of instructions
  - one to create and insert template into the DOM
  - one to run change detection and update.


<!-- 3 main goals for Ivy -->

## Ivy is Full Optimizable

- Ivy helps tree-shaking removing *dead code* from the bundle.
  - Dead code comes from libraries, Angular included.
  - Webpack uglify plugin powers Angular CLI for tree-shaking.
  - Angular Build Optimizer plugin which tells uglifly what Angular code used and what not.
- Ivy is designed to be tree-shaken by optimizers
  - if application does not require internationalization,
  - Angular compiler does not emit those instructions
  - three-shaker does not include them into the bundle.
- Tree-shaker could not optimize/break the View Engine.
  - The Angular framework is three-shakeable.
- In View Engine `Map<Component, ComponentFactory>` is not tree-shakable.
- In Ivy every component is its own factory.
- Metric: HelloWorld application is ~4.5kB, ~2.7kB with Closure Compiler.
  - Angular Elements can be bundled more efficiently.
- Ivy is ready for future bunlder/optimizer.


## Incremental Compilation

- `ng build prod` runs `tsc` and `ngc` which generates `ngfactories` for templates.
  - `ngc` compiles application libraries as well.
- Incremental compilation: libraries are compiled and deployed on npm.
- **Locality** is a *rule* that says when compile and Angular application refers to components and directives public APIs
  - safe to refer to code on npm
  - no need to know much about dependencies, Ivy adds extra information to `.d.ts` files.


## Locality Example

```javascript
@Input('property') field: string;
```

- `property` is the public API name.
- `field` is the private name, an *implementation detail*.
- Writing code against the private name obliged to regenerate the code
  - since it is possible assume every time it may have been changed.
  - for this reason Angular relies on *global compilation*.
- Ivy relies on the public name, so safe to ship code on npm.


## Ivy Flexibility

- New features are introduced in Angular new instructions are implemented in the set.
- Ivy is easier to be extended.
- Ivy is the foundation to have Angular more optimizable and extendedable.


## Ivy Features

- No `.ngfactory` complications.
- Lazy loading without a router.
- Dynamic import  and deployment.