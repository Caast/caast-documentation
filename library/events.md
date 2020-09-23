# Emitted events

The Caast Library will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data. Please refer to the [data section](library/data.md) if you want details about what information is available. You can listen for events in the widget by attaching a callback using .on().

Before listening to any event, please make sure the Caast widget is ready using this snippet. `e.detail` contain information regarding the current available configuration on your widget instance.

```javascript
document.addEventListener("caast.onReady", function (e) {
  console.log("caast.onLoadComplete", e.detail);
  // here start subscribe to any events
});
```

## onSetUser

This event is emitted when the [`setUser`](library/methods.md#setUser) method is triggered.

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

## onRouteChange

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

## onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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

## onLivePlay

This event is emitted when a user press play on the live player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

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

## onLivePause

This event is emitted when a user press pause on the live player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

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

## onVoteForLive

This event is emitted when a user has request a live on a product. Please refer to [url](library/data.md#url) for additional returned data.

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

## onQuestionClick

This event is emitted when a user click on a question. Please refer to [question_id](library/data.md#question_id) for additional returned data.

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

## onRelatedClick

This event is emitted when a user click on a related replay video. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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

## onMessageSubmit

This event is emitted when a user submit a message in chat. Please refer to [message](library/data.md#message) for additional returned data.

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

## onBasketAdd

This event is emitted when a user add an item to his basket, this event won't emit if the target DOM element is not set in the app configuration. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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

## onModalTrigger

This event is emitted when a user click on the button to open the modal. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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

## onModalShow

This event is emitted when the live modal is opened. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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

## onModalClose

This event is emitted when the live modal is closed. Please refer to [live_id](library/data.md#live_id) for additional returned data.

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
