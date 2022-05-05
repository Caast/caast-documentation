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

## infos

Caast expose a rather useful method in order to easily check, wich version of Caast Library you are running on. Run it and you will receive an object indicating the version you are running but also the actual environnement.

```javascript
caast.infos();
```

## kill

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
caast.on('onMessageSubmit', function (response) {
  console.log('your custom function receiving response', response);
});

// Advanced - Listen to events when a user submit a message in chat but check if promise is resolved or rejected.
caast
  .on('onMessageSubmit', function (response) {
    console.log('your custom function receiving response', response);
  })
  .then(function (status) {
    console.log('onMessageSubmit::subscribed', status);
  })
  .catch(function (error) {
    console.log('onMessageSubmit::error', error);
  });
```

## off

To stop listening to an event, simply call the `caast.off` method on one of the available [events](library/events.md). To implement it simply call the method when Caast is ready. It is best to assume you've start listening to an event before shutting it, but Caast Library will raise no error if you call `caast.off` on a non-listened event.

```javascript
// Stop listening to events when a user submit a message in chat
caast.off('onMessageSubmit');
```

## open

You may want to manually trigger the modal for a live which may not be loaded on the current page. This function allow you to pass a live `uid` as a parameter and will then open the Caast modal ([how to get my live UID](/advanced/find-live-uid.md)).

```javascript
caast.open('f20aa128931a449b9478f5fb69e07c3b');
```

This method also gives you the possibility to trigger the Caast Modal by passing a product reference instead of a live UID.

```javascript
caast.open({ type: 'product', id: 'PID_3U975987' });
```

## parse

<span style="color: #fff"><i>This method is part of the initial loading of Caast</i></span>

Caast has what we call a preload function, which will seek in our database if a content must be displayed on a page, if not, Caast main library is not loaded. You may encounter a perticular case where you want to render on your side the display of a bunch of lives but also want to trigger the Caast modal on click. Rather than adding `caast.open` on each of your element, you can call the parse function which will toggle Caast on specifics elements.

This function will seek elements containing the `[data-caast-open]` attribute, you must also add the `[data-caast-id]` attribute which will contain the live uid you want to trigger ([how to get my live UID](/advanced/find-live-uid.md)).

This method also work if you want to trigger a content based on a product ref/sku, you must add the `[data-caast-pid]` attribute which will contain the product ref/sku.

If your element is clicked Caast will add the `[data-caast-loading]=true` attribute while the modal content is loading, it can allow you to display a visual feedback while the content is being fetched.

Note that the Caast boot method will try to automaticaly execute this function.

```html
<!-- We assume that you have already included Caast -->

<div class="my-product">
  <strong>Product 1</strong>
  <button data-caast-open data-caast-id="f20aa128931a449b9478f5fb69e07c3b">View the live !</button>
</div>

<div class="my-product">
  <strong>Product 2</strong>
</div>

<div class="my-product">
  <strong>Product 3</strong>
  <button data-caast-open data-caast-pid="SKU_893794">View the live !</button>
</div>
```

## embed

<span style="color: #fff"><i>This method is part of the initial loading of Caast</i></span>

Caast has what we call a preload function, which will seek in our database if a live must be displayed on a page, if not, Caast main library is not loaded. You may encounter a particular case where you want to render on your side the display of a preview card but also want to trigger the Caast modal on click. A bit like a youtube embed.

This function will seek elements containing the `[data-caast-embed]` attribute in the DOM, you must also add the `[data-caast-id]` attribute which will contain the live uid you want to trigger ([how to get my live UID](/advanced/find-live-uid.md)).

If your element is clicked Caast will add the `[data-caast-loading]=true` attribute while the modal content is loading, it can allow you to display a visual feedback while the content is being fetched.

Note that the Caast boot method will try to automaticaly execute this function.

```html
<!-- We assume that you have already included Caast -->

