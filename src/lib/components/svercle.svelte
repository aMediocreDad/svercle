<svelte:options namespace="svg" />

<script lang="ts">
	export let config: { curve?: number; anchor?: number; fill?: string };

	config.fill = config.fill ?? '#fff';
	config.curve = config.curve ?? 5;
	config.anchor = config.anchor ?? 0;

	const height = 1000;
	const width = 1000;
	const halfHeight = height / 2;
	const halfWidth = width / 2;

	let path: string,
		fill: string,
		curve: number,
		anchor: number,
		curveShiftW: number,
		curveShiftH: number,
		anchorShiftW: number,
		anchorShiftH: number;

	$: {
		fill = config.fill;
		curve = config.curve * 0.18;
		anchor = config.anchor * 0.01;
		curveShiftW = Math.round(halfWidth * (1 - curve));
		curveShiftH = Math.round(halfHeight * (1 - curve));
		anchorShiftW = Math.round(halfWidth * anchor);
		anchorShiftH = Math.round(halfHeight * anchor);

		path = `
			M 0,${halfHeight - anchorShiftH}
			C 0,${curveShiftH - anchorShiftH} ${curveShiftW - anchorShiftW},0 ${
			halfWidth - anchorShiftW
		},0
			S ${curveShiftW + anchorShiftW},0 ${halfWidth + anchorShiftW},0
			${width},${curveShiftH - anchorShiftH} ${width},${halfHeight - anchorShiftH}
			${width},${curveShiftH + anchorShiftH} ${width},${halfHeight + anchorShiftH}
			${width - curveShiftW + anchorShiftW},${height} ${
			halfWidth + anchorShiftW
		},${height}
			${width - curveShiftW - anchorShiftW},${height} ${
			halfWidth - anchorShiftW
		},${height}
			0,${height - curveShiftH + anchorShiftH} 0,${halfHeight + anchorShiftH}
			0,${height + curveShiftH - anchorShiftH} 0,${halfHeight - anchorShiftH}
		`;
	}
</script>

<svg
	class="svercle-svg-element"
	version="1.1"
	xmlns="http://www.w3.org/2000/svg"
	xmlns:xlink="http://www.w3.org/1999/xlink"
	height="100%"
	width="100%"
	preserveAspectRatio="none"
	viewBox="{-halfWidth * 0.2} {-halfHeight * 0.2} {width * 1.2} {height * 1.2}"
>
	<path {fill} d={path} />
</svg>
