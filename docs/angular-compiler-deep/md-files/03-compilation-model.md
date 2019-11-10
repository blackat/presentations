## TS Compilation model

- `library.ts` compiled into `library.js`
- JavaScript code:
  - has not type information;
  - ready to be executed in the browser.
- `library.d.ts` type declaration file:
  - describe the *interface* or *public API*.


## Definition file

- `app.ts` imports a library from npm

```javascript
import {AwesomeLib} from 'awesome-lib';
// use the lib
```

- `library.d.ts` brings *type information*.

```javascript
declare class AwesomeLib {
    awesomeMethod(): string;
}
```

- TypeScript can static type check.


## <i class="fab fa-angular angular-logo-medium"></i> Compilation Model

Angular component

```javascript
@Component({
    selector: 'awesome-comp'
})
export class AwesomeComponent {
    @Input() value: string;
}
```

Component definition file (Ivy)

```javascript
export declare class AwsomeComponent() {
    value: string;
    static ngComponentDef: ng.ComponentDef<
        AwsomeComponent,
        `awesome-comp`,
        {value: 'value'}
    >;
}
```


## Definition file changed

- Similar to the TypeScript one.
- `library.d.ts` file changed: selectors, inputs...
  - component public API;
  - compiler can use the component.


## Template checking

- Compiler knows the component is an *instance* of what is in the library.
- Template uses component from library.

```html
<awesome-comp [value]="a value">
    just a component
</awesome-comp>
```

```javascript
export declare class AwesomeComponent() {
    value: string;
    static ngComponentDef: ng.ComponentDef<
        AwesomeComponent,
        `awesome-comp`,
        {value: 'value'}>;
}
```
