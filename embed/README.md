# Caast Embed

Caast embed allow you to insert a Caast card with a live of your choice into any of your content.

## Getting started

```html
<script type="text/javascript">
  (function (c, a, A, s, t, J, S) {
    (c[t] = c[t]), (J = a.createElement(A)), (S = a.getElementsByTagName(A)[0]);
    J.async = 1;
    J.src = s;
    J.setAttribute("data-caast-embed", "");
    J.setAttribute("data-app-id", MY_APP_ID);
    J.setAttribute("data-app-key", MY_APP_KEY);
    J.setAttribute("data-live-id", MY_LIVE_ID);
    S.parentNode.insertBefore(J, S);
  })(window, document, "script", "https://cdn.caast.tv/caast-latest/caastEmbed.js", "caastEmbed");
</script>
<div id="caast-live-MY_LIVE_ID"></div>
```

Be sure to replace `MY_APP_ID`, `MY_APP_KEY` and `MY_LIVE_ID` with the values matching the desired live.

## Output

This code will render the Caast Embed card and will play your live on muted state, in order to not jump scare your users. They can launch the traditionnal Caast Live Modal by clicking anywhere on this card and have the full Caast experience with questions, products chat etc..

![Caast launcher](/_media/embed.png ":size=600")

The output will be rendered directly into the DOM, which means you can extend and modify the style with a simple `<style>` tag and override desired CSS classes.
