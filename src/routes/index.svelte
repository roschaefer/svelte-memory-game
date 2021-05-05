<script context="module" lang="ts">
	export const prerender = true;
	import MemoryCard from '$lib/MemoryCard.svelte';
	let colors = ['bg-green-500', 'bg-red-500'];
	let motifs = colors.concat(colors);
</script>

<section>
	<header>
		<h1>Memory Game</h1>
	</header>
	<div class="grid grid-cols-2 gap-4 h-96 w-96">
		{#each motifs as motif, index (index)}
			<MemoryCard color={motif} />
		{/each}
	</div>
</section>
