# Tracking

You may want to retrieve some statistics Caast is emiting on his lifecycle. To insert those events into your own data solution, you may find this code useful.

!> Collecting data is subject of user's approval throught your own GDPR policies, please be sure to use those scripts after user has given his consent.

<!-- select:start -->
<!-- select-menu-labels: Available solutions -->

#### --Google DataLayer --

```js
/**
 * Send Caast events into the dataLayer
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (response) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.dataLayer !== 'undefined') {
            //********************************************************//
            //																												//
            // The dataLayer keys must be adapted to fit your need		//
            //																												//
            //********************************************************//
            window.dataLayer.push({
              eventCategory: 'live',
              eventAction: event_name,
              eventLabel: live_id,
              event: 'basic',
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

#### --Google Analytics (ga.js)--

```js
/**
 * Send Caast events into the ga.js
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (data) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.ga !== 'undefined') {
            //********************************************************//
            //																												//
            // The send keys must be adapted to fit your need					//
            //																												//
            //********************************************************//
            window.ga('send', {
              hitType: 'event',
              eventCategory: 'live',
              eventAction: event_name,
              eventLabel: live_id,
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

#### --Google Analytics (gtag.js)--

```js
/**
 * Send Caast events into the gtag
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (data) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.gtag !== 'undefined') {
            //********************************************************//
            //																												//
            // The send keys must be adapted to fit your need					//
            //																												//
            //********************************************************//
            window.gtag('event', event_name, {
              eventCategory: 'live',
              eventLabel: live_id,
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

<!-- select:end -->

## Filtering events

Caast is emitting a lots of events (detailed list available [here](/library/events.md)) so you may want to retrieve only a set of specific events. To retrieve only some events you could use the following code and adapt it to stick to your needs. Simply adapt the `whitelist_events` variable to contain only the needed events

<!-- select:start -->
<!-- select-menu-labels: Available solutions -->

#### --Google DataLayer --

```js
/**
 * Send Caast filtered events into the dataLayer
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (response) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           *  Caast whitelist events
           * */
          var whitelist_events = [
            'onModalShow',
            'onModalClose',
            'onLivePlay',
            'onLivePause',
            'onProductClick',
            'onProductDetailsClick',
            'onProductDetailsShow',
            'onProductOpen',
            'onQuestionClick',
            'onBasketAdd',
            'onShare',
          ];

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.dataLayer !== 'undefined' && whitelist_events.indexOf(event_name) > -1) {
            //********************************************************//
            //																												//
            // The dataLayer keys must be adapted to fit your need		//
            //																												//
            //********************************************************//
            window.dataLayer.push({
              eventCategory: 'live',
              eventAction: event_name,
              eventLabel: live_id,
              event: 'basic',
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

#### --Google Analytics (ga.js)--

```js
/**
 * Send Caast filtered events into the ga.js
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (data) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           *  Caast whitelist events
           * */
          var whitelist_events = [
            'onModalShow',
            'onModalClose',
            'onLivePlay',
            'onLivePause',
            'onProductClick',
            'onProductDetailsClick',
            'onProductDetailsShow',
            'onProductOpen',
            'onQuestionClick',
            'onBasketAdd',
            'onShare',
          ];

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.ga !== 'undefined' && whitelist_events.indexOf(event_name) > -1) {
            //********************************************************//
            //																												//
            // The send keys must be adapted to fit your need					//
            //																												//
            //********************************************************//
            window.ga('send', {
              hitType: 'event',
              eventCategory: 'live',
              eventAction: event_name,
              eventLabel: live_id,
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

#### --Google Analytics (gtag.js)--

```js
/**
 * Send Caast filtered events into the gtag
 * */
var checkExist = setInterval(function () {
  if (typeof window.caast !== 'undefined') {
    if (typeof window.caastIsListening === 'undefined') {
      window.caast
        .on('all', function (data) {
          /**
           *  Caast event name
           * */
          var event_name = response.type;

          /**
           *  Caast whitelist events
           * */
          var whitelist_events = [
            'onModalShow',
            'onModalClose',
            'onLivePlay',
            'onLivePause',
            'onProductClick',
            'onProductDetailsClick',
            'onProductDetailsShow',
            'onProductOpen',
            'onQuestionClick',
            'onBasketAdd',
            'onShare',
          ];

          /**
           * Retrieve product ref if available
           * */
          var product_ref = '';
          if (response.data.product_ref) {
            product_ref = response.data.product_ref;
          }

          /**
           * Retrieve live id if available
           * */
          var live_id = '';
          if (response.data.live_id) {
            live_id = response.data.live_id;
          } else if (response.data.live && response.data.live.id) {
            live_id = response.data.live.id;
          } else if (response.data.currentLive && response.data.currentLive.id) {
            live_id = response.data.currentLive.id;
          }

          if (typeof window.gtag !== 'undefined' && whitelist_events.indexOf(event_name) > -1) {
            //********************************************************//
            //																												//
            // The send keys must be adapted to fit your need					//
            //																												//
            //********************************************************//
            window.gtag('event', event_name, {
              eventCategory: 'live',
              eventLabel: live_id,
            });
          }
        })
        .then(function () {
          window.caastIsListening = true;
        });
    }
    clearInterval(checkExist);
  }
}, 500);
```

<!-- select:end -->
