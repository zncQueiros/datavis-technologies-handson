<script>
  import {scaleLog} from 'd3-scale';
  import {axisBottom} from 'd3-scale';
  import {select} from 'd3-selection';
  // Dimensions
  const width = 800;
  const height = 100;
  const margin = { top: 5, right: 5, bottom: 5, left: 5 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;
  const logscaler = scaleLog()
                    .domain([1,10])
                    .range([0,innerWidth]);
  const xAxis = axisBottom(logscaler);
  function myFunction(x){
    xAxis(select(x))
  }

  // Array
  const values = [2, 4, 6, 7, 9];
</script>

<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left},{margin.top})">
    {#each values as value}
     <circle cx={logscaler(value)} cy={innerHeight/2} r="10" fill='teal'/>
    {/each}
  </g>
  <g transform="translate({margin.left},{margin.top})" use:myFunction></g>
  <text font-size="15" x=380 y=95>x-axis</text>
</svg>

<style>
  text {
    color: teal;
  }
</style>
  