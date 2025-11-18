<script>
	import src from '$lib/images/Pet.webp';
	import Fob from './Fob.svelte';
	import { ss } from './state.svelte';

	const { index } = $props();
	const i = $derived(ss.fobs.findIndex((f) => f.id.startsWith('pet')));
</script>

<Fob bind:fob={ss.fobs[i + index]} {src} style={`opacity: ${ss.over ? 0.35 : 1}`} />
