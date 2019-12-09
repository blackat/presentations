## Debugging

<img src="images/ivy-debug-01.png" alt="Input property" width="85%"/>

- New API added to the global object `ng`.


## Element $0

<img src="images/ivy-debug-02.png" alt="Input property" width="85%"/>


## Material Example

```javascript
// grab the component instance of the DOM element stored in $0
let matDrawer = ng.getComponent($0);

// interact with the component's API
matDrawer.toggle();

// trigger change detection on the component
ng.markDirty(matDrawer);
```

- Taken from [Juri Strumpflohner blog](https://juristr.com/blog/2019/09/debugging-angular-ivy-console/)