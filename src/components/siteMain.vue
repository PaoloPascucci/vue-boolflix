<template>
  <div>
    
      <button type="button">Submit</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
        data(){
    return {
      Movies: [],
      }
      },
  mounted() {
      setTimeout(this.Callapi, 1000)
;
  },
  methods: {

   Callapi(){
           axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.Movies = response.data.response;
      })
   },
}}
</script>

<style>
div{
    height: 100vh;
}
button{
    text-align: center;
    width: 100px;
    height: 100px;
}
</style>