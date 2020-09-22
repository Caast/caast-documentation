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
    a.id = "caast_library";
    m.parentNode.insertBefore(a, m);
  })(
    window,
    document,
    "script",
    "https://cdn.caast.tv/caast-latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY",
    "caast"
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

You may want to add additionnal informations to your user object, it can be useful when interacting with Caast statistics to identify your own user database. To implement custom data the `setUser` function is available on the Caast instance. To implement it simply call the function when Caast is ready.

```javascript
document.addEventListener("caast.onReady", function (e) {
  caast.setUser({
    email: "d.copperfield@abracadabra.io",
    first_name: "David",
    last_name: "Copperfield",
  });
});
```

The function is expecting an object and you can add as much informations as you want.

### Emitted events

The Caast widget will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data. Please refer to the [data section](#caast-data) if you want details about what information is available. You can listen for events in the widget by attaching a callback using .on().

Before listening to any event, please make sure the Caast widget is ready using this snippet. `e.detail` contain information regarding the current available configuration on your widget instance.

```javascript
document.addEventListener("caast.onReady", function (e) {
  console.log("caast.onLoadComplete", e.detail);
  // here start subscribe to any events
});
```

#### onSetUser

This event is emitted when the [`setUser`](#set-custom-user-informations) function is triggered.

```javascript
caast
  .on("onSetUser", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onSetUser::subscribed", response);
  })
  .catch(function (error) {
    console.log("onSetUser::error", error);
  });
```

#### onRouteChange

This event is emitted when a Single Page App change current url.

```javascript
caast
  .on("onRouteChange", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onRouteChange::subscribed", response);
  })
  .catch(function (error) {
    console.log("onRouteChange::error", error);
  });
```

#### onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start

```javascript
caast
  .on("onLiveSubscription", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onLiveSubscription::subscribed", response);
  })
  .catch(function (error) {
    console.log("onLiveSubscription::error", error);
  });
```

#### onLivePlay

This event is emitted when a user press play on the live player, also return informations about current player time position

```javascript
caast
  .on("onLivePlay", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onLivePlay::subscribed", response);
  })
  .catch(function (error) {
    console.log("onLivePlay::error", error);
  });
```

#### onLivePause

This event is emitted when a user press pause on the live player, also return informations about current player time position.
This event is also emitted when the modal is closed.

```javascript
caast
  .on("onLivePause", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onLivePause::subscribed", response);
  })
  .catch(function (error) {
    console.log("onLivePause::error", error);
  });
```

#### onVoteForLive

This event is emitted when a user has request a live on a product

```javascript
caast
  .on("onVoteForLive", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onVoteForLive::subscribed", response);
  })
  .catch(function (error) {
    console.log("onVoteForLive::error", error);
  });
```

#### onQuestionClick

This event is emitted when a user click on a question, also return the question id

```javascript
caast
  .on("onQuestionClick", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onQuestionClick::subscribed", response);
  })
  .catch(function (error) {
    console.log("onQuestionClick::error", error);
  });
```

#### onRelatedClick

This event is emitted when a user click on a related replay video, also return the target new live id

```javascript
caast
  .on("onRelatedClick", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onRelatedClick::subscribed", response);
  })
  .catch(function (error) {
    console.log("onRelatedClick::error", error);
  });
```

#### onMessageSubmit

This event is emitted when a user submit a message in chat, return all the data related to the new message

```javascript
caast
  .on("onMessageSubmit", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onMessageSubmit::subscribed", response);
  })
  .catch(function (error) {
    console.log("onMessageSubmit::error", error);
  });
```

#### onBasketAdd

This event is emitted when a user add an item to his basket, this event won't emit if the target DOM element is not set in the app configuration. Also return live id

```javascript
caast
  .on("onBasketAdd", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onBasketAdd::subscribed", response);
  })
  .catch(function (error) {
    console.log("onBasketAdd::error", error);
  });
```

#### onModalTrigger

This event is emitted when a user click on the button to open the modal

```javascript
caast
  .on("onModalTrigger", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onModalTrigger::subscribed", response);
  })
  .catch(function (error) {
    console.log("onModalTrigger::error", error);
  });
```

#### onModalShow

This event is emitted when the live modal is opened

```javascript
caast
  .on("onModalShow", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onModalShow::subscribed", response);
  })
  .catch(function (error) {
    console.log("onModalShow::error", error);
  });
```

#### onModalClose

This event is emitted when the live modal is closed

```javascript
caast
  .on("onModalClose", function (data) {
    console.log("your custom function receiving data", data);
  })
  .then(function (response) {
    console.log("onModalClose::subscribed", response);
  })
  .catch(function (error) {
    console.log("onModalClose::error", error);
  });
```

### URL parameters

In order to trigger some specific actions on the Caast widget, you can also add hash parameters to your urls in order to programmatically execute some of the widget functionalities. There is a default configuration for each of those hash naming but **you can also customize each naming via our administration interface**.

| Default parameter name         | Action                                                                                                                 |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| caast-open                     | Open Caast widget modal if available on page                                                                           |
| caast-question\_**questionID** | Open Caast widget modal and click on specific **questionID**, resulting in video to jump to specific question's answer |
| caast-jump\_**timestamp**      | Open Caast widget modal and jump to specified **timestamp**. Timestamp is expressed in seconds.                        |

So let's say you add `#caast-jump_90` to your URL, resulting with an URL like this one `https://mywebsite.com/product/my-product#caast-jump_90`, and the Caast widget will magically open and play the video starting at 90 seconds

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
        },
        "target": {
          "element": "#service-one li:nth-child(4)",
          "position": "beforeend",
          "basket": ""
        },
        "hash": {
          "question": "caast-question_",
          "jump": "caast-jump_",
          "open": "caast-open",
        },
        "mode": "mini",
        "custom_style": "",
        "custom_style_iframe": "",
        "show_subscribe": false,
        "i18n": {
          "button": {
            "open": "Enter live room",
            "replay": "See replay",
            "send": "Send",
            "next": "Next",
            "prev": "Previous",
            "close": "Close",
            "hide": "Hide",
            "cancel": "Cancel",
            "validate": "Validate",
            "default": "Enter chatroom",
            "is_live": "See live"
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
              "replay": "Watch them while waiting for a new live !",
              "is_live": "Enter to view the live and chat with others"
            },
            "thumbnail": {
              "is_live": "Live"
            }
          },
          "subscribe": {
            "description": "Would you like to be notified before the live starts ?",
            "input_placeholder": "Enter your email",
            "success": "Registration successful! You will be notified by email of the next lives",
            "success_vote_for_live": "Thanks for your live request",
            "error": "An error has occurred",
            "error_already_mail": "You are already on the notification list"
          },

          "modal": {
            "all_lives": "All the previous lives",
            "other_questions": "Other lives questions",
            "show_questions": "Show questionss",
            "search": "Search for a question",
            "no_result_for": "No results for search {{term}}",
            "live_date": "Live from {{date}}",
            "no_questions": "Currently no questions for this live",
            "tabs": {
              "description": "Description",
              "chat": "Discussions",
              "question": "Questions",
              "product": "Products",
              "replay": "Replay"
            },
            "all_replays": "All replays"
          },
          "chat": {
            "title": "Discussions",
            "change_mode": "Click here to display only the questions during the live",
            "offline": "Chat is currently offline",
            "form": {
              "message_placeholder": "Send your message",
              "pseudo_placeholder": "Choose a nickname",
              "add_emoji": "Add a smiley",
              "as_anonymous": "Post as anonymous",
              "character_left": "{{total}} remaining characters",
              "hint_pseudo": "Cannot contain spaces and maximum 25 characters"
            },
            "message": {
              "anonymous": "Anonymous",
              "vote": "Vote for this question",
              "answered": "Question answered",
              "answered_at": "Question answered at {{time}}",
              "moderated": "Moderated content"
            },
            "emoji": {
              "search": "Search",
              "clear": "Clear",
              "notfound": "No emoji found",
              "categories": {
                "search": "Results",
                "recent": "Frequently used",
                "smileys": "Smileys & Emotion",
                "people": "Peoples",
                "nature": "Animals & Nature",
                "foods": "Food & Drinks",
                "activity": "Activities",
                "places": "Travel & Places",
                "objects": "Objects",
                "symbols": "Symbols",
                "flags": "Flags"
              }
            },
            "new_message": "View new messages"
          },
          "products": {
            "on_screen": "on screen",
            "buy_label": "Go on product page"
          }
        }
      }
    }
  },
  "lives": {
    "coming": {"data" : []},
    "current": {
      "data": [{
        "id": "f20aa128931a449b9478f5fb69e07c3b",
        "type": "live",
        "attributes": {
          "name": "Caast live event",
          "description": "A live event for christmas",
          "videoId": "a6b7e85c6433c00a4f1df62a1f7ec948",
          "chatId": "078a8000a55bc862c6bcf0a9cc72d9ec",
          "isStarted": false,
          "isFinished": false,
          "isDirectInsert": false,
          "startDate": "2020-12-25T20:00:00.000Z",
          "productActiveId": null,
          "productIds": ["310eb32e97044d96a5416b13fe7adf3d"],
          "productTimestamps": [{
            "attributes": {
              "productId": "310eb32e97044d96a5416b13fe7adf3d",
              "timestampEnd": 30,
              "timestampStart": 10
            },
            "id": "49cbb03c0d594b71aceb113278f6821a",
            "type": "productTimestamp"
          }],
          "products": [{
            "attributes": {
              "name": "A fake product",
              "thumbnailUrl": "https://mediadev.caast.tv/variants/...",
              "url": "https://www.a-fake-product.com"
            },
            "id": "310eb32e97044d96a5416b13fe7adf3d",
            "relationships": {},
            "type": "product"
          }],
          "thumbnailUrl": null,
          "urls": [
            "https://caast.tv",
          ]
        }
      }]
    },
    "passed": {"data" : []}
  },
  "live_id": "f20aa128931a449b9478f5fb69e07c3b",
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

?> _Note that the `live_id` key will be missing if the emitted event is not `onLivePlay`, `onLivePause`, `onLiveSubscription`, `onVoteForLive`, `onRelatedClick` or `onModalTrigger`._

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

| Attribute                      | Description                                                                                                                                                                                                                                              |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DATA-ATTR: **data-caast-open** | Must be placed on the DOM element triggering the modal, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                                    |
| ID: **caast-popover--toggle**  | Must be placed on the DOM element triggering the subscribe action, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                         |
| ID: **caast-popover**          | Must be placed on the DOM element wrapping your subscription template, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-popover--open` and `caast-popover--animating` classes when the subscribe button is clicked. |
| ID: **caast-input**            | Must be placed on the input element needed to fill an email for subscribe action, must be an `<input>` tag.                                                                                                                                              |
| ID: **caast-button--submit**   | Must be placed on the DOM element triggering submitting the subscribe form, must be an `<button>` tag with `type=submit`                                                                                                                                 |
| ID: **caast-response**         | Must be placed on the DOM element where you want the success/fail response, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-response--error` or `caast-response--success` class according to the action response.  |

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
