<template>
  <div class="Cont"> 
    <SiteHeader :filmSearch="searchText" @search_film="UserInput" />
          <div class="containerr">
        <h2>Film</h2>
        <div class="movie">
          <div class="UserMovie" v-for="movie in movies" :key="movie.id">
            <div v-if="movie.poster_path !=null">
            <img :src="`https://image.tmdb.org/t/p/w185/${movie.poster_path}`" :alt="movie.title">
            </div>
            <div v-else>
              <img height=278px width="185px" :src="'https://http.cat/204'" :alt="movie.title">
            </div>
            <h3>{{ movie.title }}</h3>
            <p class="orT">{{ movie.original_title }}</p>
            <flag :iso="movie.original_language"/>
            <div class="star">
            <div v-for="Star in parseInt((movie.vote_average / 2).toFixed(0))" :key="Star.id">
            <i class="fas fa-star"></i>
            </div>
            <div v-for="emptyStar in parseInt(5 - (movie.vote_average / 2).toFixed(0))" :key="emptyStar.id">
            <i class="far fa-star"></i>
            </div>
            </div>
          </div>
        </div>
        <h2>Serie TV</h2>
        <div class="show">
          <div class="UserShow" v-for="show in shows" :key="show.id">
              <div v-if="show.poster_path !=null">
                <img :src="`https://image.tmdb.org/t/p/w185/${show.poster_path}`" :alt="show.title">
            </div>
            <div v-else>
              <img height=278px width="185px" :src="'https://http.cat/204'" :alt="show.title">
              </div>
            <h3>{{show.name}}</h3>
            <p class="orT">{{ show.original_name }}</p>
            <flag :iso="show.original_language" />
            <div class="star">
            <div v-for="Star in parseInt((show.vote_average / 2).toFixed(0))" :key="Star.id">
            <i class="fas fa-star"></i>
            </div>
            <div v-for="emptyStar in parseInt(5 - (show.vote_average / 2).toFixed(0))" :key="emptyStar.id">
            <i class="far fa-star"></i>
            </div>
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
import axios from "axios";
import SiteHeader from "./components/SiteHeader.vue";
export default {
  components:{
    SiteHeader,
  },
  data() {
    return {
      movies: [],
      shows: [],
      searchText: "",
      http: "",
      
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

ul {
  list-style: none;
}
.containerr {
  display: flex;
  flex-direction: column;
  text-align: center;
}
.movie,
.show {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-self: center;
  width: 80%;
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
.UserMovie,
.UserShow {
  padding: 1rem;
  width: 200px;
}
.star{
  display: flex;
  flex-direction: row;
  justify-content: center;
}
i{
  color: #ffd43b
}
</style>