<script lang="ts">
	enum CardStates {
		hidden,
		flipped,
		revealed
	}
	export let color = 'bg-red-500';
	let flipped = CardStates.hidden;
	const handleClick = () => {
		flipped = flipped === CardStates.hidden ? CardStates.flipped : CardStates.hidden;
	};
</script>

<div class={flipped === CardStates.hidden ? 'bg-gray-500' : color} on:click={handleClick} />
