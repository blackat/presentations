# Grunt

- Describe how software is built (tasks, plug-ins, order).
- `npm` manages dependencies.
- No predefined phases.
- Phases often depends on the technologies used.
- JavaScript file descriptor runs on nodejs.


## Example of Tasks

```bash
 1  clean
 2  tslint Typescript code
 3  transpile TypeScript into JavaScript
 4  process SCSS (Sassy CSS), an extension of CSS, into CSS
 5  compile AngularJS templates
 6  merge i18n files
 7  minify CSS and JavaScript
 8  inject CSS and JavaScript minified files into `index.html`
 9  execute tests with coverage
10  deployment to repository
```


## Fake Backend

```bash
grunt serve
```

Proxy can help to redirect request to the real backend.