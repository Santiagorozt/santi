<template>
    <div class="partido">
        <form class="formulario">
            <fieldset>
                <legend>Introduzca los datos para un nuevo partido</legend>


                <select class="local" v-model="equ1">
                    
                    <option v-for="(jugadoressss, nn) in array" :key="nn">{{jugadoressss.name}}</option>


                </select><br><br>


                <select class="visitante" v-model="equ2">
                    
                    <option v-for="(jugadoressss, nn) in array" :key="nn">{{jugadoressss.name}}</option>

                </select><br><br>



                <input class="fecha" type="date" v-model="date"><br><br>
                <input class="jornada" type="text" placeholder="Jornada" v-model="round"><br><br>
                <button @click="form()" class="boton">pulse</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            array:[],
            round:'',
            date:'',
            team1:'',
            team2:''
        }
    },
    created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    methods:{
    form(){
        let post = {
            round:this.round,
            date:this.date,
            equ1:this.equ1,
            equ2:this.equ2
        };
        axios.post("http://localhost:3000/matches", post)
    },
    }
}
</script>

<style scoped>
body{
    color: rgb(243, 200, 145);
}
fieldset{
    
    background-color: rgba(231, 177, 59, 0.459);
}
.jornada{
          text-align: center;
    }
legend{
    font-size: 50px;
}
.formulario{

    
    margin-right: 500px;
        
}
.boton{
    text-align: center;
}
.local{
    text-align: center;
}
.visitante{
    text-align: center;
}
    
    .fecha{
          text-align: center;
    }
    
</style>