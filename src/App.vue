<template>
  <div id="app">
    <div v-for="(personaje, i) in personajes" :key="i" class="contenido">

    <Character :src="personaje.picture" :name="personaje.nombre" />

    </div>
  </div>
</template>

<script>
import Character from "./components/Character";
export default {
  name: "App",
  data() {
    return {
      personajes: [],
    };
  },
  components: {
    Character,
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character/?page=9")
      .then((response) => response.json())
      .then((json) => {
        let data = json.results;

        data.forEach((el) => {
          let nombre = el.name;
          let picture = el.image;

          this.personajes.push({ nombre, picture });
        });
      })
      .catch((err) => {
        console.log(`todo esta perdido rick: ${err}`);
      });
  },
};
</script>

<style lang="scss" scoped>
#app{
  background-image: url('https://rickandmortypod.com/wp-content/uploads/2018/11/cropped-RM_page-header_background1-3.png');
  background-repeat: no-repeat;
  background-position: cover;
  background-attachment: fixed;
  color: white;
  margin: 0px;
  padding: 0px;
}


</style>
