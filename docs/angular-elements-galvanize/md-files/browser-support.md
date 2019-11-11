## Browser Support
Native browser support for Custom Elements has been not fully implemented everywhere.

<a href="https://caniuse.com/#feat=custom-elementsv1" data-preview-link>Custom Elements v1</a>

- [Chrome 54](https://www.chromestatus.com/features/4696261944934400) has Custom Elements v1;
- [Safari 10.1](https://webkit.org/status/#feature-custom-elements) has Custom Elements v1;
- [Edge](https://twitter.com/AaronGustafson/status/717028669948977153) has begun prototyping;
- [Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=889230) target is v63;


## Latest News (29/08/18)

<img src="images/browser-support.jpeg">


## IE 11
<img src="images/ie11.jpg" alt="Internet Explorer 11" width="20%"/>

- `"target": "es5"`
- `encapsulation: ViewEncapsulation.Native` Shadow DOM polyfill required
- `"document-register-element": "1.8.1"`


## Web Components Polyfills
> Some browsers are still in the process of updating to support the standards for Web Components. In the mean time, [polyfills](https://www.webcomponents.org/polyfills/) simulate the missing browser capabilities as closely as possible.

<a target="_blank" rel="noopener noreferrer" href="https://github.com/webcomponents">Web Components Github repo</a>



## Feature Detect

<img src="images/detect.png" alt="Feature detect" width="50%"/>

- <span class="text-highlight">Feature-detect</span> for the necessary browser features before loading the polyfills.
- Reduce the payload to run an application more and more the Browser implements Web Components.