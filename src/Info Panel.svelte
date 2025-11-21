<script>
	import NumberFlow from '@number-flow/svelte';
	import { ss } from './state.svelte';
	import Timer from './Timer.svelte';

	const fsz = $derived(Math.min(32, 36 * Math.min(ss.scale, 1)));
	const lsz = $derived(fsz * 0.8);
</script>

{#if !ss.dlg}
	<div class="info-panel" style="font-size: {fsz}px;">
		<div class="label" style="font-size: {lsz}px;">healthy kittens</div>
		<div class="num">
			<NumberFlow value={ss.fobs.filter((f) => !f.dead).length} />
		</div>
		<div></div>
		<div class="label" style="font-size: {lsz}px;">plague-free time</div>
		<div class="timer"><Timer ticks={ss.streak_ticks} /></div>
	</div>
{/if}

<style>
	.info-panel {
		grid-area: 2/1;
		place-self: center;
		display: grid;
		place-items: center;
		gap: 5px;
		color: var(--lightblue);
		opacity: 0.7;
		pointer-events: none;
	}

	.label {
		font-family: Orbitron;
		/* font-weight: bold; */
	}

	.timer,
	.num {
		font-family: Radhiumz;
	}
</style>
