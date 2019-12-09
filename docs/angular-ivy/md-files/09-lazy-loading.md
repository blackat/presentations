## Ivy Enables Lazy Loading

- Ivy is not just about improving the built time and the size.
- Since version 2, component lazy loading just at *router level*. 
- At *component level* requires a lot of boilerplate code and some patches.


## Lazy Loading Example (ideally)

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


## View Engine Why

```javascript
this.viewContainer.createComponent(
    this.cfr.resolveComponentFactory(LazyComponent)
);
```

- Need pass via the `ComponentFactoryResolver` to load the component.