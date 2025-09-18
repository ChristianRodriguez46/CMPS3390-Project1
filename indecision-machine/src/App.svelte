<script>
  // Import components for buttons
  import Inputs from "./components/inputs.svelte";
  import Randomizer from "./components/randomizer.svelte";

  /*Define variables*/

  // handles Adding
  let choices = []; // will become to dimensional [{id, choice}]
  let id = 1;
  let input = "";

  // Remove functionality variables
  let selectedId = null; // <-- which item to removal

  /*define functions*/

  function addOption(label) {
    // pass text input then strip white space
    // If input is null or undefined -> return nothing
    const clean = (label ?? "").trim();
    if (!clean) return;

    // Increment id after adding input to array
    choices = choices.concat({ id: id++, label: clean });
    // Reset input to empty
    input = "";
  }

  function removeSelected() {
    if (selectedId === null) return;
    choices = choices.filter((c) => c.id !== selectedId);
    selectedId = null; // clear selection after removing
  }

  function decide() {
    if (choices.length === 0) {
      alert("No choices yet. Add something first!");
      return;
    }
    // picks a number from 0 - sizeof choices
    const pick = choices[Math.floor(Math.random() * choices.length)];
    alert(`Your pick: ${pick.label}`);
  }

  function select(id) {
    // click to select, click again to unselect (simple toggle)
    selectedId = selectedId === id ? null : id;
  }

  /* reactive convenience flags

    $: tells Svelte to update variables when it's conditions change
    disableAdd is true when the input is empty and disableRemove is true when nothing is selected
  */
  $: disableAdd = (input ?? "").trim() === "";
  $: disableRemove = selectedId === null;
</script>

<main>
  <div>
    <h1>Indecision Machine</h1>
  </div>

  <div class="card">
    <div>
      <!-- randomizer.svelte has access to decide function -->
      <!-- I am telling the program that there is a variable in Randomizer called disabled and passing a value -->
      <Randomizer {decide} />
    </div>
    <!-- Scrollable, selectable list -->
    <div id="listData" class="overflow-auto">
      <h2 class="text-lg font-semibold mb-2">Choices</h2>
      <ul class="rounded border">
        {#if choices.length === 0}
          <li class="px-3 py-2 text-sm opacity-70">No choices yet.</li>
        {:else}
          {#each choices as c (c.id)}
            <li class="border-b last:border-b-0">
              <button
                type="button"
                class="w-1/2 text-left px-3 py-2 hover:bg-gray-50"
                class:bg-blue-50={c.id === selectedId}
                class:ring-1={c.id === selectedId}
                class:ring-blue-300={c.id === selectedId}
                on:click={() => select(c.id)}
                aria-pressed={c.id === selectedId}
              >
                {c.label}
              </button>
            </li>
          {/each}
        {/if}
      </ul>
    </div>
    <!-- </div> -->
    <div id="inputs">
      <!-- pass value + actions + disabled flags to inputs.svelte -->
      <!-- bind:value={input} -> tells the file that it input is acessible in inputs.svelte -->
      <!-- inputs.svelte has access to the functions and variables -->
      <Inputs
        bind:value={input}
        {addOption}
        {removeSelected}
        {disableAdd}
        {disableRemove}
      />
    </div>
  </div>
</main>
