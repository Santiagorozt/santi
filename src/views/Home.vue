<template>
  <div class="inicio">
    <img alt="laLiga" src="https://elporvenir.blob.core.windows.net.optimalcdn.com/images/2020/09/04/liga.jpg">



    <Inicio mensaje="Temporada 2020-2021 /// patrocinada por Santi"/>
  </div>
</template>

<script>

import Inicio from '@/components/Inicio.vue'
export default {
  name: 'Home',
  components: {
    Inicio
  }
}
</script>

<style scoped>
  img{
    width: 1200px;
    height: 800px;
  }
</style>
