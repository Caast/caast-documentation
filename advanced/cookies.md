## Informations

Caast will drop a cookie named `CaastFgpData` on your site in order to store a unique identifier for the user navigating on your site. Regarding GDPR user approval, you may want Caast to store a cookie only when a user has accepted your Cookie consentment. To perform this, Caast can be loaded with an optionnal parameter.

All those parameters are available in our administration interface, in your app configuration.

?> Note that if you disable Caast cookies, you won't be able to cross data between live viewers and sell orders. Users uniqueness will also be impossible to be established.

## Your user has given explicit consentment and Caast is not yet loaded

If your user has already accepted Cookies consentment, you can load Caast by adding `cookiesAccepted=true` in the script call.

```html
<script type="text/javascript">
  (function (c, a, A, s, t, J, S) {
    if (!a.getElementById('caast_library')) {
      (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
      J.async = 1;
      J.src = s;
      J.id = 'caast_library';
      S.parentNode.insertBefore(J, S);
    }
  })(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY&cookiesAccepted=true', 'caast');
</script>
```

## Your user consentment is still in pending state and Caast is not yet loaded

If your user has not yet accepted Cookies consentment, you can load Caast by adding `cookiesAccepted=false` in the script call.

```html
<script type="text/javascript">
  (function (c, a, A, s, t, J, S) {
    if (!a.getElementById('caast_library')) {
      (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
      J.async = 1;
      J.src = s;
      J.id = 'caast_library';
      S.parentNode.insertBefore(J, S);
    }
  })(window, document, 'script', 'https://cdn.caast.tv/caast-latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY&cookiesAccepted=false', 'caast');
</script>
```

Congratulation, Caast is now loaded and won't store any cookie on your site, but you may want to inform us when a user has accepted your Cookies consentment. To do so, you simply have to execute the following code when the user has given his consent. This code also applied when a user decide to now allow cookies on your site

```javascript
if (window.caastLoaded && window.caast) {
  window.caast.cookiesAccepted();
}
```

Once this function is executed Caast will be notified that it is now allowed to store the `CaastFgpData` cookie on your site.

## Your user has already given his consent but decide to revoke the cookie policy parameters

There is another case where your user previously granted access to cookies storage but now decide to revoke this access. Luckily Caast also offer you a way to cancel cookie deposit. To do so, you simply have to execute the following code when the user has updated his consent.

```javascript
if (window.caastLoaded && window.caast) {
  window.caast.cookiesRejected();
}
```

Once this function is executed Caast will be notified that it is now disallowed to store the `CaastFgpData` cookie on your site and will delete it.
