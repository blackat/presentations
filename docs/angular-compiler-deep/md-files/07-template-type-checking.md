## Template type checking

```html
<account-view
    [account]="getAccount(user.id, 'primary') | async">
</account-view
```

- Template are written in HTML.
- Templates and expressions are transformed into **type check blocks**, blocks of TypeScript code.
- Block are sent to TypeScript compiler.
- Returned errors are presented in the context of the template.


## Example

```javascript
fucntion typeCheckBlock(ctx: AppComponent) {
    let cmp!: AccountViewCmp;
    let pipe!: ng.AsyncPipe;

    cmp.account /*273,356*/ = (pipe.transform(
        ctx.getAccount((ctx.user /*311,315*/).id /*311,318*/,
        "primary" /*320,329*/)
        /*300,331*/)
    /*300,338*/) /*289,339*/;
}
```

- Translated code plus *offset comments*.
- Offsets allow to return the error in the context of the HTML template.
- Ivy has improved the error contextualization even in external templates.
