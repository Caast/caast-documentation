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
  .on('all', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('all::subscribed', status);
  })
  .catch(function (error) {
    console.log('all::error', error);
  });
```

## onSetUser

This event is emitted when the [`setUser`](library/methods.md#setuser-main-library-only) method is triggered.

```javascript
caast
  .on('onSetUser', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onSetUser::subscribed', status);
  })
  .catch(function (error) {
    console.log('onSetUser::error', error);
  });
```

## onCookiesAccepted

This event is emitted when the [`cookiesAccepted`](library/methods.md#cookiesAccepted) method is triggered.

```javascript
caast
  .on('onCookiesAccepted', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onCookiesAccepted::subscribed', status);
  })
  .catch(function (error) {
    console.log('onCookiesAccepted::error', error);
  });
```

## onCookiesRejected

This event is emitted when the [`cookiesRejected`](library/methods.md#cookiesRejected) method is triggered.

```javascript
caast
  .on('onCookiesRejected', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onCookiesRejected::subscribed', status);
  })
  .catch(function (error) {
    console.log('onCookiesRejected::error', error);
  });
```

## onRouteChange

This event is emitted when a Single Page App change current url.

```javascript
caast
  .on('onRouteChange', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onRouteChange::subscribed', status);
  })
  .catch(function (error) {
    console.log('onRouteChange::error', error);
  });
```

## onLiveSubscription

This event is emitted when a user has subscribed to a live in order to be notified when a live is about to start. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onLiveSubscription', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onLiveSubscription::subscribed', status);
  })
  .catch(function (error) {
    console.log('onLiveSubscription::error', error);
  });
```

## onLivePlay

This event is emitted when a user press play on the Caast Player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

```javascript
caast
  .on('onLivePlay', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onLivePlay::subscribed', status);
  })
  .catch(function (error) {
    console.log('onLivePlay::error', error);
  });
```

## onLivePause

This event is emitted when a user press pause on the Caast Player. Please refer to [live_id](library/data.md#live_id) and [player](library/data.md#player) for additional returned data.

```javascript
caast
  .on('onLivePause', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onLivePause::subscribed', status);
  })
  .catch(function (error) {
    console.log('onLivePause::error', error);
  });
```

<!--
## onVoteForLive

This event is emitted when a user has request a live on a product. Please refer to [url](library/data.md#url) for additional returned data.

```javascript
caast
  .on('onVoteForLive', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onVoteForLive::subscribed', status);
  })
  .catch(function (error) {
    console.log('onVoteForLive::error', error);
  });
``` -->

## onQuestionClick

This event is emitted when a user click on a question. Please refer to [question_id](library/data.md#question_id) for additional returned data.

```javascript
caast
  .on('onQuestionClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onQuestionClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onQuestionClick::error', error);
  });
```

## onProductClick

This event is emitted when a user click on a product to jump to its presentation on a replay. Please refer to [product_id](library/data.md#product_id) for additional returned data.

```javascript
caast
  .on('onProductClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onQuestionClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onQuestionClick::error', error);
  });
```

## onProductDetailsClick

This event is emitted when an user click to see product's details. Please refer to [product_id](library/data.md#product_id) for additional returned data.

```javascript
caast
  .on('onProductDetailsClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onProductDetailsClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onProductDetailsClick::error', error);
  });
```

## onProductDetailsShow

This event is emitted after the product's details is displayed inside Caastw. Please refer to [product_id](library/data.md#product_id), [product_ref](library/data.md#product_ref) and [product_detailed](library/data.md#product_detailed) for additional returned data.

```javascript
caast
  .on('onProductDetailsClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onProductDetailsClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onProductDetailsClick::error', error);
  });
```

## onRelatedClick

This event is emitted when a user click on a related replay video. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onRelatedClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onRelatedClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onRelatedClick::error', error);
  });
```

## onMessageSubmit

This event is emitted when a user submit a message in Caast Chat. Please refer to [message](library/data.md#message) for additional returned data.

```javascript
caast
  .on('onMessageSubmit', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onMessageSubmit::subscribed', status);
  })
  .catch(function (error) {
    console.log('onMessageSubmit::error', error);
  });
```

## onBasketAdd

This event is emitted when a user add an item to cart, this event can be emitted by a custom selector on the webpage add to cart button or via the Caast Widget direct add to cart action. This event won't be emitted if the target DOM element or the direct add to cart action is not set in the app configuration. Please refer to [live_id](library/data.md#live_id), [product_id](library/data.md#product_id), [product_ref](library/data.md#product_ref), [product_detailed](library/data.md#product_detailed) and [from_caast](library/data.md#from_caast) for additional returned data.

```javascript
caast
  .on('onBasketAdd', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onBasketAdd::subscribed', status);
  })
  .catch(function (error) {
    console.log('onBasketAdd::error', error);
  });
