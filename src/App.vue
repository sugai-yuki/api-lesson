<template>
  <div id="app">
    <input type="text" v-model="zipCode">
    <button>住所自動入力</button>
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
  async created(){
     let api = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes?filter=postcode==2790031&apiKey=(apikey)`);
     this.data = api.data;
     this.address = this.data.allAddress;
  }
};

</script>

<style>

</style>
