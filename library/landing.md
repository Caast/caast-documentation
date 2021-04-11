# Caast Landing

Caast Landing is a fully integrated experience to allow you, in just a few lines, to render your own media channel on your website. You have the possibility to choose to display all your lives on this page, but you can also target lives with specific hashtags. Just sit and enjoy the all-in-one Caast experience.

![Caast Landing](/_media/listing.jpg ':size=600')

## Behaviour

Caast Landing will be injected in your targeted element and will fill 100% of the available space inside it. We advise to define the target inside your default content container for a better user experience. Note that style customisation inside Caast interface will allow you to adjust the styled output.

## Custom HTML

You also have the ability to inject custom HTML and styles on different part of the Caast Landing. This possibility allow you to inject custom image banner, advanced HTML, like presenting your products or anything else you might imagine. Those three area are :

- Before the live Highlight
- After the live Highlight
- After all the replays thumbnails

## Styling

Caast Landing is totally stylable via your own style declaration. You have the possibility to add styles override on the targeted page inside a classic `<style>` tag. You can also give us the style override, it will be directly merged with the final render, this option allow you to avoid editing the

```css
/*
* -----------------------------------
* Style for Caast Landing Wrapper
* -----------------------------------
*/

/*
*  Wrapper for injected content before highlight
*/
.caast-listing__before-highlight {
}
/*
*   Wrapper for injected content after highlight
*/
.caast-listing__after-highlight {
}
/*
*   Wrapper for injected content after listing
*/
.caast-listing__after-list {
}
/*
*   Wrapper for live card
*/
.caast-card {
}
/*
*   Wrapper for card player
*/
.caast-card__player {
}
/*
*   Class for card iframe
*/
.caast-card__iframe {
}
/*
*   Class for card image
*/
.caast-card__image {
}
/*
*   Wrapper for live card content
*/
.caast-card__content {
}
/*
*   Class for led visual indicator
*/
.caast-card__indicator {
}
/*
*   Class added to .caast-card__indicator for replay variation
*/
.caast-card__indicator--replay {
}
/*
*   Class added to .caast-card__indicator for soon variation
*/
.caast-card__indicator--soon {
}
/*
*   Class added to .caast-card__indicator for all variation
*/
.caast-card__indicator--all {
}
/*
*   Class for sound toggler
*/
.caast-card__sound {
}
/*
*   Class for fullscreen toggler
*/
.caast-card__fullscreen {
}
/*
*   Class for badge containing date or countdown
*/
.caast-card__badge {
}
/*
*   Class added to .caast-card__badge for planned variation
*/
.caast-card__badge--planned {
}
/*
*   Class added to .caast-card__badge for soon variation
*/
.caast-card__badge--soon {
}
/*
*   Class added to .caast-card__badge for live variation
*/
.caast-card__badge--live {
}
/*
*   Class added to .caast-card for highlight variant
*/
.caast-card--highlight {
}
/*
*   Class for big button inside highlight card
*/
.caast-listing__button {
}
/*
*  Wrapper for listing header
*/
.caast-listing__header {
}
/*
*  Wrapper for listing filters
*/
.caast-listing__header-filter {
}
/*
*   Class listing dropdown
*/
.caast-listing__dropdown {
}
/*
*   Class listing dropdown toggler
*/
.caast-listing__dropdown-toggler {
}
/*
*   Class listing dropdown menu
*/
.caast-listing__dropdown-menu {
}
/*
*   Class listing dropdown menu item
*/
.caast-listing__dropdown-item {
}
/*
*  Wrapper for small card lives listing
*/
.caast-listing {
}
```
