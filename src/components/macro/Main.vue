<template>
  <main>
    <CardContainer :film="film" />
  </main>
</template>

<script>
import CardContainer from "../sections/CardContainer.vue";
export default {
  name: "Main",
  components: {
    CardContainer,
  },
  props: {
    film: Array,
    series: Array,
  },
};
</script>

<style>
</style>