<template>
  <div id="content-rick">
      <img :src="src" alt="imagen" class="">
      <div class="text">
      <h3 class="title">{{name}}</h3>

      </div>
  </div>
</template>

<script>
export default {
name:"Character",
props:{
    src: String,
    name: String

},
}
</script>

<style lang="scss" scoped>
#content-rick{
    display: flex;
  justify-content: space-around;
  align-items: center;
}
img{
    width: 250px;
    margin: 50px 0px ;
    border-radius: 50%;
}
.text{
    width: 800px;
    display: flex;
    justify-content: start;
    h3{
        font-size: 50px;
    }
}



</style>