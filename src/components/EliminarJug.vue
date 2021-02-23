<template>
<!--- En esta template, se muestra un selector de jugadores para eliminar de la base de datos.-->
    <div class="eliminar">

        <select v-model="name">

            <option :value="jug.name" v-for="(jug, nn) in todos" :key="nn">{{jug.name}}</option>
        </select>
    </div>
</template>

<script>
import axios from 'axios'
export default {
        /*Se declara el modelo de datos, los métodos y un watcher para recueprar la información de los jugadores filtrado por el equipo. .*/ 

    data(){
        return{
            todos:[],
            name:''
        }
    },
    props:[
        "nombreEquipo"
    ],
    methods:{
        recuperarJugador(nombre){

            
            axios.get("http://localhost:3000/players?team=" + nombre)//llamada a la api
            .then(response =>{
            this.todos = response.data;
            } )
        .catch(response =>  console.log("Execepcion lanzada"));
     } 
        },
        watch:{
            nombreEquipo(nuevo){ 
                this.todos = this.recuperarJugador(nuevo);
        }
    }
}
</script>

<style scoped>

</style>