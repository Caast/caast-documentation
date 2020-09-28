# Getting started

To load the Caast Library on your website you just need to add this code at the end of your `body` tag element.

```html
<script type="text/javascript">
  (function (c, a, A, s, t, J, S) {
    (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
    J.async = 1;
    J.src = s;
    J.id = "caast_library";
    S.parentNode.insertBefore(J, S);
  })(
    window,
    document,
    "script",
    "https://cdn.caast.tv/caast-latest/caast.js?APP_ID=MY_APP_ID&APP_KEY=MY_APP_KEY",
    "caast"
  );
</script>
```

With this simple snippet Caast Library is now running on your website, lets have a look on advanced configuration in order to customize the Caast Library.

?> Caast can be configurated in a very deep way, please refer to our [advanced configuration section](configuration/README.md) for detailed informations.
