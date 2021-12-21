<template>
  <div>
    <ul>
      <li>
        <img
          :src="'https://image.tmdb.org/t/p/w342/' + films.backdrop_path"
          :alt="films.title || films.name"
        />
      </li>
      <li>{{ films.title || films.name }}</li>
      <li>{{ films.original_title || films.original_name }}</li>
      <li>{{ bandiera() }}</li>
      <li>{{ films.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    films: Object,
  },
  methods: {
    bandiera() {
      if (this.films.original_language == "it") {
        return "\uD83C\uDDEE\uD83C\uDDF9";
      } else if (this.films.original_language == "us") {
        return "\uD83C\uDDFA\uD83C\uDDF8";
      } else if (this.films.original_language == "jp") {
        return "\ud83c\uddef\ud83c\uddf5";
      } else if (this.films.original_language == "es") {
        return "\uD83C\uDDEA\uD83C\uDDF8";
      } else if (this.films.original_language == "en") {
        return " 	\ud83c\udff4\udb40\udc67\udb40\udc62\udb40";
      } else {
        return this.films.original_language;
      }
    },
  },
};
</script>

<style>
</style> 