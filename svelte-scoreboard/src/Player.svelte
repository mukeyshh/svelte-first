<script>

import {createEventDispatcher} from 'svelte';

 const dispatch = createEventDispatcher();

	export let name;
	export let points;
	let showControls=false;

	const addPoint=()=>(points+=1);
	const removePoint=()=>(points-=1);
	const toggle=()=>(showControls=!showControls)
    const onDelete=()=>dispatch("removeplayer",name);

</script>



<style>
	h1{
		color: blue;
	}
	h3{
		margin-bottom:10px ;
	}
</style>




	<div class="card">
	<h1>
		Hello {name}
		<button class="btn" on:click={toggle}>{#if showControls}-{:else}+{/if}</button>
        <button class="btn btn-danger btn-sm" on:click={onDelete}>Remove player</button>
	</h1>
	<h3>Points:{points}</h3>
{#if showControls}

	<button class="btn" on:click={addPoint}>+1</button>
	<button class="btn btn-dark" on:click={removePoint}>-1</button>
	<input type="number" bind:value={points}>

{/if}
</div>

