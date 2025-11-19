<script>
	import NumberFlow from '@number-flow/svelte';
	import { ss } from './state.svelte';
	import Timer from './Timer.svelte';

	const fsz = $derived(Math.min(32, 36 * Math.min(ss.scale, 1)));
	const lsz = $derived(fsz * 0.9);
	const alive = $derived(ss.fobs.filter((f) => !f.dead).length);
	const dead = $derived(ss.fobs.filter((f) => f.dead && f.dead !== true).length);
</script>

{#if !ss.dlg}
	<div class="info-panel {ss.over ? 'over' : ''}" style="font-size: {fsz}px;">
		<div class="timer"><Timer /></div>
		<div class="label" style="font-size: {lsz}px; margin-top: 20px;">alive</div>
		<div class="num">
			<NumberFlow value={alive} />
		</div>
	</div>
{/if}

<style>
	.info-panel {
		grid-area: 2/1;
		place-self: center;
		display: grid;
		place-items: center;
		/* background: #fff4; */
		padding: 10px;
		/* opacity: 0.3; */
		pointer-events: none;
		transition: opacity 1s;
	}

	.over {
		z-index: 2;
		/* opacity: 0.6; */
	}

	.label {
		margin-right: 20px;
		font-family: Orbitron;
	}

	.timer,
	.num {
		font-family: Radhiumz;
	}
</style>
