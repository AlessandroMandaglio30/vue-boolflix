<template>
  <div>
    <ul v-if="this.films.vote_average > 0">
      <li v-if="films.backdrop_path == null">
        <img
          src="http://www.persefone.it/blog/wp-content/themes/photobook/images/blank.png"
          :alt="films.title || films.name"
        />
      </li>
      <li v-else-if="films.backdrop_path">
        <img
          :src="'https://image.tmdb.org/t/p/w342/' + films.backdrop_path"
          :alt="films.title || films.name"
        />
      </li>
      <div class="testo-card">
        <li>
          <span>Titolo: </span>
          <p>{{ films.title || films.name }}</p>
        </li>
        <li>
          <span>Voti: </span><br />
          <div
            class="star"
            v-for="index in votos(films.vote_average)"
            :key="index"
          >
            <i class="fas fa-star"></i>
          </div>
        </li>
        <li><span>Lingua: </span>{{ bandiera() }}</li>
      </div>
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
    votos(voto) {
      return (voto = Math.ceil(voto / 2));
    },
  },
};
</script>

<style lang="scss" scoped>
ul {
  list-style: none;
  padding: 0;
  position: relative;
  width: calc((100% / 8) - 10px);
  margin: 10px;
  img {
    height: 300px;
    width: 200px;
    object-fit: cover;
    border: 1px solid;
  }
  .star {
    display: inline-block;
    color: yellow;
  }
}
.testo-card {
  display: none;
  padding: 5px;
  position: absolute;
  color: white;
  top: 0;
  left: 0;
  text-align: center;
  span {
    text-transform: uppercase;
    font-weight: bold;
  }
}

ul:hover {
  img {
    opacity: 0.1;
  }

  .testo-card {
    display: block;
  }
}
</style> 