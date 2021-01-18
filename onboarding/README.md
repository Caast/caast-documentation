# Welcome to Caast ! <!-- {docsify-ignore-all} -->

We are glad to start working with you 😃. In order to simplify your Caast implementation on your website, you will find here all the mandatory installation in order to make Caast live on your website.

#### Lets install Caast on your targeted pages

To render Caast on your pages it is a **really simple** operation. You just need one script, one script to rules them all 💍. This script can render the [Caast library](library/README.md) on a product page, but can also render the full [Caast Web TV page](library/listing.md), all the configuration is on our side. This script can either be called via any Tag Commander solution, or directly in the HTML of the targeted page.

```html
<script type="text/javascript">
  // Caast integration for {{CUSTOMER}}
  var APP_ID = "{{APP_ID}}";
  var APP_KEY = "{{APP_KEY}}";
  (function (c, a, A, s, t, J, S) {
    (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
    J.async = 1;
    J.src = s;
    J.id = "caast_library";
    S.parentNode.insertBefore(J, S);
  })(window, document, "script", "https://cdn.caast.tv/caast-latest/caast.js?APP_ID=APP_ID&APP_KEY=APP_KEY", "caast");
</script>
```

You can find more informations about Caast Library [here](library/README.md)

#### Lets install Caast Purchase Tracking

Now that Caast is alive, you may also want to track users buy orders in order to track conversions on your website. With this simple snippet, Caast will be able to track your users orders to establish proper statistics related to the user Caast data. To make it clear, if a user wtached a live and bought something, it will be available on our statistics, so we **really recommend** to implement this script to clearly identify your data.

```html
<script type="text/javascript">
  // Caast Purchase Tracking integration for {{CUSTOMER}}
  (function (c, a, A, s, t, j, S) {
    "caastEmitter" in c ||
      ((c.caastEmitter = function () {
        c.caastEmitter.q.push(arguments);
      }),
      (c.caastEmitter.q = []));
    (j = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
    j.src = s;
    j.async = 1;
    S.parentNode.insertBefore(j, S);
  })(window, document, "script", "https://cdn.caast.tv/caast-latest/caastEmitter.js", "caastEmitter");
  caastEmitter("init", {
    "APP-ID": "{{APP_ID}}",
    "APP-KEY": "{{APP_KEY}}",
  });
  //  This data is customizable on your side, but we expect at least a total and an array of products
  //  with at least those informations.
  caastEmitter("track", {
    total: 499,
    products: [
      { id: "ref1", quantity: 1, price: 100 },
      { id: "ref2", quantity: 1, price: 399 },
    ],
  });
</script>
```

You can find more informations about Caast PUrchase Tracking [here](emitter/README.md)

#### That's all

Caast is now ready to display and record all your viewers actions, do not hesitate to have a look on our documentation to customize Caast to your usage or contact us if you have any doubt or questions about Caast.

Have a nice Live !

The Caast Team
