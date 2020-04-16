## Module compilation scope

```javascript
@NgModule({
  declarations: [AppComponent, HelloComponent],
})
export class AppModule {}
```

- Angular way for modular application.
- **Module compilation scope** is the `declarations` properties.
- Angular components used in the templates.
- Developer uses a selector from a library.
- Compiler can _uniquely_ match the component.

## Export compilation scope

```javascript
@NgModule({
  declaration: [HelloComponent],
  exports: [HelloComponent],
})
export class HelloModule {}
```

- The `HelloComponent` is _in_ a module.
- The module makes available a set of components.
- The `Hello` module library implements one component and exports it to the rest of the world.

## Module and export scope

```javascript
@NgModule({
  declarations: [AppComponent],
  imports: [HelloModule],
})
export class AppModule {}
```

- Compiler can
  - _uniquely_ find the component definition;
  - figure out from the template which component is used;
  - generate code and reference accordingly;
  - helps tree-shaker to remove things not referenced.
