## 1. Tree-shaking

- **Tree-shaking** removes *dead code* from the bundle:
  - dead code comes from libraries, Angular included;
  - *Webpack uglify plugin* powers Angular CLI for tree-shaking;
  - *Angular Build Optimizer plugin* tells uglifly what code used and what not.


## Ivy is Tree-shakeable

- Ivy is designed to be tree-shaken by optimizers.
- If application does not require internationalization Angular compiler
  - not emit those instructions;
  - not include them into the bundle.


## View Engine Not Tree-shakeable

- Tree-shaker could not optimize/break the *View Engine*.
- The `@angular/core` framework is three-shakeable.
- View Engine `Map<Component, ComponentFactory>` is not tree-shakable.
- In Ivy every component **is its own factory**.


## Bundle size

- *Metric:* HelloWorld application is ~4.5kB, ~2.7kB with Closure Compiler.
- Angular Elements can be bundled more efficiently.
- Ivy is ready for future bundler/optimizer.


## 2. Incremental Compilation

- `ng build prod` runs `tsc` and `ngc` which generates `ngfactories` for templates.
- `ngc` compiles *application libraries* as well.
- **Incremental compilation** enables libraries to be compiled and deployed on npm.


## Locality

- *Locality* is a *rule*.
- An Angular application refers to components and directives *public APIs*
  - safe to refer to public API;
  - no need to know much about dependencies;
  - Ivy adds extra information to `.d.ts` files.


## Locality Example

```javascript
@Input('property') field: string;
```

- `property` is the public API name.
- `field` is the private name, an *implementation detail*.
- Writing code against the private name obliged to regenerate the code:
  - assume it may have been changed;
  - Angular must rely on *global compilation*.
- Ivy relies on the *public API*, so safer to ship code on npm.


## 3. Ivy Flexibility

- If new *features* are introduced in Angular
  - new *instructions* are implemented in the set.
- Ivy is easier to be extended.
- Ivy is the foundation to have Angular more optimizable and extendable.


## Ivy Features

- No `.ngfactory` complications.
- Lazy loading without a router.
- Dynamic import and deployment.

// add lazy import