<template>
  <div class="card">
    <div class="card__header">
      <div class="card__avatar"></div>
      <div class="card__info__wrapper">
        <p>Total Pot</p><span>{{totalPot}}</span>
        <h2>PANTHER</h2>
      </div>
    </div>
    <div class="card__body">
      <div class="card__body__item__header">
        <p>No. Matched</p>
        <p>Prize Pot</p>
      </div>
      <div class="card__body__item__body" v-for="item in table" :key="item.id">
        <p>{{item.id}}</p>
        <p>{{item.pot}}</p>
      </div>
    </div>
  </div>
</template>

<script>

import Lottery from '../../abi/Lottery'
import Web3 from 'web3'
export default {
  name: "PantherTable",
  data() {
    return {

    totalPot:1000,
      table: [
        { id: 4, pot: 2150 },
        { id: 3, pot: 760 },
        { id: 2, pot: 200 },
        { id: 1, pot: 100 }
      ]
    };
  },

  beforeCreate: async function(){
  const testnet=`https://bsc-dataseed1.binance.org:443`;
  const web3 = new Web3(new Web3.providers.HttpProvider(testnet));
  const lottery = "0x8bcdbA0F4fbb5A7bD1C897317db127a9c0b6d949";
  const methods = await new web3.eth.Contract(Lottery.abi,lottery).methods;
  methods.totalAmount().call().then(data=>this.totalPot=data);

  }


};
</script>

<style scoped lang="scss">
@import "../../theme/scss/variables.scss";
.card {
  box-shadow: 0 3px 6px #000000;
  background-color: $darkBlue2;
  border-radius: 1.687rem;
  padding: 0;
  &__avatar {
    width: 4rem;
    height: 4rem;
    background-color: $darkGray;
    border-radius: 50%;
    margin-right: 1rem;
  }
  &__header {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding-bottom: 1rem;
    background-color: $darkBlue3;
    border-bottom: 1px solid $darkGray;
    border-radius: 1.687rem;
    padding: 1rem 2rem;
  }
  &__info__wrapper {
    & p {
      font-size: 0.875rem;
      color: $darkPink;
    }
    & h2 {
      font-size: 1.5rem;
      font-weight: 600;
    }
  }
  &__body {
     padding: 1rem 2rem;
    &__item__header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      color: $darkPink;
    }
    &__item__body {
      display: flex;
      align-items: center;
      justify-content: space-between;
      color: $white;
    }
  }
}
</style>