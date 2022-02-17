<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => {points += 1};
	const removePoint = () => {points -= 1};
	const toggleControls = () => {showControls = !showControls};
	const onDelete = () => dispatch("removeplayer", name);
    
</script>

<style>
	h1 {
		color: #00aeff;
	}
</style>


<div class="card mb-4">
    <div class="card-body">
        <h1>
            {name}
            <button class="btn btn-sm" on:click="{toggleControls}">
                {#if showControls}-{:else}+{/if}
            </button>
            <button on:click="{onDelete}" class="btn btn-sm btn-danger">x</button>
        </h1>
        <h3 class="mb-3">Points: {points}</h3>
        {#if showControls}
        <button class="btn" on:click={addPoint}>+1</button>
        <button class="btn btn-dark" on:click={removePoint}>-1</button>
        <br><input type="number" bind:value="{points}">	
        {/if}
    </div>
</div>

