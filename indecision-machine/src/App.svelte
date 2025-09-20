<script>
  // Import components files for buttons
  import Inputs from "./components/inputs.svelte";
  import Randomizer from "./components/randomizer.svelte";

  /* ---------- State ---------- */
  let choices = []; // { id, label, weight }
  let id = 1; // incremental id
  let input = ""; // bound to text input
  let weight = 1; // bound to number input

  let choiceCount = [];
  let selectedId = null;
  let isWaiting = false;
  let waitMs = 1200;

  /* ---------- Helpers ---------- */

  // make sure range is 1-10.
  // - Empty/NaN → 1
  // - <1 → 1
  // - >10 → 10
  const w10 = (n) => Math.min(10, Math.max(1, Math.floor(Number(n) || 1)));

  // Keep the bound weight valid as the user types.
  $: weight = w10(weight);

  // Rebuild the expanded array of ids used for weighted random picking.
  function rebuildChoiceCount() {
    choiceCount = [];
    for (const c of choices) {
      const times = w10(c.weight); // make sure each choice's weight is valid
      for (let i = 0; i < times; i++) choiceCount.push(c.id);
    }
  }

  // Add a new option with its weight (clamped).
  function addOption(label, w = 1) {
    const clean = (label ?? "").trim();
    if (!clean) return;

    const safeW = w10(w); // enforce 1..10 here, too
    choices = choices.concat({ id: id++, label: clean, weight: safeW });

    rebuildChoiceCount();
    input = "";
    weight = 1;
  }

  // Remove the currently selected option.
  function removeSelected() {
    if (selectedId === null) return;
    choices = choices.filter((c) => c.id !== selectedId);
    selectedId = null;
    rebuildChoiceCount();
  }

  // Pick a random choice using the weighted list.
  function decide() {
    // Ignore clicks while waiting
    if (isWaiting) return;

    // If there are no choices, tell the user
    if (choiceCount.length === 0) {
      alert("No choices yet. Add something first!");
      return;
    }

    isWaiting = true;
    setTimeout(() => {
      const pickedId =
        choiceCount[Math.floor(Math.random() * choiceCount.length)];
      const picked = choices.find((c) => c.id === pickedId);
      alert(`Your pick: ${picked.label}`);
      isWaiting = false;
    }, waitMs);
  }

  // Toggle selection of a row by id.
  function select(id) {
    selectedId = selectedId === id ? null : id;
  }

  // Reactive convenience flags (auto-update):
  // - disable Add when input is empty
  // - disable Remove when nothing is selected
  // - only disable Randomizer while "waiting" (let decide() handle empty list)
  $: disableAdd = (input ?? "").trim() === "";
  $: disableRemove = selectedId === null;
  $: disableRandomizer = isWaiting;
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
                class={c.id === selectedId
                  ? "choices text-white bg-red-600 ring-2 ring-black"
                  : "choices text-white bg-black/75"}
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
