<template>
  <div id="app">
  <siteMain/>
  </div>
</template>

<script>
import siteMain from "./components/siteMain.vue" ;

export default {
  name: 'App',
  components: {
    siteMain
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
