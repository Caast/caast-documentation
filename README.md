# Introduction

Welcome to Potion Caast Widget documentation, this simple documentation website will help you to install and configure our Caast plugin on your website. If you have any problem, please contact our support via our administration interface on https://dashboard.caast.tv

# Getting started

To load our widget on your website you just need to add this code at the end of your `body` tag element. This is a really basic implementation, you will find down the page some more advanced configuration.

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

Now that the main library is loaded, you may want to custom some behaviour or customize your widget a bit. All the configuration tweaks take place in your [https://dashboard.caast.tv](dashboard) in the configuration section of your project.

### Set custom user informations

You may want to add additionnal informations to your user object, it can be useful when interacting with Caast statistics to identify your own user database. To implement custom data the `setUser` function is available on the Caast instance. To implement it simply call the function when Caast is loaded.

```javascript
document.addEventListener("Caast::onLoadComplete", function (e) {
  Caast.setUser({
    email: "johndoe@mail.com",
    first_name: "John",
    last_name: "Doe",
  });
});
```

The function is expecting an object and you can add as much as informations you want.

### Emitted events

The Caast widget will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data available in the `detail` key. Please refer to the [data section](#caast-data) if you want details about what information is available.

#### onLoadComplete

This event is emitted when all the initial data and informations are available inside the Caast Widget

```javascript
document.addEventListener("Caast::onLoadComplete", function (e) {
  console.log("Caast::onLoadComplete", e.detail);
});
```

#### onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start

```javascript
document.addEventListener("Caast::onLiveSubscription", function (e) {
  console.log("Caast::onLiveSubscription", e.detail);
});
```

#### onModalTrigger

This event is emitted when a user click on the button to open the modal

```javascript
document.addEventListener("Caast::onModalTrigger", function (e) {
  console.log("Caast::onModalTrigger", e.detail);
});
```

#### onModalLoaded

This event is emitted when the live modal is opened

```javascript
document.addEventListener("Caast::onModalLoaded", function (e) {
  console.log("Caast::onModalLoaded", e.detail);
});
```

#### onModalClosed

This event is emitted when the live modal is closed

```javascript
document.addEventListener("Caast::onModalClosed", function (e) {
  console.log("Caast::onModalClosed", e.detail);
});
```

## Caast data

In every emmited events the following data is made available for you to interact with your environment. Exposed data is about the current live informations, your platform configuration and the current user informations. All the configuration data is customizable in your [https://dashboard.caast.tv](dashboard) in the configuration section of your project.

```javascript
{
    "data": {
      "configuration": {
        "button": {
            "background": "#52FFCE",
            "color": "#333"
        },
        "target": {
            "element": ".product-stock",
            "position": "afterend"
        },
        "mode": "mini",
        "template": ...,
        "i18n": {
          "button": {
            "launch": "Lancer le live",
            "yes": "Oui",
            "no": "Non"
          },
          "product": {
            "title": {
                "has_live": "Un live est programmé pour ce produit",
                "is_live": "Un live est en cours",
                "no_live": "Ce produit n'a pas encore de présentation live"
            },
            "thumbnail": {
                "is_live": "En direct"
            }
          },
          "subscribe": {
            "description": "Souhaitez-vous être notifié des prochains live ?",
            "input_placeholder": "Saisissez votre email",
            "success": "Inscription réussie ! Vous serez notifié par mail des prochains live",
            "error": "Une erreur est survenue"
          }
        }
      },
      "has_live": true,
      "is_live": true
    },
    "user": {
        "uuid": "sfjh87687yhiushf9769KJDQ",
        "custom_fields": {...}
    }
}
```

!> _Note that the `custom_fields` key inside user informations will only be there if you used the `setUser` function._

## Customize style

Caast is totally customizable, we provide two types of widget style but you can expand basic styling via css, you just need to make sure to respect our css naming strategy in order to override implemented styles.

The available classes and their usage are described here:

```css
/*
* -----------------------------------
* Style for Caast common dom element
* -----------------------------------
*/

/* 
* Caast button to open modal
*/
.caast-toggler--button {
}
/* 
* Caast launcher title
*/
.caast-toggler--title {
}
/* 
* Caast button to open modal
*/
.caast-toggler--description {
}
/* 
* Caast led
*/
.caast-toggler--led {
}
/* 
* Caast animation for led when a live in on
*/
.caast-toggler--led-animated {
}
/*
* Caast content wrapper
*/
.caast-toggler--content {
}

/*
* -----------------------------------
* Style for Caast subscribe form
* -----------------------------------
*/

/* 
* Wrapper for subscription implementation
*/
.caast-toggler--subscription {
}
/* 
* Wrapper for subscription content
*/
.caast-subscription--wrapper {
}
/* 
* Form style for subscription
*/
.caast-subscription--form {
}
/* 
* Button variant in subsription form, this class extends .caast-toggler--button
*/
.caast-toggler--button-sm {
}
/* 
* Submit button style for subscription
*/
.caast-subscription--submit {
}
/* 
* Subscription response wrapper
*/
.caast-subscription--response {
}
/* 
* Subscription response success variant
*/
.caast-subscription--response-success {
}
/* 
* Subscription response error variant
*/
.caast-subscription--response-error {
}
/*
* -----------------------------------
* Style for Caast mini widget
* -----------------------------------
*/

/* 
* Wrapper for the mini widget implementation
*/
.caast-toggler-wrapper--mini {
}
/* 
* Wrapper for the mini widget content
*/
.caast-toggler-mini--wrapper {
}
/* 
* Wrapper for the mini widget content
*/
.caast-toggler-mini--wrapper {
}

/*
* -----------------------------------
* Style for Caast mini widget
* -----------------------------------
*/

/* 
* Wrapper for the thumbnail widget implementation
*/
.caast-toggler-wrapper--thumbnail {
}
/* 
* Wrapper for the thumbnail widget content
*/
.caast-toggler-thumbnail--wrapper {
}
/* 
* Wrapper for positioning content over the thumbnail
*/
.caast-toggler-thumbnail--overlay {
}
/* 
* Text style inside .caast-toggler-thumbnail--overlay
*/
.caast-toggler-thumbnail--title {
}
```

!> _Note that Caast will only load needed css classes depending on widget display mode and if a subscription on a live is available._

!> _Css will be totally ignored if you are using the custom template system_

## Customize HTML

Caast allow a total control over what is printed on the client side. To create your own templates for your Caast widget plugin, simply login into your [https://dashboard.caast.tv](dashboard) and go to the app configuration in the template section.

Templates are dynamic and to allow you to display conditional templates. We use [https://github.com/blueimp/JavaScript-Templates](blueimp/Javascript-Templates) to allow you to easily create template, this library is very light and you can manipulate all the variables, implement conditions and iterations.

With custome templating, you can easily extend your in place design system and relying on your available css to customize our widget.

### Template data

All the data available in the templating system is detailed in the [data section](#caast-data).

### Templating required attributes

When you create a custom template you must add some `id` on particular elements. This is a required step in order to allow Caast widget listeners to perform all the required actions like subscribe, launch the live modal etc..

- `#caast-modal--trigger` Must be placed on the DOM element triggering the modal, must be a `<button>` or a `<a>` tag in order to respect a11y.
- `#caast-live--subscribe` Must be placed on the DOM element triggering the subscribe action, must be a `<button>` or a `<a>` tag in order to respect a11y.
- `#caast-live--unsubscribe` Must be placed on the DOM element triggering the unsubscribe action, must be a `<button>` or a `<a>` tag in order to respect a11y.
- `#caast-subscription--wrapper` Must be placed on the DOM element wrapping your subscription template, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-subscription--has-form` class when the subscribe button is clicked.
- `#caast-subscription--input` Must be placed on the DOM element triggering the subscribe action, must be an `<input>` tag.
- `#caast-subscription--submit` Must be placed on the DOM element triggering the subscribe action, must be an `<button>` tag with `type=submit`
- `#caast-subscription--response` Must be placed on the DOM element where you want the success/fail response, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-subscription--response-error` or `caast-subscription--response-success` class according to the action response.

!> Omitting those attributes will lead to a non-working widget, do not hesitate to contact your support via your [https://dashboard.caast.tv](dashboard) if you have any doubt.

### Template example

Lets say you want to create a really simple but ugly launcher with a title and a big button triggering the Caast modal:

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
    background: {%=o.configuration.button.background%};
    color: {%=o.configuration.button.color%};
  }
</style>
<div class="my-custom--class">
  <h1 class="my-custom--title">
    {% if (o.has_live && o.is_live) { %}
    {%=o.configuration.i18n.product.title.is_live%} {% } else { %}
    {%=o.configuration.i18n.product.title.no_live%} {% } %}
  </h1>
  <button id="caast-toggler-modal-trigger" class="my-custom--button">
    {%=o.configuration.i18n.button.launch%}
  </button>
</div>
```
