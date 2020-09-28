# Available methods

Caast Widget expose some methods to instanciate specific Caast part of the main Library. Those methods are described here. We assume that you are implementing those methods after Caast Widget emitted the `caast.onReady` event on the DOM.

```javascript
document.addEventListener("caast.onReady", function (e) {
  // Start adding methods here, calling the caast instance
});
```

Each Caast Widget method will require at least 4 parameters, those parameters are:

| Key           | Type   | Description                                                                                                                 |
| ------------- | ------ | --------------------------------------------------------------------------------------------------------------------------- |
| liveId        | string | The Caast unique live id. Available in the administration interface                                                         |
| websiteId     | string | The Caast unique website id. Available in the administration interface                                                      |
| websiteKey    | string | The Caast unique website key. Available in the administration interface                                                     |
| targetElement | string | The DOM node id name, without the #. So if you want to target `<div id="my_node"></div>` you will set `my_node` as a value. |

## loadPlayer

The `loadPlayer` method will load the Caast Player in the targetted DOM node.

```javascript
caastWidget.loadPlayer({
  liveId: "MY_LIVE_ID",
  websiteId: "MY_APP_ID",
  websiteKey: "MY_APP_KEY",
  targetElement: "my_dom_id", // Currently only a DOM ID target is supported
});
```

## loadDescription

The `loadDescription` method will load the Caast Description in the targetted DOM node.

```javascript
caastWidget.loadDescription({
  liveId: "MY_LIVE_ID",
  websiteId: "MY_APP_ID",
  websiteKey: "MY_APP_KEY",
  targetElement: "my_dom_id", // Currently only a DOM ID target is supported
});
```

## loadChat

The `loadChat` method will load the Caast Chat in the targetted DOM node. This method will also load the Caast Questions for replay mode. This method is able to interfere with the `loadPlayer` instance in order to jump to specific timestamp in replay mode.

```javascript
caastWidget.loadChat({
  liveId: "MY_LIVE_ID",
  websiteId: "MY_APP_ID",
  websiteKey: "MY_APP_KEY",
  targetElement: "my_dom_id", // Currently only a DOM ID target is supported
});
```

## loadProducts

The `loadProducts` method will load the Caast Chat in the targetted DOM node. This method is able to interfere with the `loadPlayer` instance in order to jump to specific timestamp on product click.

```javascript
caastWidget.loadProducts({
  liveId: "MY_LIVE_ID",
  websiteId: "MY_APP_ID",
  websiteKey: "MY_APP_KEY",
  targetElement: "my_dom_id", // Currently only a DOM ID target is supported
});
```

## setUser

Please refer to [setUser](library/methods.md#setUser) method, in the Caast Library Documentation. This methods is exactly the same.
