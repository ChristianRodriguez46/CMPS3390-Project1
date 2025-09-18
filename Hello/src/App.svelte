<script>
  import Modal from "./lib/Modal.svelte";
  let modal; // bound to the Modal instance

  function openModal() {
    modal.open(); // shows the <dialog>
  }
</script>

<main class="container">
  <button class="btn" on:click={openModal} aria-haspopup="dialog">
    Hello
  </button>

  <!-- Second view lives in the modal component -->
  <Modal bind:this={modal} />
</main>
