# Svercle

![svercle-example](https://user-images.githubusercontent.com/9851733/140587531-dded69ec-507f-484a-8328-d8d3a0f43457.png)

This is the Svercle. A small svelte component that produces a configurable superellipse approximation similar to a squircle. The component is based on this [REPL](https://svelte.dev/repl/2319271d93c34981aafce411f8345be8?version=3.18.2) (I have yet to find the author, but would like to thank them for all the work).

Use this as buttons, cards, or any other element that you would like apply a funny shape to. The squircle is, after all, the cutest of all the shapes.

> Why an approximation you ask? In order to keep the generated svg small and reusable I decided to use an eight point approximation (see the REPL link above) which also allows for creating some truly interesting shapes.

## Install

```bash
#Grab the package from npm:
npm install svercle
```

## Usage

This library exports two components. A `Svercle` component and a `SvercleContainer` component.

- The `SvercleContainer` component is a simple wrapper around the `Svercle` component equipped with a grid and a slot for your content (makes it easy to use as a button).

- The `Svercle` component is the actual component that you can use. It takes a `config` object as a prop.

The `config` object has the following properties: `curve`, `anchor`, and `fill`.

- The `curve` property is a number between `0` and `10` that determines the curvature of the superellipse.

- The `anchor` property is a number between `0` and **10** that determines the corner sharpness.

- The `fill` property is a string that determines the color of the superellipse. All properties are optional, and the `curve`, and `anchor` default to 5 and 0 respectively. While `fill` defaults to `#fff`.

### Example:

```html
<script>
	import { SvercleContainer } from 'svercle';

	let config = {
		curve: 6,
		anchor: 0.2,
		fill: '#e13c6e'
	};
</script>

<button>
	<SvercleContainer {config}><span>Click me!</span></SvercleContainer>
</button>

<style>
	button {
		padding: 0;
		border: none;
		background: none;
		cursor: pointer;
	}
	span {
		padding: 1rem 2rem;
	}
</style>
```

## License

This component is licensed under the [MIT License (MIT)](./LICENSE).
