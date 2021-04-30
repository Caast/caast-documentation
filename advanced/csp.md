## Informations

Caast will perform calls to different sub domains. Those domains are:

- https://cdn.caast.tv
- https://api.caast.tv
- https://cache.caast.tv
- wss://ws.caast.tv

If your website is using Content-Security-Policy you may want to add the following rules in order to allow Caast to properly work:

```
script-src https://caast.tv https://*.caast.tv;
img-src https://*.caast.tv;
connect-src https://caast.tv https://*.caast.tv wss://*.caast.tv;
child-src https://caast.tv https://*.caast.tv;
frame-src https://caast.tv https://*.caast.tv;
```
