<script>
    export let decide = () => {};
    export let disabled = false; // disabled when empty or waiting
    export let waiting = false; // show the thinking state
</script>

<button
    type="button"
    class={waiting ? "custom animate-pulse" : "custom"}
    on:click={decide}
    {disabled}
>
    {#if waiting}
        Thinking…
    {:else}
        🎰MAKE A CHOICE!🎰
    {/if}
</button>
