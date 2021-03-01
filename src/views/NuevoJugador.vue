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
    }// toda la funcionalidad la va a tener el componente
}
</script>

<style scoped>
.boton{
     float: left;
}
.equipo{
    float: left;
}
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

.goles{
    float:left;
}

legend{
    font-size: 50px;
}
    
</style>