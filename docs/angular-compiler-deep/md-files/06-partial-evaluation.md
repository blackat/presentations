## Partial evaluation

> "Compiler actually attempt to almost run TypeScript code in decorators" - Alex Rickabaugh


## Compiler can follow references

```javascript
import {SOME_MODULES} from './some_module';

@NgModule({
    declarations: [HelloComponent, ByeComponent],
    exports: [HelloComponent, ByeComponent],
    imports: [...SOME_MODULES]
})
```

- Angular compiler contains almost a complete *TypeScript interpreter*.
- *Partial evaluation* compiler can *follow/evaluate* import references.


## Something that does not exist

```javascript
import {SOME_MODULES} from './some_module';

@NgModule({
    imports: [SOME_MODULES.modules]
})
```

```javascript
export const SOME_MODULES = {
    modules: [HelloModule, ByeModule],

    // not available at compile time
    viewportSize: {
        x: document.body.scrollWidth,
        y: document.body.scrollHeight
    }
}
```

- Some values are only available *at runtime*.


## Dynamic expressions

```javascript
SOME_MODULES: {
    "modules": [
        Reference(HelloModule),
        Reference(ByeModule)
    ],
    "viewportSize": {
        x: DynamicValue(document.body.scrollWidth),
        y: DynamicValue(document.body.scrollHeight)
    }
}
```

- `SOME_MODULES` an object with 2 properties.
- `DynamicValue` is an indicator to say *cannot get past*.


## Compilation goes on

```javascript
import {SOME_MODULES} from './some_module'
@Component({
    styles: [`
        :host {
            width: $SOME_MODULES.viewportSize.x
        }
    `]
})
```

- Compilation
  - goes on for `modules` properties;
  - *do not work* for `viewportSize`, the value cannot figured out;
  - an explicative error message is produced about styles.
