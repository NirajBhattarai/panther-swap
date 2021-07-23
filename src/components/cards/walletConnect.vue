<template>
  <div class="wallet_connect_wrapper">
    <div class="card wallet_card">
      <div class="connect_wallet_header">
        <p>Connect to a wallet</p>
        <div @click="onClose">
          <i class="fa fa-times" aria-hidden="true"></i>
        </div>
      </div>
      <div class="wallet_card_row" v-for="item in walletOptions" :key="item.name">
        <p>{{item.name}}</p>
        <img :src="item.img" alt />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WalletConnect",
  props: {
    onClose: {
      type: Function
    }
  },
  data() {
    return {
      walletOptions: [
        { name: "Metamask", img: "/images/metamask.svg" },
        { name: "TrustWallet", img: "/images/trustwallet.svg" },
        { name: "MathWallet", img: "/images/mathwallet.svg" },
        { name: "TokenPocket", img: "/images/tokenPocket.svg" },
        { name: "WalletConnect", img: "/images/walletConnect.svg" },
        { name: "Binance Chain Wallet", img: "/images/binance.svg" }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
@import "../../theme/scss/variables.scss";
.connect_wallet_header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  border-bottom: 1px solid $white;
  margin-bottom: 1rem;
  & p {
    font-size: 1.5rem;
    font-weight: 600;
    color: $white;
  }

  & .fa-times {
    color: $darkPink;
    cursor: pointer;
  }
}
.wallet_connect_wrapper {
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgb(255, 114, 13, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
}
.wallet_card {
  border: 1px solid rgb(82, 75, 99);
  min-width: 22.5rem;
}
.wallet_card_row {
  border-radius: 1rem;
  padding: 0.5rem 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: nowrap;
}
</style>