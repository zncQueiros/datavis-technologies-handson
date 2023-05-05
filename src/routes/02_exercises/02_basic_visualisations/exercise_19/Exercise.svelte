<script>
  import {scaleLinear} from "d3-scale";
  import {scaleOrdinal} from "d3-scale"
  import {extent} from "d3-scale"
  import {schemeDark2} from "d3-scale-chromatic"
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;

    const linearscalerx = scaleLinear().domain([1,10]).range([0,innerWidth]);
    const linearscalery = scaleLinear().domain([1,3]).range([0,innerHeight]);
    const classcolor = extent(values,(d)=>d.category);
    const scalecolor = scaleOrdinal().domain(classcolor).range(schemeDark2);
  
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as value}
        <circle cx={linearscalerx(value.x)} cy={linearscalery(value.y)-10} radius="5" fill={scalecolor(value.category)}></circle>
        <text x={linearscalerx(value.x)} y={linearscalery(value.y)-10}>{value.y}</text>
        <line x1={linearscalerx(value.x)} x2={linearscalerx(value.x)} y1={linearscalery(value.y)} y2={height} stroke="black"></line>
      {/each}
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  
  <li>{classcolor}</li>