## Informations

Caast will perform calls to different sub domains. Those domains are:

- https://cdn.caast.tv
- https://api.caast.tv
- https://cache.caast.tv
- wss://ws.caast.tv
- https://mux.com

If your website is using Content-Security-Policy you may want to add the following rules in order to allow Caast to properly work:

```
script-src https://caast.tv https://*.caast.tv;
img-src https://*.caast.tv;
connect-src https://caast.tv https://*.caast.tv wss://*.caast.tv https://*.mux.com;
child-src https://caast.tv https://*.caast.tv;
frame-src https://caast.tv https://*.caast.tv;
```

### Vimeo

Caast can also rely on vimeo to distribute lives and replays, Vimeo use the following domains:

- https://vimeo.com
- https://\*.vimeo.com
- https://vimeocdn.com

If you are usin Content-Security-Policy you may want to add the following rules in order to allow Caast to properly work:

```
img-src https://i.vimeocdn.com https://*.vimeocdn.com;
frame-src https://vimeo.com  https://*.vimeo.com https://vimeocdn.com;
```

### Youtube

Caast can also rely on Youtube to distribute lives and replays, Youtube use the following domains:

- https://i.ytimg.com
- https://www.youtube-nocookie.com
- https://www.youtube.com
- https://\*.youtube.com

If you are usin Content-Security-Policy you may want to add the following rules in order to allow Caast to properly work:

```
img-src https://i.ytimg.com;
frame-src https://www.youtube-nocookie.com https://www.youtube.com https://*.youtube.com;
```
