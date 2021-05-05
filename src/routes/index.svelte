<script context="module" lang="ts">
	export const prerender = true;
	import MemoryCard from '$lib/MemoryCard.svelte';
	/**
	 * Shuffles array in place. ES6 version
	 * @param {Array} a items An array containing the items.
	 */
	function shuffle(a: Array<string>): Array<string> {
		for (let i = a.length - 1; i > 0; i--) {
			const j = Math.floor(Math.random() * (i + 1));
			[a[i], a[j]] = [a[j], a[i]];
		}
		return a;
	}
	let colors = [
		'bg-green-500',
		'bg-red-500',
		'bg-blue-500',
		'bg-yellow-300',
		'bg-yellow-600',
		'bg-pink-500',
		'bg-purple-500',
		'bg-indigo-800'
	];
	let motifs = shuffle(colors.concat(colors));
</script>

<section>
	<header>
		<h1>Memory Game</h1>
	</header>
	<div class="grid grid-cols-4 gap-4 h-96 w-96">
		{#each motifs as motif, index (index)}
			<MemoryCard color={motif} />
		{/each}
	</div>
</section>
