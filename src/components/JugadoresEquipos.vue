<template>
<!--- En esta template, se renderiza una tabla de jugadores.-->
    <div class="jug">
        <table>
            <tr class="tdd" v-for="(players, index) in jugadores" :key="index">
                <td> {{players.name}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    /* Se declara el objeto que recoge la información de los jugadores, así como las llamadas a la API para recueprar la información. */

    data(){
        return{
            jugadores:[],
            nombre: '',
            name: '',
            scores: ''
        }
    },
    props:[
      "nombreJugadores"
    ],
     created(){
        axios.get('http://localhost:3000/players?team=' + this.nombreJugadores)
        .then(response =>{
            this.jugadores = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    envioJugadores(){
        let post = {
            nombre: this.nombre,
            name: this.name,
            scores: this.scores
        };
        axios.post("http://localhost:3000/players?team", post)
    },
    name: 'JugadoresEquipos',
}
</script>

<style scoped>

</style>