<script lang="ts">
	import SvercleContainer from '$lib/components/svercle-container.svelte';

	let config = {
		curve: 5,
		anchor: 0,
		fill: '#e13c6e'
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
	<a href="https://www.npmjs.com/package/svercle"><h1>Svercle</h1></a>
</header>
<main>
	<ul>
		<li>
			<span>{config.curve}</span>
			<input id="curve" type="range" bind:value={config.curve} min="0" max="10" step="0.1" />
			<label for="curve">Curve</label>
		</li>
		<li>
			<span>{config.anchor}</span>
			<input id="anchor" type="range" bind:value={config.anchor} min="0" max="10" step="0.1" />
			<label for="anchor">Anchor</label>
		</li>
		<li>
			<span>{height}</span>
			<input id="height" type="range" bind:value={height} min="50" max="300" step="10" />
			<label for="height">Width</label>
		</li>
		<li>
			<span>{width}</span>
			<input id="width" type="range" bind:value={width} min="50" max="300" step="10" />
			<label for="width">Height</label>
		</li>
	</ul>

	<div class="svercle" style="--height: {h}; --width:{w}">
		<SvercleContainer {config}>Hello!</SvercleContainer>
	</div>
</main>
<footer>
	Lots of <span>💖</span> to whomever made this
	<a href="https://svelte.dev/repl/2319271d93c34981aafce411f8345be8?version=3.18.2" rel="noopener"
		>REPL example</a
	>
</footer>

<style>
	:global(body) {
		min-height: 100%;
		display: grid;
		place-content: center;

		font-family: sans-serif;
		text-align: center;
		font-weight: 700;
		--color: #e13c6e;
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
		filter: drop-shadow(2px 1px 6px #e13c6e6c);
	}

	div.svercle {
		color: whitesmoke;
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
		font: bold 2rem sans-serif;
		color: darkslategray;
	}

	span {
		font-size: 1.1rem;
	}

	input {
		accent-color: var(--color);
	}

	footer {
		font-size: 0.9rem;
		text-align: center;
		color: darkslategray;
	}

	a {
		color: var(--color);
		text-decoration: none;
	}

	a:hover,
	a:focus-visible {
		text-decoration: underline;
	}

	footer span {
		filter: hue-rotate(345deg) saturate(0.5) brightness(1.5);
	}
</style>
