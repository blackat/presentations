> Why does Angular have a compiler at all? - Alex Richabaugh

- The Angular compiler turns the *template declarative syntax* into *imperative code*.
- Template declares *what* to render but not *how* to
  - render elements
  - update elements (change detection).


## Declarative templates

```javascript
@Component({
  selector: "app-root",
  template: `
    <div style="text-align:center">
      <h1> Welcome to {{ title }}!</h1>
    </div>`,
  styleUrls: [...]
})
export class AppComponent {
    @Input() title = "Angular!";
}
```

- *Angular declarative syntax* to write HTML, bindings, etc.
- Compiler provides *change detection mechanism*.


## Imperative code

- **Angular compiler** transforms the template into *imperative code*.
- **Angular runtime** executes the application code.
- Less boilerplate code.
- Optimizations follow browser evolution.


## Angular compiler overview

- `@angular/compiler-cli`: TypeScript transformer pipeline which includes two CLI tools
  - `ngtsc`: Angular TypeScript compiler, substitutes Angular decorators with Angular runtime instructions, e.g.: `@Component` with `00defineComponent`.
  - `ngcc`: Angular Compatibility Compiler, converts pre-ivy modules into ivy ones, can work on-the-fly as well via Webpack.
- `@angular/compiler`: Angular Ivy Compiler.
- `@angular/core`: Angular decorators.


## Angular Ivy compiler model

- Ivy model foresees to compile Angular decorators into `static properties`.
- Decorators not need global knowledge of the application except for `@Component`.
- `@Component` required information coming from `@NgModule`.
- *Transitive closure* of the exports of that module imports, so the selectors used by the component template.


## Compiler enables decoupling

- Compiler enable to decouple the *what* from the *how*.
- Browsers change quite often so the *how* template are rendered should change to have better performance.
- Templates and decorators can be compiled differently w.r.t. ES5, ES6, etc.
- Rendering architecture can evolve with null or small changes on application side.


## Let's compile

```bash
npm install -g @angular/cli     // to install the Angular CLI
ng new angular-nine-ivy         // or the name you want
```

```javascript
"scripts": {
    "ng": "ng",
    ...
    "ngc": "ngc"
}
```

With Ivy enabled `ngtsc` behaves like `ngc`.


## Decorators into static properties

```javascript
AppComponent.0fac = function AppComponent_Factory(t) { return new (t || AppComponent)(); };
AppComponent.0cmp = i0.00defineComponent({
  type: AppComponent, selectors: [["app-root"]],
  inputs: { title: "title" }, decls: 3, vars: 1, consts: [[2, "text-align", "center"]],
  template: function AppComponent_Template(rf, ctx) { if (rf & 1) {
        i0.00elementStart(0, "div", 0);
        i0.00elementStart(1, "h1");
        i0.00text(2);
        i0.00elementEnd();
        i0.00elementEnd();
    } if (rf & 2) {
        i0.00advance(2);
        i0.00textInterpolate1(" Welcome to ", ctx.title, " ");
    } }, styles: [""] });
/*@__PURE__*/ (function () { i0.0setClassMetadata(AppComponent, [{
        type: Component,
        args: [{
                selector: 'app-root',
                template: `
    <div style="text-align:center">
      <h1>
        Welcome to {{ title }}
      </h1>
    </div>
  `,
                styleUrls: ['./app.component.css']
            }]
    }], null, { title: [{
            type: Input
        }] }); })();
```

## app.component.d.ts

```javascript
import * as i0 from "@angular/core";
export declare class AppComponent {
  title: string;
  static ɵfac: i0.00FactoryDef<AppComponent>;
  static ɵcmp: i0.00ComponentDefWithMeta<AppComponent, "app-root", never, { "title": "title";}, {}, never>;
}
```

This is the public API of the component.