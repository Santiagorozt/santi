<template>
<!-- En esta template se muestra una tabla con los elementos de los jugadores y también las funcionalidades de añadir goles y eliminar jugador
que realizan llamadas a métodos declarados en la sección script.-->
  <div class="clase">


      <table>


        <tr class="fila" v-for="(jugadores, nn) in array" :key="nn">
          <td @click="informacionJugador(jugadores.id,jugadores.name,jugadores.team,jugadores.scores)"> {{jugadores.name}}</td>
        </tr>


      </table>


        <div class="infoJ" v-if="name!=''"><!-- se caragara cuando se apriete sobre el  jugador del equipor  -->

            <ul v-for="(jugadores, nn) in array" :key="nn">
                <li>{{jugadores.name}}</li>
                <li>{{jugadores.team}}</li>
                <li>Goles: {{jugadores.scores}}</li>
            </ul>

            <input type="number" placeholder="numeroGoles" v-model="anadirGol">
            <button @click="jugadoresEqui()">Añadir goles</button><!-- metodos que se le pasan-->
            <button @click="eliminarJug()">Eliminar jugador</button>

        </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    /*Se declara el modelo de datos, los métodos y un watcher para recueprar la información de los jugadores filtrado por un criterio que llega en la llamada al método. .*/ 
  data(){
    return{
      array:[],

      id:'',

      name:'',

      team:'',

      scores:'',

      anadirGol:''
    }
  },
   props:[

     "nombreEquipo"

   ],
   watch:{

        nombreEquipo(nuevo){ 

            this.array = this.descript(nuevo);
        }
    },
   methods:{
     descript(nombreEquipo){

        axios.get('http://localhost:3000/players?team=' + nombreEquipo)

        .then(response =>{

          this.array = response.data;

        } )
        .catch(response => alert("Errores: " + response.status));
     },
    informacionJugador(id,name,team,scores){

        this.id = id;

        this.name = name;

        this.team = team;

        this.scores = scores;

    },     
     jugadoresEqui(){
         let post = {

            id:this.id,

            name:this.name,

            team:this.team,


            scores: parseInt(this.scores) + parseInt(this.anadirGol)
        };
        axios.put("http://localhost:3000/players/" + this.id, post)
     },
     eliminarJug(){

        axios.delete("http://localhost:3000/players" + this.id);
     }
   }
};
</script>


<style scoped>
    .clase{

        float: right;
  background-color: burlywood;
        margin-right: 500px;
    }
    .infoJ{
     font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif; 
    
    background-color: brown;
    margin-right: 50%;
}
legend{
    font-size: 50px;
}

    
</style>