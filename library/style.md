# Customize style

Caast is totally customizable, you can simply expand styling via css, you just need to make sure to respect our css naming strategy in order to override implemented styles.

## Launcher style

The launcher is the Caast Library implementation dipslaying informations regarding the incoming live, its DOM is directly inserted in your HTML.

The Caast launcher looks like this :

![Caast launcher](/_media/launcher.png ':size=400')

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

The Caast Launcher has a subcribe form allowing you to request your users email address in order to automatically send a notification email when a live is about to start.

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

<div style="display:none">

## Modal style <!-- {docsify-ignore} -->

The Caast Launcher will load a modal when a user decide to enter the Chatroom or watch a replay. The modal contain the video, a description about your live, a slider with your recorded products if defined in database, replay videos if availables, and a chatrrom if in live or all the asked questions if it is a replay mode.

The Caast Modal module looks like this:

![Caast Modal](/_media/modal.png ':size=600')

```css
/*
* -----------------------------------
* Style for Caast modal
* -----------------------------------
*/

/* 
* Modal background overlay
*/
.caast-modal__overlay {
}
/* 
* Wrapper for modal
*/
.caast-modal__wrapper {
}
/* 
* Class added to .caast-modal__wrapper when modal is open
*/
.caast-modal__wrapper--open {
}
/* 
* Wrapper for modal container
*/
.caast-modal__container {
}
/* 
* Class on modal close button
*/
.caast-modal__close {
}
/* 
* Wrapper for modal content
*/
.caast-modal__content {
}
/* 
* Wrapper for modal actions
*/
.aast-modal__actions {
}
/* 
* Wrapper for modal left content
*/
.caast-modal__content-left {
}
/* 
* Wrapper for modal left background blurred image
*/
.caast-modal__content-left-background  {
}
/* 
* Wrapper for modal left currently presented product
*/
.caast-modal__content-left-on-screen {
}
/* 
* Wrapper for modal live section
*/
.caast-modal__live-container {
}
/* 
* Wrapper for modal left content
*/
.caast-modal__content-right {
}
```

!> _Note that Caast will only load needed css classes depending on widget display mode and if a subscription on a live is available._

!> _Css wont be injected if you are using the custom template system except for the modal style definition_

## Iframe styles <!-- {docsify-ignore} -->

Caast inject modules like video description, Chat, questions, related videos or products carousel via iframe, so you won't be able to customize the style of those elements using a traditionnal `<style>` approach on your webpage. Nevertheless, you can create in our admin, custom styles which will be injected in the iframes. Customizable elements will be grouped here by type to easily target what you want to customize.

### Iframe Products Carousel <!-- {docsify-ignore} -->

The Caast Products Carousel is a complete module in realtime indicating to your audience which product is currently presented on screen.

The Caast Products Carousel module looks like this:

![Caast Products Carousel](/_media/products.png ':size=600')

```css
/*
* -----------------------------------
* Style for Caast Producst Carousel Module
* -----------------------------------
*/
/* 
* Class for product
*/
.caast-modal__product-item {
}
/* 
* Class for product image
*/
.caast-modal__product-item__image {
}
/* 
* Class for product content
*/
.caast-modal__product-item__content {
}
/* 
* Class for product link
*/
.caast-modal__product-item__link {
}
/* 
* Class for product slider arrow
*/
.caast-modal__product-arrow {
}
/* 
* Class added to .caast-modal__product-arrow for next arrow
*/
.caast-modal__product-arrow-next {
}
/* 
* Class added to .caast-modal__product-arrow for disabled state
*/
.caast-modal__product-arrow--disabled {
}
```

### Iframe Description <!-- {docsify-ignore} -->

The Caast Description is a content area returning video title, date and description. The description can contain html tags like `<strong>`,`<a>`,`<small>` or `<i>`. Feel free to add custom styles to it.

