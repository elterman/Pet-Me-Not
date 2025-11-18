<script>
	import Prompt from './Prompt.svelte';
	import { ss } from './state.svelte';
	import Toolbar from './Toolbar.svelte';

	const style = $derived(`gap: ${50 * ss.scale}px;`);
</script>

<div class="prompts" {style}>
    <Prompt />
    <Toolbar />
</div>

<style>
	.prompts {
        grid-area: 3/1;
        place-self: center;
		display: grid;
        place-items: center;
		margin-bottom: 15px;
	}
</style>
