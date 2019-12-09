## 1. Tree-shaking

- Operation to remove **dead code**.
- Not referenced instructions can be omitted from the bundle.
- Smaller bundles.
- *Webpack uglify plugin* powers Angular CLI for tree-shaking
- *Angular Build Optimizer plugin* tells uglifly which code is referenced.


## 2. Locality

- **Global compilation:** currently Angular compiler requires a *global static analysis*.
- All the compilation outputs have to be analyzed.
- Complex to combine AOT libraries into a JIT application.
- Compiler should relies only on decorator and its class.
- Extra metedata information are added to the `*.d.ts` files.


## Locality: public API

```javascript
@Component({
  selector: 'lib-mylib',
  template: `
    <p>Please input your phone</p>
    <input #phone placeholder="phone number" />
  `
})
export class MylibComponent implements OnInit {

  @Input('phone-number') private phone: string;
  ...
}
```

- `phone-number` will be part of the API.
- `phone` is an implementation detail, so the global compilation.
- Ivy compiler relies on public API.


## Locality: public API compiled

```javascript
import { OnInit } from '@angular/core';
import * as i0 from "@angular/core";
export declare class MylibComponent implements OnInit {
    private phone;
    constructor();
    ngOnInit(): void;
    static ofac: i0.ooFactoryDef<MylibComponent>;
    static ocmp: i0.ooComponentDefWithMeta<MylibComponent,
        "lib-mylib", never, { 'phone': "phone-number" }, {}, never>;
}
```

- `phone-number` is part of the public API.
- Ivy compiler relies safely on the public API.


## Input Property

<img src="images/input-property.png" alt="Input property" width="85%"/>


## 3. Incremental Compilation

- `ng build prod` runs `tsc` and `ngc` which generates `ngfactories` for templates.
- `ngc` compiles *application libraries* as well.
- **Incremental compilation** enables libraries to be compiled and deployed on npm.


## 4. Ivy Flexibility

- If new *features* are introduced in Angular
  - new *instructions* are implemented in the set.
- Ivy is easier to be extended.
- Ivy is the foundation to have Angular more optimizable and extendable.
