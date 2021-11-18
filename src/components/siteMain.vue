<template>
<div>
    <div class="header">
    <Search :filmSearch="searchText" @search_film="UserInput"/>
    <movie
    v-for="movie in Movies"
    :key="movie.id"
    title="movie.title"
    original="movie.original_title"
    language="movie.original_language"
    vote="movie.vote_average"
     />
</div>
</div>
  
</template>

<script>
import axios from "axios";
import Search from"./Search.vue"
export default {
    components: {
        Search
    },
  data() {
    return {
      Movies: [],
      searchText:"",
    };
  },
  methods: {
    UserInput(text) {
        this.searchText = text
      axios
        .get(`https://api.themoviedb.org/3/movie?api_key=2a36e3808dc852382706a41d635e3434e&query=${this.searchText}`)
        .then((response) => {
          this.Movies = response.data.results;
        });
    },
  },
};
</script>

<style>
.header {
  height: 100px;
  text-align: center;
}
ul{
    list-style: none;
}
</style>