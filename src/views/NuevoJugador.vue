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
    margin-top: 10%;
    background-color: brown;
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
    
</style>