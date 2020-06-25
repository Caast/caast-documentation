# Introduction

Welcome to Caast Widget documentation, this simple documentation website will help you to install and configure the Caast library on your website. If you have any problem, please contact our support via our administration interface.

?> Caast library is still under development, documentation will be updated on a regular basis.

# Getting started

To load the Caast library on your website you just need to add this code at the end of your `body` tag element. This is a really basic implementation, you will find down the page some more advanced configuration.

```html
<script type="text/javascript">
  (function (i, s, o, g, r, a, m) {
    (i[r] = i[r]), (a = s.createElement(o)), (m = s.getElementsByTagName(o)[0]);
    a.async = 1;
    a.src = g;
    m.parentNode.insertBefore(a, m);
  })(
    window,
    document,
    "script",
    "https://cdn.potion.social/caast-latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY",
    "Caast"
  );
</script>
```

With this simple snippet Caast is now running on your website, lets have a look on advanced configuration in order to customize the widget a bit.

## Advanced configuration

Now that the main library is loaded, you may want to custom some behaviour or customize the Caast library a bit. All the configuration tweaks takes place in your dashboard in the configuration section of your project.

### Define where the widget must be loaded

By default Caast widget will look on your HTML for a DOM node with the id `caast__wrapper`, but maybe you don't want or cannot change your page HTML. To allow you a smooth integration, Caast widget can be loaded into any DOM element on your page. To change the default behaviour simply go to your dashboard and go into the configuration section of your project.

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

### Set custom user informations

You may want to add additionnal informations to your user object, it can be useful when interacting with Caast statistics to identify your own user database. To implement custom data the `setUser` function is available on the Caast instance. To implement it simply call the function when Caast is loaded.

```javascript
document.addEventListener("caast.onLoadComplete", function (e) {
  Caast.setUser({
    email: "d.copperfield@abracadabra.io",
    first_name: "David",
    last_name: "Copperfield",
  });
});
```

The function is expecting an object and you can add as much as informations you want.

!> If you are planning to provide an email information, it will automatically pre-fill forms inside the widget, we support `email`, `e_mail` and `mail` as key naming.

### Emitted events

