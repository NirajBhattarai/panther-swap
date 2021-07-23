<template>
  <div class="header">
    <WalletConnect v-if="showModal" :onClose="handleModal" />
    <div @click="onMenuClick">
      <LogoIcon />
    </div>
    <div class="button_wrapper__auth">
    <button class="login__button"> Log In</button>
    <CustomButton text="Sign Up" :onClick="handleModal" />
    <CustomButton text="connect" :onClick="handleModal" />
    </div>
  </div>
</template>

<script>
import CustomButton from "./buttons/custombutton.vue";
import WalletConnect from "./cards/walletConnect.vue";
import LogoIcon from "./icons/logo.vue";

export default {
  name: "Header",
  components: {
    CustomButton,
    WalletConnect,
    LogoIcon,
  },
  props: {
    onMenuClick: {
      type: Function,
    },
  },
  data() {
    return {
      showModal: false,
    };
  },
  methods: {
    handleModal() {
      console.log("running");
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style lang="scss">
@import "../theme/scss/variables.scss";
.header {
  background-color: rgb(18, 24, 39);
  height: 4rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1rem;
  padding-top: 2.7rem;
  position: sticky;
  top: 0;
}
.button_wrapper__auth{
  min-width: 19rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.login__button{
  color: $darkPink;
  background-color: transparent;
  border: none;
  font-size: 1.5rem;
  font-weight: 600;
}
.menu_icon {
  font-size: 1.5rem;
  color: $darkPink;
  cursor: pointer;
}
.contact {
  background-color: $darkPink;
  color: $white;
  padding: 0.5rem;
  font-family: "Mitr", sans-serif;
}
</style>
