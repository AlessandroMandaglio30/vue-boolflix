<template>
  <div>
    <section class="film">
      <Card v-for="(films, i) in film" :key="i" :films="films" />
    </section>
    <section class="series">
      <Card v-for="(films, i) in series" :key="i" :film="films" />
    </section>
  </div>
</template>

<script>
import Card from "../commons/Card.vue";
export default {
  name: "CardContainer",
  components: {
    Card,
  },
  props: {
    film: Array,
    series: Array,
  },
};
</script>

<style>
</style>