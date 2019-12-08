## Libraries compiler

- The compilation of an Angular application is just half of the process.
- Libraries, the application depends on, have to be compatible with the *new runtime*.
- `ngcc`, *Angular compatibility compiler*, new compiler to convert and compile the libraries.
- `ViewEngine` libraries to be converted into Ivy instructions.
- *Libraries can participate in the Ivy runtime* and be fully compatible.


## Automatic Conversion

- The new compiler makes libraries compatible with the new engine.
- Maintainers do not have to rewrite important of the libraries.
- Conversion happens during the *build or installation process*.


## Ivy Plan

| Angular version  | ngcc           |
| ---------------- |------------------------------------------------------ |
| 9                |app on Ivy (opt-out) and libraries VE compatible       |
| 10               |stabilize Ivy instruction set, libraries ship Ivy code |
| 11               |`ngcc` backup for obsolete libraries or not updated yet|


## ngcc Validation

- `ngcc-validation` [project](https://github.com/angular/ngcc-validation) to validate compatibilities.


## Bundle size

- *Metric:* HelloWorld application is ~4.5kB, ~2.7kB with Closure Compiler.
- *Angular Elements* can be bundled more efficiently.
- Ivy is ready for future bundler/optimizer.