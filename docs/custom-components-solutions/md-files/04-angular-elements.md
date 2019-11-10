# Angular Elements

- **Core concepts**
  - Angular components _transformed_ into custom elements.
  - Transformation produces `NgElement` that extends `HTMLElement`.
  - Registration of the custom components.

<--->

# Implementation

```javascript
@NgModule({
  declarations: [PocLibraryComponent],
  imports: [],
  exports: [PocLibraryComponent],
  entryComponents: [PocLibraryComponent]
})
export class PocLibraryModule {
  constructor(private injector: Injector) {
    const element = createCustomElement(PocLibraryComponent, {
      injector
    });

    customElements.define('poc-element', element);
  }
}
```

<--->

# MonoRepo

- Create application and library.
- Render the component in the application.
- `"builder": "@angular-devkit/build-ng-packagr:build"`
- No way to build as custom elements.
- Only the application project support the build:
  - `"builder": "@angular-devkit/build-angular:browser"`

<--->

# Modified App

- Change the generated application.
- Add transformation and registration.
- Remove `bootstrap` and add `entryComponent`.
- Tweak the build to bundle the custom components.
- Use what tranformed by `createCustomElement`.
- <a href="../sl-head-first-angular-elements/" target="_blank">More...</a>

<--->

# 2 Apps

- One to boostrap.
- One to define custom elements.
- Is it possible to import Angular components?
- Not a clean solution.
- `import * from main.bundle.app1.js`

<--->

# Angular Example

- Angular component started in [2 manners](https://angular.io/guide/elements).
- Boilerplate code in the service.
- How to build the final library?

# Waiting

- [Feature request](https://github.com/angular/angular-cli/issues/13999).
- Solution a la Vue
  - create a library
  - mutliple bundles
  - use in Angular app as Angular component
  - use elsewhere as custom component

# Angular 8

- Ivy elements wrap Angular components as custom element.
