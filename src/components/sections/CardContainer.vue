<template>
  <div class="container-card">
    <h4>LE TUE RICERCHE PER FILM:</h4>
    <section class="film">
      <Card
        v-for="(films, i) in filmsOrderByPopularity"
        :key="i"
        :films="films"
      />
    </section>
    <h4>LE TUE RICERCHE PER SERIE:</h4>
    <section class="series">
      <Card
        v-for="(films, i) in seriesOrderByPopularity"
        :key="i"
        :films="films"
      />
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
  computed: {
    filmsOrderByPopularity() {
      const films = this.film;
      return films.sort((a, b) => {
        return b.popularity - a.popularity;
      });
    },
    seriesOrderByPopularity() {
      const seriesTv = this.series;
      return seriesTv.sort((a, b) => {
        return b.popularity - a.popularity;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.container-card {
  width: 90%;
  margin: 10px auto;
  .film,
  .series {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    text-align: center;
  }
  h4 {
    font-size: 30px;
  }
}
</style>