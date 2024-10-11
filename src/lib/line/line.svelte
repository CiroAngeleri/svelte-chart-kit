<script lang="ts">
	import * as d3 from 'd3';
	type Props = {
		x: any;
		y: any;
		data: any;
	};
	let { data = [], x, y }: Props = $props();

	const line = d3.line().x(x).y(y);
</script>

<path fill="none" stroke="steelblue" stroke-width="1.5" d={line(data)} />
