<template>
  <div id="app">
    <input type="text" v-model="zipCode">
    <button @click="zipCodeChange()">住所自動入力</button>
    <p>Address：{{address}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default{
  data(){
    return{
      zipCode: "",
      address: "",
    };
  },
  methods: {
    async zipCodeChange() { 
      let api = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/1000001?apiKey=(apikey)`);
      this.data = api.data;
      this.address = this.data.allAddress;
    }
  }
};

</script>

<style>

</style>

