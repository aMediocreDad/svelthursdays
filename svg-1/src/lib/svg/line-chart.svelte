<script>
	export let prices_by_date = {
		y2008: 170,
		y2009: 100,
		y2010: 160,
		y2011: 120,
		y2012: 130,
		y2013: 200
	};

	let y2008, y2009, y2010, y2011, y2012, y2013;

	$: ({ y2008, y2009, y2010, y2011, y2012, y2013 } = prices_by_date);
</script>

<svg
	version="1.2"
	xmlns="http://www.w3.org/2000/svg"
	width="100%"
	height="100%"
	viewbox="0 0 1000 1000"
>
	<g class="labels">
		<text x="50" y="320">2008</text>
		<text x="150" y="320">2009</text>
		<text x="250" y="320">2010</text>
		<text x="350" y="320">2011</text>
		<text x="450" y="320">2012</text>
		<text x="250" y="340">Year</text>
	</g>
	<g class="labels y-labels">
		<text x="40" y="10">300'</text>
		<text x="40" y="100">200'</text>
		<text x="40" y="200">100'</text>
		<text x="40" y="300">0</text>
		<text x="20" y="150" class="y-label-title">Price</text>
	</g>
	<path d="M50 0v300" />
	<path d="M50 299h500" />
	<g stroke-dasharray="0 4 0">
		<line x1="50" y1={300 - y2008} x2="150" y2={300 - y2009} />
		<line x1="150" y1={300 - y2009} x2="250" y2={300 - y2010} />
		<line x1="250" y1={300 - y2010} x2="350" y2={300 - y2011} />
		<line x1="350" y1={300 - y2011} x2="450" y2={300 - y2012} />
		<line x1="450" y1={300 - y2012} x2="550" y2={300 - y2013} />
	</g>
</svg>

<style>
	svg {
		--color: #111;
	}

	line,
	path {
		stroke: var(--color);
	}

	.labels {
		font-size: 12px;
		font-family: sans-serif;
		text-anchor: start;
	}
	.y-labels {
		text-anchor: end;
	}

	.y-label-title {
		text-anchor: start;
		transform: rotate(90deg);
		transform-origin: 2% 14%;
	}
</style>
