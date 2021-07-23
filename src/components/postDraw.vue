<template>
  <div class="grid__wrapper">
    <WalletConnect v-if="showWallet" :onClose="handleWallet" />
    <div class="grid_col_1">
      <div class="input__container">
        <p class="lotnumer">Select Lottery Number</p>
        <div class="lottery__input">
          <input  v-model="numInput" type="number" @change="handleSearch" />
          <CustomButton v-on:click="handleSearch()" text="Search" />
        </div>
      </div>

      <div class="card">
        <div class="id_container">
          <p class="id">Round #1</p>
          <p class="date">
            May 01, 2:00 UTC
            Round #1
          </p>
        </div>
        <div class="number__prize__container">
          <div class="avatar"></div>
          <div class="info">
            <p>Winning numbers</p>
            <h2 >
            <span v-for =" i in winingNumber" :key ="i">{{i+`,`}}&nbsp;</span>
            </h2>
          </div>
        </div>
        <div class="number__prize__container">
          <div class="avatar"></div>
          <div class="info">
            <p>Total prizes</p>
            <h2>14,048 PANTHER</h2>
          </div>
        </div>
        <div class="card_table_wrapper">
          <div class="table_header_xser">
            <p>No. Matched</p>
            <p>Winners</p>
            <p>Prize Pot</p>
          </div>
          <div class="table_body_xser" v-for="item in table" :key="item.id">
            <p>{{item.id}}</p>
            <p>{{item.winner}}</p>
            <p>{{item.pot}}</p>
          </div>
        </div>
        <div class="flex">
          <CustomButton text="Unlock Wallet" style="margin:auto" :onClick="handleWallet" />
        </div>
      </div>
    </div>
    <div class="grid_col_2"></div>
  </div>
</template>

<script>
import CustomButton from "./buttons/custombutton.vue";
import WalletConnect from "./cards/walletConnect.vue";
import Web3 from 'web3'
import Lottery from '../abi/Lottery'

export default {
  name: "PostDraw",
  components: {
    CustomButton,
    WalletConnect
  },
  data() {
    return {
      table: [
        { id: 4, winner: 0, pot: "7,024" },
        { id: 3, winner: 0, pot: "7,024" },
        { id: 2, winner: 0, pot: "7,024" },
        { id: 1, winner: 0, pot: "7,024" }
      ],
      showWallet: false,
      numInput:0,
      winingNumber:[]
    };
  },

  beforeCreate: async function(){
  const testnet=`https://data-seed-prebsc-1-s1.binance.org:8545/`;
  const web3 = new Web3(new Web3.providers.HttpProvider(testnet));
  const lottery = "0x8bcdbA0F4fbb5A7bD1C897317db127a9c0b6d949";
  const methods = await new web3.eth.Contract(Lottery.abi,lottery).methods;
  methods.historyNumbers(this.numInput,0).call().then(data=>this.winingNumber[0]=data);
  methods.historyNumbers(this.numInput,1).call().then(data=>this.winingNumber[1]=data);
  methods.historyNumbers(this.numInput,2).call().then(data=>this.winingNumber[2]=data);
  methods.historyNumbers(this.numInput,3).call().then(data=>this.winingNumber[3]=data);
  },
  methods: {
  created: async function()
  {
  console.log("helo");
  },
  
  handleSearch:  async function()
    {
  const testnet=`https://data-seed-prebsc-1-s1.binance.org:8545/`;
  const web3 = new Web3(new Web3.providers.HttpProvider(testnet));
  const lottery = "0x8bcdbA0F4fbb5A7bD1C897317db127a9c0b6d949";
  const methods = await new web3.eth.Contract(Lottery.abi,lottery).methods;
  methods.historyNumbers(this.numInput,0).call().then(data=>this.winingNumber[0]=data);
  methods.historyNumbers(this.numInput,1).call().then(data=>this.winingNumber[1]=data);
  methods.historyNumbers(this.numInput,2).call().then(data=>this.winingNumber[2]=data);
  methods.historyNumbers(this.numInput,3).call().then(data=>this.winingNumber[3]=data);
    },
    handleWallet() {
      this.showWallet = !this.showWallet;
    }
  }
};
</script>

<style scoped lang="scss">
@import "../theme/scss/variables.scss";
.lotnumer {
  color: $white;
}
.lottery__input {
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
.grid__wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-top: 2rem;
}
.grid_col_1,
.grid_col_2 {
  width: calc(50% - 1rem);
}
.id_container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1rem;
  .id {
    font-weight: 600;
    color: $white;
  }
  .date {
    color: $white;
  }
}
.number__prize__container {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
  .avatar {
    width: 4rem;
    height: 4rem;
    background-color: $blue;
    border-radius: 50%;
    margin-right: 1rem;
  }
  p {
    color: $darkPink;
  }
}
.table_header_xser {
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: $darkPink;
  border-top: 1px solid $darkGray;
  padding-top: 1rem;
}
.table_body_xser {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-weight: 500;
  color: $white;
}
.flex {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 1rem;
  button {
    padding-top: 0.6rem;
    padding-bottom: 0.6rem;
  }
}
</style>