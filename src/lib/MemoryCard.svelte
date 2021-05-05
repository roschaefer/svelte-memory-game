<script>
	export let color = 'bg-red-500';
	let flipped = true;
	const handleClick = () => {
		flipped = !flipped;
	};
</script>

<div class={flipped ? color : 'bg-gray-500'} on:click={handleClick} />
