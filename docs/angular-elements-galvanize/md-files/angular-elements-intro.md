## Nitty-Gritty

**Angular Elements** <span class="text-highlight">library</span> provides a way to write custom components that can be used <span class="text-highlight">everywhere</span> without any Angular knowledge:
- CMS;
- HTML and Vanilla JavaScript;
- React, Vue, etc;
- legacy AngularJS application instead of the `ngUpdate`.

Note:
just a note


## Angular Elements Are

- <p class="fragment fade-in-then-out">[Angular Components][angular component] packed as [Custom Elements][custom elements].</p>
- <p class="fragment fade-in-then-out">Self-bootstrapping components powered by [Custom Elements][custom elements].</p>
- <p class="fragment fade-in-then-out">[Angular Component][angular component] on the inside, standards on the outside. (Rob Wormald).</p>
- <p class="fragment fade-in-then-out">[Angular Components][angular component] glued together with [Custom Elements][custom elements], kinda like Custom Elements on steroids (Pascal Precht).</p>

<!-- References -->
[custom elements]: https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements
[web components]: https://developer.mozilla.org/en-US/docs/Web/Web_Components
[angular component]: https://angular.io/guide/architecture-components
[web technologies]: https://developer.mozilla.org/en-US/docs/Web


## Registration at Glance

<img src="images/custom-element-sequence.png" alt="Custom Element at glance">

[angular.io](https://angular.io/guide/elements)

Note:
- in the directive world, AngularJS renders the custom component
- in the custom elements world must be the browser, register and use