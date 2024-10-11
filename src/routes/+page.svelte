<script lang="ts">
	import Line from '$lib/line/line.svelte';
	import * as d3 from 'd3';
	import data from '../__mocks__/data.json';

	type Datum = (typeof data)[number];

	const width = 300;
	const height = 300;

	const xDomain = d3.extent(data, (d: Datum) => new Date(d.date)) as [Date, Date];
	const yDomain = [0, d3.max(data, (d: Datum) => d.close)] as [0, number];
	const xRange = width;
	const xScale = d3.scaleUtc(xDomain, [0, xRange]);
	const yScale = d3.scaleLinear(yDomain, [height, 0]);

	const x = (d: Datum) => xScale(new Date(d.date));
	const y = (d: Datum) => yScale(d.close);
</script>

<svg {width} {height} viewBox="0 0 {width} {height}" style:max-width="100%" style:height="auto">
	<Line {x} {y} {data} />
</svg>
