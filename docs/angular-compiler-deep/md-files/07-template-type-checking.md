## Template type checking

```html
<account-view
    [account]="getAccount(user.id, 'primary') | async">
</account-view
```

- Template are written in Angular template syntax.
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


## Example ngc

```javascript
...
"angularCompilerOptions": {
    "fullTemplateTypeCheck": true,
    "strictTemplates": true,
    ...
}
```

```javascript
src/app/app.component.html:7:13 - error NG2339: Property 'name' does not exist on type 'string'.

7       <td>{{hero.name}}</td>
              ~~~~~~~~~

  src/app/app.component.ts:5:16
    5   templateUrl: './app.component.html',
                     ~~~~~~~~~~~~~~~~~~~~~~
    Error occurs in the template of component AppComponent.
```