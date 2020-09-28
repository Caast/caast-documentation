# Available methods

Caast Library expose some methods to allow you to perform operations on your site. Those methods are described here. We assume that you are implementing those methods after Caast Library emitted the `caast.onReady` event on the DOM.

```javascript
document.addEventListener("caast.onReady", function (e) {
  // Start adding methods here, calling the caast instance
});
```

## infos

Caast expose a rather useful method in order to easily check, wich version of Caast Library you are running on. Run it and you will receive an object indicating the version you are running but also the actual environnement.

```javascript
caast.infos();
```

## setUser

You may want to add additionnal informations to your Caast Library user object, it can be useful when interacting with Caast statistics to identify your own user database. To implement custom data the `caast.setUser` method is available on the Caast instance. Adding informations will alter the `user` data on returned informations. To see what data looks like, please refer to [user](library/data.md#user) data informations.

```javascript
caast.setUser({
  email: "d.copperfield@abracadabra.io",
  first_name: "David",
  last_name: "Copperfield",
});
```

## on

Caast Library will emit events accross different lifecycle of the application. Those events will allow you to retrieve lots of usefull informations in order to push events into your analytics, CRM or custom tracking events.

The Caast `on` method receive two parameters, the first one is a `string` refering to an available [events](library/events.md), and the second parameter is a `function` receiving data as a parameter. The `on` method will then return a promise.

?> Note that the returned data will merge global Caast configuration and specific data regarding the called event. More informations on the [events](library/events.md) section.

```javascript
// Basic - Listen to events when a user submit a message in chat
caast.on("onMessageSubmit", function (data) {
  console.log("your custom function receiving data", data);
});

// Advanced - Listen to events when a user submit a message in chat but check if promise is resolved or rejected.
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

## off

To stop listening to an event, simply call the `caast.off` method on one of the available [events](library/events.md). To implement it simply call the method when Caast is ready. It is best to assume you've start istening to an event before shutting it, but Caast Library will raise no error if you call `caast.off` on a non-listened event.

```javascript
// Stop listening to events when a user submit a message in chat
caast.off("onMessageSubmit");
```
