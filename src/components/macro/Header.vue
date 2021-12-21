<template>
  <header>
    <div class="container-header">
      <div>
        <img :src="require('../../assets/img/logo.png')" alt="logo-boolflix" />
      </div>
      <div>
        <input type="text" v-model="searchFilm" />
        <button @click="$emit('ricerca', searchFilm)">Cerca</button>
      </div>
    </div>
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

<style lang="scss" scoped>
header {
  height: 60px;
  background-color: #000;
  .container-header {
    height: 100%;
    width: 95%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    img {
      width: 150px;
    }
    input {
      margin-right: 10px;
      border-radius: 10px;
      border: none;
      padding: 5px;
    }
    button {
      padding: 5px;
      border-radius: 10px;
      border: none;
      text-align: center;
      cursor: pointer;
    }
  }
}
</style>