<template>
<div>
      <div class="main">
      <ul>
        <li>{{title}}</li>
        <li>{{original_title}}</li>
        <li>{{original_language}}</li>
        <li>{{vote_average}}</li>
      </ul>
    </div>
</div>
</template>

<script>
export default {
  props:{
    title:String,
    original_title:String,
    original_language:String,
    vote_average:String,
  }
}
</script>

<style>

</style>