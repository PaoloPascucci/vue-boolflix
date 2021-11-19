<template>
<div>
    <div class="header">
    <Search :filmSearch="searchText" @search_film="UserInput"/>
    <div class="containerr">
    <movie
    v-for="movie in movies" :key="movie.id" >
    <h3>{{movie.title}}</h3>
    <p class="orT">{{movie.original_title}}</p>
    <p id="orL">{{movie.original_language}}</p>
    <flag :iso="movie.original_language" />
    <p class="Va">{{movie.vote_average}}</p>
    </movie>
      
    </div>
</div>
</div>
  
</template>

<script>
import axios from "axios";
import Search from"./Search.vue"
export default {
    components: {
        Search,
        
    },
  data() {
    return {
      movies: [],
      searchText:"",
    };
  },
  methods: {
    UserInput(text) {
        this.searchText = text
      axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=3281705aad86751855ca2a484ec980fb&query=${this.searchText}`)
        .then((response) => {
          this.movies = response.data.results;
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
.containerr{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
movie{
    padding:1rem
}
h3{
    color :white;
}
.orT, #orL, .Va{
    font-weight: bold;
}
#orL{
    color: greenyellow;
}
.Va{
    color :red;
}

</style>