<script>
    // props from parent
    export let option = ""; // bound to App's `input`
    export let weight = 1; //default weight is 1
    export let addOption = (o, w) => {}; // called to add
    export let removeSelected = () => {}; // removes currently selected item
    export let disableAdd = true; // disable Add when input empty
    export let disableRemove = true; // disable Remove when nothing selected

    function onAdd() {
        if (disableAdd) return; // do nothing if empty
        addOption(option, weight);
    }

    function onRemove() {
        if (disableRemove) return; // do nothing if nothing selected
        removeSelected();
    }
</script>

<div id="formDiv" class="flex justify-around">
    <form id="" on:submit|preventDefault class="flex justify-center gap-3">
        <div id="Input-div">
            <div class="gap-1">
                <label for="option" class="text-sm font-medium">Option:</label>
                <input
                    id="option"
                    type="text"
                    bind:value={option}
                    placeholder="Type a choice..."
                    class="outline outline-1 outline-offset-1 rounded px-3 py-2 m-3 w-64 bg-gray-50"
                />
            </div>

            <div class="gap-1">
                <label for="weight" class="text-sm font-medium">Weight:</label>
                <input
                    id="weight"
                    type="number"
                    bind:value={weight}
                    min="1"
                    max="10"
                    placeholder="Enter a weight...(1-10)"
                    class="outline outline-1 outline-offset-1 rounded px-3 py-2 m-3 w-64 bg-gray-50"
                />
            </div>
        </div>

        <button
            type="button"
            on:click={onAdd}
            class="custom"
            disabled={disableAdd}
        >
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
</div>