The Caast widget will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data available in the `detail` key. Please refer to the [data section](#caast-data) if you want details about what information is available.

#### onLoadComplete

This event is emitted when all the initial data and informations are available inside the Caast Widget

```javascript
document.addEventListener("caast.onLoadComplete", function (e) {
  console.log("caast.onLoadComplete", e.detail);
});
```

#### onSetUser

This event is emitted when the [`setUser`](#set-custom-user-informations) function is triggered.

```javascript
document.addEventListener("caast.onSetUser", function (e) {
  console.log("caast.onSetUser", e.detail);
});
```

#### onRouteChange

This event is emitted when a Single Page App change current url.

```javascript
document.addEventListener("caast.onRouteChange", function (e) {
  console.log("caast.onRouteChange", e.detail);
});
```

#### onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start

```javascript
document.addEventListener("caast.onLiveSubscription", function (e) {
  console.log("caast.onLiveSubscription", e.detail);
});
```

#### onLivePlay

This event is emitted when a user press play on the live player, also return informations about current player time position

```javascript
document.addEventListener("caast.onLivePlay", function (e) {
  console.log("caast.onLivePlay", e.detail);
});
```

#### onLivePause

This event is emitted when a user press pause on the live player, also return informations about current player time position.
This event is also emitted when the modal is closed.

```javascript
document.addEventListener("caast.onLivePause", function (e) {
  console.log("caast.onLivePause", e.detail);
});
```

#### onVoteForLive

This event is emitted when a user has request a live on a product

```javascript
document.addEventListener("caast.onVoteForLive", function (e) {
  console.log("caast.onVoteForLive", e.detail);
});
```

#### onQuestionClick

This event is emitted when a user click on a question, also return the question id

```javascript
document.addEventListener("caast.onQuestionClick", function (e) {
  console.log("caast.onQuestionClick", e.detail);
});
```

#### onModalTrigger

This event is emitted when a user click on the button to open the modal

```javascript
document.addEventListener("caast.onModalTrigger", function (e) {
  console.log("caast.onModalTrigger", e.detail);
});
```

#### onModalLoaded

This event is emitted when the live modal is opened

```javascript
document.addEventListener("caast.onModalLoaded", function (e) {
  console.log("caast.onModalLoaded", e.detail);
});
```

#### onModalClosed

This event is emitted when the live modal is closed

```javascript
document.addEventListener("caast.onModalClosed", function (e) {
  console.log("caast.onModalClosed", e.detail);
});
```

## Caast data

In every emmited events the following data is made available for you to interact with your environment. Exposed data is about the current live informations, your platform configuration and the current user informations. All the configuration data is customizable in your dashboard in the configuration section of your project.

```javascript
{
  "credentials": {
    "APP_ID": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
    "APP_KEY": "SP_S6EByQ50YFiSpmZS0fho8_Hg-7HsOagOmhDyxAwg"
  },
  "config": {
    "id": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
    "type": "app",
    "attributes": {
      "name": "Caast Live for Christmas",
      "uid": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
      "secret": "SP_S6EByQ50YFiSpmZS0fho8_Hg-7HsOagOmhDyxAwg",
      "redirectUri": "https://caast.tv",
      "configuration": {
        "color": {
          "button_background": "#52FFCE",
          "button_color": "#333",
          "live": "#FF015C"
        },
        "target": {
          "element": "#service-one li:nth-child(4)",
          "position": "beforeend"
        },
        "mode": "mini",
        "i18n": {
          "button": {
            "open": "Enter live room",
            "replay": "See replay",
            "send": "Send"
          },
          "product": {
            "title": {
              "is_live": "A live is in progress",
              "countdown": "Live presentation in",
              "today": "A live is scheduled today at",
              "tomorrow": "A live is scheduled tomorrow at",
              "date": "A live is scheduled on",
              "no_live": "This product does not have a live presentation yet",
              "replay": "Several lives are available for this product"
            },
            "description": {
              "default": "Ask your questions now",
              "replay": "Watch them while waiting for a new live !"
            },
            "thumbnail": {
              "is_live": "Live"
            }
          },
          "subscribe": {
            "description": "Would you like to be notified before the live starts ?",
            "input_placeholder": "Enter your email",
            "success": "Registration successful! You will be notified by email of the next lives",
            "error": "An error has occurred",
            "error_already_mail": "You are already on the notification list"
          }
        }
      }
    }
  },
  "lives": [
    {
      "id": "f20aa128931a449b9478f5fb69e07c3b",
      "type": "live",
      "attributes": {
        "name": "Caast live event",
        "description": "A live event for christmas",
        "videoId": "a6b7e85c6433c00a4f1df62a1f7ec948",
        "chatId": "078a8000a55bc862c6bcf0a9cc72d9ec",
        "isStarted": false,
        "isFinished": false,
        "startDate": "2020-12-25T20:00:00.000Z",
        "thumbnailUrl": null,
        "urls": [
          "https://caast.tv",
        ]
      }
    }
  ],
  "user": {
    "uuid": "1d5f65e4d53b20fcb223a7dc0aec3ea0",
    "custom_fields": {
      "email": "d.copperfield@abracadabra.io",
      "first_name": "David",
      "last_name": "Copperfield"
    }
  },
  "player": {
    "seconds": 36.8
  },
  "question": "452159334435456999954edb1a04d779",
  "questions": [
    {
      "id":"452159334435456999954edb1a04d779",
      "type":"question",
      "attributes": {
        "questionerName":"David Copperfield",
        "question":"What is the product price ?",
        "sentAt":"2020-12-25T21:07:57.000Z",
        "answered":true,
        "moderated":false,
        "answerTimestamp":44
      }
    },
    {
      "id":"27bb4a0bbda54303a5a02005b19924f5",
      "type":"question",
      "attributes":{
        "questionerName":"AlonzoBistro",
        "question":"Is it available in other colors ?",
        "sentAt":"2020-12-25T21:12:34.000Z",
        "answered":true,
        "moderated":false,
        "answerTimestamp":96
      }
    }
  ]
}
```

?> _Note that the `custom_fields` key inside user informations will only be there if you used the `setUser` function._

?> _Note that the `lives` key can be empty if no lives are planned on the current page._

?> _Note that the `player` key will be missing if the emitted event is not `onLivePlay` or `onLivePause`._

?> _Note that the `question` key will be missing if the emitted event is not `onQuestionClick`._

?> _Note that the `questions` key will be missing if the modal is not yet opened._

## Customize style

Caast is totally customizable, we provide two types of widget style but you can expand basic styling via css, you just need to make sure to respect our css naming strategy in order to override implemented styles.

The available classes and their usage are described here:

### Global style

```css
/*
* -----------------------------------
* Style for Caast common dom element
* -----------------------------------
*/

/* 
* Wrapper for widget
*/
.caast-toggler {
}
/* 
* Wrapper for widget content
*/
.caast-toggler__content {
}
/* 
* Widget title
*/
.caast-toggler__title {
}
/* 
* Class added to .caast-toggler__title when a live is on
*/
.caast-toggler__title--animated {
}
/* 
* Widget description
*/
.caast-toggler__description {
}
/* 
* Wrapper for widgets actions like subscribe and launch live
*/
.caast-toggler__actions {
}
/* 
* Wrapper for countdown when a llive is about to start
*/
.caast-countdown {
}
/* 
* Wrapper for countdown minutes
*/
.caast-countdown__minutes {
}
/* 
* Wrapper for countdown seconds
*/
.caast-countdown__seconds {
}
/* 
* Widget button
*/
.caast-button {
}
/* 
* Class added to .caast-button when loading
*/
.caast-button--loading {
}
```

### Subcribe form style

```css
/*
* -----------------------------------
* Style for Caast subscribe form
* -----------------------------------
*/

/* 
* Wrapper for subscription popover
*/
.caast-popover {
}
/* 
* Class added to .caast-popover when open
*/
.caast-popover--open {
}
/* 
* Class added to .caast-popover when open
*/
.caast-popover--animating {
}
/* 
* Class extending .caast-button
*/
.caast-button--circle {
}
/*
* Wrapper for input grouped with button
*/
.caast-input-group {
}
/*
* Wrapper inside .caast-input-group to properly wrap the submit button
*/
.caast-input-group-append {
}
/*
* Widget input
*/
.caast-input {
}
/*
* Wrapper for form response
*/
.caast-response {
}
/* 
* Class added to .caast-response when success
*/
.caast-response--success {
}
/* 
* Class added to .caast-response when error
*/
.caast-response--error {
}
```

### Modal style

```css
/*
* -----------------------------------
* Style for Caast modal
* -----------------------------------
*/

/* 
* Modal background overlay
*/
.caast-modal__overlay {
}
/* 
* Wrapper for modal
*/
.caast-modal__wrapper {
}
/* 
* Class added to .caast-modal__wrapper when modal is open
*/
.caast-modal__wrapper--open {
}
/* 
* Wrapper for modal container
*/
.caast-modal__container {
}
/* 
* Class on modal close button
*/
.caast-modal__close {
}
/* 
* Wrapper for modal content
*/
.caast-modal__content {
}
/* 
* Wrapper for modal live section
*/
.caast-modal__live-container {
}
/* 
* Wrapper for modal chat section
*/
.caast-modal__chat-container {
}
/* 
* Wrapper for modal questions section
*/
.caast-modal__questions-container {
}
/* 
* Class for modal questions ul
*/
.caast-modal__questions-list {
}
/* 
* Class for modal questions li
*/
.caast-modal__questions-item {
}
/* 
* Class added to .caast-modal__questions-item when a response is being responded
*/
.caast-modal__questions-item--active {
}
/* 
* Class for modal questions link
*/
.caast-modal__questions-link {
}
/* 
* Class for modal questions author
*/
.caast-modal__questions-author {
}
```

### Thumbnail widget variant

```css
/*
* -----------------------------------
* Style for Caast thumbnail widget
* -----------------------------------
*/

/* 
* Wrapper for the thumbnail content
*/
.caast-toggler__thumbnail {
}
```

!> _Note that Caast will only load needed css classes depending on widget display mode and if a subscription on a live is available._

!> _Css wont be injected if you are using the custom template system except for the modal style definition_

## Customize HTML

Caast allow a total control over what is printed on the client side. To create your own templates for your Caast widget plugin, simply login into your dashboard and go to the app configuration in the template section.

Templates are dynamic and to allow you to display conditional templates. We use [blueimp/Javascript-Templates](https://github.com/blueimp/JavaScript-Templates) to allow you to easily create template, this library is very light and you can manipulate all the variables, implement conditions and iterations.

With custom templating, you can easily extend your in place design system and relying on your available css to customize the Caast library to fit exactly on your website.

### Template data

All the data available in the templating system is detailed in the [data section](#caast-data).

### Templating required attributes

When you create a custom template you must add some `id` on particular elements. This is a required step in order to allow Caast widget listeners to perform all the required actions like subscribe, launch the live modal etc..

| ID                         | Description                                                                                                                                                                                                                                              |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **#caast-modal--trigger**  | Must be placed on the DOM element triggering the modal, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                                    |
| **#caast-popover--toggle** | Must be placed on the DOM element triggering the subscribe action, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                         |
| **#caast-popover**         | Must be placed on the DOM element wrapping your subscription template, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-popover--open` and `caast-popover--animating` classes when the subscribe button is clicked. |
| **#caast-input**           | Must be placed on the input element needed to fill an email for subscribe action, must be an `<input>` tag.                                                                                                                                              |
| **#caast-button--submit**  | Must be placed on the DOM element triggering submitting the subscribe form, must be an `<button>` tag with `type=submit`                                                                                                                                 |
| **#caast-response**        | Must be placed on the DOM element where you want the success/fail response, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-response--error` or `caast-response--success` class according to the action response.  |

!> Omitting those attributes will lead to a non-working widget, do not hesitate to contact your support via your dashboard if you have any doubt.

### Template example

Lets say you want to create a really simple and not so pretty launcher with a title and a big button triggering the Caast modal **only vsible** if a live is on. No subscription form, just a pure launcher.

<!-- prettier-ignore -->
```html
<style>
  .my-custom--class {
    background: white;
    padding: 20px;
  }
  .my-custom--title {
    color: black;
    margin-bottom: 20px;
    font-size: 20px;
  }
  .my-custom--button {
    background: {%=o.config.attributes.configuration.color.button_background%};
    color: {%=o.config.attributes.configuration.color.button_color%};
  }
</style>
<div class="my-custom--class">
  <h1 class="my-custom--title">
    {% if (o.lives && o.lives.length > 0) { %}
      {%=o.config.attributes.configuration.i18n.product.title.is_live%} 
    {% } else { %} 
      {%=o.config.attributes.configuration.i18n.product.title.no_live%} 
    {% } %}
  </h1>
  {% if (o.lives && o.lives.length > 0) { %}
  <button id="caast-modal--trigger" class="my-custom--button">
    {%=o.config.attributes.configuration.i18n.button.open%}
  </button>
  {% } %}
</div>
```

!> _Currently you can only customize the Caast launcher but you will soon be able to customize anything inside the modal. You can always override styles with css if needed_
