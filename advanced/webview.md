# Embed Caast with webview

Caast can be embedded in your apps by using Webview. Caast is using HTML5 video in order to display lives, we are also using in some specific cases, video provider like Youtube, Vimeo or Twitch. If you are using one of those specific providers we encourage you to follow the available ressources you can find online in order to be compliant to embed those contents.

Regarding the standard Caast HTML5 video tag, we are implementing Caast using the `allowInline` attribute. Most of the time you wont encounter any problem embedding your content in your application.

## ios known issues <!-- {docsify-ignore} -->

You may encounter issues with iOS regarding the `allowInline` attribute, please have a look on the documentation provided by apple regarding this specific issue: https://developer.apple.com/documentation/webkit/wkwebviewconfiguration most of the time, simply set this [option](https://developer.apple.com/documentation/webkit/wkwebviewconfiguration/1614793-allowsinlinemediaplayback) to true will solve your problems.

```javascript
let webConfiguration = WKWebViewConfiguration();
webConfiguration.allowsInlineMediaPlayback = true;
```

## android known issues <!-- {docsify-ignore} -->

Caast can rely on localStorage in order to store debug informations, please make sure to enable these flags on the webview options:

```javascript
WebSettings webSettings = webviewInstance.getSettings();
webSettings.setJavaScriptEnabled(true);
webSettings.setDomStorageEnabled(true);
```
