# Emitted events

The Caast Library will also emit some custom events in order to implement some code on your side. Those events are emitted on each widget action and return some custom data. Please refer to the [data section](library/data.md) if you want details about what information is available. You can listen for events in the Caast Library by attaching a callback using .on().

Before listening to any event, please make sure the Caast Library is ready using this snippet. `e.detail` contain information regarding the current available configuration on your instance.

```javascript
document.addEventListener('caast.onLoaded', function (e) {
  console.log('caast.onLoadComplete', e.detail);
  // here start subscribe to any events
});
```

## All events

This event is emitted when any other event is triggered. It returns an object containing two attributes: type (with the received event name) and data (with the event data).

```javascript
caast
  .on('all', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('all::subscribed', response);
  })
  .catch(function (error) {
    console.log('all::error', error);
  });
```


## onSetUser

This event is emitted when the [`setUser`](library/methods.md#setUser) method is triggered.

```javascript
caast
  .on('onSetUser', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onSetUser::subscribed', response);
  })
  .catch(function (error) {
    console.log('onSetUser::error', error);
  });
```

## onCookiesAccepted

This event is emitted when the [`cookiesAccepted`](library/methods.md#cookiesAccepted) method is triggered.

```javascript
caast
  .on('onCookiesAccepted', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onCookiesAccepted::subscribed', response);
  })
  .catch(function (error) {
    console.log('onCookiesAccepted::error', error);
  });
```

## onCookiesRejected

This event is emitted when the [`cookiesRejected`](library/methods.md#cookiesRejected) method is triggered.

```javascript
caast
  .on('onCookiesRejected', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onCookiesRejected::subscribed', response);
  })
  .catch(function (error) {
    console.log('onCookiesRejected::error', error);
  });
```

## onRouteChange

This event is emitted when a Single Page App change current url.

```javascript
caast
  .on('onRouteChange', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onRouteChange::subscribed', response);
  })
  .catch(function (error) {
    console.log('onRouteChange::error', error);
  });
```

## onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onLiveSubscription', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onLiveSubscription::subscribed', response);
  })
  .catch(function (error) {
    console.log('onLiveSubscription::error', error);
  });
```

## onLivePlay

This event is emitted when a user press play on the Caast Player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

```javascript
caast
  .on('onLivePlay', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onLivePlay::subscribed', response);
  })
  .catch(function (error) {
    console.log('onLivePlay::error', error);
  });
```

## onLivePause

This event is emitted when a user press pause on the Caast Player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

```javascript
caast
  .on('onLivePause', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onLivePause::subscribed', response);
  })
  .catch(function (error) {
    console.log('onLivePause::error', error);
  });
```

## onVoteForLive

This event is emitted when a user has request a live on a product. Please refer to [url](library/data.md#url) for additional returned data.

```javascript
caast
  .on('onVoteForLive', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onVoteForLive::subscribed', response);
  })
  .catch(function (error) {
    console.log('onVoteForLive::error', error);
  });
```

## onQuestionClick

This event is emitted when a user click on a question. Please refer to [question_id](library/data.md#question_id) for additional returned data.

```javascript
caast
  .on('onQuestionClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onQuestionClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onQuestionClick::error', error);
  });
```

## onProductClick

This event is emitted when a user click on a product to jump to its presentation on a replay. Please refer to [product_id](library/data.md#product_id) for additional returned data.

```javascript
caast
  .on('onProductClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onQuestionClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onQuestionClick::error', error);
  });
```

## onProductDetailsClick

This event is emitted when an user click to see product's details. Please refer to [product_id](library/data.md#product_id) for additional returned data.

```javascript
caast
  .on('onProductDetailsClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onProductDetailsClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onProductDetailsClick::error', error);
  });
```

## onLiveTabClick

This event is emitted when a user switch tab inside the caast modal. It returns a "tab" attribute with the tab name. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onLiveTabClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onLiveTabClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onLiveTabClick::error', error);
  });
```

## onRelatedClick

This event is emitted when a user click on a related replay video. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onRelatedClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onRelatedClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onRelatedClick::error', error);
  });
```

## onMessageSubmit

This event is emitted when a user submit a message in Caast Chat. Please refer to [message](library/data.md#message) for additional returned data.

```javascript
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

## onBasketAdd

This event is emitted when a user add an item to cart, this event can be emitted by a custom selector on the webpage add to cart button or via the Caast Widget direct add to cart action. This event won't be emitted if the target DOM element or the direct add to cart action is not set in the app configuration. Please refer to [live_id](library/data.md#live_id), [product_id](library/data.md#product_id), [product_ref](library/data.md#product_ref) and [from_caast](library/data.md#from_caast) for additional returned data.

```javascript
caast
  .on('onBasketAdd', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onBasketAdd::subscribed', response);
  })
  .catch(function (error) {
    console.log('onBasketAdd::error', error);
  });
```

## onModalTrigger

This event is emitted when a user click on the button to open the modal. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalTrigger', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onModalTrigger::subscribed', response);
  })
  .catch(function (error) {
    console.log('onModalTrigger::error', error);
  });
```

## onModalShow

This event is emitted when the live modal is opened. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalShow', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onModalShow::subscribed', response);
  })
  .catch(function (error) {
    console.log('onModalShow::error', error);
  });
```

## onModalClose

This event is emitted when the live modal is closed. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalClose', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onModalClose::subscribed', response);
  })
  .catch(function (error) {
    console.log('onModalClose::error', error);
  });
```

## onReminderClick

This event is emitted when the user click on the reminder button. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onReminderClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onReminderClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onReminderClick::error', error);
  });
```

## onPhoneReminderClick

This event is emitted once the user is inside the reminder dropdown and click on the phone reminder option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onPhoneReminderClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onPhoneReminderClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onPhoneReminderClick::error', error);
  });
```

## onPhoneReminderSubmitted

This event is emitted when the user successfully send his phone number to get a reminder when the live will starts. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onPhoneReminderSubmitted', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onPhoneReminderSubmitted::subscribed', response);
  })
  .catch(function (error) {
    console.log('onPhoneReminderSubmitted::error', error);
  });
```

## onGoogleCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Google Calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onGoogleCalendarClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onGoogleCalendarClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onGoogleCalendarClick::error', error);
  });
```

## onOutlookCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Outlook calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onOutlookCalendarClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onOutlookCalendarClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onOutlookCalendarClick::error', error);
  });
```

## onAppleCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Apple calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onAppleCalendarClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onAppleCalendarClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onAppleCalendarClick::error', error);
  });
```

## onYahooCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Yahoo calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onYahooCalendarClick', function (data) {
    console.log('your custom function receiving data', data);
  })
  .then(function (response) {
    console.log('onYahooCalendarClick::subscribed', response);
  })
  .catch(function (error) {
    console.log('onYahooCalendarClick::error', error);
  });
```
