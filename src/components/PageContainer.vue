<template>
  <div class="container">
  <nav class="nav-bar">
   <div class="nav-item">
        <input v-model="choiceAdd" type="text" placeholder="Find Movie and TvSeries">
        <button @click="searchSelection">START</button>
  </div> 
  </nav>
  <!--Stampo i film-->
  <div>
  <h1>FILM</h1>
  <ul>
  <li v-for="movie in movies" :key="movie.id">
        <span>Title:</span> {{ movie.title }} <br />
        <span>Original title:</span> {{ movie.original_title }} <br />
        <span>Language:</span>
        <img :src="require(`@/assets/img/countryFlag ${CountryFlag[movie.original_language]}`)" alt="img"/>
        {{ movie.original_language }} <br />
        <span>Vote:</span> {{ movie.vote_average }} <br />
      </li>
  </ul>
  </div> 
  <div>
  <h1>FILM</h1>
  <ul>
  <li v-for="movie in movies" :key="movie.id">
        <span>Title:</span> {{ movie.title }} <br />
        <span>Original title:</span> {{ movie.original_title }} <br />
        <span>Language:</span>
        <img :src="require(`@/assets/img/countryFlag ${CountryFlag[movie.original_language]}`)" alt="img"/>
        {{ movie.original_language }} <br />
        <span>Vote:</span> {{ movie.vote_average }} <br />
      </li>
  </ul>
  </div> 
 </div>
</template>

<script>
import axios from "axios";
//import Card from "./Card.vue";

export default {
  name: "PageContainer",
  components: {
       //Card ,
       },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3",
      apiKey: "101bdb8aeb0a4c2dc51b37e2fefe850c",
      movies: [],
      series: [],
      choiceAdd: "",
      countryFlag:{
          en: "./img/uk.png",
          it: "./img/italy.png",
          es: "./img/spain.png",
          de: "./img/german.png",
          ja:"./img/japan.png",
          chn: "./img/china.png",
       },
    };
  },
  methods: {
   searchType(url, textQuery, dataKey) {
      axios
        .get(this.apiUrl + url, {
          params: {
            api_key: this.apiKey,
            query: textQuery,
            language: "en",
          },
        })
        .then((el) => {
          this[dataKey] = el.data.results;
        });
    },

    searchSelection(){
    this.searchType("/search/movie", this.choiceAdd, "movie");
      this.searchType("/search/tv", this.choiceAdd, "movie");

    },
  },
   mounted() {
   
  }, 
};
</script>

<style lang="scss">
.container{
    background-color:grey;
    height: 800px;
    .nav-bar{
        background-color:black;
        height:80px;
        .nav-item{
             text-align: center;
             padding-top:20px;
        }
    }
}


</style>