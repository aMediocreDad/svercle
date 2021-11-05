<script lang="ts">
	import Svercle from './svercle.svelte';

	export let config: {
		curve?: number;
		anchor?: number;
		fill?: string;
	};
</script>

<div class="container">
	<Svercle {config} />
	<slot />
</div>

<style>
	.container {
		position: relative;
		width: 100%;
		height: 100%;
		display: grid;
		place-items: center;
	}
	.container :global(svg.svercle-svg-element) {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		width: 100%;
		z-index: -1;
	}
</style>
