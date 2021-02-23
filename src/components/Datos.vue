<template>
  <!-- Esta template renderiza la tabla de jugadores con el nombre y el score-->
  <div class="contenido">
      <table>

        <tr class="fila" v-for="(jugador, nn) in datos" :key="nn">
          

          <td> {{jugador.name}}</td>
          <td>{{jugador.scores}}</td>
          
          
        </tr>
      </table>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  /*Se declara el modelo de datos, los métodos y un watcher para recueprar la información de la base de datos.*/ 
  data(){
    return{
      datos:[]
    }
  },
   props:[
     "nombreEquipo"
   ],
   watch:{
        nombreEquipo(nuevo){ 
            this.datos = this.recuperarInfo(nuevo);
        }
    },
   methods:{
     recuperarInfo(nombreEquipo){
        axios.get('http://localhost:3000/players?team=' + nombreEquipo)
        .then(response =>{
          this.datos = response.data;
        } )
        .catch(response =>  console.log("Execpcion lanzada"));
     }
   }
};
</script>

<style scoped>
</style>