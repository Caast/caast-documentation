#### Version 2.4.3

- (feature): add fallback function after initial canLoadCaast internal behaviour. If no live is available for the current page, Caast will look in DOM for [data-caast-embed] and [data-caast-open] attributes. If nodes are found, caast will execute related methods [caast.parse](/library/methods?id=parse) / [caast.embed](/library/methods?id=embed).
- (feature): add new option for add to cart function in order to allow javascript interpretaion in order to be able to compute checkout url
- (feature): implement base features for caast displayed in iframe
- (feature): performance imporvements on live listing
- (fix): on onepage website caast was calling a function twice on url change.
- (fix): on landing page, triggering the caast modal on the highlight was causing a gray placeholder instead of keeping the video
- (fix): sometimes a hidden live was impossible to load due to our canLoadCaast internal methods

#### Version 2.4.0

- (feature): update methods to open caast Modal via url parameters, this methods is now also available on the landing pages. You can read the [documentation](/advanced/configuration?id=trigger-library-with-url-hash)
- (feature): performance improvement for the landing page.
- (feature): improve performance for products search in database
- (feature): add a waiting screen while vimeo is encoding the replay of a live

#### Version 2.3.9

- (feature): add two new methods on caast instance, [caast.open](/library/methods?id=open) and [caast.parse](/library/methods?id=parse)
- (feature): reduce caast initial bundle size
- (feature): optimize iteration on landing sections
- (feature): optimize landing API response time
- (feature): implement better debug mode options
- (feature): add ability to add parameters to trigger specific actions on player via url view ([documentation](/advanced/cookies.md))
- (fix): better implementation of time consumption with the differents players
- (fix): reminder button was causing random page refresh
- (fix): cookies functions were badly intercepting available configuration of caast
- (fix): update outlook and macOS calendar generated files
- (fix): random behaviour for autoplay on landing page

#### Version 2.3.0

- (feature): global loading ability. You can load Caast globally on a high traffic website without impacting your website performance.
- (feature): add trailer to your lives, this trailer will then be disabled 15 minutes before your lives start
- (feature): add autodisable for premoderation, like the trailer the premoderation will be disabled 15 minutes before your lives start
- (feature): update UI for product detailed view
- (feature): add dynamic entry to custom headers for cart data
- (fix): whitelist parameters is now in strict mode
- (fix): fix an issue with autostart on youtube lives
- (fix): migrate emitter to xhr instead of websockets, also reduce collected data

#### Version 2.2.0

- (feature): split initial Caast script in order to reduce our impact on website
- (feature): ability to remove cookies from differents video providers
- (feature): more add to cart options
- (feature): ability to choose a default displayed tab on Caast Widget Modal
- (fix): random issue with muted video on ios
- (fix): empty tab on live without chat/questions

#### Version 2.1.0

- (fix): minor feedbacks and bug issues after 2.0.0 release
- (feature): advanced cookies methods available for GDPR compliance ([documentation](/advanced/cookies.md))

#### Version 2.0.0 ⭐️🍾🎉

- (feature): complete rewrite of the Caast Widget Modal UI/UX after a long period of exchanges and co-creation with our customers. Enjoy a new unified interface shared between desktop and mobile.
- (feature): new custom video player for replays. The player now display visual chapters per products, allowing to quickly jump click to the presented product
- (feature): better responsive performance and a completely new mobile experience
- (feature): localStorage has been migrated to cookies in order to be compliant with GDPR, you can also set your own cookie lifetime via our administration interface.
- (feature): completely new product experience. Caast now handle product variations and options with a direct visual impact on the product details.
- (feature): advanced add to cart options, allowing Caast to handle way more ecommerce frameworks to properly handle a direct add to cart experience on lives and replays.
- (feature): smooth integration with **Lengow** and **Awin**. No need to prepare products anymore in our interface, simply import them from your product feed platform.
- (feature): drop IE 11 support, allowing Caast to drop a lot of weight and be as fast as light.

