<template>
  <div>
    <input type="text" v-model="searchFilm" />
    <button @click="ricerca">Click</button>
    <section class="film">
      <Card v-for="(films, i) in film" :key="i" :films="films" />
    </section>
    <section class="series">
      <Card v-for="(films, i) in series" :key="i" :films="films" />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import Card from "../commons/Card.vue";
export default {
  name: "CardContainer",
  components: {
    Card,
  },
  data() {
    return {
      film: [],
      series: [],
      searchFilm: "",
    };
  },
  methods: {
    ricerca() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "792a0b569103cf3befd0baf28b152492",
            query: this.searchFilm,
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
            query: this.searchFilm,
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

<style>
</style>