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
  text-align: center;
  background-color: #2c3e50;
}
</style>
