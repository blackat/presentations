## Welcome to Angular

```javascript
@Component({
  selector: 'app-root',
  template: `
    <div style="text-align:center">
      <h1>
        Welcome to {{title}}!
      </h1>
    </div>`,
  styleUrls: []
})
export class AppComponent {
  @Input() title = 'Angular!';
}
```

```bash
$ ng build  // aot activated by default
```


## Compiled Component

```javascript
AppComponent.ngComponentDef = defineComponent({
        selectors: [['app-root']],
        factory: function() { return new AppComponent();}
    },
    template: function(flags, context) {
        if (flags & 1) {
            elementStart(0, "div", 0);
            elementStart(1, "h1");
            text(2);
            elementEnd();
            elementEnd();
        } if (flags & 2) {...}
    },
    directives: [...]
  });
```

- Decorators get compiled into **static fields**.
- Compiled code is into static fields.


## Knowns at Compile Time

<img src="images/incremental-dom.png" alt="Virtual DOM" width="75%"/>

- Every component is *its own factory*.
- Runtime does *not interpret* the component.
- Ivy runtime is an instruction set like ASM for templates.