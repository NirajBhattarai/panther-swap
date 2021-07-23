<template>
  <div class="card">
    <p class="unlock_wallet_text">Click Here to Participate</p>
    <div style="text-align:center">
      <div class="inputbox">
        <input v-model="first_number" type="number" @change="handleSearch" /> &nbsp;
        <input v-model="second_number" type="number" @change="handleSearch" />&nbsp;
        <input v-model="third_number" type="number" @change="handleSearch" />&nbsp;
        <input v-model="fourth_number" type="number" @change="handleSearch" />&nbsp;
      </div>
      <CustomButton v-on:click="participate()" text="Participate" />
    </div>
  </div>

  <div id="card" class="card">
    <p class="unlock_wallet_text">Approve Token to Participate on Lottery</p>
    <div style="text-align:center">
    <div class="inputbox">
    <input v-model="minimumNumber" type="number" @change="handleSearch" />
    </div>
      <CustomButton v-on:click="approve()" text="Approve Token" />
    </div>
  </div>
</template>
<script>
import CustomButton from "../buttons/custombutton.vue";
import BEP20 from "../../abi/BEP20";
import Lottery from "../../abi/Lottery";

import Web3 from "web3";
export default {
  name: "UnlockWallet",
  components: {
    CustomButton,
  },
  data() {
    return {
      numInput: 0,
      admin_token: 0,
      first_number: 0,
      second_number: 0,
      third_number: 0,
      fourth_number: 0,
      maxNumber: "",
      minimumNumber: 10000,
      claim_reward: 0,
      testnet: `https://bsc-dataseed1.binance.org:443`,
      web3: new Web3(
        Web3.givenProvider || new Web3.providers.HttpProvider(this.testnet)
      ),
      lottery: "0x8bcdbA0F4fbb5A7bD1C897317db127a9c0b6d949",
      bep20: "0x549A17EA726EC949E657d731D1707160788b5f02",
    };
  },
  methods: {
    participate: async function () {
      const methods = await new this.web3.eth.Contract(
        Lottery.abi,
        this.lottery
      ).methods;
      this.web3.eth.getAccounts().then(async (addresses) => {
        methods
          .buy(this.minimumNumber, [
            this.first_number,
            this.second_number,
            this.third_number,
            this.fourth_number,
          ])
          .send({
            from: addresses[0]
          }).then(data=>{
      console.log(data);
      alert('Participated Scuccessfully');
      });
      });
    },

    

  approve: async function () {
      const methods = await new this.web3.eth.Contract(BEP20.abi, this.bep20)
        .methods;
      this.web3.eth.getAccounts().then(async (addresses) => {
        console.log(addresses);
        console.log(methods);

        await methods
          .approve(this.lottery, this.minimumNumber).send({
           from: addresses[0]
        }).then(data=>{
        console.log(data);
        alert('Desposited Success');
        });


      });
    },
  },
};
</script>

<style scoped lang="scss">
@import "../../theme/scss/variables.scss";

.unlock_wallet_text {
  font-weight: 600;
  font-size: 1.25rem;
  text-align: center;
  margin-bottom: 1rem;
}

.inputbox {
  border-radius: 1rem;
  padding: 0.5rem;
  background-color: $darkGray;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 2rem;

  & input {
    width: 100%;
    background-color: transparent;
    border: none;
    height: 2rem;
    font-size: 1rem;
    color: $white;
    font-family: "Mitr", sans-serif;
    &:focus {
      outline: none;
    }
  }
}

.card {
  margin-bottom: 2rem;
}
</style>