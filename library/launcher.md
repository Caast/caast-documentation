# Launcher

Caast launcher is the Caast Library implementation dipslaying informations regarding the incoming live, its DOM is directly inserted in your HTML.

The Caast launcher looks like this :

![Caast launcher](/_media/launcher.png ':size=400')

The launcher version is usually used on product pages because the size footprint is really small and won't degrade your SEO performance.

## Templating

The Caast launcher can be totally customized via custom template HTML, please refer to the [dedicated section](advanced/templating.md) if you need this kind of behaviour.

## Style

Caast is totally customizable, you can simply expand styling via css, you just need to make sure to respect our css naming strategy in order to override implemented styles.

```css
/*
* -----------------------------------
* Style for Caast common DOM element
* -----------------------------------
*/

/* 
* Wrapper for widget
*/
.caast-toggler {
}
/* 
* Wrapper for widget content
*/
.caast-toggler__content {
}
/* 
* Wrapper for the thumbnail content
*/
.caast-toggler__thumbnail {
}
/* 
* Widget title
*/
.caast-toggler__title {
}
/* 
* Class added to .caast-toggler__title when a live is on
*/
.caast-toggler__title--animated {
}
/* 
* Widget description
*/
.caast-toggler__description {
}
/* 
* Wrapper for widgets actions like subscribe and launch live
*/
.caast-toggler__actions {
}
/* 
* Wrapper for countdown when a llive is about to start
*/
.caast-countdown {
}
/* 
* Wrapper for countdown minutes
*/
.caast-countdown__minutes {
}
/* 
* Wrapper for countdown seconds
*/
.caast-countdown__seconds {
}
/* 
* Widget button
*/
.caast-button {
}
/* 
* Class added to .caast-button when loading
*/
.caast-button--loading {
}
```

## Launcher subscribe form style

If activated, the Caast Launcher has a subcribe form allowing you to request your users email address in order to automatically send a notification email when a live is about to start.

The Caast launcher subscribe form, looks like this:

![Caast launcher subscribe](/_media/launcher_subscribe.png ':size=400')

```css
/*
* -----------------------------------
* Style for Caast subscribe form
* -----------------------------------
*/

/* 
* Wrapper for subscription popover
*/
.caast-popover {
}
/* 
* Class added to .caast-popover when open
*/
.caast-popover--open {
}
/* 
* Class added to .caast-popover when open
*/
.caast-popover--animating {
}
/* 
* Class extending .caast-button
*/
.caast-button--circle {
}
/*
* Wrapper for input grouped with button
*/
.caast-input-group {
}
/*
* Wrapper inside .caast-input-group to properly wrap the submit button
*/
.caast-input-group-append {
}
/*
* Widget input
*/
.caast-input {
}
/*
* Wrapper for form response
*/
.caast-response {
}
/* 
* Class added to .caast-response when success
*/
.caast-response--success {
}
/* 
* Class added to .caast-response when error
*/
.caast-response--error {
}
```
