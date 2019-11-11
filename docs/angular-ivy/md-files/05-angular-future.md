## Libraries compiler

- The compilation of an Angular application is just half of the process.
- Libraries, the application depends on, have to be compatible with the *new runtime*.
- `ngcc`, *Angular compatibility compiler*, new compiler to convert and compile the libraries.
- `ViewEngine` libraries to be converted into Ivy instructions.
- *Libraries can participate in the Ivy runtime* and be fully compatible.


## Automatic Conversion

- The new compiler makes libraries compatible with the new engine.
- Maintainers do not have to rewrite important of the libraries.
- Conversion happens during the *build or installation process*.


## Ivy Plan

| Angular version  | ngcc           |
| ---------------- |------------------------------------------------------ |
| 9                |app on Ivy (opt-out) and libraries VE compatible       |
| 10               |stabilize Ivy instruction set, libraries ship Ivy code |
| 11               |`ngcc` backup for obsolete libraries or not updated yet|


## ngcc Validation

- `ngcc-validation` [project](https://github.com/angular/ngcc-validation) to validate compatibilities.


## Lazy Loading

- Ivy is not just about improving the built time and the size.
- Since version 2, component lazy loading just at *router level*. 
- At *component level* requires a lot of boilerplate code and some patches.


## Lazy Loading Example

```javascript
@Component(...)
export class AppComponent{
  constructor(
      private viewContainer: ViewContainer,
      private cfr: ComponentFactoryResolver) {

    // lazy click handler
    async lazyload() {
      // use the dynamic import
      const {LazyComponent} = await import('./lazy/lazy.component');
      this.viewContainer.createComponent(LazyComponent);
    }
  }
}
```

- Click on an image, lazy load the bundle and add the component to the view.


## View Engine Way

```javascript
this.viewContainer.createComponent(this.cfr.resolveComponentFactory(LazyComponent));
```

- Need pass via the `ComponentFactoryResolver` to load the component.


## Bundle size

- *Metric:* HelloWorld application is ~4.5kB, ~2.7kB with Closure Compiler.
- *Angular Elements* can be bundled more efficiently.
- Ivy is ready for future bundler/optimizer.
