<template>
<div  id= "card" class="card">
    <p class="unlock_wallet_text">Enter the Number Of Token To Send Admin</p>
    <div class="inputbox">
          <input  v-model="admin_token" type="number" @change="handleSearch" />
          <CustomButton v-on:click="sendAdmin()" text="Send" />
     </div>
</div>

  <div  id= "card" class="card">
    <p class="unlock_wallet_text">Enter Drawing Phase</p>       
          <CustomButton v-on:click="enterDrawingPhase()" text="Enter Drawing Phase" />
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Enter the Random Number</p>
    <div class="inputbox">
          <input  v-model="numInput" type="number" @change="handleSearch" />
          <CustomButton v-on:click="draw()" text="Draw" />
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Reset Lottery</p>
    <div class="inputbox">
          <CustomButton v-on:click="reset()" text="Reset" />
     </div>
</div>

  <div  id= "card" class="card">
    <p class="unlock_wallet_text">Claim Reward</p>
    <div class="inputbox">
          <input  v-model="claim_reward" type="number" @change="handleSearch" />
          <CustomButton v-on:click="claimReward()" text="Send" />
     </div>
</div>


<div  id= "card" class="card">
    <p class="unlock_wallet_text">Set Maximum Number</p>
    <div class="inputbox">
          <input  v-model="maxNumber" type="text" @change="handleSearch" />
          <CustomButton v-on:click="setMaxNumber()" text="SetMaxNumber" />
     </div>
</div>


<div  id= "card" class="card">
    <p class="unlock_wallet_text">Set minimum Number</p>
    <div class="inputbox">
          <input  v-model="minimumNumber" type="text" @change="handleSearch" />
          <CustomButton v-on:click="minimum()" text="SetMinimum" />
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">minimum Number</p>
    <div class="inputbox">
          <CustomButton v-on:click="getMinimum()" text="GetMinimum" />
     </div>
     <div>
     <p>{{minimumNumber}}</p>
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Admin</p>
    <div class="inputbox">
          <CustomButton v-on:click="getAdmin()" text="GetAdmin" />
     </div>
     <div>
     <p>{{admin}}</p>
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Panther Account</p>
    <div class="inputbox">
          <CustomButton v-on:click="getPantherAccount()" text="GetPanther" />
     </div>
     <div>
     <p>{{panther}}</p>
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Total Addresses</p>
    <div class="inputbox">
          <CustomButton v-on:click="getTotalAddresses()" text="Get TotalAddresses" />
     </div>
     <div>
     <p>{{totalAddress}}</p>
     </div>
</div>

<div  id= "card" class="card">
    <p class="unlock_wallet_text">Total Amount</p>
    <div class="inputbox">
          <CustomButton v-on:click="getTotalAmount()" text="Get TotalAmount" />
     </div>
     <div>
     <p>{{totalAmount}}</p>
     </div>
</div>

</template>
<script>
import CustomButton from "../buttons/custombutton.vue";
import BEP20 from '../../abi/BEP20'
import Lottery from '../../abi/Lottery'
import Web3 from 'web3'
export default {
  name: "AdminUnlockWallet",
  components: {
    CustomButton
  },
  data(){

  return{
     numInput:0,
     admin_token:0,
     first_number:0,
     second_number:0,
     third_number:0,
     fourth_number:0,
     maxNumber:'',
     minimumNumber:0,
     claim_reward:0,
     admin:'',
     panther:'',
     totalAddress:0,
     totalAmount:0,
    testnet:`https://bsc-dataseed1.binance.org:443`,
    web3 : new Web3(Web3.givenProvider|| new Web3.providers.HttpProvider(this.testnet)),
    lottery : "0x8bcdbA0F4fbb5A7bD1C897317db127a9c0b6d949",
    bep:"0x549A17EA726EC949E657d731D1707160788b5f02"
  };
  },
  methods: {

  claimReward:async function()
  {
const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{

  methods.claimReward(this.claim_reward).send({
      from: addresses[0],
      gas: 2100000,
      gasPrice: "210000",
    })
  });

  
  },

  minimum: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{

  methods.setMinPrice(this.minimumNumber).send({
      from: addresses[0],
      gas: 37391,
      gasPrice: "10000000000",
    })
  });
  },

   getMinimum: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  methods.minPrice().call().then(data=>this.minimumNumber=data);


  },


  getAdmin: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  methods.owner().call().then(data=>this.admin=data);
  },

  getPantherAccount: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  methods.panther().call().then(data=>this.panther=data);
  },

  getTotalAddresses: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  methods.totalAddresses().call().then(data=>this.totalAddress=data);
  },

  getTotalAmount: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  methods.totalAmount().call().then(data=>this.totalAmount=data);
  },

  sendAdmin: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;

  this.web3.eth.getAccounts().then(async addresses=>{

  methods.adminWithdraw(this.admin_token).send({
     from: addresses[0],
      gas: 42187,
      gasPrice: "10000000000",
    })
  });
  },


setMaxNumber: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{
  methods.setMaxNumber(this.maxNumber).send({
      from: addresses[0],
      gas: 2100000,
      gasPrice: "210000",
    })
  });
  },


  draw: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{

  methods.drawing(this.numInput).send({
      from: addresses[0]
    })
  });
},

reset: async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{

  methods.reset().send({
      from: addresses[0]
    })
  });
},


participate:async function()
  {
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{
  methods.buy(10000,[this.first_number,this.second_number,this.third_number,this.fourth_number]).send({
      from: addresses[0],
      gas: 2100000,
      gasPrice: "210000",
    })

  });
  },

enterDrawingPhase: async function()
{
  const methods = await new this.web3.eth.Contract(Lottery.abi,this.lottery).methods;
  this.web3.eth.getAccounts().then(async addresses=>{
  methods.enterDrawingPhase().send({
      from: addresses[0]
    })

  });
},



approve: async function()
  {
const methods = await new this.web3.eth.Contract(BEP20.abi,this.bep20).methods;
this.web3.eth.getAccounts().then(async data=>{
await methods
    .approve(this.lottery, 1000000) // hydrolottery hashcode
    .send({
        from: data[0],
        gas: 210000,
        gasPrice: "21000",
      })
}); }}
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

.card{
margin-bottom:2rem;
}
</style>