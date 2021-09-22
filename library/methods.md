# Available methods

Caast Library expose some methods to allow you to perform operations on your site. Those methods are described here. We assume that you are implementing those methods after Caast Library emitted the `caast.onLoaded` event on the DOM.

```javascript
document.addEventListener('caast.onLoaded', function (e) {
  // Start adding methods here, calling the caast instance
});
```

Note that this event can be emitted twice, Caast library will previously check if something has to be displayed on a page. If nothing is configurated to be displayed, you wont receive ddata from Caast and Caast will not trigger this event two times. On the other hand, if Caast is configurated to send data to a specific page, Caast library will load the main library in order to display lives. Once this is done you will receive this event a second time. To be sure to distinguish thoses events, you can check if the response contain `preload: true`, an example is shown below.

```javascript
document.addEventListener('caast.onLoaded', function (e) {
  // Start adding methods here, calling the caast instance
  if (e.detail.preload) {
    // You cannot call methods labeled with [main library only]
    console.log('Caast preload script');
  } else {
    // You can call any method
    console.log('Caast main script');
  }
});
```

?> In order to be as light as possible, the preload script does not contain some functions, those functions are labeled with the **[main library only]** attribute.

## infos _[main library only]_

Caast expose a rather useful method in order to easily check, wich version of Caast Library you are running on. Run it and you will receive an object indicating the version you are running but also the actual environnement.

```javascript
caast.infos();
```

## setUser _[main library only]_

You may want to add additionnal informations to your Caast Library user object, it can be useful when interacting with Caast statistics to identify your own user database. To implement custom data the `caast.setUser` method is available on the Caast instance. Adding informations will alter the `user` data on returned informations. To see what data looks like, please refer to [user](library/data.md#user) data informations.

```javascript
caast.setUser({
  email: 'd.copperfield@abracadabra.io',
  first_name: 'David',
  last_name: 'Copperfield',
});
```

## reboot _[main library only]_

Caast expose a reboot method in order easily rebuild Caast if you need it.

```javascript
caast.reboot();
```

## kill _[main library only]_

Caast expose a kill method in order easily kill Caast if you need it. Note that this method will totally remove Caast from the DOM and the window object, so you will need to load the library again if this function is executed.

```javascript
caast.kill();
```

## cookiesAccepted

In order to be compliant with [GDPR](advanced/gdpr.md) restrictions, you may want to ask consent from your user before Caast place a cookie on your website. Once a user has accepted your Cookies policies, you just have to call `caast.cookiesAccepted` in order to allow Caast to place a cookie, you can find more details about it [here](advanced/gdpr.md#cookie).

The `caast.cookiesAccepted` method return a promise.

```javascript
caast.cookiesAccepted().then(function () {
  console.log('Caast just place a cookie on your website !');
});
```

## cookiesRejected

In order to be compliant with [GDPR](advanced/gdpr.md) restrictions, you may want to be able to update Caast behaviour if cookie deposit is now revoked. Once a user has updated your Cookies policies, you just have to call `caast.cookiesRejected` in order to tell Caast to remove the inplace cookie and prevent further cookie deposit until user preference has changed. You can find more details about it [here](advanced/gdpr.md#cookie).

The `caast.cookiesRejected` method return a promise.

```javascript
caast.cookiesRejected().then(function () {
  console.log('Caast has deleted its cookie on your website !');
});
```

## on

Caast Library will emit events accross different lifecycle of the application. Those events will allow you to retrieve lots of usefull informations in order to push events into your analytics, CRM or custom tracking events.

The Caast `on` method receive two parameters, the first one is a `string` refering to an available [events](library/events.md), and the second parameter is a `function` receiving data as a parameter. The `on` method will then return a promise.

?> Note that the returned data will merge global Caast configuration and specific data regarding the called event. More informations on the [events](library/events.md) section.

```javascript
// Basic - Listen to events when a user submit a message in chat
caast.on('onMessageSubmit', function (data) {
  console.log('your custom function receiving data', data);
});

// Advanced - Listen to events when a user submit a message in chat but check if promise is resolved or rejected.
caast
  .on('onMessageSubmit', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onMessageSubmit::subscribed', response);
  })
  .catch(function (error) {
    console.log('onMessageSubmit::error', error);
  });
```

## off

To stop listening to an event, simply call the `caast.off` method on one of the available [events](library/events.md). To implement it simply call the method when Caast is ready. It is best to assume you've start istening to an event before shutting it, but Caast Library will raise no error if you call `caast.off` on a non-listened event.

```javascript
// Stop listening to events when a user submit a message in chat
caast.off('onMessageSubmit');
```

## open

You may want to manually trigger the modal for a live which may not be loaded on the current page. This function allow you to pass a live `uid` as a parameter and will then open the Caast modal.

```javascript
caast.open('f20aa128931a449b9478f5fb69e07c3b');
```

## parse

Caast has what we call a preload function, which will seek in our database if a live must be displayed on a page, if not, Caast main library is not loaded. You may encounter a perticular case where you want to render on your side the display of a bunch of lives but also want to trigger the Caast modal on click. Rather than adding `caast.open` on each of your element, you can call the parse function which will toggle Caast on specifics elements.

This function will seek elements containing the `[data-caast-open]` attribute, you must also add the `[data-caast-id]` attribute which will contain the live uid you want to trigger.

?> To retrieve a live UID, simply go to your Caast adminsitration interface, edit the desired live, and copy the uid available in the URL ![Caast live UID](/_media/url-live-uid.png)

If you element is clicked Caast will add the `[data-caast-loading]=true` attribute while the modal content is loading, it can allow you to display a visual feedback while the content is being fetched.

Once your HTML is ready, you just need to [call the caast library](/library/README.md) and call the `caast.parse()` function once Caast is available.

```html
<!-- We assume that you have already included Caast -->

<div class="my-product">
  <strong>Product 1</strong>
  <button data-caast-open data-caast-id="f20aa128931a449b9478f5fb69e07c3b">
    View the live !
  </button>
</div>

<div class="my-product">
  <strong>Product 2</strong>
</div>

<div class="my-product">
  <strong>Product 3</strong>
  <button data-caast-open data-caast-id="c8542679eb3344aa83e1f39d1477d3f5">
    View the live !
  </button>
</div>

<script type="text/javascript">
  document.addEventListener('caast.onLoaded', function (e) {
    caast.parse();
  });
<script>
```

You can see a demo here to better understand how this function work.

[Open codesandbox](https://codesandbox.io/s/caast-parse-example-docr0?file=/index.html)
