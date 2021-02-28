<template>
<!-- Se renderiza un formulario para insertar un nuevo jugador-->
    <div class="nuevoJugador">
        <form>
            <fieldset>
                <legend>Nuevo jugador</legend>
                <input  class="input nombre" type="text" placeholder="nombre jugador" v-model="name"><br><br>
                <input class="input equipo" type="text" placeholder="equipo" v-model="team"><br><br>
                <input class="input goles" type="number" placeholder="goles" v-model="scores"><br><br>
                <button class="boton" @click="datitos()">Enviar</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    /* Se declaran las variables que se recogen de la base de datos relativa a los jugadores, así como un método para enviar los datos y guardarlos en la base de datos */
    data(){
        return{
            name: '',
            team: '',
            scores: ''
        }
    },
    methods:{
        datitos(){
            let datosJugador = {
                name:this.name,
                team:this.team,
                scores: parseInt(this.scores)
            };
            axios.post("http://localhost:3000/players", datosJugador); 
        }
    },
}
</script>

<style scoped>
      fieldset{
      background-color: rgba(231, 177, 59, 0.459);   
       margin-right: 1100px;
      }
      legend{
    font-size: 50px;
}

</style>