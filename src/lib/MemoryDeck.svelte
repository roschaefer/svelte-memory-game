<script lang="ts">
	import { CardState } from '$lib/cardStates.ts'
	import MemoryCard  from '$lib/MemoryCard.svelte';
	const { hidden, revealed, flipped } = CardState
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

	let motifs = colors.concat(colors).map((color, index) => ({ color, state: hidden })) ;

	function handleClick (toFlip) {
		const flippedMotifs = motifs.filter(motif => motif.state === flipped)
		if (flippedMotifs.length >= 2) {
			const [one, other] = flippedMotifs
			if(one.color === other.color) {
				one.state = revealed
				other.state = revealed
			} else {
				one.state = hidden
				other.state = hidden
			}
		}
		toFlip.state = flipped
		motifs = motifs
	};
</script>

<div class="grid grid-cols-4 gap-4 h-96 w-96">
	{#each motifs as motif, i (i)}
		<MemoryCard motif={motif} on:click={handleClick(motif)} />
	{/each}
</div>
