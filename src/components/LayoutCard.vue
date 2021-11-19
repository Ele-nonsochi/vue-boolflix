<template>
  <div>
    <div class="nav-bar">
      <h1>BOOLFLIX</h1>
      <NavBar @choiceAdd="searchSelection"></NavBar>
    </div>
    <main>
      <Card :film="movies" :series="series" :countryFlag="flags" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import NavBar from "./NavBar.vue";
import Card from "./Card.vue";

export default {
  name: "LayoutCard",
  components: {
    NavBar,
    Card,
  },

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3",
      apiKey: "101bdb8aeb0a4c2dc51b37e2fefe850c",
      movies: [],
      series: [],
      pickMedia: "",
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

    searchSelection(choiceAdd) {
      this.pickMedia = choiceAdd;
      this.searchType("/search/movie", this.pickMedia, "movies");
      this.searchType("/search/tv", this.pickMedia, "series");
    },
  },

  mounted() {},
};
</script>

<style lang="scss">
.nav-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 70px;
  padding: 20px 30px;
  background-color: #040404;
  h1 {
    color: red;
  }
}
</style>