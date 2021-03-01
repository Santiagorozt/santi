<template>
    <div class="equipos">
        <h1>Equipos</h1>
        <table>
            <tr class="tdd" v-for="(equi, index) in todosEquipos" :key="index">
                <td> {{equi.name}}
                    <span>
                        <ul class="lista" v-for="(jugadores, index) in todosJugadores" :key="index">
                            <li v-if="equi.name == jugadores.team"> {{jugadores.name}} </li>
                        </ul>
                    </span>
                </td>
            </tr>
        </table>
    </div>
    <button class="boton" @click="mostrarNuevo">Nuevo jugador</button>

    <div v-show="show">
        <NuevoJugadorrr/>
    </div>
</template>

<script>
import axios from "axios";
import NuevoJugadorrr from '@/components/NuevoJugadorrr.vue'
export default {
    data(){
        return{
            todosEquipos:[],
            todosJugadores:[],
            show:false
        }
    },
     created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.todosEquipos = response.data;
        } )
        .catch(response => alert("Errores: " + response.status)),
    
        axios.get('http://localhost:3000/players')
        .then(response =>{
            this.todosJugadores = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    components:{
      NuevoJugadorrr
    },
    methods:{
        mostrarNuevo: function(){
            this.show = !this.show;
        }
    }
}
</script>



<style scoped>
#equipos{
    margin-top: 0%;
}
td{
    border: red;
    background-color: rgba(231, 177, 59, 0.459);
}
button{
    margin-left: 10%;
}
</style>
