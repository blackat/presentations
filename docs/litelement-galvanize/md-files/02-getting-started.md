# Getting Started

- Install Node.js version 8 or later, consider `nvm`, Node Version Manager.
- For [Windows 10](https://polymer-library.polymer-project.org/3.0/docs/tools/polymer-cli#windows-10) consider to install WSL and a Linux distro, then `bash` prompt.
- Otheriwse use a [Stackblitz](https://stackblitz.com/edit/polymer-element-example?file=index.js) starter project.
- `npm install -g polymer-cli`

<--->

# Element project

- `mkdir litelement-row-block-poc && cd litelement-row-block-poc`
- `npm install lit-element`
- `npm install @webcomponents/webcomponentsjs`
- `touch litelement-row-block.js`

<--->

# Live demo

```bash
polymer serve
```

[Click to galvanize](http://127.0.0.1:8081/components/litelement-polymer-row-block-poc/demo/)

<--->

# Tools

Use bundler (Webpack or Rollup) and/or a transpiler to build for production the element.
