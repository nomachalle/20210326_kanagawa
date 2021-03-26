<template>
  <div id="app">
    <div id="adress">
      <input type="number" v-model="postNumber">
      <button class="button" @click="inputAdress">住所自動入力</button>
    </div>
    <div id="result">
      <p>Address : </p>
      <p>{{showAdress}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      postNumber:'',
      showAdress:'',
    };
  },
  methods: {
    inputAdress(){
      //関数内にaxiosを使用してAPIを叩く処理を記述する。
      //APIのURLは「エンドポイント/postcode/パスパラメータ?クエリパラメータ」
      axios.get('https://apis.postcode-jp.com/api/v4/postcodes/1000001?apikey=D7Z47W2ExYtYvjGRVc6pmORmb3VZOyBYMJ98Qcz')
      //showAdressに住所を表示する。
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