#### Version 1.81

- (feature): implement live preview feature, when a live is started, the thumbnail turn into a player with sound disabled
- (feature): add better uuid generation when localstorage is enabled

#### Version 1.71

- (feature): rewrite analytics methods and add fallback when websocket is not launched
- (fix): no events was triggered on related videos click

#### Version 1.61

- (feature): implement GET method and custom headers options for in live purchase
- (fix): error with Youtube Player
- (fix): better visual error for nickname

#### Version 1.51

- (feature): implement loader for landing mode
- (fix): **caastListing** on Caast Widget method ([documentation](/widgets/methods.md?id=loadlisting)) is now marked as deprecated. You should now use use caast.js and custom configuration to implement a landing page
- (fix): various UI and UX feedback for landing page behaviour

#### Version 1.41

- (feature): complete rewrite of the Caast Modal with new fullscreen feature
- (fix): optimization of eventListeners
- (fix): optimization for resize and mobile responsive
- (fix): better cache management in API
- (fix): remove dead code

#### Version 1.31

- (fix): error while changing Caast related video, question were not updated
- (fix): problem with cache clear in API

#### Version 1.24

- (fix): issue with responsive **caastListing** on Caast Widget method ([documentation](/widgets/methods.md?id=loadlisting))
- (feature): implement method to hide a specific live from lives listing

#### Version 1.23

- (feature): rewrite event emission system for Caast Player

#### Version 1.22

- (fix): issue with related videos

#### Version 1.21

- (fix): issue while changing video provider

#### Version 1.20

- (feature): rewrite live provider class
- (fix): minor error in message moderation

#### Version 1.19

- (feature): add custom code injection for **caastListing**. It will allow to inject custom HTML code in 3 differents parts of the **caastListing** HTML.
- (fix): youtube was sometimes unable to load a video

#### Version 1.18

- (fix): prevent multiple instanciations of Caast libraries
- (fix): remove dead code

#### Version 1.17

- (feature): add new widget method, **caastWidget.loadListing**, it will allow you to integrate in a few lines, a fully integrated WebTV experience on your website, please refer to [documentation](/widgets/methods.md?id=loadlisting) for details about this feature.

#### Version 1.16

- (fix): error while changing live provider between replay and live mode
- (fix): minor responsive errors

#### Version 1.15

- (feature): add Facebook as available broadcast provider

#### Version 1.14

- (feature): extends configuration values
- (fix): minor error with twitch provider

#### Version 1.13

- (feature): add new library, **caastEmbed**, it will allow you to diffuse a Caast live in your blogs, please refer to [documentation](/embed/README.md) for details about this feature.
- (feature): add possibility to handle configuration per device type (mobile or desktop)
- (feature): add Twitch as available broadcast provider
- (feature): add possibility to dynamically add product to your website cart.
- (fix): remove some useless UI elements
- (fix): optimize API response size

#### Version 1.12

- (feature): add new library, **caastEmitter**, to track specific product on a purchase page, please refer to [documentation](/emitter/README.md) for details about this feature.
- (feature): rebuild questions interface in admin
- (feature): you can now load Caast widget and launch at specific timestamps or question id via url parameters ([see documentation](/configuration/README.md#trigger-library-with-url-hash))
- (feature): replay mode allow you to click on product to jump to first displayed time
- (feature): new UI for nickname and implement GDPR consent
- (feature): added possibility to override configuration per live and per URL
- (feature): new UI for question moderation in admin
- (fix): optimize API response size
- (fix): minor error on live save
- (fix): optimize statistics calculation time

#### Version 1.11

- (feature): migrate modal content to React
- (feature): add new library, **caastWidget**, to include only specific Caast feature, please refer to [documentation](/widgets/README.md) for details about this feature.
- (feature): add new Caast Chat, realtime, full branded with custom events and lots of incoming feature ;)
- (feature): migrate Caast config to state management library
- (fix): optimize library file size

#### Version 1.10

- (feature): initial release of Caast Library
