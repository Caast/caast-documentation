# Picture-in-Picture

<style>
.pip-intro {
  display: flex
}
.pip-intro__img {
  flex: 0 0 200px; 
  margin-left: 40px
}

@media (max-width: 768px) {
  .pip-intro {
    flex-direction: column;
  }
  .pip-intro__img {
    flex: auto;
    margin-left: 0;
  }
}

</style>
<div class="pip-intro">
  <div>
  Caast can allow your user to keep navigating on your website if you choose to toggle the picture-in-picture (lets call it PiP to gain time). The PiP is an option to reduce the Caast Player on a corner of the user screen and keep it active while navigating.
  </div>
  <div class="pip-intro__img">

![Preview PiP](/_media/pip.gif)

  </div>

</div>

## Troubleshooting

To mimic the PiP on any website, we move the current website inside an iframe in order to allow the player to stay active while navigating. This can lead to some issues regarding the CSP set on site.

**X-Frame-Options = DENY (RFC7034)**

Possible solution: Set X-Frame-Options = SAMEORIGIN

**Content-Security-Policy: frame-ancestors 'none'; (CSP level 2)**

Possible solution: Content-Security-Policy: frame-ancestors 'self';
