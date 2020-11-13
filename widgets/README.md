# Getting started

To load the Caast Widget Library on your website you just need to add this code at the end of your `body` tag element. This is a really basic implementation, you will find down the page some more advanced configuration.

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
    "https://cdn.caast.tv/caast-latest/caastWidget.js",
    "caast"
  );
</script>
```

With this simple snippet Caast Library is now injected on your website, lets have a look on specific widget call in order to build your own Caast Library implementation.

!> Caast Widget cannot be loaded with Caast Library. This library is available to allow you to build your own display of the Caast Interface.

## Customize style

Currently Caast Widget is only customizable via injected styles in our different components. Those styles can be injected in our administration interface. Nevertheless, we are working on offering you the ability to add a style parameter on each Caast Widget instance in order to have a really frictionless experience.

The injected styles will rely upon the Caast Library css classes naming available [here](library/style.md#iframe-styles)
