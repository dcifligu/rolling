
<template>
  <svg
    ref="svgRef"
    width="1920"
    height="604"
    viewBox="0 0 1920 604"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
  >
    <g id="Group 17">
      <line v-for="i in 30" :key="i" :x1="1920" :y1="(i - 1) * 15 + 0.5" :y2="(i - 1) * 15 + 0.5" stroke="white"/>
    </g>
  </svg>
</template>
