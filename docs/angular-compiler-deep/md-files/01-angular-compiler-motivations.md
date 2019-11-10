
> Why does Angular have a compiler at all? - Alex Richabaugh

- The Angular compiler turns the template into code *runtime* can execute.
- At runtime, generated JavaScript code
  - render elements
  - update elements (change detection).


## Declarative templates

```javascript
@Component({
  selector: "app-root",
  template: `
    <div style="text-align:center">
      <h1> Welcome to {{ title }}!</h1>
    </div>
    <input [(ngModel)]="title">`,
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


## JIT vs. AoT

- **JIT:** imperative code is generated at *runtime*
  - compiler comes with the application
  - mainly for development
- **AoT:** imperative code is generated at *built time*
  - execution is faster
  - build slower
  - mainly for production
