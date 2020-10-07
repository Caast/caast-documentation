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

In order to trigger some specific actions on the Caast Library, you can also add hash parameters to your urls in order to programmatically execute some of the widget functionalities. There is a default configuration for each of those hash naming but **you can also customize each naming via our administration interface**.

| Default parameter name  | Action                                                 |
| ----------------------- | ------------------------------------------------------ |
| caast-open              | Open Caast Library modal if available on page          |
| caast-question\_**ID**  | Open Caast Library modal and jump to question ID       |
| caast-jump\_**SECONDS** | Open Caast Library modal and jump to specified seconds |

So let's say you add `#caast-open` to your URL, resulting with an URL like this one `https://mywebsite.com/product/my-product#caast-open`, and the Caast Library Modal will magically open.

## Mails

Caast allow you to send email when a user decide to be notified of an incoming live. Those email are totally customizable and inherits some variables to allow you to deliver dynamic contents.

We use Liquid powered by Shopify for templating. You can find more informations about use of variables, filters on this [link](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

The reminder mail expose those variables:

```json
{
  "receiver": {
    "mail": "Mail of user who receive mail"
  },
  "live": {
    "name": "Name of live",
    "description": "Description of live",
    "start_date_full": "Start date formated like this %d/%m/%y %H:%M",
    "start_time": "Start date hours formated like this %H:%M",
    "start_date": "Start date formated like this %d/%m/%y",
    "thumbnail_url": "Thumbnail of live in absolute url",
    "products": [
      {
        "name": "Name of product",
        "thumbnailUrl": "Product thumbnail",
        "url": "Url of product in absolute url"
      }
    ]
  }
}
```

You can also access global variables regarding your Caast configuration, it will be easy to build your design configuration in order to make a perfectly branded email.

```json
{
  "website_configuration": {
    "color": {
      "button_background": "#000",
      "button_color": "#FFF",
      "header_background": "#000",
      "header_color": "#FFF",
      "product_background": "#fff",
      "product_color": "#333",
      "product_border": "#E7E7E7",
      "product_fill_buy": "#CCC",
      "product_active_background": "#fff",
      "product_active_color": "#333",
      "product_active_border": "#000",
      "product_active_fill_buy": "#000",
      "product_live_background": "#000",
      "product_live_color": "#FFF",
      "question_background": "#FFF",
      "question_border": "#000",
      "question_color": "#333",
      "question_active_background": "#000",
      "question_active_border": "#000",
      "question_active_color": "#FFF",
      "pseudo_background": "rgba(0,0,0, .05)",
      "pseudo_color": "#333",
      "chat_send_background": "#000",
      "chat_send_color": "#FFF",
      "live": "#FF015C"
    }
  }
}
```
