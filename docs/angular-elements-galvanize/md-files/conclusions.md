## Conclusions: cross browser

- polyfills do not always simulate the expected behavior
- not all the polyfills are the same <span class="emoji-steam-face"/>
- `CSS` loading issues in the Shadow DOM
- still not possible to unregister a custom element <span class="emoji-angry-face"/>


## Conclusions: worflow

- packing is not really straightforward as the all implementation cycle
- size is bigger than expected (303 KB), Ivy should solve the issue
- specific design is part of the component (Material, Bootstrap)


## Conclusions: binding

```html
<script>
    document.getElementById("el").addEventListener("selectedValue", function(value) {
        alert("Output from the component " + 
            JSON.stringify(value.detail));
      });
</script>
```

- parent/child component interactions more verbose
- do you really need to share your components?