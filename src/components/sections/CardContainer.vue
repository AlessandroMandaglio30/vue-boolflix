<template>
  <div>
    <input type="text" v-model="searchFilm" />
    <button @click="ricerca">Click</button>
    <Card v-for="(films, i) in film" :key="i" :films="films" />
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
    },
  },
};
</script>

<style>
</style>