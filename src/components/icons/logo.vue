<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    width="322"
    height="78"
    viewBox="0 0 322 78"
  >
    <defs>
      <filter id="a" x="0" y="0" width="322" height="78" filterUnits="userSpaceOnUse">
        <feOffset dy="3" input="SourceAlpha" />
        <feGaussianBlur stdDeviation="3" result="b" />
        <feFlood flood-opacity="0.161" />
        <feComposite operator="in" in2="b" />
        <feComposite in="SourceGraphic" />
      </filter>
    </defs>
    <g class="c" transform="matrix(1, 0, 0, 1, 0, 0)">
      <text class="a" transform="translate(9 55)">
        <tspan x="0" y="0">PATHER</tspan>
        <tspan class="b" y="0">SWAP</tspan>
      </text>
    </g>
  </svg>
</template>

<script>
export default {
  name: "LogoIcon",
};
</script>

<style>
.a {
  fill: #fff;
  font-size: 45px;
  font-family: SegoeUI-BoldItalic, Segoe UI;
  font-weight: 700;
  font-style: italic;
}
.b {
  fill: #d9113a;
}
</style>