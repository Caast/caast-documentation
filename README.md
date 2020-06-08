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
    "https://cdn.potion.social/latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY",
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

### Events

The Caast widget will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data availables in the `detail` key

The Caast data object in events looks like this:

```javascript
{
    "data": {
        "config": {
            "button": {
                "background": "#52FFCE",
                "color": "#333",
                "name": "Lancer le live"
            },
            "mode": "thumbnail"
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

_Note that the `custom_fields` key inside user informations will only be there if you used the `setUser` function._

Now you know more about the data, let's have a look on how to implement events listener and retrieve the custom data.

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
