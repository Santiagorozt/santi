<template>
    <div class="clasif">


      <h1 class="portada">futbolistas</h1>


        <table class="table">

            <tr class="filas" v-for="(jugadores, nn) in array" :key="nn" >
                <td> <button @click="nomb(jugadores.name)"> {{jugadores.name}} </button></td>
            </tr>

        </table>



    </div>

    <div class="componente">


        <JugadoresComponent :nombreEquipo="variable"></JugadoresComponent>
    </div>
</template>

<script>


import JugadoresComponent from '@/components/JugadoresComponent.vue'

import axios from "axios";
export default {


    data(){
        return{
            array:[],
            variable: '',
            id:'',
            team:'',
            scores:''
        }
    },
    created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    name: 'Clasificacion',

    methods:{

        nomb(datos){

            this.variable = datos;
        }
    },
    components:{
        JugadoresComponent
    }
}
</script>

<style scoped>
    .clasificacion{
        margin-right: 700px;
    }
</style>
