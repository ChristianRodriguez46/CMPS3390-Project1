<script>
    // props from parent
    export let value = ""; // bound to App's `input`
    export let addOption = (v) => {}; // called to add
    export let removeSelected = () => {}; // removes currently selected item
    export let disableAdd = true; // disable Add when input empty
    export let disableRemove = true; // disable Remove when nothing selected

    function onAdd() {
        if (disableAdd) return; // do nothing if empty
        addOption(value);
    }

    function onRemove() {
        if (disableRemove) return; // do nothing if nothing selected
        removeSelected();
    }
</script>

<form on:submit|preventDefault class="flex items-end gap-3">
    <div class="flex flex-col gap-1">
        <label for="option" class="text-sm font-medium">Option:</label>
        <input
            id="option"
            type="text"
            bind:value
            placeholder="Type a choice..."
            class="outline outline-1 outline-offset-1 rounded px-3 py-2 w-64"
        />
    </div>

    <button type="button" on:click={onAdd} class="custom" disabled={disableAdd}>
        Add
    </button>

    <button
        type="button"
        on:click={onRemove}
        class="custom"
        disabled={disableRemove}
    >
        Remove
    </button>
</form>
