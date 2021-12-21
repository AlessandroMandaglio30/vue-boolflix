<template>
  <div id="app">
    <Header @ricerca="ricerca" />
    <Main :film="film" :series="series" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/macro/Header.vue";
import Main from "./components/macro/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      film: [],
      series: [],
    };
  },
  methods: {
    ricerca(payload) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "792a0b569103cf3befd0baf28b152492",
            query: payload,
            language: "it-IT",
          },
        })
        .then((response) => {
          console.log(response.data.results);
          this.film = response.data.results;
          console.log(this.film);
        })
        .catch(function (error) {
          console.log(error);
        });
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "792a0b569103cf3befd0baf28b152492",
            query: payload,
            language: "it-IT",
          },
        })
        .then((response) => {
          console.log(response.data.results);
          this.series = response.data.results;
          console.log(this.series);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/global.scss";
</style>
