<script>
  // Import components for buttons
  import Inputs from "./components/inputs.svelte";
  import Randomizer from "./components/randomizer.svelte";

  /*Define variables*/

  // handles Adding
  let choices = []; // will become to dimensional [{id, choice}]
  let id = 1;
  let input = "";
  let weight = 1;

  let choiceCount = [];
  // Remove functionality variables
  let selectedId = null; // <-- which item to removal

  let isWaiting = false; // true while we wait
  let waitMs = 1200; // delay in milliseconds (change if you want)

  /*define functions*/

  function rebuildChoiceCount() {
    // Start fresh each time
    choiceCount = [];
    for (const c of choices) {
      // make sure weight is a positive integer (default 1)
      // make sure minimum is at least 1
      const times = Math.max(1, Math.floor(Number(c.weight) || 1));
      for (let i = 0; i < times; i++) {
        choiceCount.push(c.id); // duplicate id "weight" times
      }
    }
  }

  function addOption(label, w = 1) {
    const clean = (label ?? "").trim();
    if (!clean) return;

    const safeW = Math.max(1, Math.floor(Number(w) || 1));

    // now each choice stores its own weight
    choices = choices.concat({ id: id++, label: clean, weight: safeW });

    rebuildChoiceCount(); // keep the derived array in sync
    input = "";
    weight = 1;
  }

  function removeSelected() {
    if (selectedId === null) return;
    choices = choices.filter((c) => c.id !== selectedId);
    selectedId = null;
    rebuildChoiceCount(); // keep derived array in sync
  }

  function decide() {
    if (isWaiting) return; // ignore clicks while waiting
    if (choiceCount.length === 0) {
      alert("No choices yet. Add something first!");
      return;
    }

    isWaiting = true; // start waiting
    setTimeout(() => {
      const pickedId =
        choiceCount[Math.floor(Math.random() * choiceCount.length)];
      const picked = choices.find((c) => c.id === pickedId);
      alert(`Your pick: ${picked.label}`);
      isWaiting = false; // done waiting
    }, waitMs);
  }

  function select(id) {
    // click to select, click again to unselect (simple toggle)
    selectedId = selectedId === id ? null : id;
  }

  /* reactive convenience flags (auto-update)

    $: tells Svelte to update variables when it's conditions change
    disableAdd is true when the input is empty and disableRemove is true when nothing is selected
  */
  $: disableAdd = (input ?? "").trim() === "";
  $: disableRemove = selectedId === null;
  $: disableRandomizer = isWaiting || choiceCount.length === 0;
</script>

<main>
  <div class="card">
    <div>
      <h1>Indecision Machine</h1>
    </div>
    <div>
      <!-- randomizer.svelte has access to decide function -->
      <!-- I am telling the program that there is a variable in Randomizer called disabled and passing a value -->
      <Randomizer {decide} disabled={disableRandomizer} waiting={isWaiting} />
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
                class="choices"
                class:bg-blue-50={c.id === selectedId}
                class:ring-1={c.id === selectedId}
                class:ring-blue-300={c.id === selectedId}
                on:click={() => select(c.id)}
                aria-pressed={c.id === selectedId}
              >
                {c.label} ({c.weight})
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
        bind:option={input}
        bind:weight
        {addOption}
        {removeSelected}
        {disableAdd}
        {disableRemove}
      />
    </div>
  </div>
</main>
