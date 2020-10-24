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
      let api = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipCode}?apiKey=mAsjDYpxxtqT7S33f7RegxyCMK4VXBFLrqJxPbd`);
      this.data = api.data;
      this.address = this.data[0].allAddress;
    }
  }
};

</script>

<style>

</style>

