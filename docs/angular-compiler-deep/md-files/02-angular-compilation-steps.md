## Compilation steps

![alt text](./images/compiler-steps.png)

- *TypeScript compiler* has 3 steps.
- Angular compiler `ngc` is built on top.
- Add 2 more steps (import `ngfactory`).
- *Angular compiler add generated template TypeScript code.*


## Program Creation

![alt text](./images/compiler-steps.png)

- TypeScript *process* to discover app source files.
- Start from `tsconfig.json`
- Use `import` to discover all the other files.


## Analysis

![alt text](./images/compiler-steps.png)

- Angular compiler takes all the TS files.
- Class by class look for *Angular things* (decorators, etc).
- Gather isolated information (e.g. components but not modules).


## Resolve

![alt text](./images/compiler-steps.png)

- Angular compiler looks again at the whole application.
- Look at things in a larger picture (modules).
- Global decisions and optimizations.


## Type checking

![alt text](./images/compiler-steps.png)

- Ask TypeScript to check any errors:
  - in the application;
  - in the templates (expression validations).


## Emit

![alt text](./images/compiler-steps.png)

- The most expensive code in compilation.
- TypeScript code transformation.
- Generated JavaScript code ready to run in the browser .
- Imperative code added to Angular class
  - template functions to components...