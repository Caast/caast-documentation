# Template

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

Lets say you want to create a really simple and not so pretty launcher with a title and a big button triggering the Caast modal **only vsible** if a live is on. No subscription form, just a pure launcher.

<!-- prettier-ignore -->
```html
<style>
  .my-custom--class {
    background: white;
    padding: 20px;
  }
  .my-custom--title {
    color: black;
    margin-bottom: 20px;
    font-size: 20px;
  }
  .my-custom--button {
    background: {%=caast.config.attributes.configuration.color.button_background%};
    color: {%=caast.config.attributes.configuration.color.button_color%};
  }
</style>
<div class="my-custom--class">
  <h1 class="my-custom--title">
    {% if (caast.lives && caast.lives.length > 0) { %}
      {%=caast.config.attributes.configuration.i18n.product.title.is_live%} 
    {% } else { %} 
      {%=caast.config.attributes.configuration.i18n.product.title.no_live%} 
    {% } %}
  </h1>
  {% if (caast.lives && caast.lives.length > 0) { %}
  <button id="caast-modal--trigger" class="my-custom--button">
    {%=caast.config.attributes.configuration.i18n.button.open%}
  </button>
  {% } %}
</div>
```

!> _Only the launcher is fully customizable via template injection. To alter the modal or widgets style, you can only rely on style override. You can also decide to make your own Caast implementation using our [widget library](widgets/README.md)_
