<template>
<svg xmlns="http://www.w3.org/2000/svg" class="lottery" xmlns:xlink="http://www.w3.org/1999/xlink" width="61.25" height="49.833">
  <defs>
    <filter id="Icon_awesome-ticket-alt" x="0" y="0" width="61.25" height="49.833" filterUnits="userSpaceOnUse">
      <feOffset dy="3" input="SourceAlpha"/>
      <feGaussianBlur stdDeviation="4.5" result="blur"/>
      <feFlood flood-color="red" flood-opacity="0.412"/>
      <feComposite operator="in" in2="blur"/>
      <feComposite in="SourceGraphic"/>
    </filter>
  </defs>
  <g id="Icon_awesome-ticket-alt-2" data-name="Icon awesome-ticket-alt" transform="translate(13.5 10.5)">
    <g transform="matrix(1, 0, 0, 1, -13.5, -10.5)" filter="url(#Icon_awesome-ticket-alt)">
      <path id="Icon_awesome-ticket-alt-3" data-name="Icon awesome-ticket-alt" d="M7.611,10.208H26.639V21.625H7.611ZM31.4,15.917a2.854,2.854,0,0,0,2.854,2.854v5.708A2.854,2.854,0,0,1,31.4,27.333H2.854A2.854,2.854,0,0,1,0,24.479V18.771a2.854,2.854,0,0,0,2.854-2.854A2.854,2.854,0,0,0,0,13.063V7.354A2.854,2.854,0,0,1,2.854,4.5H31.4A2.854,2.854,0,0,1,34.25,7.354v5.708A2.854,2.854,0,0,0,31.4,15.917ZM28.542,9.733a1.427,1.427,0,0,0-1.427-1.427H7.135A1.427,1.427,0,0,0,5.708,9.733V22.1a1.427,1.427,0,0,0,1.427,1.427H27.115A1.427,1.427,0,0,0,28.542,22.1Z" transform="translate(13.5 6)" fill="#d9113a"/>
    </g>
  </g>
</svg>

</template>

<script>
export default {
    name: "LotteryIcon"
}
</script>

<style scoped>
.lottery{
    margin-left: -15px;
}
</style>