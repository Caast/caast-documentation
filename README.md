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
    "https://cdn.potion.social/latest/library.js",
    "Caast"
  );

  document.onreadystatechange = function () {
    if (document.readyState == "complete") {
      Caast.init();
    }
  };
</script>
```

With this simple snippet Caast is now running on your website, lets have a look on advanced configuration in order to customize the widget a bit.

## Advanced configuration

Now that the main library is loaded, you may want to alter some configuration behaviour. Most configuration tweaks take place in your [https://dashboard.caast.tv](dashboard) in the configuration section of your project.

Nevertheless you can also add some property on the loaded library on your website. Let's have a look to an advanced instanciation but keep in mind that the library must be previously loaded.

```javascript
Caast.init({
  target: "#potion-caast",
  events: {
    onLoadComplete: function (data) {
      console.log("onLoadComplete", data);
    },
    onLiveSubscription: function (data) {
      console.log("onLiveSubscription", data);
    },
    onModalTrigger: function (data) {
      console.log("onModalTrigger", data);
    },
    onModalLoaded: function (data) {
      console.log("onModalLoaded", data);
    },
    onModalClosed: function (data) {
      console.log("onModalClosed", data);
    },
  },
}).then(function () {
  console.log("Caast is ready to boot");
});
```

### target

The target parameter allow you to define in which DOM element the Caast widget will be embedded. You are free to pass an ID or a class in this parameter. Note that this parameter can also be configurated in your [https://dashboard.caast.tv](dashboard).

### events

The events parameter will allow you to trigger custom functions on the life cycle of the widgets, every function receive a Caast object containing several informations regarding the current page you are looking for and more advanced data about the incoming live, if there is one.

The Caast data object is looking like this:

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
        "uuid": "sfjh87687yhiushf9769KJDQ"
    }
}
```

Now you know more about the data, let's have a look to the custom events available in the widget.

#### onLoadComplete

This function is triggered when all the initial data and informations are available inside the Caast Widget

#### onLiveSubscription

This function is triggered when a user has subscribed to a live in order to be notified when a live is about to start

#### onModalTrigger

This function is triggered when a user click on the button to open the modal

#### onModalLoaded

This function is triggered when the live modal is opened

#### onModalClosed

This function is triggered when the live modal is closed
