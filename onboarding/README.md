# Hello {{CUSTOMER}}, welcome to Caast ! <!-- {docsify-ignore-all} -->

We are glad to start working with you 😃. In order to simplify your Caast implementation on your website, you will find here all the mandatory information in order to integrate Caast on your website.

#### Let's install Caast Widget and Landing

This script is used to render Caast widget on a product page, a landing on a dedicated page or anything else related to Caast live display.

To insert Caast on a page it is a **really simple** operation. This script can either be called via any Tag Management solution (Google Tag Manager, Commander Acts etc..) or directly in the HTML of the targeted page.

```html
<script type="text/javascript">
  // Caast integration for {{CUSTOMER}}
  var APP_ID = '{{APP_ID}}';
  var APP_KEY = '{{APP_KEY}}';
  (function (c, a, A, s, t, J, S) {
    (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
    J.async = 1;
    J.src = s;
    J.id = 'caast_library';
    S.parentNode.insertBefore(J, S);
  })(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caast.js?APP_ID=' + APP_ID + '&APP_KEY=' + APP_KEY, 'caast');
</script>
```

You can find more information about [Caast library](library/README.md) or [Caast Landing](library/landing.md).

#### Let's install Caast Purchase Tracking

Now that Caast is live, you may also want to track users's checkout in order to track conversions on your website. **This snippet must be placed on your checkout page, right after a user successfully buy something on your website.**

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

#### That's all

Caast is now ready to display lives and record your viewers actions, do not hesitate to have a look on our documentation to customize Caast to your usage or contact us if you have any doubt or questions about Caast.

Have a nice Live !

The Caast Team