```

## onProductOpen

This event is emitted when a user click on the button to go to the product page. Please refer to [live_id](library/data.md#live_id), [product_id](library/data.md#product_id), [product_ref](library/data.md#product_ref) and [product_detailed](library/data.md#product_detailed) for additional returned data.

```javascript
caast
  .on('onProductOpen', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onProductOpen::subscribed', status);
  })
  .catch(function (error) {
    console.log('onProductOpen::error', error);
  });
```

## onModalTrigger

This event is emitted when a user click on the button to open the modal. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalTrigger', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onModalTrigger::subscribed', status);
  })
  .catch(function (error) {
    console.log('onModalTrigger::error', error);
  });
```

## onModalShow

This event is emitted when the live modal is opened. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalShow', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onModalShow::subscribed', status);
  })
  .catch(function (error) {
    console.log('onModalShow::error', error);
  });
```

## onModalClose

This event is emitted when the live modal is closed. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onModalClose', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onModalClose::subscribed', status);
  })
  .catch(function (error) {
    console.log('onModalClose::error', error);
  });
```

## onReminderClick

This event is emitted when the user click on the reminder button. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onReminderClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onReminderClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onReminderClick::error', error);
  });
```

## onPhoneReminderClick

This event is emitted once the user is inside the reminder dropdown and click on the phone reminder option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onPhoneReminderClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onPhoneReminderClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onPhoneReminderClick::error', error);
  });
```

## onPhoneReminderSubmitted

This event is emitted when the user successfully send his phone number to get a reminder when the live will starts. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onPhoneReminderSubmitted', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onPhoneReminderSubmitted::subscribed', status);
  })
  .catch(function (error) {
    console.log('onPhoneReminderSubmitted::error', error);
  });
```

## onEmailReminderClick

This event is emitted once the user is inside the reminder dropdown and click on the email reminder option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onEmailReminderClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onEmailReminderClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onEmailReminderClick::error', error);
  });
```

## onEmailReminderSubmitted

This event is emitted when the user successfully send his email to get a reminder when the live will starts. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onEmailReminderSubmitted', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onEmailReminderSubmitted::subscribed', status);
  })
  .catch(function (error) {
    console.log('onEmailReminderSubmitted::error', error);
  });
```

## onGoogleCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Google Calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onGoogleCalendarClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onGoogleCalendarClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onGoogleCalendarClick::error', error);
  });
```

## onOutlookCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Outlook calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onOutlookCalendarClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onOutlookCalendarClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onOutlookCalendarClick::error', error);
  });
```

## onAppleCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Apple calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onAppleCalendarClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onAppleCalendarClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onAppleCalendarClick::error', error);
  });
```

## onYahooCalendarClick

This event is emitted once the user is inside the reminder dropdown and click on the Yahoo calendar option. Please refer to [live_id](library/data.md#live_id) for additional returned data.

```javascript
caast
  .on('onYahooCalendarClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onYahooCalendarClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onYahooCalendarClick::error', error);
  });
```

## onShare

This event is emitted once the user share the live using one of caast UI element. Please refer to [share](library/data.md#share) for additional returned data.

```javascript
caast
  .on('onShare', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onShare::subscribed', status);
  })
  .catch(function (error) {
    console.log('onShare::error', error);
  });
```

## onReaction

This event is emitted once the user click on an emoji to react during a live. Please refer to [live_id](library/data.md#live_id) and [emoji](library/data.md#emoji) for additional returned data.

```javascript
caast
  .on('onReaction', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onReaction::subscribed', status);
  })
  .catch(function (error) {
    console.log('onReaction::error', error);
  });
```

## onExtensionDetailsClick

This event is emitted when an extension card or announcement is clicked. Please refer to [extensionDetails](library/data.md#extensionDetails) for additional returned data.

```javascript
caast
  .on('onExtensionDetailsClick', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onExtensionDetailsClick::subscribed', status);
  })
  .catch(function (error) {
    console.log('onExtensionDetailsClick::error', error);
  });
```

## onExtensionDetailsShow

This event is emitted when an extension iframe has finished loading. Please refer to [extensionDetails](library/data.md#extensionDetails) for additional returned data.

```javascript
caast
  .on('onExtensionDetailsShow', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onExtensionDetailsShow::subscribed', status);
  })
  .catch(function (error) {
    console.log('onExtensionDetailsShow::error', error);
  });
```

## onExtensionDetailsClose

This event is emitted when an extension sidebar is closed. Please refer to [extensionDetails](library/data.md#extensionDetails) for additional returned data.

```javascript
caast
  .on('onExtensionDetailsClose', function (response) {
    console.log('your custom function receiving the response', response);
  })
  .then(function (status) {
    console.log('onExtensionDetailsClose::subscribed', status);
  })
  .catch(function (error) {
    console.log('onExtensionDetailsClose::error', error);
  });
```
