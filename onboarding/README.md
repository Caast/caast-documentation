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
  })(
    window,
    document,
    'script',
    'https://cdn.caast.tv/caast-latest/caast.js?APP_ID=' +
      APP_ID +
      '&APP_KEY=' +
      APP_KEY,
    'caast'
  );
</script>
```

You can find more information about [Caast library](library/README.md) or [Caast Landing](library/landing.md).

?>If you want further informations about installing Caast Purchase Tracking, please click [here](onboarding/tracking.md?CUSTOMER={{CUSTOMER}}&APP_ID={{APP_ID}}&APP_KEY={{APP_KEY}})

#### That's all

Caast is now ready to display lives, do not hesitate to have a look on our documentation to customize Caast to your usage or contact us if you have any doubt or questions about Caast.

Have a nice Live !

The Caast Team
