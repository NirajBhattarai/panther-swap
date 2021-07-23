<template>
  <button :class="['default', variant]" :disabled="disabled" @click="onClick">{{ text }}</button>
</template>

<script>
export default {
  name: "CustomButton",
  props: {
    variant: {
      type: String
    },
    text: {
      type: String,
      required: true
    },
    disabled: {
      type: Boolean
    },
    onClick: {
      type: Function
    },
    active: {
      type: Boolean
    }
  }
};
</script>

<style scoped lang="scss">
@import "../../theme/scss/variables.scss";
.default {
  background-color: $darkPink;
  border-radius: 1rem;
  box-shadow: rgb(14 14 44 / 40%) 0px -1px 0px inset;
  padding: 0.25rem 1rem;
  border: none;
  font-family: Mitr, sans-serif;
  font-size: 1rem;
  color: $white;
  font-weight: 600;
  text-transform: capitalize;
  cursor: pointer;
  transition: all 0.4s;
  &:disabled {
    background-color: $darkGray;
    color: $darkPink;
    box-shadow: none;
  }
}
.active {
  background-color: $darkPink;
}
.inactive {
  background-color: transparent;
   box-shadow: none;
   color: $darkPink;
}
</style>
