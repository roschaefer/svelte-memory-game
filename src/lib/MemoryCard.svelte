<script lang="ts">
	import { CardState } from '$lib/cardStates.ts'
	export let motif: { id: number, state: CardState, color: string }
</script>

<div class={motif.state === CardState.hidden ? 'bg-gray-500' : motif.color} on:click />
