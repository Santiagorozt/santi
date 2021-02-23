<template>
    <div class="equipos">
        <h1>Equipos de la liga </h1>


        <table>

            <tr class="tdd" v-for="(equipos, index) in arrayEquipos" :key="index">

                <td> {{equipos.name}}</td>


                <td><JugadoresEquipos :nombreJugadores ="equipos.name"/></td>
            </tr>
        </table>


        <button type="submit">Nuevo jugador</button>
    </div>
</template>

<script>
import axios from "axios";


import JugadoresEquipos from '@/components/JugadoresEquipos.vue'

export default {

    data(){

        return{
            arrayEquipos:[],
            variable: ''
        }
    },
     created(){
        axios.get('http://localhost:3000/clubs')

        .then(response =>{         // llamada a la api

            this.arrayEquipos = response.data;

        } )
        .catch(response => alert("Errores: " + response.status));
    },

    name: 'Equipos',


    components:{

      JugadoresEquipos
    }
}
</script>


<style scoped>
td{
    border: red;
    background-color: burlywood;
}
</style>
