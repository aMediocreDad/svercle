<script lang="ts">
	import SvercleContainer from '$lib/components/svercle-container.svelte';

	let config = {
		curve: 5,
		anchor: 0,
		fill: '#ED2F5B'
	};

	let height = 250;
	let width = 250;

	let h, w;

	$: {
		h = `${height}px`;
		w = `${width}px`;
	}
</script>

<header>
	<h1>Svercle</h1>
</header>
<main>
	<ul>
		<li>
			<label for="curve">Curve</label>
			<input id="curve" type="range" bind:value={config.curve} min="0" max="10" step="0.1" /><span
				>{config.curve}</span
			>
		</li>
		<li>
			<label for="anchor">Anchor</label>
			<input id="anchor" type="range" bind:value={config.anchor} min="0" max="10" step="0.1" /><span
				>{config.anchor}</span
			>
		</li>
		<li>
			<label for="height">Width</label>
			<input id="height" type="range" bind:value={height} min="50" max="300" step="10" /><span
				>{height}</span
			>
		</li>
		<li>
			<label for="width">Height</label>
			<input id="width" type="range" bind:value={width} min="50" max="300" step="10" /><span
				>{width}</span
			>
		</li>
	</ul>

	<div style="--height: {h}; --width:{w}">
		<SvercleContainer {config}>Hello!</SvercleContainer>
	</div>

	<footer style="--ellipse:data:url(image/svg+xml;utf8,{SvercleContainer})" />
</main>

<style>
	:global(body) {
		min-height: 100vh;
		display: grid;
		place-content: center;

		font-family: sans-serif;
		text-align: center;
		font-weight: 700;
		--color: #ed2f5b;
		color: var(--color);
	}

	h1 {
		font-size: 4rem;
		color: darkslategray;
		text-transform: uppercase;
	}

	main {
		display: grid;
		grid-template-rows: 200px 500px;
		place-items: center;
	}

	div {
		width: var(--height);
		height: var(--width);
		border: 3px dashed #1116;
		border-radius: 10px;
		align-self: baseline;
	}
	div :global(svg) {
		filter: drop-shadow(2px 1px 6px #ed2f5b6c);
	}

	ul {
		list-style: none;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
	}

	li {
		display: grid;
		gap: 0.5rem;
	}

	label {
		user-select: none;
	}

	input {
		accent-color: var(--color);
	}

	span {
		font: bold 2rem sans-serif;
		color: darkslategray;
	}

	footer {
		background-image: var(--ellipse);
	}
</style>
