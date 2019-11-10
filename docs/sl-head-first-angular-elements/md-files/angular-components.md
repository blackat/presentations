## Angular Components

How <span class="text-highlight">**Custom Elements**</span> are implemented in Angular.

```html
<app-root>
    <some-fancy-component>
        [attr.role]="aCoolExpression"
        [aProperty]="aProperty"
        (anEvent)="doSomethingPlease()">
    </some-fancy-component>
</app-root>
```


## Angular Components &#8594; CE

| Angular Component            | Custom Element                 |
| ---------------------------- | ------------------------------ |
| `@Input`                     | properties                     |
| `@Output`                    | events                         |
| `@HostBinding/@HostListener` | attributes/observed attributes |
| lifecycle hooks              | lifecycle hooks                |

Note:
- How to implement a component w.r.t. the standard platform API
- How a parent and a child can interact
- How to **interact** with a web component: input, output, reactions
    - common component comunication, how to share information among components
    - `@Input` decorator: **parent pass data to child** with input binding
        - @Input and @Input('givemesome') with alias component property
        - input property setter to intercept a value from the parent
        - intercept input property changes with `ngOnChanges()`, detect changes upon the input property value, from lifecycle hook interface `OnChanges`
    - lifecycle managed by Angular, lifecycle hook interface from the core library
        - `OnInit`, `OnChanges`
    - `@Output` decorator: **parent listens for child event**
        - child `EventEmitter` property is an output property
    - Parent interacts with child via local variable
        - A parent component cannot use data binding to read child properties or invoke child methods.
        - local variable, `#timer`, for instance
```html
<button (click)="timer.start()">Start</button>
<button (click)="timer.stop()">Stop</button>
<div class="seconds">{{timer.seconds}}</div>
<app-countdown-timer #timer></app-countdown-timer>
```
- `@HostBinding` bind to input properties in the host element
    - directive can change the properties of the host element
    - a directive can link an internal property to an input property on the host element
    - bind to input properties on our host element
- `@HostBinding`, `@HostListener` CE Attributes / ObserveredAttributes
    - `@HostListener` listening to output events from the host element
    - `@HostBinding` bind to input properties in the host element
        - only way to set the CSS class to the host element within the component.
        - “@HostBinding decorator, we’re able to configure our host element from within the component.”