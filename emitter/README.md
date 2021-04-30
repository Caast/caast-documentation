# Caast Emitter

Caast emitter is a pixel tracking javascript library allowing you to easily send purchased items on your purchase page. It will allow you to send qualified data to Caast in order to properly identify your ROI.

## Getting started

```javascript
(function (c, a, A, s, t, j, S) {
  'caastEmitter' in c ||
    ((c.caastEmitter = function () {
      c.caastEmitter.q.push(arguments);
    }),
    (c.caastEmitter.q = []));
  (j = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
  j.src = s;
  j.async = 1;
  S.parentNode.insertBefore(j, S);
})(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caastEmitter.js', 'caastEmitter');
caastEmitter('init', {
  'APP-ID': 'MY_APP_ID',
  'APP-KEY': 'MY_APP_KEY',
});
```

## Caast strict mode

You can also decide to push to Caast API only the products related to the ones you have in our system. Adding `onlyCaastProducts: true` on the `init` method, will perform a check on the `products` key defined in the track method. With this parameter, we will only register purchase items if they containe one of our product. In this way, you can be sure that purchase which are non-related to Caast, won't be registered in our database.

```javascript
caastEmitter('init', {
  'APP-ID': 'MY_APP_ID',
  'APP-KEY': 'MY_APP_KEY',
  onlyCaastProducts: true,
});
```

## Track purchase

Once caastEmitter is instanciated, you can invoke this method to send to Caast, purchase informations about the validated checkout.

```javascript
caastEmitter('track', {
  total: 499,
  products: [
    { id: '1', quantity: 1, price: 100 },
    { id: '2', quantity: 1, price: 399 },
  ],
});
```

!> This is an example with static data, **you must send dynamic informations based on the current checkout data**.

## Data properties

| Clé de propriété | Type de valeur   | Description du paramètre                                                                                                                                                                                                                                                                                                          |
| ---------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| total            | integer or float | Total value of the purchase operation                                                                                                                                                                                                                                                                                             |
| products         | array of objects | Array of json objects with the unique product identifier referenced in caast's registered products, you can also specify `quantity` and `price`, price will refer to product price, not total price based on price \* quantity. _Obligatoire_: `id` et `quantity`. Exemple : `[{'id': 'ABC123', 'quantity': 2, 'price': 119.99}]` |

### Advanced details about products data

When you trigger the [track purchase method](emitter/README.md#track-purchase), there are some mandatory datas to pass to Caast in order to have perfect statistics. Let's take this example:

```javascript
caastEmitter('track', {
  total: 299, // The total amount of the purchase
  products: [
    {
      id: '1', // The id must match the product ref in our database
      quantity: 1, // The quantity for this product
      price: 299, // the unit price for this product
    },
  ],
});
```

Those informations are mandatory for Caast in order to successfully cross your sells datas and live viewers. Note that you can pass any other custom data for a product if you want be able to perform advanced analysis with your statistics. Example:

```javascript
caastEmitter('track', {
  total: 299, // The total amount of the purchase
  products: [
    {
      id: '1', // The id must match the product ref in our database
      quantity: 1, // The quantity for this product
      price: 299, // the unit price for this product
      productCategory: 12,
      sku: 'P382798',
    },
  ],
});
```
