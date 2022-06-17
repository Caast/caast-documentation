# Targetting DOM

By default Caast Library will look on your HTML for a DOM node with the id `caast-wrapper`, but maybe you don't want or cannot change your page HTML. To allow you a smooth integration, Caast Library can be loaded into any DOM element on your page. To change the default behaviour simply go to your dashboard and go into the configuration section of your project.

On the configuration object, you will notice this particular section:

```json
"target": {
  "element": "#caast-wrapper",
  "position": "beforeend",
  "overwrite": false
}
```

- The `element` section is the DOM node where you want the widget to be loaded, it can be a class name or and id but also a really specific selector like `#product-tab li:nth-child(3)`, be sure to try specific selector on your javascript console before using them on production.
- The `overwrite` section is to specify if Caast will replace all the content that is inside the `element`, if you set this option on `true`, the position option will be ignored.
- The `position` section is to specify where you want to insert the Caast widget around your `element`. Those values can be :

| Value           | Description                                      |
| --------------- | ------------------------------------------------ |
| **beforebegin** | Before the element itself                        |
| **afterbegin**  | Just inside the element, before its first child. |
| **beforeend**   | Just inside the element, after its last child.   |
| **afterend**    | After the element itself.                        |

This code can help you to better understand this behaviour

```html
<!-- beforebegin -->
<div id="caast-wrapper">
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</div>
<!-- afterend -->
```
