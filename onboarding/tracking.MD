# Hello {{CUSTOMER}}, welcome to Caast ! <!-- {docsify-ignore-all} -->

We are glad to start working with you 😃. In order to simplify your Caast implementation on your website, you will find here all the mandatory information in order to integrate Caast Tracking on your website.

#### Let's install Caast Purchase Tracking

You may also want to track users's checkout in order to track conversions on your website. **This snippet must be placed on your checkout page, right after a user successfully buy something on your website.**

With this simple snippet, Caast will be able to track your users orders, to establish proper statistics mixed with Caast analytics. To make it clear, if a user watched a live and bought something, it will be available on Caast analytics, so we **really recommend** to implement this script to clearly identify your data and better track your ROI.

!>Note that this example is using static data, **you must pass dynamic data to Caast**, retrieved from the current checkout process

```html
<script type="text/javascript">
  // Caast Purchase Tracking integration for {{CUSTOMER}}
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
    'APP-ID': '{{APP_ID}}',
    'APP-KEY': '{{APP_KEY}}',
  });
  //  This data must be customized for your site, but we expect at least a total and an array of products
  //  with at least those information.
  caastEmitter('track', {
    total: 499,
    products: [
      { id: 'ref1', quantity: 1, price: 100 },
      { id: 'ref2', quantity: 1, price: 399 },
    ],
  });
</script>
```

You can find more information about Caast Purchase Tracking [here](emitter/README.md)
