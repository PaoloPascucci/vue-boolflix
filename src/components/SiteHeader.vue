<template>
<div class="header">
        <input type="search" name="Movie" id="Movie" placeholder="cerca qui i film" v-model="UserInput" />
        <button @click="$emit('search_film', UserInput)" type="button">Search</button>
</div>
</template>
<script>
export default {
    data(){
        return{
            UserInput:"",
        }
    }
}
</script>

<style>
.header {
  text-align: center;
}
</style>