<template>
  <div class="toggler_wrapper">
    <div class="toggle_button_wrapper">
      <CustomButton
        text="Next draw"
        :variant="active===1 ? 'active': 'inactive'"
        :onClick="()=>onToggle(1)"
      />
      <CustomButton
        text="Past draws"
        :variant="active===2 ? 'active': 'inactive'"
        :onClick="()=>onToggle(2)"
      />
      <CustomButton
        text="Admin draws"
        :variant="active===3 ? 'active': 'inactive'"
        :onClick="()=>onToggle(3)"
      />
    </div>
  </div>
</template>

<script>
import CustomButton from "../buttons/custombutton.vue";

export default {
  name: "ToggleButton",
  props: {
    onToggle: {
      type: Function,
    },
    active: {
      type: String,
    },
  },
  components: {
    CustomButton,
  },
};
</script>

<style scoped lang="scss">
@import "../../theme/scss/variables.scss";
.toggle_button_wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 2rem;
  border-radius: 2rem;
  max-width: 23.2rem;
  background-color: $darkGray;
  margin: auto;
}
</style>