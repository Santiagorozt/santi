<template>
    <div class="eliminar">
        <form>
            <fieldset>
                <legend>Eliminar Jugador</legend>

                <select class="equip" v-model="name">

                    <option :value="equipos.name" v-for="(equipos, nn) in arrayEquipos" :key="nn">{{equipos.name}}</option>
                </select>

                    <EliminarJug class="jugador" :nombreEquipo="name"></EliminarJug>

                <button class="boton" @click="borrar()">Eliminar Jugador</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from "axios";

import EliminarJug from '@/components/EliminarJug.vue'

export default {
    data(){
        return{
            arrayEquipos:[],

            scores:'',

            arrayJugadores:[],

            team:'',

            id:'',
            
            name:''
            
            

        }
    },
    methods:{
        jugadores(){
            axios.get('http://localhost:3000/players')
            .then(response =>{
                this.arrayJugadores = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
        equipos(){
            axios.get('http://localhost:3000/clubs')
            .then(response =>{
                this.arrayEquipos = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
        
        borrar(){
            axios.delete("http://localhost:3000/players/" + this.id);
        }
    },
    created(){
            this.equipos();
            this.jugadores();
    },
    components:{
        EliminarJug
    }
}
</script>
<style scoped>
    .equipos{
        float: left;
        
    }
    .jugadores{
        float: left;
      
    }
    .boton{
        float: left;
       
    }
    fieldset{
    
    margin-right: 60%;
    background-color: rgba(231, 177, 59, 0.459);
}
legend{
    font-size: 50px;
}
</style>