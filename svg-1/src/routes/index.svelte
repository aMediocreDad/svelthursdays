<script>
	import LineChart from '$lib/svg/line-chart.svelte';
</script>

<h1>Svelthursday SVG</h1>

<!-- This type of import does not work -->
<svg width="100%" height="100%">
	<use href="/line-chart.svg" />
</svg>

<!-- This does! -->
<LineChart />
