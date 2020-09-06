<template>
  <div id="app">
    <!-- iteracion del contenido -->
    <div v-for="(personaje, i) in personajes" :key="i" class="contenido">
      <Character :src="personaje.picture" :name="personaje.nombre" />
    </div>
  </div>
</template>

<script>
//importando componente de character
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
    //llamada de la api rick and morty
    fetch("https://rickandmortyapi.com/api/character/?page=9")
      .then((response) => response.json())
      .then((json) => {
        let data = json.results;
        //iterando el llamado a la api para extraer nombre e imagen
        data.forEach((el) => {
          let nombre = el.name;
          let picture = el.image;
          //enviando la carga y data al array en data
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
// configuracion de lo impreso en pantalla de la data solicitada
#app {
  background-image: url("https://rickandmortypod.com/wp-content/uploads/2018/11/cropped-RM_page-header_background1-3.png");
  background-repeat: no-repeat;
  background-position: cover;
  background-attachment: fixed;
  color: white;
  margin: 0px;
  padding: 0px;
}
</style>
