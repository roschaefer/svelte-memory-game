<script lang="ts">
	import { CardState } from '$lib/cardStates.ts'
	import MemoryCard  from '$lib/MemoryCard.svelte';
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

	let motifs = colors.concat(colors).map((color, index) => ({ id: index, color, state: CardState.hidden })) ;

	function handleClick (index) {
		const flipped = motifs.filter(motif => motif.state === CardState.flipped)
		if (flipped.length >= 2) {
			const [one, other] = flipped
			if(one.color === other.color) {
				one.state = CardState.revealed
				other.state = CardState.revealed
			} else {
				one.state = CardState.hidden
				other.state = CardState.hidden
			}
		}
		const toFlip = motifs.find(motif => motif.id === index)
		toFlip.state = CardState.flipped
		motifs = motifs
	};
</script>

<div class="grid grid-cols-4 gap-4 h-96 w-96">
	{#each motifs as motif (motif.id)}
		<MemoryCard motif={motif} on:click={handleClick(motif.id)} />
	{/each}
</div>