<div class="my-blog-template">
  <h1>My blog title</h1>
  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam molestie, arcu in semper suscipit, orci nunc convallis velit, non mattis diam diam ut
    arcu. Nulla facilisi. Aliquam erat volutpat. Sed tincidunt magna nulla, a malesuada urna faucibus eu. Aenean et faucibus purus. Quisque quis
    lectus tincidunt, dictum velit nec, imperdiet neque. Sed ut imperdiet purus. Proin consequat sem nec lectus placerat facilisis. Vivamus facilisis
    urna id purus lacinia, vitae consectetur enim rutrum. Ut eget felis ut ipsum imperdiet convallis et vitae eros. Vivamus mattis nunc vel lectus
    pharetra varius. Morbi tincidunt sem leo, ut rhoncus magna tincidunt ac. Duis semper, eros non facilisis fringilla, justo elit consectetur ante,
    ut rutrum risus dolor cursus orci. Aliquam ultricies tempus lorem ac semper. Etiam dictum odio turpis, ut iaculis leo bibendum nec.
  </p>

  <div data-caast-embed data-caast-id="c8542679eb3344aa83e1f39d1477d3f5"></div>

  <p>
    Nam et mollis nulla, vel viverra risus. Vestibulum justo tortor, tempus eu bibendum vel, molestie id elit. Quisque aliquam mi ut tellus laoreet,
    nec fermentum velit luctus. Suspendisse non massa libero. Donec interdum ornare ipsum, vitae laoreet orci rutrum eget. Donec aliquet tellus vel
    massa pulvinar scelerisque vitae et libero. Integer vel sapien luctus, suscipit massa a, cursus nisi. Nullam quis tellus quis enim convallis
    vestibulum ac quis tellus. Nam scelerisque vulputate cursus. Suspendisse gravida enim sagittis, tincidunt nisl in, interdum quam. Ut diam nibh,
    ultricies fermentum eros sit amet, tincidunt porttitor sapien. Ut consectetur lacus sed malesuada pretium.
  </p>
</div>
```

## render

You may want to manually render the Caast DOM. Our common way to display Caast, is to parse the current url and check on our APIs if something need to be displayed on this particular page. Nevertheless you may want to have a full control of this aspect. The `caast.render` method is there for you.

Please refer to [this documentation](/library/README.md?mode=advanced) because this method need previous configuration.

The render method accepts different parameters, details are presented here:

| Property | Type             | Description                                                                                                                                                                                                                                         |
| -------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| target   | string \| object | The target where the Caast DOM will be injected. you can provide a string that will be used as a querySelector value or an advanced object described below. If nothing is provided Caast will render the DOM in the target defined in configuration |
| query    | object           | An object of values described below, that can be used to perform the Caast query instead of the current url value. If empty, Caast will be based upon current URL                                                                                   |

### target <!-- {docsify-ignore} -->

The target property can either be a string representing a querySelector value, or an advanced object described below

| Property | Type            | Description                                                                                                                                                                                                                         |
| -------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| desktop  | string\| object | The target where the Caast DOM for desktop experience will be injected. You can provide a string that will be used as a querySelector value or an advanced target object, [please refer to this documentation](/advanced/target.md) |
| mobile   | string\| object | The target where the Caast DOM for mobile experience will be injected. You can provide a string that will be used as a querySelector value or an advanced target object, [please refer to this documentation](/advanced/target.md)  |

```javascript
caast.render({ target: '#my-target' });
caast.render({
  target: {
    desktop: {
      element: '#my-target-desktop',
      position: 'afterbegin',
    },
    mobile: {
      element: '#my-target-mobile',
      position: 'afterbegin',
    },
  },
});
caast.render({
  target: { desktop: '#my-target-desktop', mobile: '#my-target-mobile' },
});
```

### query <!-- {docsify-ignore} -->

| Property   | Type   | Description                                                     |
| ---------- | ------ | --------------------------------------------------------------- |
| product_id | string | The product SKU that is matching the ref field in our database  |
| seller_id  | string | The seller UID that is matching the external id in our database |

```javascript
caast.render({ query: { product_id: 'SKU_765KJHKJ' } });
caast.render({ query: { seller_id: '98279574' } });
caast.render({ query: { product_id: 'SKU_765KJHKJ', seller_id: '98279574' } });
```

?> You can also totally omit the query options, and rely on the settings you've defined previously via the [advanced setup](/library/README.md?mode=advanced). If nothing is provided, the render method will seek for contents matching the current url.

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
