## Virtual DOM

<img src="images/virtual-dom.png" alt="Virtual DOM" width="75%"/>

- A JSON object gets manipulated when node added/removed.
- *Diff* algo: transformation sequence for the DOM.
- Msemory footprint, new tree at each change.
- Whole interpreter shipped to the browser.


## Incremental DOM

- Component decorator/template compiled into two *instruction sequences*:
  - **view creation** renders the component the first time;
  - **change detection** updates the component at change detection.
- Component references instructions, easy to *remove from runtime* unused ones.
- [Faster](http://google.github.io/incremental-dom/#why-incremental-dom), [better](https://medium.com/google-developers/introducing-incremental-dom-e98f79ce2c5f) *bundle size* and *memory footprint*.


## View Engine Template (8.2.9)

<pre><code class="hljs" data-line-numbers="3-6,9-13" data-trim data-noescape>
export function View_AppComponent_0(_l) {
  return i1.ovid(0,
    [
      (_l()(),
      i1.oeld(0, 0, null, null, 1, "h1", [], null, null, null, null, null)),
      (_l()(), i1.oted(1, null, ["Welcome to ", "!"]))
    ],
    null,
    function(_ck, _v) {
      var _co = _v.component;
      var currVal_0 = _co.title;
      _ck(_v, 1, 0, currVal_0);
    }
  );
}
</code></pre>

- *View creation* and *change detection*.
- View Engine can execute it.

