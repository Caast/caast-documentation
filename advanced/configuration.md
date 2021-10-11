## Targetting DOM injection

By default Caast Library will look on your HTML for a DOM node with the id `caast__wrapper`, but maybe you don't want or cannot change your page HTML. To allow you a smooth integration, Caast Library can be loaded into any DOM element on your page. To change the default behaviour simply go to your dashboard and go into the configuration section of your project.

On the configuration object, you will notice this particular section:

```json
"target": {
  "element": "#caast__wrapper",
  "position": "beforeend"
}
```

- The `element` section is the DOM node where you want the widget to be loaded, it can be a class name or and id but also a really specific selector like `#product-tab li:nth-child(3)`, be sure to try specific selector on your javascript console before using them on production.
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
<div id="caast__wrapper">
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</div>
<!-- afterend -->
```

## Trigger Library with url hash

In order to trigger some specific actions on the Caast Library, you can also add hash parameters to your urls in order to programmatically execute some of the widget functionalities. There is a default configuration for each of those hash naming but **you can also customize each naming via our administration interface** by editing those keys :

```javascript
"hash": {
  "question": "caast-question",
  "jump": "caast-jump",
  "open": "caast-open"
}
```

In order to trigger specific actions, you must pass some required data. You can find here all the necessary parameters.

| Default parameter name                       | Action                                                                                          |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| caast-open/**LIVE_UID**                      | Open Caast Library modal. UID can be optionnal but the event will open the first live available |
| caast-question/**LIVE_UID**/**QUESTION_UID** | Open Caast Library modal and jump to specific question UID                                      |
| caast-jump/**LIVE_UID**/**SECONDS**          | Open Caast Library modal and jump to specified seconds                                          |

So let's say you add `#caast-open` to your URL, resulting with an URL like this one `https://mywebsite.com/product/my-product#caast-open/f20aa128931a449b9478f5fb69e07c3b`, and the Caast Library Modal will magically open.

[How to find my live UID ?](advanced/find-live-uid.md)

[How to find my question UID ?](advanced/find-question-uid.md)
