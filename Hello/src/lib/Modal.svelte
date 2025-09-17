<script>
  // reference to <dialog> element.
  let dlg;

  export function open() {
    dlg?.showModal();
  }
  export function close() {
    dlg?.close();
  }

  // Close when clicking the shaded backdrop, not the inner content.
  function onBackdropClick(e) {
    if (e.target === dlg) close();
  }

  /* ? - optional chaining operator in JavaScript
       - safely access a property or call a method only if the left-hand side is neither null nor undefined. 
  */
</script>

<!-- HTML component for displaying content; ex: alerts, confirmation boxes, and custom popups -->
<dialog
  bind:this={dlg}
  on:click={onBackdropClick}
  aria-labelledby="hello-title"
>
  <!-- method="dialog" lets the OK button close the modal without extra JS -->
  <form method="dialog">
    <h2 id="hello-title">
      <slot name="title">Hello World</slot>
    </h2>

    <div class="body">
      <slot><!-- default body if none provided -->Hello World</slot>
    </div>

    <div class="actions">
      <button class="btn" autofocus>OK</button>
    </div>
  </form>
</dialog>
