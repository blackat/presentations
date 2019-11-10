# Getting Started

- Install Node.js version 8 or later, consider `nvm`, Node Version Manager.
- For [Windows 10](https://polymer-library.polymer-project.org/3.0/docs/tools/polymer-cli#windows-10) consider to install WSL and a Linux distro, then `bash` prompt.
- Otheriwse use a [Stackblitz](https://stackblitz.com/edit/polymer-element-example?file=index.js) starter project.
- `npm install -g polymer-cli`

<--->

# Element project

- `mkdir polymer-row-block-poc && cd polymer-row-block-poc`
- `polymer init`
- Select `polymer-3-element`.

```bash
README.md
demo/index.html #demo of the element
index.html #generated API reference
node_modules
package-lock.json
package.json #configuration file for the Polymwer CLI
polymer-row-block.js #element source code
polymer.json #configuration of the Polymer CLI
test #unit tests for the element
```

<--->

# Live demo

```bash
polymer serve
```

[Click to galvanize](http://127.0.0.1:8081/components/polymer-row-block/demo/)

<--->

# Plymer tools & Co.

- [Polymer CLI](https://polymer-library.polymer-project.org/3.0/docs/tools/polymer-cli): serve, test, init new projects.
- [polymer.json](https://polymer-library.polymer-project.org/3.0/docs/tools/polymer-json): configure Polymer project and build.
- [Web Component Tester](https://polymer-library.polymer-project.org/3.0/docs/tools/tests): end-to-end testing environment by Polymer team.
- [Polymer Decorators](https://github.com/Polymer/polymer-decorators): TypeScript decorators for Polymer.
- [Polymer Bunlder](https://github.com/Polymer/tools/tree/master/packages/bundler): packaging library for production.
- [Polymer Tools Monorepo](https://github.com/Polymer/tools): all the available tools.
