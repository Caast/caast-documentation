#### Version 1.24

- (fix): issue with responsive **caastListing** on Caast Widget method ([documentation](/widgets/listing.md))
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

- (feature): add new widget method, **caastWidget.loadListing**, it will allow you to integrate in a few lines, a fully integrated WebTV experience on your website, please refer to [documentation](/widgets/listing.md) for details about this feature.

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
