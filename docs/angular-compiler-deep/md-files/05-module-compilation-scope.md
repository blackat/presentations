## Module compilation scope

```javascript
@NgModule({
    declarations: [
        AppComponent,
        HelloComponent
    ]
})
export class AppModule {}
```

- Developer uses a selector from a library.
- Compiler has to *uniquely* match the component.
- `NgModule` holds component declarations usable in app templates.
- **Module compilation scope** is this set of components.



## Export compilation scope

```javascript
@NgModule({
    declaration: [HelloComponent],
    exports: [HelloComponent]
})
export class HelloModule {}
```

- The `HelloComponent` is in a module.
- The module makes available a set of components.


## Module and export scope

```javascript
@NgModule({
    declarations: [AppComponent],
    imports: [HelloModule]
})
export class AppModule {}
```

- Compiler can
  - *uniquely* find the component definition;
  - figure out from the template which component is used;
  - generate code and reference accordingly;
  - helps tree-shaker to remove things not referenced.