<template>
  <Cabecera></Cabecera>
  <header>
    <div class="d-flex justif">
      <div class="first-container d-flex gap-3 ">
      <i class="fa-solid fa-chevron-left text-center align-self-center"></i>
      <h2 class="fs-5 align-self-center m-0">Promociones activas</h2>
    </div>
    <div class="second-container d-flex gap-3">
      <label for="" class="p-1 px-5 bg-primary rounded bg-opacity-75 text-white">Crear slider</label>
      <label for="" class="p-1 px-5 rounded border">Previsualizar</label>
    </div>
    </div>
  </header>


    <Asidenav />

  <Work />




</template>

<script>
import HelloWorld from './components/Asidenav.vue'
import Cabecera from './components/Navbar.vue'
import Asidenav from './components/Asidenav.vue'
import Work from './components/Work.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Cabecera,
    Asidenav,
    Work
  }
}
</script>

<style>
body {
  padding-top: 5em;
  padding-left: 4.5em;
}


</style>
