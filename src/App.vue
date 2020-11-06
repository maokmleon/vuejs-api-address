<template>
  <div>
    <input type="text" v-model="zip" />
    <button @click="getAddress">検索</button>
    <p>住所: {{ address }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zip: "",
      address: ""
    };
  }, 
  methods: {
    getAddress() {
      axios.get(
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.zip}?apiKey=ZuHHHbCNtHydbD2UIIvJ3QYPgtzXSao4QYQWj5M`
        )
          .then((res) =>{
          console.log(res),
          this.zip = res.data.[0].postcode,
          this.address = res.data[0].allAddress;
        }
      );
    }
  },
  computed:{
    
  }
};
</script>