```css
/*
* -----------------------------------
* Style for Caast Description Module
* -----------------------------------
*/
/* 
* Wrapper for modal description section
*/
.caast-modal__content-description {
}
/* 
* Class for H1
*/
.caast-modal__content-header-title {
}
/*
* Class added to .caast-modal__content-header-title when video is live
*/
.caast-modal__content-header-title--live {
}
/* 
* Class for date in description
*/
.caast-modal__content-header-date {
}
/* 
* Class for description content, this span can receive html tags like strong, small , img etc...
*/
.caast-modal__content-description > span {
}
/* 
* Class for description scroller, this markup will appear if related videos are available and out of scroll area
*/
.caast-modal__content-description__scroller {
}
/* 
* Class added to .caast-modal__content-description__scroller when description scroller should be hidden 
*/
.caast-modal__content-description__scroller--hidden {
}
```

### Iframe Chat <!-- {docsify-ignore} -->

The Caast Chat is a complete module in realtime allowing your users to chat with the Caaster or between them. The `.caast-modal__chat-message` design for chat questions is reused in the [questions](#iframe-questions) module.

The Caast Chat module looks like this:

![Caast Chat](/_media/chatroom.png ':size=400')

```css
/*
* -----------------------------------
* Style for Caast Chat Module
* -----------------------------------
*/
/* 
* Wrapper for modal chat section
*/
.caast-modal__chat-container {
}
```

### Iframe Questions <!-- {docsify-ignore} -->

The Caast Questions is a module regrouping all the questions asked during the live. Each question will jump to the replay related timestamp. The `.caast-modal__chat-message` design is taken from the [chat](#iframe-chat) module. So please refer to available classes to edit it, to distinguish them, `.caast-modal__chat-message--link` is added to the `.caast-modal__chat-message` wrapper.

The Caast Questions module looks like this:

![Caast Chat](/_media/questions.png ':size=400')

```css
/*
* -----------------------------------
* Style for Caast Questions Module
* -----------------------------------
*/
/*
*   Wrapper for search header
*/
.caast-modal__content-header-right--search {
}
/*
*   Wrapper for search
*/
.caast-modal__search {
}
/*
*   Class for search input
*/
.caast-modal__search-input {
}
/*
*   Class for search input SVG icon
*/
.caast-modal__search-icon {
}
/* 
* Wrapper for modal questions section
*/
.caast-modal__questions-container {
}
/* 
* Wrapper for no questions placeholder
*/
.caast-modal__no-questions {
}
/* 
* Wrapper for no questions SVG placeholder
*/
.caast-modal__no-questions-svg-wrapper {
}
/* 
* Wrapper for questions
*/
.caast-modal__questions-wrapper {
}
/* 
* Class for questions list
*/
.caast-modal__questions-list {
}
/* 
* Class for questions from other lives
*/
.caast-modal__questions-list--other {
}
/* 
* Class added to .caast-modal__chat-message indicating that question is clickable
*/
.caast-modal__chat-message--link,
.caast-modal__chat-message--link * {
}
```

### Iframe Related videos <!-- {docsify-ignore} -->

The Caast Related Videos is a module used to display all the related videos on a smae product page.

The Caast Related Videos module looks like this:

![Caast Related Videos](/_media/related_videos.png ':size=600')

```css
/*
* -----------------------------------
* Style for Caast Realted Videos Module
* -----------------------------------
*/
/* 
* Wrapper for modal replay header
*/
.caast-modal__related-header {
}
/* 
* Class for replay header title h2
*/
.caast-modal__related-title {
}
/* 
* Wrapper for video replay
*/
.caast-modal__related-video {
}
/* 
* Class for video replay image
*/
.caast-modal__related-video-image {
}
/* 
* Class indicating video is live
*/
.caast-modal__related-video-live {
}
/* 
* Class for video replay image play SVG
*/
.caast-modal__related-video-play {
}
/* 
* Class for video replay title
*/
.caast-modal__related-video-title {
}
```

</div>
