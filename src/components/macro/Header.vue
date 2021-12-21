<template>
  <header>
    <input type="text" v-model="searchFilm" />
    <button @click="$emit('ricerca', searchFilm)">Click</button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchFilm: "",
    };
  },
};
</script>

<style>
</style> 