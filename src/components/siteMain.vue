<template>
  <div class="Cont"> 
    <div class="header">
      <Search :filmSearch="searchText" @search_film="UserInput" />
      <div class="containerr">
        <h2>FIlm</h2>
        <div class="movie">
          <movie v-for="movie in movies" :key="movie.id">
            <h3>{{ movie.title }}</h3>
            <p class="orT">{{ movie.original_title }}</p>
            <flag :iso="movie.original_language" />
            <p class="Va">{{ movie.vote_average }}</p>
          </movie>
        </div>
        <h2>Serie TV</h2>
        <div class="show">
          <show v-for="show in shows" :key="show.id">
            <h3>{{show.title}}</h3>
            <p class="orT">{{ show.original_title }}</p>
            <flag :iso="show.original_language" />
            <p class="Va">{{ show.vote_average }}</p>
          </show>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./Search.vue";
export default {
  components: {
    Search,
  },
  data() {
    return {
      movies: [],
      shows: [],
      searchText: "",
    };
  },
  methods: {
    UserInput(text) {
      this.searchText = text;
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=3281705aad86751855ca2a484ec980fb&query=${this.searchText}`
        )
        .then((response) => {
          this.movies = response.data.results;
        });
      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=3281705aad86751855ca2a484ec980fb&query=${this.searchText}`
        )
        .then((r) => {
          this.shows = r.data.results;
        });
    },
  },
};
</script>

<style>
h2 {
  margin: 1rem;
}
.header {
  text-align: center;
}
ul {
  list-style: none;
}
.containerr {
  display: flex;
  flex-direction: column;
}
.movie, .show{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-self: center;
  width: 80%;
}
movie {
  padding: 1rem;
}
.orT,
#orL,
.Va,
h3 {
  font-weight: bold;
}
#orL {
  color: greenyellow;
}
.Va {
  color: red;
}
</style>