# How Caast works

Caast's implementation was originally designed to limit client-side work. Just install a script on your website and let the magic happen.

Once our script is set, Caast will look in its database if lives or videos are linked to the url the user is consulting. If the url has linked contents, our APIs could either return a [classic launcher](library/launcher.md) or a [landing page](library/landing.md).

![Caast lifecycle](/_media/caast-loading-flow.jpg)

## What if my URLs change regularly ?

Caast can be connected to any product feed, so technically if the product feed is updated, Caast will also update all related products and their URLs. But in some cases, especially if you own a marketplace store, you may want to display content only for a product sold by a specific vendor. Luckily, Caast can handle this kind of situation as well. You'll need a special setup, but we promise it won't be complicated to implement.

To start this specific implementation, please refer to the [advanced setup method](library/README.md?mode=advanced)
