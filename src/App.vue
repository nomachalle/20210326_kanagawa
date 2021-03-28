<template>
  <div id="app">
    <div id="adress">
      <input type="number" v-model="postcode">
      <button class="button" @click="inputAddress">住所自動入力</button>
    </div>
    <div id="result">
      <p>Address : </p>
      <p>{{showAddress}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      postcode:'',
      showAddress:'',
    };
  },
  methods: {
    async inputAddress(){
      await axios.get(
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?apikey=D7Z47W2ExYtYvjGRVc6pmORmb3VZOyBYMJ98Qcz`
        ).then((response) => {
          this.showAddress = response.data[0].allAddress;
        })
    }
  }
}
</script>

<style>
#app {
  margin: 10px;
}
.button {
  margin-left: 5px;
  border-width: 1px;
  border-radius: 20px;
}
.button:hover {
  color: #aaa;
  cursor: pointer;
}
#result {
  display: flex;
}
#result p:nth-child(2) {
  margin: auto 10px;
}


</style>