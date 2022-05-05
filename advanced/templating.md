# Templating

Caast Library allow a total control over what is printed on the client side. To create your own templates for your Caast Library Launcher, simply login into your dashboard and go to the app configuration in the template section.

Templates are dynamic and allow you to display conditional templates. We use [blueimp/Javascript-Templates](https://github.com/blueimp/JavaScript-Templates) to easily create template, this library is very light and you can manipulate all the variables, implement conditions and iterations.

With custom templating, you can easily extend your in place design system and relying on your available css to customize the Caast Library to fit exactly on your website.

## Template data

All the data available in the templating system is detailed in the [data section](library/data.md).

## Template required attributes

When you create a custom template you must add some `id` on particular elements. This is a required step in order to allow Caast widget listeners to perform all the required actions like subscribe, launch the live modal etc..

| Attribute                      | Description                                                                                                                                                                                                                                              |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DATA-ATTR: **data-caast-open** | Must be placed on the DOM element triggering the modal, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                                    |
| ID: **caast-popover--toggle**  | Must be placed on the DOM element triggering the subscribe action, must be a `<button>` or a `<a>` tag in order to respect a11y.                                                                                                                         |
| ID: **caast-popover**          | Must be placed on the DOM element wrapping your subscription template, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-popover--open` and `caast-popover--animating` classes when the subscribe button is clicked. |
| ID: **caast-input**            | Must be placed on the input element needed to fill an email for subscribe action, must be an `<input>` tag.                                                                                                                                              |
| ID: **caast-button--submit**   | Must be placed on the DOM element triggering submitting the subscribe form, must be an `<button>` tag with `type=submit`                                                                                                                                 |
| ID: **caast-response**         | Must be placed on the DOM element where you want the success/fail response, a `<div>` tag is advised. Note that this DOM will programmatically receive the `caast-response--error` or `caast-response--success` class according to the action response.  |

!> Omitting those attributes will lead to a non-working widget, do not hesitate to contact your support via your dashboard if you have any doubt.

## Template example

The following example demonstrate how to rely on live states in order to display conditionnal UI elements.

<!-- prettier-ignore -->
```html
<a class="custom-caast-launcher" data-caast-open="" rel="nofollow" target="_blank">
  <div class="custom-caast-launcher__wrapper">
    <div class="custom-caast-launcher__indicator">
      {% if (caast.live.attributes.isFinished) { %}
        <div class="custom-caast-launcher__indicator-led"></div>
        {%=caast.data.config.attributes.configuration.i18n.listing.status.replay%} 
      {% } else if (caast.live.attributes.isStarted) { %}
        <div class="custom-caast-launcher__indicator-led custom-caast-launcher__indicator-led--animated"></div>
        {%=caast.data.config.attributes.configuration.i18n.listing.status.live%} 
      {% } else { %}
        <div class="custom-caast-launcher__indicator-led"></div>
        {%=caast.data.config.attributes.configuration.i18n.listing.status.soon%} 
      {% } %}
    </div>
    <img class="custom-caast-launcher__img" src="{%=caast.live.attributes.displayThumbnailUrl%}" alt="{%=caast.live.attributes.name%}" />
    <div class="custom-caast-launcher__infos">
      <strong class="custom-caast-launcher__title">{%=caast.live.attributes.name%}<strong>
      <small class="custom-caast-launcher__date">
        {% 
        var d=new Date(Date.parse(caast.live.attributes.startDate)); 
        print(d.toLocaleDateString('fr-FR', { month: 'long', day: 'numeric', hour: 'numeric', minute: '2-digit' })); 
        %}
      </small>
    </div>
  </div>
</a>
```

!> _Only the launcher is fully customizable via template injection. To alter the modal or landing styles, you can only rely on css definition override._
