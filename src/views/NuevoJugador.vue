<template>
    <div class="nuevoJugador">
        <NuevoJugadorrr></NuevoJugadorrr>
    </div>
</template>

<script>
import NuevoJugadorrr from '@/components/NuevoJugadorrr'
export default {
    components:{
        NuevoJugadorrr
    }
}
</script>

<style scoped>
fieldset{
    margin-top: 0%;
    background-color: rgba(231, 177, 59, 0.459);
}
legend{
    font-size: 50px;
}
.nombre{
        float: left;
}
.equipo{
    float: left;
}
.goles{
    float:left;
}
.boton{
     float: left;
}
legend{
    font-size: 50px;
}
    
</style>