# Getting started

<!-- select:start -->
<!-- select-menu-labels: Installation mode -->

#### --Simple--

To load the Caast Library on your website you just need to add this code at the end of your `body` tag element.

```html
<script type="text/javascript">
  // Replace those values by those available in your administration interface
  var CAAST_APP_ID = 'YOUR_APP_ID';
  var CAAST_APP_KEY = 'YOUR_APP_KEY';
  (function (c, a, A, s, t, J, S) {
    if (!a.getElementById('caast_library')) {
      (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
      J.async = 1;
      J.src = s;
      J.id = 'caast_library';
      S.parentNode.insertBefore(J, S);
    }
  })(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caast.js?APP_ID=' + CAAST_APP_ID + '&APP_KEY=' + CAAST_APP_KEY, 'caast');
</script>
```

With this simple snippet Caast Library is now running on your website, lets have a look on advanced configuration in order to customize the Caast Library.

#### --Advanced--

Advanced mode will give you full control over how Caast should behave on your website. By default Caast will send to our APIs the current url and check if a live is linked to it. 99% of the times this method will fill your needs, but in some case the url is not enought to check if content are availables, for exemple you may want to check if caast is linked to the current product reference or the current seller identifier if you own a marketplace.

To implement advanced mode you can call Caast with the following code:

```html
<script type="text/javascript">
  window.caastSettings = {
    app_id: 'YOUR_APP_ID',
    app_key: 'YOUR_APP_KEY',
    autoboot: true,
    product_id: 'YOUR_PRODUCT_ID',
    seller_id: 'YOUR_SELLER_ID',
  };
  (function (c, a, A, s, t, J, S) {
    if (!a.getElementById('caast_library')) {
      (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
      J.async = 1;
      J.src = s;
      J.id = 'caast_library';
      S.parentNode.insertBefore(J, S);
    }
  })(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caast.js', 'caast');
</script>
```

As you can see you now have a `window.caastSettings` object, the available parameters are detailed here:

| key name   | type    | description                                                                                                                                               |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| app_id     | string  | Your APP_ID, available in your App dashboard                                                                                                              |
| app_key    | string  | Your APP_KEY, available in your App dashboard                                                                                                             |
| autoboot   | boolean | If set to false, caast will not automatically boot, you will have to manually call the `caast.render()` method in order to trigger caast flow and display |
| product_id | string  | If set, Caast will perform a lookup on our APIs if a live or a video is available for this particular product_id                                          |
| seller_id  | string  | If set, Caast will perform a lookup on our APIs if a live or a video is available for this particular seller_id                                           |

?> Note that `product_id` and `seller_id` can be cumulated

<strong>A note about autoboot</strong>

The autoboot options allows you to have full control about when Caast should start fetchoing the database and display process [see how it works here](/advanced/how-to.md). If you set the autoboot parameter to `false`, you will have to use the `caast.render` method. This method is heavily [detailed here](/library/methods.md#render) but the Caast team will help you to setup this process if you need to.

<!-- select:end -->
