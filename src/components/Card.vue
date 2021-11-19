<template>
  <main>
    <h2>FILM</h2>
    <div class="wrapped">
      <div class="card">
        <div v-for="movie in film" :key="movie.id">
          <img class="poster" :src="getImg(movie.poster_path)" alt="img" />
          <div class="overlay">
            <h5 class="title">Title: {{ movie.title }}</h5>
            <h5 class="title" v-if="movie.title !== movie.original_path">
              Original Title: {{ movie.original_title }}
            </h5>
            <span class="flag"
              >Language : <img :src="getFlag(movie.original_language)"
            /></span>
            <span class="title"
              >Vote:
              <i
                v-for="(number, i) in getVote(movie.vote_average)"
                :key="i"
                class="fa fa-star"
              ></i>
              <i
                v-for="(number, i) in 5 - getVote(movie.vote_average)"
                :key="i"
                class="fa fa-star-o"
              ></i>
            </span>
            <h5 class="overview">Plot: {{ movie.overview }}</h5>
          </div>
        </div>
      </div>
    </div>

    <h2>SERIES TV</h2>
    <div v-for="serie in series" :key="serie.id">
      <img class="poster" :src="getImg(serie.poster_path)" alt="img" />
      <div class="overlay">
        <h5>Title: {{ serie.name }}</h5>
        <h5 v-if="serie.title !== serie.original_path">
          Original Title: {{ serie.original_title }}
        </h5>
        <span>Language : <img :src="getFlag(serie.original_language)" /></span>
        <span
          >Vote:
          <i
            v-for="(number, i) in getVote(serie.vote_average)"
            :key="i"
            class="fa fa-star"
          ></i>
          <i
            v-for="(number, i) in 5 - getVote(serie.vote_average)"
            :key="i"
            class="fa fa-star-o"
          ></i>
        </span>
        <h5>Plot: {{ serie.overview }}</h5>
      </div>
    </div>
  </main>
</template>


<script>
export default {
  name: "Card",
  components: {},
  props: {
    film: Array,
    series: Array,
    flags: Object,
  },
  data() {
    return {
      countryFlag: {
        en: require("svg-country-flags/png100px/gb.png"),
        it: require("svg-country-flags/png100px/it.png"),
        es: require("svg-country-flags/png100px/es.png"),
        de: require("svg-country-flags/png100px/de.png"),
        default: "@/assets/world-map.png",
      },
    };
  },
  methods: {
    //Prendo l'immagine
    getImg(object) {
      const urlImg = "https://image.tmdb.org/t/p/";
      const imgSize = "w342";
      if (!object) {
        return "https://d994l96tlvogv.cloudfront.net/uploads/film/poster/poster-image-coming-soon-placeholder-no-logo-500-x-740_24946.png";
      }
      return urlImg + imgSize + object;
    },
    //Prendo la lingua/bandiera
    getFlag(countryLang) {
      if (!this.countryFlag[countryLang]) {
        return require("@/assets/world-map.png");
      }
      return this.countryFlag[countryLang];
    },
    //Voto stella
    getVote(number) {
      return Math.ceil(number / 2);
    },
  },
};
</script>

<style lang="scss">
@import "@/style/card.scss";
</style>